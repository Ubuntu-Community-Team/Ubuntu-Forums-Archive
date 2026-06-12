---
title: "Help! Login screen in arabic after reboot in 8.04"
date: 2008-05-27
forum: General Help
---

### Post by Kroma2008 on 2008-05-27
I'm new to Ubuntu, so maybe I'm doing something very wrong and the solution is simple.
After the last reboot my login user name  field is in arabic (or something alike, it writes from right to left) :confused: So i can't input my username --> no acces to my system. I'm falling back to WinXP now :(
An image of this login screen [is here]("http://www.flickr.com/photos/51956045@N00/2528402177/"). 
I have a QWERTY keyboard with spanish layout. Ubuntu 8.04 on an Acer Notebook with dual boot.
What has happened?
How do I get back to spanish keyboard in the login screen and my system back again?

---

### Post by sdowney717 on 2008-05-27
perhaps it is a locales issue you can try restarting and going to a command prompt

[http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_add_locales_to_Ubuntu_the_command_line_way](http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_add_locales_to_Ubuntu_the_command_line_way)

 How to add locales to Ubuntu the command line way

    * Open up a terminal 

    * Generate a /var/lib/locales/supported.d/local from /usr/share/i18n/SUPPORTED: 

cat /usr/share/i18n/SUPPORTED | grep "en\|ru" > /var/lib/locales/supported.d/local

This example shows all Russian (ru) and English (en) locales being chosen. Look through /usr/share/i18n/SUPPORTED to find the ones for you, then put them in a list, replacing en\|ru and separating each language with a \| (backslash, bar). If you only want one language, just put it in quotes.

    * Then regenerate all of the locales: 

dpkg-reconfigure locales

    * Then set your locale: 

update-locale LANG=en_US.UTF-8

In this step, make sure to choose the language and country that you would like your computer to think it is in. Here, I choose en_US, the United States version of English. Once again, look at your /var/lib/locales/supported.d/local or /usr/share/i18n/SUPPORTED for the one right for you. You may also want to research locales, using the Internet.
That was easy, now the command

lxterm

will open up the Unicode version of xterm or your translated software will display things properly, like vim.

---

### Post by Kroma2008 on 2008-05-28
Thank you sdowney717.
But still in trouble:
cat /usr/share/i18n/SUPPORTED | grep "en" >  var/lib/locales/supported.d/local 
gives back:
"-bash: /var/lib/locales/supported.d/local: Permiso denegado" (Access denied) even when executed with sudo.

Any other suggestion?
Maybe it has something to do with xorg?

---

### Post by Kroma2008 on 2008-05-29
Solved!
the xorg.conf file was gone.
Logged in as root and configured the file again with Xorg -configure which generated a file named xorg.conf.new. I renamed this to xorg.conf and everything is running now.

For some unknown reason the xorgconfig script is not making a xorg.conf file, so this was the problem.

---

