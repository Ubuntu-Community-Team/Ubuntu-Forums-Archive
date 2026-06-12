---
title: "Why is there no Joomla package?"
date: 2007-05-18
forum: General Help
---

### Post by johann_p on 2007-05-18
I am a bit surprised that [Joomla](http://www.joomla.org/) CMS does not seem to be included in the Ubuntu package repositories?

Any opinions about why it isn't included and whether it should be included?

---

### Post by scaine on 2007-05-18
I was about to say, "of course not, a cms is just a website - why would it be packaged?", but I've just (luckily for my dignity) checked and discovered that Typo3, Zope and Drupal are all packaged.

I'm afraid I don't have an explanation as to why you can get Drupal, and not Joomla, Mambo, Xoops, Nucleus, or any of the [other myriad cms's]("http://www.opensourcecms.com/").

I don't know a huge amount about it, but my web host uses the [Fantastico]("http://en.wikipedia.org/wiki/Fantastico_(web_hosting)") scripts to automate the deployment of a massive number of cms, galleries and other tools for websites.  Hmm - just checked my own link wikipedia there - Fantastico is commercial software and has come under some fire in certain quarters for deploying un-secured cms's!

Looks like you might be out of luck.  :(

If it's any consolation, I seem to remember Joomla being a breeze to install manually, even without Fantastico...

---

### Post by fsando on 2007-06-13
I think it's not really worth it to have those CMSes as packages - the packages don't work as expected anyway.
I've installed drupal, serenditpity and typo3 - none of those installs worked - I had to get them from their respective websites and install them manually.
One point though: One CMS (don't recall which) needed some extra php stuff which was installed. So: if there is a package for your preferred cms, check its dependencies in synaptics - if any do an install. I the whole system actually works - then you're fine, if it doesn't, just uninstall the main package, download it from their site and follow instructions from there.

The reason why they didn't work was that they apparently didn't know where apache has its root folder on my machine (and anyway I prefer to control that part myself)

---

### Post by johann_p on 2007-06-13
I have installed the drupal and typo3 packages as well as Zope/Plone and had no problems. If a CMS is popular, I do not see why there should not be a package for it. Joomla definitely is one of the more popular CMS available.
Sure there are hundreds of opensource/free CMS out there and it is probably not worth to include the more exotic ones, but one of the reasons why I use Ubuntu is that the package selection is quite good in most areas --- there are also many different media players etc. and I like to have that choice. Why should it be different with CMS?

---

### Post by az on 2007-06-13
> **johann_p said:**
> 
Any opinions about why it isn't included and whether it should be included?

It isn't included because there is no one who has packaged it and will maintain it for Debian or Ubuntu.  The moment someone wants to do that, it will be in.

The criteria for a package to enter the repos is that is it DFSG-compliant and not much else.  It just takes someone to want to package it.  There is no meaning to Joomla not being in the repos.  It just happened.

In the case of some web applications like drupal, it is packaged, but not many of the modules are packaged along with it.  It makes sense to manage your LAMP stack with the repos, but manage your web application by hand.

---

### Post by johann_p on 2007-06-13
> **az said:**
> It isn't included because there is no one who has packaged it and will maintain it for Debian or Ubuntu.  The moment someone wants to do that, it will be in.

The criteria for a package to enter the repos is that is it DFSG-compliant and not much else.  It just takes someone to want to package it.  There is no meaning to Joomla not being in the repos.  It just happened.

In the case of some web applications like drupal, it is packaged, but not many of the modules are packaged along with it.  It makes sense to manage your LAMP stack with the repos, but manage your web application by hand.

Thanks, that is what I wanted to know :)

---

