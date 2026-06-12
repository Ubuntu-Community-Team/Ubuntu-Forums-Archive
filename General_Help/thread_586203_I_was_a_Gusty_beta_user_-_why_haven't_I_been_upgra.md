---
title: "I was a Gusty beta user - why haven't I been upgraded OUT of Beta?!?"
date: 2007-10-22
forum: General Help
---

### Post by Jim March on 2007-10-22
My boot process is still very obviously in a beta state.  It's not clean.  I also didn't get the full Compiz tuning software until I manually did:

>  sudo apt-get install compizconfig-settings-manager

So now I'm wondering what else was left out?

I'm getting all kinds of weird hal and similar errors flashing by too fast to spot.  And boot is a LOT longer now than under Feisty.  I also had to manually delete the old Feisty WiFi keyring in order to use the new login-connected keyring.

So I have to wonder if I've even GOT full production code, or am I still in a half-arsed beta state?

Look, beta users are supposed to get smoothly upgraded to production code piece by piece, right?  They damned well should, esp. on a system never once touched by Automatix, EasyUbuntu or similar abominations.

If Gutsy beta users are being left behind, then there is ZERO incentive to beta test Ubuntu ever again.  We don't need that.

Does anybody have a clue how I can capture all the weird boot text I'm getting, and otherwise confirm whether or not I'm on production code?

Jim March

---

### Post by shad0w_walker on 2007-10-22
A. Beta isn't half arsed so got go insulting it. With out it there wouldn't be a final version to upgrade to.

B. I have been running the beta version since tribe 4, I have yet to hear of a feature I am missing.

C. For the bootup messages, check your log viewer.

---

### Post by Jim March on 2007-10-22
I'm not "insulting beta" - I'm insulting still HAVING beta.

And yeah, I've checked System>Administration>System Log and don't see anything related to "hal" which is a big part of what's flashing by on boot.

---

### Post by Soarer on 2007-10-22
compizconfig-settings-manager is in Universe. It is not installed by default on Gutsy final.

Have you enabled all repos & reloaded, then updated?

---

### Post by jocko on 2007-10-22
If you installed the beta, and have installed all updates since then, you now have the final version.

---

### Post by Jim March on 2007-10-22
> It is not installed by default on Gutsy final.

Really?  A number of online guides refer to it directly.  But maybe that's the case.  Doesn't explain the boot weirdness...or the VERY long boot times.  All articles on Gutsy note that at minimum, boot speed isn't any worse than Fiesty.  On mine it's a crawl, with a LONG blank pause after login and without the normal Gnome startup stuff (little "nautilus" and similar icons).

> Have you enabled all repos & reloaded, then updated?

Oh yeah.  First thing I tried.  

Right now I'm trying to figure out how to display the boot-up text.

---

### Post by Soarer on 2007-10-22
> **Jim March said:**
> 
Right now I'm trying to figure out how to display the boot-up text.

System>>Preferences>>Control Centre>>Startup Manager

Uncheck 'Splash' & check 'show text'

---

### Post by Jim March on 2007-10-22
> System>>Preferences>>Control Centre>>Startup Manager

Oh crap.  I don't have it.  Seriously - checked "administration" too, and "control center" - nada.  Also nothing doing on "Startup Manager" in any submenu.

Looked under "Applications>System Tools", nothing...even "accessories", nope.  I'm under Gnome, remember...not KDE.  I have XFCE available as a "spare" desktop in case Gnome loses it's mind, but I don't normally use it.  (I've tested it though, it reports as Xubuntu 7.10...)

So I seem to be missing *another* Gutsy component!?

Dammit...

---

### Post by Soarer on 2007-10-22
It's optional.

Install 'gnome-control-centre' in Synaptic.

Stay cool, Jim. It's all good. :)

---

### Post by Jim March on 2007-10-22
> jim@jim-acer:~$ sudo apt-get install gnome-control-centre
[sudo] password for jim:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-control-centre
jim@jim-acer:~$ sudo apt-get install gnome-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-control-center is already the newest version.
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 libportaudio2 xserver-xorg-video-psb libpostproc0d
  libavformat0d libdvdnav4 libavcodec0d libntfs-3g5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Hokay...

> jim@jim-acer:~$ sudo gnome-control-center

Well that worked.  So it's loaded, it's BEEN loaded, but it's not in my menus.

Sigh.

Inside, there's no "startup manager".  There IS "bootup manager".  In there I see a "log bootup messages (bootlogd).  So I guess we can use that...

Arright, lemme go check via restart...

---

### Post by Soarer on 2007-10-22
Startup Manager is under System about 2/3 of the way down (at least on mine).

I can run it in a terminal, but don't need to 'sudo' it (but changes require the password).

Menu items don't always come up until a reboot.

---

### Post by Jim March on 2007-10-22
Startup manager is just not there.  Period, even after two reboots.

And "bootlogd" isn't an answer either:

> jim@jim-acer:~$ bootlogd
bootlogd: cannot find console device 136:0 in /dev
jim@jim-acer:~$ 


I did manage to edit my menus such that "control center" exists.  Note that it was loaded per apt-get but not visible - yet MORE evidence that I'm in a "funky beta state".

This didn't happen with Feisty - ran that just fine from Alpha4 on, no sweat.

---

### Post by Lord_Dicranius on 2007-10-22
I gotta add that I've been running Gutsy since tribe 3 and I don't have a "startup manager" or "bootup manager" in my Gnome Control Center either.

---

### Post by forestpixie on 2007-10-22
I don't have startup manager either since tribe5

As far as the upgraded or not goes I was under the impression that if you'd got all the updates as they came along, by the time it was released you'd have the same. Which I did - after I had to do a clean install nothing seems to have changed, other than the really odd problem I had which caused the reinstall

---

### Post by Lord_Dicranius on 2007-10-22
> **forestpixie said:**
> mines in system > preferences after enabling by edit menus.
The "bootup/startup manager" option?  Or the Control Center option?

---

### Post by forestpixie on 2007-10-22
changed it again once I had another read :) but control centre wasn't there by default

---

### Post by Lord_Dicranius on 2007-10-22
Ah, gotcha :-p  Yeah, I don't think I had Control Center there by default either.  I had to add it manually.  But I'm not seeing this "bootup/startup manager" that was mentioned earlier *shrug*

---

### Post by Foaming Draught on 2007-10-22
I used to see references to the Control Centre, and wonder what folk were talking about.  This is the first time that I knew I had to enable it from Preferences/Main Menu.

And nary a sign of a Startup Manager nor a Boot Manager in this newly-enabled Control Centre.

---

### Post by LanDan on 2007-10-22
maybe a stupid question but did you do
apt-get dist-upgrade

---

### Post by Lord_Dicranius on 2007-10-22
> **LanDan said:**
> maybe a stupid question but did you do
apt-get dist-upgrade
Not I.  When I updated I downloaded the tribe 3 image (back when it was released, I didn't just download it the other day for those who aren't following the entire thread lol) and updated from Feisty.

---

### Post by LanDan on 2007-10-22
> **Lord_Dicranius said:**
> Not I.  When I updated I downloaded the tribe 3 image (back when it was released, I didn't just download it the other day for those who aren't following the entire thread lol) and updated from Feisty.

i mean can you try it now

---

### Post by forestpixie on 2007-10-22
startupmanager is in sysnaptic as is boot up manager as  :)

so I guess this would do it

```
sudo apt-get install startupmanager bum
```

---

### Post by Lord_Dicranius on 2007-10-22
Here's what I got after running "sudo aptitude dist-upgrade"

```

lorddicranius@icarus:~$ sudo aptitude dist-upgrade
[sudo] password for lorddicranius:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
lorddicranius@icarus:~$ 

```

---

### Post by Lord_Dicranius on 2007-10-22
> **forestpixie said:**
> startupmanager is in sysnaptic as is boot up manager as  :)

so I guess this would do it

```
sudo apt-get install startupmanager bum
```
Ah, I see.  Trying to install now...

---

### Post by LanDan on 2007-10-22
another stupid question ;)

aptitude install whicheverisyourflavor-desktop

---

### Post by Lord_Dicranius on 2007-10-22
> **forestpixie said:**
> startupmanager is in sysnaptic as is boot up manager as  :)

so I guess this would do it

```
sudo apt-get install startupmanager bum
```
This worked!  I see 'em both in my Control Center :-D  Thanks forestpixie.  Now to take a gander through here to see what I can come up with.

---

### Post by Lord_Dicranius on 2007-10-22
Well, I marked the box for "show text on boot".  Got some stuff open I gotta finish up before trying to reboot though, so I'll be back as soon as I'm able to reboot :)

---

### Post by forestpixie on 2007-10-22
cool - glad you're ok - wonder how Jim March is?

---

### Post by Lord_Dicranius on 2007-10-22
> **forestpixie said:**
> cool - glad you're ok - wonder how Jim March is?
Hopefully what we've been working on here in the past few posts helps him on his way too *crossing fingers*

---

### Post by forestpixie on 2007-10-22
I'd hate for him to feel left out :)

---

### Post by Jim March on 2007-10-22
Well yeah, I finally have startup manager.  But there ain't a damn thing in here that will let me save a log of what's going on.

At least I'll be able to see the crap...

Again: was all this stuff (the control center, the startup manager) there by default on people's new Gutsy production systems?

Because if it was, and us poor schmucks who started with beta didn't have it, then...we just can't trust the Ubuntu beta program.  Yikes.

---

### Post by LanDan on 2007-10-22
> **Jim March said:**
> Well yeah, I finally have startup manager.  But there ain't a damn thing in here that will let me save a log of what's going on.

At least I'll be able to see the crap...

Again: was all this stuff (the control center, the startup manager) there by default on people's new Gutsy production systems?

Because if it was, and us poor schmucks who started with beta didn't have it, then...we just can't trust the Ubuntu beta program.  Yikes.

eeuuhhh, why you think they call it BETA?

---

### Post by Jim March on 2007-10-22
> eeuuhhh, why you think they call it BETA?

Bullpuckey.

Once they've got PRODUCTION code working, they need to push it (with it's configuration) to their beta users.  That's just basic...and it's what they've done in the past.

If THAT policy has changed...this distro is in trouble.

---

### Post by LanDan on 2007-10-22
> **Jim March said:**
> Bullpuckey.

Once they've got PRODUCTION code working, they need to push it (with it's configuration) to their beta users.  That's just basic...and it's what they've done in the past.

If THAT policy has changed...this distro is in trouble.

what policy? where can i find that, you signed up for an early testing stage of an OS.
you did this to help? because you like to squash bugs?
or is it because you think BETA means production ready and wanted to be the first one with the goodies?

if its the last case i'm sorry to dissapoint you, BETA means buggy, testing if something works or crashes and things go wrong as they should.

---

### Post by Jim March on 2007-10-22
During Feisty this was stated policy.  Something went wrong on Gutsy.

---

### Post by LanDan on 2007-10-22
> **Jim March said:**
> During Feisty this was stated policy.  Something went wrong on Gutsy.

stil don't really understand what policy you mean here, you have a link?

---

### Post by forestpixie on 2007-10-22
> Again: was all this stuff (the control center, the startup manager) there by default on people's new Gutsy production systems?

No it wasn't on mine by default at all. To tell the tale I installed tribe5, then when the rc came out I updated to that then by the time the final was released I had no updates to install as the version I had (updated rc) was the final version due to a week or so of updates every day. 

I would have to assume that if you were getting updates from when you installed the beta till a day or two before it was finally released then you had the same.

---

### Post by Jim March on 2007-10-22
It was discussed during the Fiesty betal, on the Feisty dev forum.

I'd go find it, except this forum's search engine is broken.

Ghaaa.

---

### Post by LanDan on 2007-10-22
> **Jim March said:**
> It was discussed during the Fiesty betal, on the Feisty dev forum.

I'd go find it, except this forum's search engine is broken.

Ghaaa.

i never tried fiesty so i wouldn't know, i'd have to take your word for it..
but it is and stays beta testing, did you file a bug about this already on launchpad?

---

### Post by Jim March on 2007-10-22
I started this thread to try and figure out WTF.  As is I can't even figure out how to log the boot.  So I'm damned if I have enough here yet to file a credible-sounding bug report.

---

### Post by LanDan on 2007-10-22
> **Jim March said:**
> I started this thread to try and figure out WTF.  As is I can't even figure out how to log the boot.  So I'm damned if I have enough here yet to file a credible-sounding bug report.

if you meaning logging the boot process, you might want to have a look at dmesg, the old ones are stored in /var/log/

anything can go wrong during beta testing, thats why they need  you to check the logs, figure out what happens and go wrong with help of the forums here and report it back to launchpad so the devs now what they should fix to make sure the not so bravehearted who start with the release have as little as problems possible..


p.s.

are you guys ready for Hardy already?  it sounds like they need you!

---

### Post by forestpixie on 2007-10-22
have you installed bum - there's an option in there for bootlogd

Edit - it installs in system> admin

---

### Post by Foaming Draught on 2007-10-23
Jim March has a point, although I wouldn't have put it in the way he has, I love Gutsy.

I've downloaded religiously all updates since one of the early Tribes, so I should have a similar config to the recent production release.  But I didn't have Gnome Control Centre, nor Start-up Manager nor the infelicitously named bum, (nor even knew that they existed in the repos).  If the production release included GNOME Control Centre and Start-up Manager, but my incremental Gutsy didn't, what else am I missing?

FD

---

### Post by forestpixie on 2007-10-23
the release didn't include sum or bum, I only found them by looking on google during this thread - but did have control centre - but that wasn't enabled by default.

---

