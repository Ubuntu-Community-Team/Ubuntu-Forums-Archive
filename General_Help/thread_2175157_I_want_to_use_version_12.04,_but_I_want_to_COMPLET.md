---
title: "I want to use version 12.04, but I want to COMPLETELY remove Unity"
date: 2013-09-17
forum: General Help
---

### Post by jukingeo on 2013-09-17
Hello All,

I have been an avid user of Ubuntu since I had Hardy Heron back in 2006.  Later I switched to Lucid which was the first LTS OS and I has happy with that.   The next LTS update was 12.04 and I finally managed to get my wife on board to use Linux as well.

Now enter the problem.   Since I have been using the Ubuntu Studio variant of Ubuntu since Hardy, I have pretty much a different desktop...XFCE.  While I was not too happy about that, the format pretty much stayed the same with having the taskbar on the bottom and the navigation system was like that of traditional Gnome.

Since my wife doesn't need the features of Ubuntu Studio, I set her up with standard 12.04.   Immediately I knew something was amiss when I saw that flyout menu on the left side with symbols and not words and the taskbar was on the top (and couldn't be moved as such).   Also everything was on opposite sides.

While both my wife and I 'tried' to get around Unity, we both agree that it is no good and wanted to do away with it.   So I came here to the forums.   As it turns out, there is a way to install the Gnome-Classic desktop which would restore most of the features of the older style Gnome desktop.  However, we were still forced to have the taskbar on top.   My wife did learn to use 12.04 this way and for the most part everything was fine.

Enter my twin 6 year old sons.   They have grown interested in computers of late and sometimes we let them play games on the computer.    However, they are button mashers and in the heat of an on-line game battle they have disturbed some kind of setting and now the awful Unity desktop is back.   Worse, changing the login back to Gnome Classic is not working, the desktop keeps smiling back at me going 'ha ha, you still have me...Unity.'   

Another thing that has been disturbed is the log-off.  The computer will not shut down, nor restart, it goes back to the login screen.   So now I am pissed off and I hard booted my wifes machine (shut off manually and restarted using the power button) and I put her back into Windows.

Now this is what I would like to do and in this order:

1)  If there is a way to fix this and get my wife's CLASSIC gnome back, I would like step by step instructions to do so.
2)  Next I would like to know a way to OBLITERATE Unity completely.  That is right, I want it OFF her system and I don't want to have anything to do with it anymore.  If this means manually removing 100 files using the terminal, so be it.
3)  I would like to know how I can 'child proof' the computer.  I intend to give my sons their own login and in that login I want to block all keyboard combos, shortcuts or anything that would disturb the settings of the machine.  In other words they can push the control, alt, and shift keys (as most the games they play use these keys), but the computer will ignore combination presses, meaning that if normally pressing ALT+W switches a desktop function or feature of Ubuntu.  I would like Ubuntu to ignore the combination.

Now if I can't obliterate Unity completely, I would like to know which version of Ubuntu still has the traditional Gnome desktop.   If I revert to that version, will my wife still keep her settings?

Note to developers:  I would appreciate it if you would still offer a choice in regards to the desktop that is preferred.   I know there are many of us that do not like Unity and I for one, didn't appreciate it being jammed down my throat, when I upgraded to 12.04.   The old Gnome envirnment was fine, there was nothing wrong with it.  While I do appreciate that I can go back to an older desktop, I don't like the fact that a certain key combination can bring the offending Unity desktop environment back.   I do hope that future versions of Ubuntu will at least give you a choice.  Although I wouldn't mind if you went back to the traditional Gnome interface and offered Unity as the option.

Thank You,

Geo

---

### Post by jukingeo on 2013-09-17
Hello All,

As the title says, I want to continue to use Ubuntu version 12.04, but I would like to use it with the traditional Gnome desktop.   But I would like to know how to completely obliterate Unity.  It is causing problems and I simply do not want it on my system.   I want Gnome Classic and that is all.

Thank You.

Geo

---

### Post by david98 on 2013-09-17
Here's a link that you may find useful  [http://linux-software-news-tutorials...untu-1204.html]("http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html")

---

### Post by Iowan on 2013-09-17
Threads merged.

---

### Post by oldos2er on 2013-09-17
> **jukingeo said:**
> Note to developers:  I would appreciate it if you would still offer a choice in regards to the desktop that is preferred.   I know there are many of us that do not like Unity and I for one, didn't appreciate it being jammed down my throat, when I upgraded to 12.04.   The old Gnome envirnment was fine, there was nothing wrong with it.  While I do appreciate that I can go back to an older desktop, I don't like the fact that a certain key combination can bring the offending Unity desktop environment back.   I do hope that future versions of Ubuntu will at least give you a choice.  Although I wouldn't mind if you went back to the traditional Gnome interface and offered Unity as the option. 

GNOME killed Gnome 2.x, that decision had nothing to do with Ubuntu or Canonical.

Nothing is "jammed down your throat," if you want to try [Xubuntu]("http://xubuntu.org/"), [Lubuntu]("http://lubuntu.net/"), or [Kubuntu]("http://www.kubuntu.org/") visit the appropriate website. For more info see [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by HiImAStaticCharge on 2013-09-17
Try Ubuntu GNOME.
[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

Also I would suggest, like oldos2ersaid give Xubuntu a try.

I am not too familiar with the Parental Controls on Ubuntu so sorry I cannot be of further help. The only way I know to get rid of Unity is to, well, not use it at all.

---

### Post by ibjsb4 on 2013-09-17
Yet another idea :)

Do a terminal only install with either the mini.iso or the alt install cd and then:

```
sudo apt-get install --no-install-recommends gnome-session-fallback nautilus && sudo apt-get install firefox synaptic gnome-terminal lightdm
```

With that, you will be on your marry way to rolling your own gnome-classic (and only gnome-classic) desktop.  I think you been around long enough to figure out what packages you want from there :)

And one question.  I too have been running ubuntu since hardy, but I had to wait for it to come out in 2008.  How did you get it in 2006 :p

---

### Post by mastablasta on 2013-09-18
Unity is here to stay. 

I am not sure what bothered you in Xubuntu. the bottom panel can be removed (right click on it to remove it). the top panel can be moved (right click on it to move it). 

you can turn of desktop shortcuts easilly (somewhere in system settings). i know you can in Kubuntu. if you create their own acocunt, just don't give them admin rights. they can mess it up completelly and yet their mess won't affect the entire sytsem but only their accounts. i have a two year old and that what i did. he pushes all kinds of buttons.

If you want something that has a lot of customisation options in GUI - Xubuntu or Kubuntu are a good choice.

btw MATE desktop is the continuation of old Gnome 2. Linux Mint has a spin with it and they also contribute to Mate. it can also be installed in Ubuntu. i wonder how long will it remain relevant though.

---

### Post by CatKiller on 2013-09-18
Installing Gnome as an alternative to Unity is as simple as installing Gnome Panel. There's nothing stopping you from putting the window list (or anything else for that matter) on the bottom panel. I have no idea why you keep logging yourself out rather than shutting down. Keyboard shortcuts are easy to edit.

Personally, I'm rocking the Gnome 3/Compiz combo, but whatever floats your boat.

---

### Post by Impavidus on 2013-09-18
1) The old gnome is more or less gone. I wasn't happy with unity either, so I switched to Xubuntu, which uses xfce, with which you seem familiar. It's highly configurable, so you can put whatever bars, buttons and other things you want on the top, bottom or sides. A fresh install of Xubuntu works and will get rid of all dirty configurations present, but converting Ubuntu to Xubuntu is possible. Install **xubuntu-desktop** ...
2) ... and read [here](http://www.psychocats.net/ubuntu/purexubuntu) how to get rid of Unity.
3) If you give your sons their own login without sudo permission, they won't be able to change any setting on the computer except for there own accounts. At least, until they've learned how to get into the recovery console. If you make a backup of the settings stored on their account and save that in a directory to which they don't have write access, you can always restore their settings in an instant in case they mess something up.

---

### Post by buzzingrobot on 2013-09-18
Installing the Mate desktop (mate-desktop.org) is the easiest way to return to the old  fashioned Gnome 2 interface Ubuntu used to use. It's the old Gnome 2 code recompiled and tweaked a bit to work in modern environments. (E.g., names have been changed to prevent conflicts with Gnome 3 items that continue to use the traditional Gnome names.)

Panels, etc., work as you are used to.

There are instructions at mate-desktop.org, posted by users, for removing Unity and then installing Mate. I've tried them and found them error prone and problematic. I don't think it is worth the risk and hassle. 

Once Mate is installed, Unity is effectively hidden and not used. So, personally, I'm not sure I see a reason to try to delete it.  In addition, because you will be pulling from the Ubuntu repositories, you will pull in pieces of Unity support as dependencies when you install new applications. That won't affect how Mate looks and works, but it does mean that some of the stuff you may have worked hard to delete is inevitably going to come back.

Another approach is to install Ubuntu via a mini.iso or network install, and avoid selecting any desktop environment.  This will give you a barebones command line environment.  Then, you manually add repos to sources.list, install X, etc., and then install Mate.

---

### Post by jukingeo on 2013-09-19
> **david98 said:**
> Here's a link that you may find useful  [http://linux-software-news-tutorials...untu-1204.html]("http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html")

Thank You.  I gave it a quick look over and it seems it might do the trick.  I will try and give it a shot.

> **oldos2er said:**
> GNOME killed Gnome 2.x, that decision had nothing to do with Ubuntu or Canonical.

Still Ubuntu could have given an option to stay with 2.x or Unity.  Having that choice would have made the 12.04 deal sweeter.

> 
Nothing is "jammed down your throat,"

That depends on one's point of view and I can see your's is in favor of Unity, or you wouldn't have written that.

>  if you want to try [Xubuntu]("http://xubuntu.org/"), [Lubuntu]("http://lubuntu.net/"), or [Kubuntu]("http://www.kubuntu.org/") visit the appropriate website. For more info see [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

I had thought about going the route of one of those and it would seem simpler to install a whole new OS.  But I am worried about loosing settings and information on that machine.

> **HiImAStaticCharge said:**
> Try Ubuntu GNOME.
[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

Also I would suggest, like oldos2ersaid give Xubuntu a try.

I did have my wife's machine set up on Gnome-Classic, but for some reason whatever key combo it was that my son hit, made Unity rear it's ugly head and it seems to be stuck on it.  Logging off and back into 'Gnome-Classic' STILL takes me to Unity.  I might end up going that route if the procedure that David98 recommended doesn't work.

> 
I am not too familiar with the Parental Controls on Ubuntu so sorry I cannot be of further help. The only way I know to get rid of Unity is to, well, not use it at all.

Well, the whole idea was not to use Unity and that worked fine with Gnome Classic, but for some reason, I can't get back to it.

> **mastablasta said:**
> Unity is here to stay.

Perhaps it is here to stay, but on my computer I am giving it the boot.  ...And that is boot out not boot up.

> 
I am not sure what bothered you in Xubuntu. the bottom panel can be removed (right click on it to remove it). the top panel can be moved (right click on it to move it). 

Nothing really. It just seems rather bland. The XFCE desktop came with Ubuntu Studio.  I just am not as happy with the XFCE inferface as I was with Gnome.  Again, even here I would have liked a choice (upon install).   However, I did try to change it, but then Jack stopped functioning.  It is just that it seems that 12.04 is 'attuned' to the XFCE desktop for some reason.  When I went back to it, Jack started to work again.   At any rate, I never had the XFCE desktop on my wife's machine, which is the one with the issue.

> 
you can turn of desktop shortcuts easilly (somewhere in system settings). i know you can in Kubuntu. if you create their own acocunt, just don't give them admin rights. they can mess it up completelly and yet their mess won't affect the entire sytsem but only their accounts. i have a two year old and that what i did. he pushes all kinds of buttons.

If you want something that has a lot of customisation options in GUI - Xubuntu or Kubuntu are a good choice.

I think my wife would like the flexibilty that Kubuntu offers and I have seen it myself, it does have nice 'pretty' desktop.  But doesn't Kubuntu also use Compiz?  Also I am under the impression that with Kubuntu there might be more my sons might mess up on it.   But I didn't know that you can shut off the desktop shortcuts that easily.  I tried to look through the Unity DE for such a setting, but couldn't find it.  But, yeah, once I fix this, if there is a setting to turn off the shortcuts, then that would elminate most of the issue with my kids using the machine.  Then I can set them up with their own user profile and that profile would have the shortcuts disabled.

> 
btw MATE desktop is the continuation of old Gnome 2. Linux Mint has a spin with it and they also contribute to Mate. it can also be installed in Ubuntu. i wonder how long will it remain relevant though.

I did try to use Cinnamon and I had that on both machines for a while, but I had some issues with it.  Certain things were not working.  Cinnamon seemed to prefer to work in it's native Linux Mint OS.  So I ended up taking it off both systems.  In fact it was Cinnamon that caused trouble with Jack with my Ubuntu Studio.   So for me I had to go back to XFCE.

I will say that if I am going to change the OS, I would still stick with one of the Ubuntu flavors.  I have trusted Ubuntu for a long time and the support in these forums is great.  There is no denying that.  And I have tried other Linux flavors too.  I just kept coming back to Ubuntu.

> **Impavidus said:**
> 1) The old gnome is more or less gone. I wasn't happy with unity either, so I switched to Xubuntu, which uses xfce, with which you seem familiar. It's highly configurable, so you can put whatever bars, buttons and other things you want on the top, bottom or sides. A fresh install of Xubuntu works and will get rid of all dirty configurations present, but converting Ubuntu to Xubuntu is possible. Install **xubuntu-desktop** ...

While I am not fully happy with XFCE, it certainly was much easier to get around than with Unity.  So it would seem logical to go this route since I already have it with Ubuntu Studio.   But it does have me wonder, why did Ubuntu Studio go with a Xubuntu desktop?   Could that be because of Unity in that the developers couldn't get Unity to work with Ubuntu Studio?

> 
2) ... and read [here](http://www.psychocats.net/ubuntu/purexubuntu) how to get rid of Unity.
3) If you give your sons their own login without sudo permission, they won't be able to change any setting on the computer except for there own accounts. At least, until they've learned how to get into the recovery console. If you make a backup of the settings stored on their account and save that in a directory to which they don't have write access, you can always restore their settings in an instant in case they mess something up.

Well, having them create a problem and then restoring from a backup is a solution, but I would rather not have the problem occur in the firstplace.   My sons have caused problems on both of our machines and 9 times out of 10, it was done through a keyboard shortcut.   So I think a simple solution as creating their own account and have the shortcuts disabled would certainly go a long way.

> **buzzingrobot said:**
> Installing the Mate desktop (mate-desktop.org) is the easiest way to return to the old  fashioned Gnome 2 interface Ubuntu used to use. It's the old Gnome 2 code recompiled and tweaked a bit to work in modern environments. (E.g., names have been changed to prevent conflicts with Gnome 3 items that continue to use the traditional Gnome names.)

Panels, etc., work as you are used to.

There are instructions at mate-desktop.org, posted by users, for removing Unity and then installing Mate. I've tried them and found them error prone and problematic. I don't think it is worth the risk and hassle. 

You won me over with '...I don't think it is worth the risk and hassle'.  Ok, so I will avoid that approach.

> 
Once Mate is installed, Unity is effectively hidden and not used. So, personally, I'm not sure I see a reason to try to delete it.  In addition, because you will be pulling from the Ubuntu repositories, you will pull in pieces of Unity support as dependencies when you install new applications. That won't affect how Mate looks and works, but it does mean that some of the stuff you may have worked hard to delete is inevitably going to come back.

That is my problem with Unity, it has a bad habit of coming back.  I have tried the 'hidden' approach by using the Gnome Classic.  But even with that I couldn't move the taskbar from the top.  I couldn't switch the 'reversed' icons on the taskbar (min,max,close, on the left side rather than the right side).  Now one of my son's did something fooky with the shortcuts and now Unity has reared it's ugly head.  So as Mastablasta, it appears Unity wants to stay.   But I, on the other hand, just want to give it the final kick in the keester and get it off my system.   I want to run the operating system on my machines, I don't want the operating system to run me.  THAT is why I wanted to get away from Windows in the first place.

> 
Another approach is to install Ubuntu via a mini.iso or network install, and avoid selecting any desktop environment.  This will give you a barebones command line environment.  Then, you manually add repos to sources.list, install X, etc., and then install Mate.

If that were the only way to do it, then yes I would try it.  But it does seem that easier options have presented themselves.


Well, thank you everyone for the information.  I think I am going to try what Dave98 linked to first.  If that doesn't work, then I will try another OS.  I will have my wife look at the desktops and see if she prefers Xubuntu or Kubuntu.

Now the only other question I have is whatever route I go that was suggested here, does my wife still keep her settings and programs?  I sure hate to have to start all over from scratch.

Geo

---

### Post by buzzingrobot on 2013-09-19
Canonical could only have offered a choice to stay with Gnome 2 if they had decided to, and been able to, take over maintenance and development of Gnome 2.  For a perspective on how successful that might have been, consider the impact of Mate, or the lack thereof.

I find it increasingly difficult to understand the griping about the demise of Gnome 2.  People act as if that was a personal act of spite directed at them. In reality, it was a rather small group of developers deciding they wanted to do something else.  That's what open source and free software are *all* about:  Developer freedom.  If you think they're all about *user* choice, you are wrong. Users who pay for software -- on whom developers are financially dependent -- have magnitudes more influence on product development.

In any case, Linux has more variety, more quality, in DE's than it ever has.  Right now is the golden moment for DE's.   You want choice?  This is very likely as good as it gets.

---

### Post by oldos2er on 2013-09-19
You can install the various desktop environments in your current OS without installing an entirely new OS, see [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available) for more info.

---

### Post by jukingeo on 2013-09-19
Sorry David98  it didn't work...in fact it blew the partition.  I tried the recovery and it didn't work. 

The wife and I need to decide what we are going to do next.   Needless to say I am not happy (not with you mind you, but the people that attached this crap Unity to Ubuntu).

> **oldos2er said:**
> You can install the various desktop environments in your current OS without installing an entirely new OS, see [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available) for more info.

I did that already.  I said so above.  My wife was running with Gnome Classic for a LONG time now.   However, as I  also mentioned above, my kids were using the machine and pushed some sort of key combination that 'locked' Unity in no matter what you select on the login.  You select Gnome, you get Unity, you select Gnome-Classic, you get Unity. You Select Gnome (no effects), guess what?  you get Unity.    It is STUCK in Unity.   

Anyway the point is moot now as I was hoping the procedure suggested by David98 as an attempt to get my Gnome Classic back and keep my information.  Apparently something went wrong in that process.

> **oldos2er said:**
> You can install the various desktop environments in your current OS without installing an entirely new OS, see [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available) for more info.

> **buzzingrobot said:**
> 
I find it increasingly difficult to understand the griping about the demise of Gnome 2.  People act as if that was a personal act of spite directed at them. In reality, it was a rather small group of developers deciding they wanted to do something else.  That's what open source and free software are *all* about:  Developer freedom.  If you think they're all about *user* choice, you are wrong. Users who pay for software -- on whom developers are financially dependent -- have magnitudes more influence on product development.

Some people welcome change, others resist it.  I can go both ways.  Gnome the way it was, worked.  It was a very similar interface to Windows and many people liked that.  I KNOW I am not along here.  I have seen the countless Unity vs Gnome2 wars that go on here.   Even though the decision was made to move on into a different direction, I still feel that upon installation the option should have been given to allow the installer to select an option.  Do you want the old tried and true Gnome Classic, or do you want to try the new Unity.

> In any case, Linux has more variety, more quality, in DE's than it ever has.  Right now is the golden moment for DE's.   You want choice?  This is very likely as good as it gets.

Yes, that IS true. And yes I DID change the DE.  I even tried a couple different ones.  MY main gripe is that Unity kept showing it's ugly head when something went wrong and I didn't appreciate that.  And this time it got STUCK in Unity.  Thus if it wasn't there to begin with and only Gnome, then I wouldn't have this problem in the first place.

Anyway, the decision is in.   I am going to put Ubuntu Studio on my wife's machine too.  Since I am already familiar with it, it seemed like the logical choice to go with.   The best part...NO UNITY!

EDIT:

I was in the process of showing my wife all the Gnome VS Unity posts here (most seem to be in favor of Gnome BTW) and I came across this:

[http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome](http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome)

Hmmmm, so it was a Compiz issue...figures.  Would have been nice to know this beforehand.   More then likely my son's 'button mashing' must have disrupted a setting within Compiz and probably that is what was forcing Unity to be on top.

Oh, well, it is water under the bridge now.  Luckily we DO have most of the stuff on that computer backed up and it is very easy to put the programs back on using the Ubuntu Software Center.


Geo

---

### Post by stinkeye on 2013-09-19
> **jukingeo said:**
> 
EDIT:

I was in the process of showing my wife all the Gnome VS Unity posts here (most seem to be in favor of Gnome BTW) and I came across this:

[http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome](http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome)

Hmmmm, so it was a Compiz issue...figures.  Would have been nice to know this beforehand.   More then likely my son's 'button mashing' must have disrupted a setting within Compiz and probably that is what was forcing Unity to be on top.

Oh, well, it is water under the bridge now.  Luckily we DO have most of the stuff on that computer backed up and it is very easy to put the programs back on using the Ubuntu Software Center.


Geo

You should have two Gnome-classic sessions...
[LIST]
[*]Gnome-classic..............(window manager **compiz** with unity plugin disabled and gnome-panel enabled)
[*]Gnome-classic(no-effects)................(window manager **metacity** with gnome-panel enabled...unity won't start as it's a plugin for compiz)
[/LIST]

---

### Post by buzzingrobot on 2013-09-19
The dependencies that may install various bits and pieces of Unity on a Mate install do *not* affect the appearance or behavior of Mate. Unity is more than the Launcher and the panel.

If there's some configuration tweak Gnome 2 could do that Mate can't, I haven't run into it. After all, it's the same code.

You might look at Linux Mint 15's Mate edition. Based on Ubuntu 13.04 -- minus Unity -- it defaults to one panel on the bottom and uses Mint's own menu.  That can be removed and the old 'Applications Places Setting' menu enabled with a few clicks. (Right click on panel to add/remove applets. The menus are applets.) You can move the panel to the top or add a new one.  Grab an ISO and run it live to check it out.

You can also find howtos to do a minimal Ubuntu install and then add Mate.  This involves installing from the "mini.iso" which is very barebones and downloads packages rather than copying from the DVD. The advantage in this case is it gives you the option of selecting the desktop environment/window manager.  Ignore all the Ubuntu stuff and pick something else.  Then, once that's up, go to mate-desktop.org and follow the install instructions.

---

### Post by jukingeo on 2013-09-23
> **stinkeye said:**
> You should have two Gnome-classic sessions...
[LIST]
[*]Gnome-classic..............(window manager **compiz** with unity plugin disabled and gnome-panel enabled)
[*]Gnome-classic(no-effects)................(window manager **metacity** with gnome-panel enabled...unity won't start as it's a plugin for compiz)
[/LIST]

Actually in the end it didn't matter.  As the other fellow pointed out with his Compiz issue, for some reason no matter what was selected on the login, I just kept getting the Unity desktop.


> **buzzingrobot said:**
> The dependencies that may install various bits and pieces of Unity on a Mate install do *not* affect the appearance or behavior of Mate. Unity is more than the Launcher and the panel.

If there's some configuration tweak Gnome 2 could do that Mate can't, I haven't run into it. After all, it's the same code.

You might look at Linux Mint 15's Mate edition. Based on Ubuntu 13.04 -- minus Unity -- it defaults to one panel on the bottom and uses Mint's own menu.  That can be removed and the old 'Applications Places Setting' menu enabled with a few clicks. (Right click on panel to add/remove applets. The menus are applets.) You can move the panel to the top or add a new one.  Grab an ISO and run it live to check it out.

You can also find howtos to do a minimal Ubuntu install and then add Mate.  This involves installing from the "mini.iso" which is very barebones and downloads packages rather than copying from the DVD. The advantage in this case is it gives you the option of selecting the desktop environment/window manager.  Ignore all the Ubuntu stuff and pick something else.  Then, once that's up, go to mate-desktop.org and follow the install instructions.


Well, I talked things over with my wife and I did say to stay with Ubuntu, but use a different variant such as Xubuntu or Kubuntu.   I am more familiar with the former as Ubuntu Studio uses the same XFCE desktop environment.   In the end I just said, "If you don't mind the extra audio/video applications loaded on the system, then just why not go with Ubuntu Studio".   It seemed like the logical choice since I already am familiar with Ubuntu Studio.

One thing I did notice that being that my wife's machine is slightly newer and thus faster than mine (her's is an Ivy Bridge machine).  Ubuntu Studio boots up VERY fast.  Way faster than Unity Ubuntu.  Another bonus is that my wife certainly can use the photo processing features of Ubuntu Studio and already I am showing her around GIMP. 

The taskbar min, max, restore are in the same places as they are in Windows and I put the taskbar on the bottom.  So far she's happy with it.   But since it is a fresh install, there is just a few things left to do to customize it to her liking.

Another good thing is that we do have the three year support on Ubuntu Studio.   One thing though, I hope Ubuntu Studio NEVER goes with Unity.

Geo

---

### Post by dcstar on 2013-09-26
I don't really understand the issues here, I have been using the Gnome 3 desktop on my 12.04 system (I tried and abandoned Mate because it was full of problems and missing Gnome 2 utilities) by simply following the instructions that used to be at the top of these forums. I am sure a quick search should find them or the many other HOWTOs already on the 'net on this subject.

Not exactly the same as Gnome 2 but close enough for me.

---

### Post by cmcanulty on 2013-09-26
in fallback or classic you can add , move, or delete panels as you wish just use win+alt+rt click for all the setup options

---

### Post by 3rdalbum on 2013-09-26
> **jukingeo said:**
> 
I did that already.  I said so above.  My wife was running with Gnome Classic for a LONG time now.   However, as I  also mentioned above, my kids were using the machine and pushed some sort of key combination that 'locked' Unity in no matter what you select on the login.

I do wish you would stop saying that - there is NO key combination you can POSSIBLY press that will prevent you from being able to log into a different desktop. The thing about kids is that they sometimes aren't as truthful as you'd hope - when I was a kid, if I messed around with my father's computer and caused a problem, I certainly wouldn't have owned up to messing around. I've no idea what they did, but it certainly wasn't a "key combination".

> Even though the decision was made to move on into a different direction, I still feel that upon installation the option should have been given to allow the installer to select an option.  Do you want the old tried and true Gnome Classic, or do you want to try the new Unity.

Unity was available to be installed in Ubuntu 10.10 and co-installed with Gnome 2.x in Ubuntu 11.04. That was ample transition time, considering that this is Linux and it moves quickly. Also, considering that Unity is based on Gnome 3 and it took some work to allow Gnome 2 and Gnome 3 to coexist.

If you've been out of the loop since 10.04, that's no fault of Ubuntu's. The software selection changes from version to version, and just because Banshee gets put into the default installation instead of Rhythmbox, doesn't mean that Ubuntu is "shoving Banshee down your throat". It just means that it's the default music player. You want something different? Fine and great, just install the different one.

Ubuntu has always been about giving you a good general-purpose desktop by default, and then you can customise it afterward. Before Ubuntu came along, most distros asked you exactly what packages you want at installation time, which was rather confusing for new users. All the others had a massive default install containing three web browsers, five text editors, an icon editor, a text-to-speech toy, several OpenGL games that wouldn't work out-of-the-box because you had no graphics drivers yet, two music players, two video players, and maybe seven different choices of desktop clock. Ubuntu is NOT in the business of asking "What desktop do you want", it's in the business of getting you up and running quickly, and then you can install the desktop you want. Or hey, install a respin that has the desktop you want.

If you disagree with that, fine - there's plenty of distros that do things the old way and will happily make you download a 4.4 gigabyte installation DVD with three different desktops on it. I think Ubuntu, with its rapid changes, was never really for you.

---

### Post by jukingeo on 2013-09-29
> **dcstar said:**
> I don't really understand the issues here, I have been using the Gnome 3 desktop on my 12.04 system (I tried and abandoned Mate because it was full of problems and missing Gnome 2 utilities) by simply following the instructions that used to be at the top of these forums. I am sure a quick search should find them or the many other HOWTOs already on the 'net on this subject.

Not exactly the same as Gnome 2 but close enough for me.

If you read through the whole thread this is the issue I was having:

[http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome](http://ubuntuforums.org/showthread.php?t=2133572&highlight=unity+gnome)

Somehow one of my twin boys, whom is 6 years old, was playing a game and activated some kind of key combination that no matter how you logged in, Unity, Gnome Classic, Gnome Classic (no effects).  It ALWAYS came up in Unity.   Apparently as it seems when you install a new desktop environment it lays ON TOP OF Unity....it doesn't replace it.   Unity uses Compiz which was something I never liked.  Apparently my kids did something that screwed up Compiz in which it always put Unity ON TOP.    In effect this was kind of like jamming Unity down my throat and I didn't appreciate that.   So OFF the system it went.   So as long as Standard Ubuntu uses Unity/Compiz and there are no easy way to correct the issues I mentioned above, then I am no longer going to use it.   Luckily the other variants of Ubuntu still have their desktop environments as it was laid out in Windows.   Thusfar, I am going to stick with Ubuntu Studio.

Geo

---

### Post by jukingeo on 2013-09-29
> **3rdalbum said:**
> I do wish you would stop saying that - there is NO key combination you can POSSIBLY press that will prevent you from being able to log into a different desktop. The thing about kids is that they sometimes aren't as truthful as you'd hope - when I was a kid, if I messed around with my father's computer and caused a problem, I certainly wouldn't have owned up to messing around. I've no idea what they did, but it certainly wasn't a "key combination".

No, I am not going to stop saying it.  Key combination or not, there is something WRONG with Ubuntu Unity.  Did you read the other thread I posted up in here?  It seems like the pro Unity people here seem to skim right over that.   Nevermind the if the fault lies at my kids for breaking the desktop, the fact remains that I couldn't correct the issue.   I wanted to get rid of Unity, that didn't work, so off the system the OS went.

> 

If you've been out of the loop since 10.04, that's no fault of Ubuntu's.

No, not been out of the loop.  I just prefer to use LTS versions 

> 
 The software selection changes from version to version, and just because Banshee gets put into the default installation instead of Rhythmbox, doesn't mean that Ubuntu is "shoving Banshee down your throat". It just means that it's the default music player. You want something different? Fine and great, just install the different one.

Yes, fine and true.  But if something went wrong with Rhythmbox and the system defaulted to Banshee all the time...I would consider that being jammed down my throat.

> 
Ubuntu has always been about giving you a good general-purpose desktop by default, and then you can customise it afterward. Before Ubuntu came along, most distros asked you exactly what packages you want at installation time, which was rather confusing for new users. All the others had a massive default install containing three web browsers, five text editors, an icon editor, a text-to-speech toy, several OpenGL games that wouldn't work out-of-the-box because you had no graphics drivers yet, two music players, two video players, and maybe seven different choices of desktop clock. Ubuntu is NOT in the business of asking "What desktop do you want", it's in the business of getting you up and running quickly, and then you can install the desktop you want. Or hey, install a respin that has the desktop you want.

Yeah, but you don't get the issue.  I HAD changed the desktop, something went wrong and it went back to Unity.  I tried to correct the problem and all I got was Unity.   THAT is the part I don't like.   I think it would have been nicer to have an option in the beginning at install to offer the old Gnome or Unity.

> 
If you disagree with that, fine - there's plenty of distros that do things the old way and will happily make you download a 4.4 gigabyte installation DVD with three different desktops on it. I think Ubuntu, with its rapid changes, was never really for you.

No, I been using Ubuntu for a long time and for the most problem had no issues with it.  Perhaps I might like the direction it is heading.  I think Ubuntu is STILL for me, but not Unity.  They can keep it along with the other Unity lovers out there.

---

### Post by buzzingrobot on 2013-09-29
If your system was broken to the extent that it was simultaneously displaying elements of two different interfaces, then the obvious recourse was a reinstallation. 

I've successfully installed and used several DE's on Ubuntu without encountering your problem.  So have many thousands of other users.  If your experience was common, it would be commonly known and expereinced.

The fixation on removing/replacing Unity is misplaced and unnecessary. When you switch to another DE, the Unity interface does not display. It isn't necessary to remove Unity to avoid using it. 

No keyboard combination in the sense you use the phrase exists.  Keystrokes are interpreted and acted on.  Sounds like your kids triggered something that wasn't benign. I'd put my money on a bug in whatever app/game they were using.

---

### Post by CatKiller on 2013-09-29
The thread you posted describes the very simple solution to stopping Unity in a Compiz session.

---

### Post by JKyleOKC on 2013-09-29
> **jukingeo said:**
> No, I am not going to stop saying it.  Key combination or not, there is something WRONG with Ubuntu Unity.  Did you read the other thread I posted up in here?  It seems like the pro Unity people here seem to skim right over that.   Nevermind the if the fault lies at my kids for breaking the desktop, the fact remains that I couldn't correct the issue.   I wanted to get rid of Unity, that didn't work, so off the system the OS went.It sounds as if you're well on the way to solving the immediate problem. After reading the whole thread, my best guess as to what happened is that some of the boys' key-pounding got them into the Compiz setup dialogs, and in trying to get out of it they did in fact change some critical setting. They could also have done the same thing by changing some other system setting though. To correct the issue, of course, you have to find the root cause of it -- and all too often that's so difficult that re-installing everything is the only practical solution (as you discovered).

Giving them their own account, with no administrator privileges, would limit damage to their own account and not impact your wife's settings at all. It's quite easy to disable display of the "recovery" options from the GRUB menus, although doing so makes it more difficult to recover from actual system crashes. In your place, though, I would accept that tradeoff to keep inquisitive youngsters from getting into the works...

You might investigate the benefits of having your "/home" directory on a separate partition from the rest of the system. Many of us do this, to protect our settings and data when we want to make major system changes such as switching to a different o/s within the Linux family. There's a lot of instruction and discussion about this in the forums.

Finally, I'm no fan of Unity myself, and have gone so far as to try installing Debian on a test system in place of Xubuntu (which has been my preferred flavor of Ubuntu since 2007) to see how different it might be. I found it quite easy to use, and so much like Xubuntu that I'll have no problem at all moving to it if Canonical eventually makes *buntu unacceptable to me. All of the *buntu variants are, after all, based on Debian itself, so much of the look and feel are the same. The one major difference I've seen so far is in the support areas; the forums here are the most helpful I've encountered anywhere in the more than 40 years I've been dealing with computers!

---

