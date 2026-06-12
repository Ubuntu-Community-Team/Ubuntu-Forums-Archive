---
title: "I'm trying to us XFE to create folders, doesn't work in Ubuntu 14.04"
date: 2014-07-21
forum: General Help
---

### Post by RogerDavis on 2014-07-21
Software version is 1.37

Can't create folders in Ubuntu 14.04

I can't create folders in Ubuntu 14.04. I can get the box to appear, but I can't type in a folder name to create it.  It just doesn't accept the input.  

Is this a problem in 14.04?  I think there was no problem in 12.04.

---

### Post by kc1di on 2014-07-21
Hi RogerDavis,

I find no problem here with 14.04 , xfce and creating new folders in thunar. I'm not sure that's what your talking about , a little more information about what your trying to do may be helpful. 

so something else must be going on with your install. 
could it be a permissions problem?

Sorry mistook xfe for xfce - not using xfe here.

---

### Post by Morbius1 on 2014-07-21
I can confirm this odd behaviour.

Just installed xfe in Ubuntu 14.04 and the dialogue box comes up but doesn't allow input.

Xubuntu is my distro of choice and XFE works as designed there so it seems to be an Ubuntu - perhaps Unity specific - bug. Time to see if there's a bug report on this.

[COLOR=#0000cd]**Ummm**[/COLOR] ... it would appear as though you already submitted a bug report: [http://sourceforge.net/p/xfe/bugs/193/](http://sourceforge.net/p/xfe/bugs/193/)

---

### Post by The Cog on 2014-07-21
I don't have any such problem here. I wonder if it's a problem with themes? Try a few different themes to see if a font becomes visible.
I'm using the Clearlooks-Phenix theme here (have to install packages clearlooks-phenix-theme and gkt2-engines for this).

P.S.
It may also be significant that I am using Xubuntu (clean install, not an upgrade), not Ubuntu with xfce installed over the top.

Edit:
Oops, I misread XFE as XFCE. Sorry. Please ignore this post.

---

### Post by Morbius1 on 2014-07-21
This is getting curiouser and curiouser.

I have Mint17-Cinnamon installed as a VBOX guest and XFE also works as designed. Mint17 is based on Ubuntu 14.04 but with Unity removed and Cinnamon added so ....

---

### Post by RogerDavis on 2014-07-21
Please note that XFCE has nothing to do with this.  I don't use it, never have.

I'm using Ubuntu 14.04 with Gnome Flashback Metacity.  I've seen no other text windows that won't accept input anywhere else.

I believe this is a bug, so I filed the bug report.  But I was hoping it was just some simple checkbox or something that I missed.

It seems that some people have this problem, some not.

---

### Post by Morbius1 on 2014-07-21
For what it's worth:

I found another bug report the content of which meant absolutely nothing to me: [xfe can't work with ibus input method ]("https://bugs.launchpad.net/ubuntu/+source/xfe/+bug/1029256")

So as an experiment I turned it off: System Settings > Language Support > Keyboard Input Method System > From IBUS to None:
[ATTACH=CONFIG]254888[/ATTACH]
Had to logoff and log on again.

Now I can add a new file in XFE:
[ATTACH=CONFIG]254889[/ATTACH]

Since I normally use Xubuntu I can honestly say I've never used XFE in Ubuntu before. Has this worked for you in the past since the bug report is 2 years old now?

[COLOR=#0000cd]**EDIT**: For completeness sake:[/COLOR]

*** In Xubuntu the "Keyboard Input Method System" combo box defaults to blank. When selected the only option is none which may be why it's not an issue in Xubuntu.
*** In Mint-Cinnamon there is no "Keyboard Input Method System" option at all - at least I can't find it - which may explain why it's not an issue there either.

---

### Post by grahammechanical on 2014-07-21
So, this is not a bug with Ubuntu 14.04 or with Gnome Session Flashback (Metacity) but with XFE. And I should not need to google to find out what XFE is.

---

### Post by Morbius1 on 2014-07-21
I have no idea what you just said but if a utility works everywhere except Ubuntu ( and I don't know that to be true yet ) you can blame the utility or you can blame ubuntu.

The OP placed his bug report with the folks at xfe.

The bug report I referenced was placed with Ubuntu.

Since the ubuntu bug report hasn't been addressed in 2 years I'm guessing it never will so the choice by the OP was the wise one regardless of where the bug exists.

My only observation is that 2 other distros - both based on Ubuntu but with different DE's - do not exhibit this bug.

---

### Post by kc1di on 2014-07-21
It's not a bug in xubuntu - xfe works fine there. not sure about lubuntu so i'm thinking it's a unity bug.

---

### Post by RogerDavis on 2014-07-22
I'm not at that computer right now, can check out things on Thursday.

I suspect that the ibus is the problem, just sounds right to me.  Congratulations on finding that shortcoming!!!

But if I turn it off, what else am I losing???

---

### Post by Morbius1 on 2014-07-22
That I do not know. This is the very first time I've even seen a reference to IBus.

According to the archwiki: [https://wiki.archlinux.org/index.php/IBus](https://wiki.archlinux.org/index.php/IBus)
> **IBus** (*Intelligent Input Bus*) is an [input method framework]("http://en.wikipedia.org/wiki/Input_method"), a system for entering foreign characters.

If you are not in the habit of entering foreign characters my guess is it's not an issue to turn it off but I really have no idea.


* Still curious as to why this is an Ubuntu only phenomenon. Does Xubuntu and Mint disable it or have they developed an Even More Intelligent Input Bus ( EMIBus )?*

---

### Post by kc1di on 2014-07-23
I can tell you Ibus is not installed by default on the Xubuntu /xfce.  
Thus this may indeed be the problem if it's part of the unity/ubuntu install.

---

### Post by Morbius1 on 2014-07-23
> **kc1di said:**
> I can tell you Ibus is not installed by default on the Xubuntu /xfce.  
Thus this may indeed be the problem if it's part of the unity/ubuntu install.
> tester1@vxub1404:~$ apt-cache rdepends ibus | grep unity
  unity-settings-daemon
  unity-control-center
  unity-control-center
  unity-settings-daemon
  unity-control-center
  unity-control-center
You may be on to something there ;)

---

### Post by RogerDavis on 2014-07-24
SUCCESS!

  Turn off ibus and restart, it works!

---

### Post by JirkaEspace on 2014-12-30
The same problem on my Ubuntu 14.04 LTS - localization: Czech (cs-CZ), Xfe 1.37 fresh install (through Software Center).

And because I was not sure about other impacts of turning IBus off, I have found another solution:

> sudo apt-get purge ibus
(& logoff/logon, not sure if it was necessary)

And it works for me! Source:  [COLOR=#000080]t3rmix[/COLOR] [http://sourceforge.net/p/xfe/bugs/193/#30a4](http://sourceforge.net/p/xfe/bugs/193/#30a4)

---

