---
title: "amsn offline"
date: 2007-12-09
forum: General Help
---

### Post by grim192 on 2007-12-09
i installed amsn and it worked fine, however i wanted to check the sound was working after installing the o/s, so i went to youtube using firefox and it wouldn't play the video because it didn't have the correct codec. it asked me whether to to scan for updates so i did and then it became unresponsive after about 5 minutes and i couldn't do anything. i ended up having to turn it off the pc using the power switch and ever since i cant log into amsn it just stays in offline mode. i've tried un-installing and re-installing but it doesn't work. This is what it looks like and it wont give me the option to log in

[http://img527.imageshack.us/my.php?image=screenshotes4.png](http://img527.imageshack.us/my.php?image=screenshotes4.png)

any help would be appreciated :)

grim

---

### Post by moffa on 2007-12-09
you can get the debug menu by pressing ctrl-alt-s

I disable all event sounds in amsn as it interferes with everything else:
Preferences > Appearance > Play sounds when contacts sign in or ..

hope that helps.

---

### Post by grim192 on 2007-12-09
thanks :)

i've got no sound atm, need to sort that out.

the log that it gives me is as follows, does it mean anything to you ? :-

[16:13:36] Catch in proc trans (title ): can't read "lang(title)": no such variable
[16:13:36] Catch in proc trans (followtext ): can't read "lang(followtext)": no such variable
[16:13:36] Catch in proc trans (filters ): can't read "lang(filters)": no such variable
[16:13:36] Catch in proc trans (savetofile ): can't read "lang(savetofile)": no such variable
[16:13:36] Catch in proc trans (clear ): can't read "lang(clear)": no such variable
[16:13:36] Catch in proc trans (close ): can't read "lang(close)": no such variable
[16:13:36] System language is en_gb.utf-8
[16:13:36] Removed _ variant. Now system language is en
[16:13:36] Language "en" is in available languages, using it
[16:13:36] Matching language en!
[16:13:36] LoadLoginList: starting
[16:13:36] LoadLoginList: HOME=/home/grim/.amsn, HOME2=/home/grim/.amsn, HOMEE=/home/grim/.amsn
[16:13:36] LoadLoginList: getting an initial profile
[16:13:36] LoadLoginList: using default profile
[16:13:36] load_config: Started. HOME=/home/grim/.amsn, config(login)=
[16:13:36] load_config: loading file /home/grim/.amsn/config.xml
[16:13:36] load_config: Config loaded
[16:13:36] load_config: Empty login !!! FIXING
[16:13:36] Plugins System: load_config: No plugins.xml]
[16:13:36] PLUGIN : Nudge
[16:13:36] load_lang called from a plugin
[16:13:36] load_lang called from a plugin
[16:13:36] Catch in proc trans (add_clmenuitem ): can't read "lang(add_clmenuitem)": no such element in array
[16:13:36] PLUGIN : Winks
[16:13:36] PLUGIN : Cam Shooter
[16:13:36] load_lang called from a plugin
[16:13:36] load_lang called from a plugin
[16:13:36] PLUGIN : remind
[16:13:36] load_lang called from a plugin
[16:13:36] load_lang called from a plugin
[16:13:36] load_my_pic: Trying to set display picture /home/grim/.amsn/displaypic/UbuntuLogo.png
[16:13:36] skin default 's scrollbar loaded
[16:13:36] Event --changedSkin-- fired with caller -gui-- and args : 
[16:13:36] Event --show_login_screen-- fired with caller -gui-- and args : 
[16:13:36] logging out, creating loginscreen : show_login_screen 
[16:13:36] LoadLoginList: starting
[16:13:36] LoadLoginList: getting profiles
[16:13:36] LoadLoginList: HOME=/home/grim/.amsn, HOME2=/home/grim/.amsn, HOMEE=/home/grim/.amsn
[16:13:36] registering http secure socket 
[16:13:36] Event --loggingIn-- fired with caller -protocol-- and args : 
[16:13:36] logging in, destroying loginscreen : loggingIn 
[16:13:37] check_web_ver: Current= 0.96.91 New=0.96
[16:13:37] Three days (in seconds) :604800
[16:13:37] Difference time (in seconds): 604801
[16:13:37] Not yet 3 days or no new version
[16:13:37] gotNexusReply: loginurl=https://login.live.com/login2.srf
[16:13:37] gotNexusReply: finished before authentication took place

grim

---

### Post by grim192 on 2007-12-10
bumpage :(

grim

---

### Post by praxis22 on 2007-12-11
open a terminal type the following:

**sudo rm -rf /home/grim/.amsn **

This will delete your settings folder, then try to launch the program again.

It seems to me you're having problems with applications software as opposed to the OS itself, so you may be better served asking for help or reading the faq on the amsn site etc.

I would also advise that you don't tweak stuff you don't understand. 

failing that it may be quicker to back up any files etc that you may have saved out (DO NOT take any config file backups) and the do a flat re-install, formatting the drive in the process.

You can actually boot from a live CD and see if your apps work there, if they do they it's your install that's the problem, and that is controlled by the config files, which work out of the box. 

Perhaps they should do a bumper sticker that says, "Linux, with great power comes great responsibility" :)

---

### Post by grim192 on 2007-12-12
it worked :)

i know what caused it, i changed the settings in the preferences to open my email account but it was obviously wrong. what do i need to change to open my homail account ?

grim

---

### Post by UK-Wobbie on 2007-12-12
> **grim192 said:**
> it worked :)

i know what caused it, i changed the settings in the preferences to open my email account but it was obviously wrong. what do i need to change to open my homail account ?

grim

Put in firefox if you have got firefox installed on your ubuntu computer! :)

---

### Post by grim192 on 2007-12-13
> **UK-Wobbie said:**
> Put in firefox if you have got firefox installed on your ubuntu computer! :)

i tried that and it didn't work, atm it says $mozilla. it shows when i get an email but wont open an error message pops up which i'll post later when i'm home.

grim

---

### Post by praxis22 on 2007-12-13
> **grim192 said:**
> it worked :)

i know what caused it, i changed the settings in the preferences to open my email account but it was obviously wrong. what do i need to change to open my homail account ?

grim

Like I said, if you don't understand it, don't mess with it.

---

### Post by grim192 on 2007-12-13
> **praxis22 said:**
> Like I said, if you don't understand it, don't mess with it.

yeah but playing with it is the only way to find out how it works, i now know not to do that again lol

grim

---

### Post by praxis22 on 2007-12-13
This is true, but you're breaking it, then expecting others to fix it.

This is Linux, if if doesn't work out of the box that's one matter, but you break it you fix it. That's how you learn. 

In that respect, "how do I..." is one thing, "I killed it HELP ME!" is another. 

But that was kind of the point of the thread you posted in.

---

### Post by grim192 on 2007-12-14
> **praxis22 said:**
> This is true, but you're breaking it, then expecting others to fix it.

This is Linux, if if doesn't work out of the box that's one matter, but you break it you fix it. That's how you learn. 

In that respect, "how do I..." is one thing, "I killed it HELP ME!" is another. 

But that was kind of the point of the thread you posted in.

i don't intentially set out to  break it and i expend all my resources before i ask for help. its all part of the learning curve.

i do appreciate the help, thanks :) 

grim

---

