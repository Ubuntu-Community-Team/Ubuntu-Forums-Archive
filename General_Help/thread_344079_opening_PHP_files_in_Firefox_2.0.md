---
title: "opening PHP files in Firefox 2.0"
date: 2007-01-22
forum: General Help
---

### Post by telga on 2007-01-22
Good day Gentlemen, how are you?

So I'm a web developer and I've just upgraded to Edgy Eft. The problem I'm having is opening local .php files (any file which has php embedded in it) in Firefox 2.0. I dont expect the PHP code to be executed on the local system, but with Debian sarge & Firefox 1.5 I could open the .php files and view the xhtml output on my local system. With Edgy/FF2 it just pops up a download dialogue. SO is this a firefox problem or a edgy problem or what? Any quick fix? I've got Opera installed and it does exactly what FF1.5 did, that is, display the webpage from the local system minus php output. Thanks very much for your time,

Carie

---

### Post by RobNY on 2007-01-22
Are the php files in question being served locally by apache?  Was php installed (as an apache mod)?

When you open the file in response to the dialog, do you see the php code itself or the output from the php script?

Sounds like a content-type issue which would be caused if PHP was misconfigured (or not configured) within the webserver.

---

### Post by telga on 2007-01-22
> **RobNY said:**
> Are the php files in question being served locally by apache?  Was php installed (as an apache mod)?

When you open the file in response to the dialog, do you see the php code itself or the output from the php script?

Sounds like a content-type issue which would be caused if PHP was misconfigured (or not configured) within the webserver.

I'm not actually trying to run the php code, hence no apache. I just want to view the xhtml (the webpage) with my web browser from my local hdd. I DO have the php5 package installed in hopes that it would clear up my problem, but nothing changed. And when I attempt to open the file in firefox, it pops up the download dialogue. When I set "open with firefox" within that, it just opens another firefox window with another download dialogue. I'm not trying to get the php code itsself to run on the local system, just view the page. Thanks

Carie

---

### Post by RobNY on 2007-01-22
So you want to view the PHP source code in Firefox.

I'm somewhat sure this has to do with the mime-type associated with PHP files.  In Nautilus, right click on a PHP file and view properties.  On the "basic" tab you will see that the mime-type is set to application/x-php.

Unfortunately, I have no clue how to change this or to manually install a handler in Firefox for this mime-type.  It is likely somewhere in the /usr/share/mime-info/gnome-vfs.* config.

Sorry.  Someone smarter will need to chime in here.

---

### Post by forger on 2008-07-04
> **RobNY said:**
> Someone smarter will need to chime in here.

[The post linked here]("http://ubuntuforums.org/showthread.php?p=5320430#post5320430") may do exactly what you ask for :)

---

