---
title: "Flash doesn't work"
date: 2016-02-11
forum: General Help
---

### Post by russkyca on 2016-02-11
I can't get Flash to work.   I've installed every flash-oriented package to no avail.

I remember when you had to install from the Adobe website but when I try, a screen pops up wanting to use the software center which is worthless because using it, it installs a package but then Flash doesn't work.

I upgraded to 15.10 but it seems like nothing works in 15.10.  

I know that Chrome has built-in flash but I want to use Firefox for it (as well).  

I just find it puzzling that Ubuntu has all these flash plug-in packages but NONE work.   Maybe, it's time to try another distro and see if the experience is anything different?

---

### Post by QIII on 2016-02-11
Hello!

What do you mean when you say it doesn't work?

---

### Post by russkyca on 2016-02-11
> **QIII said:**
> Hello!

What do you mean when you say it doesn't work?
Probably what others mean?   When you go to the 'Adobe test page' - you have those 'f' symbols and when you try to play a video that uses flash, it doesn't work.  What is the point of all these flash packages if flash doesn't work?   Whoever programs this should be replaced.

 
flashplugin-installer

or

adobe-flashplugin

Doesn't matter.   It's the same result.

---

### Post by QIII on 2016-02-11
Well, that'll be an indictment of Adobe, not Ubuntu.  Nobody at Canonical "programs" flash.

Adobe, which *does* develop Flash, quit developing Flash for Linux several years ago.  Although they are providing some security updates for a bit longer yet, the version of Flash that we are left with is archaic.  If particular websites insist on a newer version of Flash, then there is nothing anyone in the Linux community -- any distro -- can do about it.  Changing distros will not help at all.

Since Flash is proprietary, there's not much to be done.  Chrome has its own version of Flash built in.  Chrome, of course, is also proprietary.

To the larger picture of the person's rant above:  If one's preferred applications are developed for Windows, they won't work on Linux.  Not Linux' fault.  The people to direct complaints to are those who develop the apps for Windows without producing a Linux version.

---

### Post by russkyca on 2016-02-11
If no one wants to help, I'll go install Debian or Fedora.   It is showing Adobe Flash Player 17.0 and I really don't know what is going on except I don't want to spend any more time on it.   Ubuntu 15.10 is really buggy regarding this as two flash packages and you have nothing but problems and nothing working suggests bad programming.

> **QIII said:**
> Well, that'll be an indictment of Adobe, not Ubuntu.  Nobody at Canonical "programs" flash.

Adobe, which *does* develop Flash, quit developing Flash for Linux several years ago.  Although they are providing some security updates for a bit longer yet, the version of Flash that we are left with is archaic.  If particular websites insist on a newer version of Flash, then there is nothing anyone in the Linux community -- any distro -- can do about it.  Changing distros will not help at all.

Since Flash is proprietary, there's not much to be done.  Chrome has its own version of Flash built in.  Chrome, of course, is also proprietary.

To the larger picture of the person's rant above:  If one's preferred applications are developed for Windows, they won't work on Linux.  Not Linux' fault.  The people to direct complaints to are those who develop the apps for Windows without producing a Linux version.
I know that the distros use Flash ver. 11.2 in Linux and at least, it works to some extent.   I'm talking about installing multiple flash packages and nothing works.   As bad as Flash is, I think this is a new experience for me with Ubuntu so I will try another distro and see if anything is different.

---

### Post by QIII on 2016-02-11
>  I'm talking about installing multiple flash packages and nothing works.

Again:  If the websites demand a more recent version of Flash, then there is nothing to be done about it.  And, I'll repeat this, too:  Nobody at Canonical programs Flash.  It's not bad programming.  It's an unsupported technology because Adobe doesn't develop Flash for Linux any longer.

Flash for Linux is dead.  Nobody in the Linux world can help.  I am sorry.

Fedora 23 and Debian both have 11.2.  That is the latest version that will work on Linux, unless you use Chrome instead of Firefox.  But you are welcome to choose whichever distro you want.

Best wishes.

---

### Post by howefield on 2016-02-11
> **russkyca said:**
> I just find it puzzling that Ubuntu has all these flash plug-in packages but NONE work. 

[Adobe]("http://www.adobe.com/uk/software/flash/about/") must be lying to me in that case..

---

### Post by QIII on 2016-02-11
Ah!  Chrome!

:)

---

### Post by howefield on 2016-02-11
> **QIII said:**
> Ah!  Chrome!

:)

Spit.. cough.. splutter.. nno no :)

It's Firefox. (also have the same version in Chromium)

No point explaining how seeing as the OP is off some place else.

---

### Post by QIII on 2016-02-11
I'd love to know!

Some sort of PPA chicanery?

User agent spoofery?

---

### Post by howefield on 2016-02-11
ajgreeny gets the credit.. [http://ubuntuforums.org/showthread.php?t=2311381&p=13429770&viewfull=1#post13429770](http://ubuntuforums.org/showthread.php?t=2311381&p=13429770&viewfull=1#post13429770)

---

### Post by QIII on 2016-02-11
Noice!

Can believe it with a webupd8 PPA.  But still, why doesn't evil Canonical do this?

Oh, wait.  Proprietary.  Never mind.

---

### Post by ajgreeny on 2016-02-11
Yes, very simple!

@ russkyca
Uninstall anything you have installed at present for flash just to be sure you're starting clean.
Install adobe-flashplugin from the canonical-partner repos and this alone in chromium will give you the latest flash version, 20.0.0.306 in chromium and version 11.2.202.569 in firefox.

You can also get that 20.0.0.306 version of flash to work in firefox by installing the freshplayer-plugin from the ppa at [https://launchpad.net/~nilarimogard/...ubuntu/webupd8](https://launchpad.net/~nilarimogard/...ubuntu/webupd8)

I've been using this for some time now with no problems.

---

### Post by buzzingrobot on 2016-02-11
For the OP:

Adobe and Google have an agreement by which Adobe provides Google, exclusively, a version of Flash that is, more or less, kept feature current with the Windows versions of Flash.  That version is only distributed by Google in Chrome.

As you've read here, Adobe stopped adding feature updates to the version of Flash it makes available for Linux a few years ago.  Since then it has added only security patches. The same product is packaged with *all* Linux distributions. When these updates are released, my experience has been that they appear in Ubuntu updates within 24 hours, usually less.  

I believe Adobe will stop the security patches sometime next year.

The ongoing problems you had with Flash seemed due to visiting sites that require a version not available in Linux apart, perhaps, from the separate product used in Chrome.  Repeatedly using different methods to install Flash likely aggravated the situation.

---

### Post by russkyca on 2016-02-11
> **ajgreeny said:**
> Yes, very simple!

@ russkyca
Uninstall anything you have installed at present for flash just to be sure you're starting clean.
Install adobe-flashplugin from the canonical-partner repos and this alone in chromium will give you the latest flash version, 20.0.0.306 in chromium and version 11.2.202.569 in firefox.

You can also get that 20.0.0.306 version of flash to work in firefox by installing the freshplayer-plugin from the ppa at [https://launchpad.net/~nilarimogard/...ubuntu/webupd8](https://launchpad.net/~nilarimogard/...ubuntu/webupd8)

I've been using this for some time now with no problems.I'd like to do this but I have a vibe that it won't work.   My reasoning:  I've already uninstalled and then installed 'adobe-flashplugin'

I do have an update, though.   It's not as desirable a situation as the one you outlined, though.   I'd much rather have it work at a later version.   Also, it's not ideal what I have right now.

For some reason, there is some flash blocker going on.   I right click and I have a drop-down of options including 'allow flash from this site.'    Any idea of what is going on and how I can start from scratch not including a fresh install of the OS?

On any page that has flash, it's the same:   the 'f' and I have to right click to get the option to allow flash from the site.   

Your suggestion is to uninstall everything and then re-install adobe-flashplugin and that this will result in Adobe Flash ver. 11.2 being installed and working? 

Then, use the ppa and the freshplugin to get ver. 20.0.0.306?

Edit:  The launchpad link doesn't work.

IT was my fault... I had a Flash Block extension on... which I forgot about - I wasn't using this Xubuntu for a while - I have Ubuntu Gnome on another partition.   But, Xubuntu was at 15.04 and I booted up and upgraded.   I forgot the darn extension was enabled.   Sorry, sorry, sorry...  I disabled the extension and now it works.   This is what is displayed when I go to the Flash site (to test if it's working):
You have version 17,0,0,169 installed

I would like to try ajgreeny's steps, though. :)

---

### Post by QIII on 2016-02-11
I just installed from [webupd8]("http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html").

Works fine.

---

### Post by deadflowr on 2016-02-11
> You have version 17,0,0,169 installed

What are you running?
 Because that is not any version used in either regular firefox on linux, nor chrome/chromium.

---

### Post by ajgreeny on 2016-02-12
> **russkyca said:**
> I would like to try ajgreeny's steps, though. :)
So try them.  They have worked for all my installs on 5 separate machines, and 4 virtual machine installations with versions from 14.04 to 15.10.  Adobe flashplugin is not available for 16.04 (not so far at least) so I'm not sure about that version, but 16.04 is still two months away so a lot may happen in that time.

The important thing for Ubuntu versions up to 15.10 is to make sure that you have only those two packages installed to get flash version 20.0.0.306; ie, adobe-flashplugin and freshplayerplugin.  Uninstall pepperflashplugin which you may have installed previously, as well as flashplugin-installer if you tried that.

To install the freshplayerplugin you will need to run commands
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
``` one by one, as shown in the link from QIII at post #17.

---

### Post by russkyca on 2016-02-13
> **deadflowr said:**
> What are you running?
 Because that is not any version used in either regular firefox on linux, nor chrome/chromium.Xubuntu (upgraded to 15.10 from 15.04)

4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

> **ajgreeny said:**
> So try them.  They have worked for all my installs on 5 separate machines, and 4 virtual machine installations with versions from 14.04 to 15.10.  Adobe flashplugin is not available for 16.04 (not so far at least) so I'm not sure about that version, but 16.04 is still two months away so a lot may happen in that time.

The important thing for Ubuntu versions up to 15.10 is to make sure that you have only those two packages installed to get flash version 20.0.0.306; ie, adobe-flashplugin and freshplayerplugin.  Uninstall pepperflashplugin which you may have installed previously, as well as flashplugin-installer if you tried that.

To install the freshplayerplugin you will need to run commands
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
``` one by one, as shown in the link from QIII at post #17.I misread what you had there and at first, I uninstalled the freshplayerplugin.   Realized what I did and reinstalled it.   Then, I uninstalled the pepperflashplugin.   I closed Firefox and restarted it.   I just thought I'd check the flash player test (going to About Flash Adobe site) and now it shows 'Version information:  You have version 20,0,0,306 installed.'

Huh? :)  I was expecting to see 11.2 (back to normal for Linux users).   I thought I'd have to do the webupd8 method to get ver. 20?  

What happened?

---

### Post by ajgreeny on 2016-02-13
Are you completely sure you removed freshplayerplugin?

Without that package I do not think you can get flash 20.0.0.306 in firefox though you will have it in chromium.

What does command ```
dpkg --list freshplayerplugin
``` show as output.

---

### Post by Dennis N on 2016-02-13
I have also installed the freshplayer plugin, and see that the old plugin is still available under Tools > Addons > Plugins. All you would need to do there to return to the 11.2 plugin is disable the new one, and enable the 11.2, which is the only one which can use hal-flash.

EDIT: No, this does not work. Both are listed, but only the freshplayer plugin works no matter which I select. Sorry about that!

---

