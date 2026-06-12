---
title: "gmail &amp; python 2.4.1"
date: 2005-05-08
forum: General Help
---

### Post by Zelut on 2005-05-08
I've got two questions that I'd appreciate any help with.  I'm fairly new to ubuntu but not new to linux.  I used to be a red hat user until they shut it down & went fedora.  Anyway, so far I'm enjoying ubuntu & the base package almost fits my needs perfectly.

There is one problem that I'm stuck with.  Included below is my install output for a gmail notifier.  (sudo dpkg -i gmail-notify-1.6.deb)

Selecting previously deselected package gmail-notify.
(Reading database ... 105297 files and directories currently installed.)
Unpacking gmail-notify (from gmail-notify-1.6.deb) ...
dpkg: dependency problems prevent configuration of gmail-notify:
gmail-notify depends on python (<< 2.4); however:
 Version of python on system is 2.4.1-0ubuntu2.
gmail-notify depends on python2.3-gtk2 (>= 2.2.0); however:
 Package python2.3-gtk2 is not installed.
dpkg: error processing gmail-notify (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gmail-notify

My question is concerning the python versions.  It looks like ubuntu comes with 2.4.1 but its listed as 2.4.1-0ubuntu2.  The gmail notifier is dependent on 2.4.1+.  Is there a way I can bypass the check for standard 2.4.1 or... not sure what I should do there.

Also, is the python2.3-gtk2 not install by default?  I guess I'll just download python-gtk2 & install that from source?  

Thanks in advance for any help.  So far I'm really impressed with the community here.

---

### Post by Martin Witte on 2005-05-08
I installed it from here: [https://addons.update.mozilla.org/extensions/moreinfo.php?id=173&vid=504](https://addons.update.mozilla.org/extensions/moreinfo.php?id=173&vid=504), that works fine for me.

---

### Post by Zelut on 2005-05-08
I've seen the firefox plugin mentioned before.  My only issue is when I DONT have my browser up... if I'm not browsing is there any notification? 

Thanks for the suggestion though.  I may use that if something else doesn't come up.

---

### Post by Chrysaor on 2005-05-08
Just another suggestion if gmail notifier doesn't work, maybe use gmail pop3 and use something like gdesklets to notify when mail arrives, with this you won't have to use a browser for plugin.

---

### Post by Zelut on 2005-05-09
Yeah, that is another solution too...  I guess I'll try out the firefox plugin & see how I like that.  I just figured as long as I have firefox open I could just have a tab for the gmail & be notified that way.

Maybe I need to roll up my sleeves & look into the gmail notifier code & see what I can do there.  Thats why we all like OSS right? :)

---

### Post by MemoryDump on 2005-05-09
[QUOTE=kuyaedz]I've got two questions that I'd appreciate any help with.  I'm fairly new to ubuntu but not new to linux.  I used to be a red hat user until they shut it down & went fedora.  Anyway, so far I'm enjoying ubuntu & the base package almost fits my needs perfectly.

There is one problem that I'm stuck with.  Included below is my install output for a gmail notifier.  (sudo dpkg -i gmail-notify-1.6.deb)

Selecting previously deselected package gmail-notify.
(Reading database ... 105297 files and directories currently installed.)
Unpacking gmail-notify (from gmail-notify-1.6.deb) ...
dpkg: dependency problems prevent configuration of gmail-notify:
gmail-notify depends on python (<< 2.4); however:
 Version of python on system is 2.4.1-0ubuntu2.
gmail-notify depends on python2.3-gtk2 (>= 2.2.0); however:
 Package python2.3-gtk2 is not installed.
dpkg: error processing gmail-notify (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gmail-notify

My question is concerning the python versions.  It looks like ubuntu comes with 2.4.1 but its listed as 2.4.1-0ubuntu2.  The gmail notifier is dependent on 2.4.1+.  Is there a way I can bypass the check for standard 2.4.1 or... not sure what I should do there.

Also, is the python2.3-gtk2 not install by default?  I guess I'll just download python-gtk2 & install that from source?  

Thanks in advance for any help.  So far I'm really impressed with the community here.[/QUOTE]


I'm having the exact same problem trying to install the gmail-notify package. Any solutions?

Thanks
-MD

---

### Post by Zelut on 2005-05-09
I actually got it to work.  Problem was when trying to dpkg -i or ./configure but I got it to work without all that.

simply edit the notifier.conf file to match your settings:

gmailusername="your_user_name"
gmailpassword="your_password"

browserpath="your_browser (ie; firefox %u)"

the rest you can probably leave alone...

After that try to fun notifier.py in a terminal window or just "run application" and run notifier.py.  works great for me.

---

