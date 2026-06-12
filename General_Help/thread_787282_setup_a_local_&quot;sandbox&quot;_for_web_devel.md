---
title: "setup a local &quot;sandbox&quot; for web devel"
date: 2008-05-08
forum: General Help
---

### Post by jimmy the saint on 2008-05-08
I am attempting to learn how to build a website for a group that I help out with and have settled on drupal.  Everywhere I look people are playing with their drupal "sandboxes."  After some looking I discovered that most are essentially talking about a local web environment on their computer.
How do I set this up?  I don't want it network accessible, just local.  I would like to be able to play with my drupal site without worrying about an internet connection and ftp.

Thanks for your input, I know its probably a bone-head question.

---

### Post by jimmy the saint on 2008-05-09
Ok.  does anyone know of a good guide to set up lamp on a laptop strictly for local development?  I have read a couple,  but they are all geared toward setting it up for outside access and that is not what i want.  I do not know enough about this to know what parts are for local access and what parts are for granting outside access or for configuring it as such.

---

### Post by FakeOutdoorsman on 2008-05-09
[Apache, mySQL, PHP]("https://wiki.ubuntu.com/ApacheMySQLPHP") at Ubuntu Wiki

---

### Post by mrmonday on 2008-05-09
The simplest solution for localhost is to just use XAMPP [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html"). That has Apache+MySQL+PHP all set up and pre-configured for you. If you feel like putting more effort in (I highly recommend you do, using synaptic it'll run at start up and be less hassle =), just install apache+php+mysql+phpmyadmin from synaptic, and any apache modules you want to use. 

CMS wise I recommend [TangoCMS]("http://www.tangocms.org/") over drupal (2.0 will be out in less than a month if you can wait). It has less features, but it is very easy to use.

---

