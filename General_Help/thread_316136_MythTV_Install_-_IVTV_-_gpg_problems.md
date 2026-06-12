---
title: "MythTV Install - IVTV - gpg problems"
date: 2006-12-10
forum: General Help
---

### Post by Titus A Duxass on 2006-12-10
Just doing a new MythTV install by following this HowTo: > [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

During the IVTV install IAW:
> [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy) 
I get to the step where you add the key to the repository with:> 
wget [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg) -O- | sudo apt-key add -
I get the following error:

Cannot write to  80DF6D58.gpg (Broken pipe).

I have worked around this by adding the gpg key that apt-get gives me in the error report.

Is this a normal error or have I made a booboo?

---

### Post by superm1 on 2006-12-10
Normally during this step you are supposed to be entering your password, which won't be easily apparent.  If you had modified your /etc/apt/sources.list in the last few minutes, you wouldn't have been asked for it.  You can break this up into two steps if you want.

```
 wget http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg 
 sudo apt-key add 80DF6D58.gpg
```

---

### Post by Titus A Duxass on 2006-12-11
Thanks for the info, I suspected that it had something to do with passwords.

As an aside, during the install of the various packages, which took 20 Mins, I notice some OpenOffice packages being downloaded, are they really necessary?

What are all the font packages for?

---

### Post by superm1 on 2006-12-11
Various different users reported to me that certain fonts were missing for themes and such.  If you use aptitude instead of apt-get, you will get a lot more of the packages then are really necessary.  Indeed, this possibly could be trimmed down - but at this point you will have about 1.9 gigs of packages for the entire system.  This is probably sufficient (unless of course you identify something in the list that really isn't necessary and can indicate why :))

---

### Post by Titus A Duxass on 2006-12-11
Aptitude versus Apt-get, I never thought that it would have a major impact.  I always use Aptitude over Apt-get, I even have all the aliases set up, and never realised the impact.
I will try a fresh install using Apt-get.

For further info: the combined front end/back end Howto cross refers you to another HowTo for setting up over hardware items, I think it is the multimedia one.  The HowTo describes how to get nvidia installed throught Synaptic, at this stage in the MythTV install process we only have a command line system.
This could be a little confusing for some users.

The IVTV HowTo is now a very simple task, heart felt thanks for this one.

---

### Post by superm1 on 2006-12-11
> **Titus A Duxass said:**
> Aptitude versus Apt-get, I never thought that it would have a major impact.  I always use Aptitude over Apt-get, I even have all the aliases set up, and never realised the impact.
I will try a fresh install using Apt-get.

For further info: the combined front end/back end Howto cross refers you to another HowTo for setting up over hardware items, I think it is the multimedia one.  The HowTo describes how to get nvidia installed throught Synaptic, at this stage in the MythTV install process we only have a command line system.
This could be a little confusing for some users.

The IVTV HowTo is now a very simple task, heart felt thanks for this one.

Aye, I walked a buddy through setting up his first myth box through my howto.  He was a big confused too by getting nvidia prop. drivers earlier in the process.  I'll have to try to remember to update that so that a user can do it later in the process.

Btw.  I was the same way using aptitude all the time, until I realized how much extra stuff it manages to pull in during the process.  I was quite shocked myself :)

---

### Post by Titus A Duxass on 2006-12-11
> Aye, I walked a buddy through setting up his first myth box through my howto. He was a big confused too by getting nvidia prop. drivers earlier in the process. I'll have to try to remember to update that so that a user can do it later in the process. - Why not just add the two lines needed, sudo apt-get nvidia-?? (forgottten what it is exactly) followed by nvidia-xconfig?

I appreciate that cross-referencing to other documents saves typing but cross-referencing just for two commands seems a little excessive.  By the way this is all meant as positve comments.

---

### Post by godlike on 2006-12-14
Not sure what hardware you have but i just wrote a howto for mythtv with a haupauge WINTV PVR 150 (which should work with most Haupoauge cards) and an usbmce2 remote. Its still waiting approval from a moderator but you can check out a copy here 
[http://godlike.ca/e107_plugins/content/content.php?content.9](http://godlike.ca/e107_plugins/content/content.php?content.9)

if you like

Hope it helps ya or someone else 

cheers

---

### Post by Titus A Duxass on 2006-12-14
Godlike - Thanks very much for the link.  However, your HowTo is not much use to me for the following reasons:
a). I don't have an ATI card
b). I don't want to install myth on top of a full desktop environment
c). I don't have a remote
d). I'm not in North America

Howrver, I'm it will be of use to someone.  You may want to consider changing the colours of your text, orange is a little difficult to read.

My install is based on a lightweight Gnome desktop, I use pieces from the community HowTo, bits from Hyam's HowTo along with bits from my own experience.  I end up with a standalone, near pure mythtv installation that uses about 1.6gb.

Once again thanks for your link.

---

### Post by superm1 on 2006-12-14
> **Titus A Duxass said:**
> Godlike - Thanks very much for the link.  However, your HowTo is not much use to me for the following reasons:
a). I don't have an ATI card
b). I don't want to install myth on top of a full desktop environment
c). I don't have a remote
d). I'm not in North America

Howrver, I'm it will be of use to someone.  You may want to consider changing the colours of your text, orange is a little difficult to read.

My install is based on a lightweight Gnome desktop, I use pieces from the community HowTo, bits from Hyam's HowTo along with bits from my own experience.  I end up with a standalone, near pure mythtv installation that uses about 1.6gb.

Once again thanks for your link.

Titan,

1.6GB?  Oooh this sounds appealing.  The smallest I can seem to make mine is about 1.8 for a frontend 2.2 for a backend.  Probably somewhere in the middle for a combo box, but I don't have any of these.

---

### Post by godlike on 2006-12-15
Hrmmm thats a good idea actually. Would probablly run on older machines alot better too.

---

### Post by Titus A Duxass on 2006-12-16
I am finding the 1.6gb is about the smallest for a FrontEnd/BackEnd combination.

I can probably reduce that a bit with another WM, but gnome is the only one that I can place the mythfrontend in the start up programmes.

If I can find out how to set mythfrontend as a start up programme from the command line, then I can play around with the WM.  I think the ultimate would be Openbox.

---

### Post by superm1 on 2006-12-16
> **Titus A Duxass said:**
> I am finding the 1.6gb is about the smallest for a FrontEnd/BackEnd combination.

I can probably reduce that a bit with another WM, but gnome is the only one that I can place the mythfrontend in the start up programmes.

If I can find out how to set mythfrontend as a start up programme from the command line, then I can play around with the WM.  I think the ultimate would be Openbox.
Titus, 

Look around at the help.ubuntu.com/community/MythTV pages.  I have a howto on the standalone frontend page for edgy that explains how to use openbox and start up with it.

---

### Post by Titus A Duxass on 2006-12-16
SuperM1,
Thanks, my problem is that (this is my opinion) your script complicates an otherwise simple issue.
With gnome I just add mythfrontend to start up through admin  => preferences => sessions and get user mythtv to auto-login by configuring gdm.conf.  That's it.  My problem is that I cannot find the same facility in any other WM.

---

