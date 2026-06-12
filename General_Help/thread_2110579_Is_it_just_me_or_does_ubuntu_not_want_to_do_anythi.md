---
title: "Is it just me or does ubuntu not want to do anythin?"
date: 2013-01-30
forum: General Help
---

### Post by craigrobbo on 2013-01-30
Alright guys, So I decided I wanted to make the switch over to Ubuntu for general computing and day to day use.

I seem to have never ending issues with everything I try to do

First things first.

I cannot for the life of me get skype to install.

First issue was down to me being on the AMD64 platform, So I followed a guide to allow me to force 32bit architecture install, Then there were other installations saying Librarys were missing (there was a lot of them so i apologies for not typing them here), When I tried to install these, it was more errors and so and and so forth...

next issue, I cannot get unity 3D to start / run...

First time around i got errors to the effect of missing files, I reinstalled Ubuntu then I got errors saying here was no objects to apply(or to that effect) I really wanted to use the nice 3D visuals like the cube, wobbly windows etc. i have no unity 3D Icon in the control panel either?

next thing, May seem minor but some of my shortcuts do not work, Or maybe they are not supposed to.
In windows 7 on Firefox if I want to go back a page, I can press backspace, this doesn't seem to work on Ubuntu same when in picture viewer, pressing the left and right arrow keys do not change the image to the next one?

So far I have been a little scared to try anything else due to everything going wrong so many times.

I am using the latest build of Ubuntu 12.1 and have reinstalled maybe 4 times so far, currently I am on a 100% fresh install...

All help is totally appreciated

---

### Post by DominikST95 on 2013-01-30
Skype is no problem...Just download the latest version here:

[http://www.skype.com/intl/en/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/)

double-click the .deb file, you will get, and Skype will install.

The nice and fancy cube effects are done with Compiz, not with Unity ;) For more information: 
[http://askubuntu.com/questions/145356/how-can-i-enable-wobbly-windows-without-using-ccsm](http://askubuntu.com/questions/145356/how-can-i-enable-wobbly-windows-without-using-ccsm)

Hope, I could help at least a bit ;)

---

### Post by grahammechanical on 2013-01-30
It well and truly could be you.

I used 12.04, 12.10 as my daily working OS while they were under development. They worked fine. I am now using 13.04 development version as a daily working OS. Some of us who do testing are starting to get bored because of the stability of the development versions.

How did you try to install Skype? It is in the Ubuntu Software Centre and USC usually installs applications just fine. I have not installed Skype myself and that is nothing to do with the fact that Skype is now owned by Microsoft. I would not let that stop me using free (as in not paying) software.

Ubuntu now has a lot of what are called Multiarch libraries. These are supposed to make running 32bit applications on a 64bit OS more efficient.

Firefox not working on Linux the way it works in Windows 7 is not a Ubuntu fault.

This I do not understand:

> next issue, I cannot get unity 3D to start / run...

Unity 3D is the default User Interface. Did you un-install it at sometime?

>  i have no unity 3D Icon in the control panel either?

What 3D icon? What control panel?

This is not so easy to get:

> I really wanted to use the nice 3D visuals like the cube, wobbly windows etc

The Compiz special effects are not being developed any more. Many of them are not supported in 12.10 (such as wobbly windows). The developer does not have time to maintain them. Needs volunteers.

Many things that users were accustomed to do in the past are no longer possible and that is due in a lot of cases to the change from Gnome 2 to Gnome 3. Things (such as themes; guides) that worked in Ubuntu 10.04 now cannot work in 12.04 onwards.

Regards.

---

### Post by craigrobbo on 2013-01-30
I have tried the installs in the above link but non will install ( it says there is an error during installation) i`ve tried getting a 64bit version to but this doesn't seem to work either.

---

### Post by SeijiSensei on 2013-01-30
> **grahammechanical said:**
> Firefox not working on Linux the way it works in Windows 7 is not a Ubuntu fault.

I had a similar experience using Firefox on Windows after using it on Linux for a very long time.  If you double-click a word in the Windows version, say while writing a comment like this, Firefox on Linux will highlight only the word.  On Windows it highlights the word and the trailing space.  Mozilla [says]("https://bugzilla.mozilla.org/show_bug.cgi?id=452948") this conforms to Windows standards, though they do not tell us where this "standard" comes from.  To fix this, you have to change a configuration setting via about:config, not the most user-friendly of interfaces!

I note this just to point out that even supposedly cross-platform applications like Firefox have these quirks, and they are not the fault of Ubuntu or Linux.  In this case I prefer the Linux default of ignoring the trailing whitespace.

---

### Post by craigrobbo on 2013-01-30
> **grahammechanical said:**
> It well and truly could be you.

I used 12.04, 12.10 as my daily working OS while they were under development. They worked fine. I am now using 13.04 development version as a daily working OS. Some of us who do testing are starting to get bored because of the stability of the development versions.

How did you try to install Skype? It is in the Ubuntu Software Centre and USC usually installs applications just fine. I have not installed Skype myself and that is nothing to do with the fact that Skype is now owned by Microsoft. I would not let that stop me using free (as in not paying) software.

Ubuntu now has a lot of what are called Multiarch libraries. These are supposed to make running 32bit applications on a 64bit OS more efficient.

Firefox not working on Linux the way it works in Windows 7 is not a Ubuntu fault.

This I do not understand:



Unity 3D is the default User Interface. Did you un-install it at sometime?



What 3D icon? What control panel?

This is not so easy to get:



The Compiz special effects are not being developed any more. Many of them are not supported in 12.10 (such as wobbly windows). The developer does not have time to maintain them. Needs volunteers.

Many things that users were accustomed to do in the past are no longer possible and that is due in a lot of cases to the change from Gnome 2 to Gnome 3. Things (such as themes; guides) that worked in Ubuntu 10.04 now cannot work in 12.04 onwards.

Regards.


This clears a few things up.

I guess I can no longer have the nice looking Ubuntu with it not being supported. 

When I was googling how to get the transitions in ubuntu one link said in control panel(or whatever it is called in linux) there was a Unit 3D Icon to make adjustments to transitions etc.

Now for skype I think it is an architect issue, Unfortunately skype does not show up in the software center?

---

### Post by craigrobbo on 2013-01-30
Alright to clear some stuff up, When I try to install skype here is the error I get

Selecting previously unselected package skype.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 148032 files and directories currently installed.)
Unpacking skype (from .../skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.

dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...

---

### Post by sdowney717 on 2013-01-30
```
Unpacking skype (from .../skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) ...
```

It looks like you got the wrong version

here is mine running 4.1

---

### Post by craigrobbo on 2013-01-30
> **sdowney717 said:**
> ```
Unpacking skype (from .../skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) ...
```

It looks like you got the wrong version

here is mine running 4.1

if I try to install the x86 version it comes up with 'wrong architecture' error.

I can't win :(

Don't make me go back to windows, please

---

### Post by sdowney717 on 2013-01-30
I am running 64 bit ubuntu 12.04, not 12.10

At this site you can get the ubuntu 12.04 multiarch
[http://beta.skype.com/en/download-skype/skype-for-computer/](http://beta.skype.com/en/download-skype/skype-for-computer/)

I would try that one.

OR do this here
[http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html](http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html)

```
To install skype in Ubuntu/Linux Mint open Terminal (Press Ctrl+Alt+T) and copy the following commands in the Terminal:
wget -O skype http://download.skype.com/linux/skype-ubuntu-precise_4.1.0.20-1_i386.deb
sudo dpkg -i skype
sudo apt-get -f install && sudo rm skype

```

---

### Post by na5h on 2013-01-30
Based on what I've been able to tell from [this post]("http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package"), you have to install the 32-bit packages like this:
```
sudo apt-get install package-name:i386
```

I'm a little confused about this whole 32-bit/64-bit issue that you've been talking about. You said you had to "force a 32-bit architecture install" because you were "on the AMD64 platform"? As far as I know, the 32-bit version of Ubuntu should work just fine on both 32-bit and 64-bit processors. But if you have a 64-bit processor, why not just install the 64-bit version of Ubuntu?

---

