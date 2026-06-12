---
title: "[SOLVED] Unable to enter text after configuring SCIM"
date: 2007-10-28
forum: General Help
---

### Post by pyongyangmetro on 2007-10-28
My locale is en_GB but I want to type occasionally in Korean. So I installed SCIM.

Under Feisty, I used im-switch to set SCIM as my default IM, then just used the relevant hotkeys to switch to Korean when necessary.

The problem is, under Gutsy this isn't working. Applications now default to "X Input method" and **I can't type anything at all**, Roman or Korean, until I right-click and change the IM to SCIM. Then everything is great for a while, until it goes back to X Input Method again. This reversion is apparently random, or at least I haven't been able to characterise it.

This is happening in terminal, dialog boxes, gedit, firefox, openoffice - everything. But not always!

I am a relative noob to Linux so I hope it's something simple - im-switch output included below for starters:

```
$ im-switch -l

Your input method setup under en_GB locale as below.
=======================================================
The configuration "/home/pyongyangmetro/.xinput.d/en_GB" is defined as a link pointing to
scim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is manual.
 link currently points to scim
scim - priority 0
scim-immodule - priority 0
default - priority 10
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default none scim scim-hangul scim-hangul_xim scim-immodule th-xim 
=======================================================
```

Anyone, please help if you can, it's driving me crazy!

---

### Post by jamo on 2007-10-28
I have exactly the same issues here on Gutsy with Japanese input. I tried to change the behavior with "im-switch" but that does not help.

---

### Post by pyongyangmetro on 2007-10-29
> **jamo said:**
> I have exactly the same issues here on Gutsy with Japanese input. I tried to change the behavior with "im-switch" but that does not help.

I found a bug report at [https://bugs.launchpad.net/ubuntu/+bug/153233]("https://bugs.launchpad.net/ubuntu/+bug/153233"), which looks promising. But I'm not absolutely sure that it's the same problem as we're having. And the "problem solved" link seems to just point back to im-switch again. :confused:

This whole scim issue doesn't seem to be on anyone's radar at the moment.

---

### Post by chang47 on 2007-10-29
Just want to add that I have the same problem.  Scim is running but the hot key doesn't do anything.  No problem in 7.04.  Still checking and reading to see if I can make any sense out of this...  Will check back later to see if any solution here.

---

### Post by chang47 on 2007-10-30
Found a solution to my problem. Try this if you have scim running but unable to activate it with the hot keys i.e. ctrl+space, shift+space

First remove scim 
sudo apt-get remove scim

Note that apt-get will also remove Chinese from the system.;(

Now put the language support back by:
sudo apt-get install language-support-zh  (this for Chinese only)

I assume you know how to install other languages yourselves.

Then go to [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
and follow the instruction there.

After the install, when you launch an app that scim supports scim will showup in sys tray.  From there it is busness as usual.

Hope this helps some poor souls.

Later!

---

### Post by jenhsun on 2007-10-31
Better solution
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)

---

### Post by tacutu on 2007-10-31
I experienced some strange behavior with japanese input, too. The fastest solution was to dump scim and use uim instead. Dunno if that work for korean, though.

---

### Post by EFobes on 2007-10-31
> **chang47 said:**
> Found a solution to my problem. Try this if you have scim running but unable to activate it with the hot keys i.e. ctrl+space, shift+space

First remove scim 
sudo apt-get remove scim

Note that apt-get will also remove Chinese from the system.;(

Now put the language support back by:
sudo apt-get install language-support-zh  (this for Chinese only)

I assume you know how to install other languages yourselves.

Then go to [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
and follow the instruction there.

After the install, when you launch an app that scim supports scim will showup in sys tray.  From there it is busness as usual.

Hope this helps some poor souls.

Later!

This was the only solution that worked for me. I am a very absolute beginner to UBUNTU  and IT in general so maybe the others (Including replies to your post) would work for more advanced beginners

Thanks! &#12354;&#12426;&#12364;&#12392;&#12358;(arigato)

---

### Post by pyongyangmetro on 2007-11-01
> **jenhsun said:**
> Better solution
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)

This one worked for me (I ended up at [http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6)). Thanks to you and everyone else who answered. =D>

PM

---

### Post by jdw32 on 2007-11-09
I have just installed Gutsy, the last few releases of Ubuntu were no problem using SCIM / Open Office for Chinese (my default locale is en_AU.utf-8), but this one just doesn't want to work.  When I press CTRL+SPACE in Open Office it doesn't activate the SCIM input window. A bit of forum trawling for answers has left me a little confused as to a permanent fix, notable exception - I haven't tried chang47's solution  of uninstalling/reinstalling yet (but I will at some stage!).

However, a quick and dirty work-around (as opposed to a better solution) is to run it all from the same Terminal (Applications/Accessories/Terminal) and type the following :

$ export XMODIFIERS="@im=scim"
$ export LC_CTYPE="zh_CN.utf-8"  // (substitute zh_CN.utf-8 with the input locale of your choice, e.g. ko_KR.utf-8 for Korean)

$oowriter

hit "CTRL+SPACE and away you go...

Note that this will only work for that particular terminal session, unless you type those export commands into your ~/.bash_profile and log out/log in.

This will keep me sane until a fix is available...hope it helps some fellow Ubuntu users.

Cheers!

---

### Post by Edaw 0 on 2007-11-12
> **chang47 said:**
> Found a solution to my problem. Try this if you have scim running but unable to activate it with the hot keys i.e. ctrl+space, shift+space

First remove scim 
sudo apt-get remove scim

Note that apt-get will also remove Chinese from the system.;(

Now put the language support back by:
sudo apt-get install language-support-zh  (this for Chinese only)

I assume you know how to install other languages yourselves.

Then go to [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
and follow the instruction there.

After the install, when you launch an app that scim supports scim will showup in sys tray.  From there it is busness as usual.

Hope this helps some poor souls.

Later!

This worked for me too. &#44048;&#49324;&#54633;&#45768;&#45796;!

---

