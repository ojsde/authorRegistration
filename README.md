Key data
============

- name of the patch: Registration as author
- author: Felix Gründer
- current version: 1.0.0.0
- tested on OJS version: 2.4.6
- github link: https://github.com/ojsde/authorRegistration.git
- community plugin: no
- date: 25.5.2016

Description
============

When a user wants to register as author, it can easily happen that the "register as author" checkbox is overlooked. Thus this checkbox is actived automatically when the user is likely to be an author - that means if the user gets to the registration form via the "about/submission" or the "information/authors" page.

Installation
============

This is a minor patch - it's just necessary to add this code snippet 

		$referrer = (isset($_SERVER['HTTP_REFERER']) ? $_SERVER['HTTP_REFERER'] : null);
		$authorPattern = '/information\/authors|about\/submissions/';
		if (preg_match($authorPattern, $referrer)) {
			$this->setData('registerAsAuthor', 1);
		}

to the following file

		classes/user/form/RegistrationForm.inc.php

to the function

		initData()
		
right after this line:

		$this->setData('registerAsReader', 1);
