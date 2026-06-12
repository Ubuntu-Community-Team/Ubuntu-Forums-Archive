---
title: "HOWTO: functional eye-candy with Avant-Window-Navigator"
date: 2008-04-22
forum: General Help
---

### Post by reacocard on 2008-04-22
This thread is a repost of my old guide, which can be found here: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

[CENTER][COLOR="Red"]_**[SIZE="7"]Attention: [/SIZE]**_[/COLOR]
[SIZE="3"]Due to my lack of time/interest and my recent change of distro to Archlinux, these repositories are no longer maintained. I would instead recommend that you follow the instructions outlined here: [http://wiki.awn-project.org/Installation:Ubuntu#PPA](http://wiki.awn-project.org/Installation:Ubuntu#PPA)[/SIZE]


_**[SIZE="6"]Info:[/SIZE]**_[/CENTER]

**_What is it?:_**
AWN is a compositing dock-like taskbar. It is similar to the dock in OSX, but supports features such as custom themes, applets that can do anything from displaying battery life to showing Dilbert, and much more.

**_Links:_**
AWN in Launchpad: [https://launchpad.net/awn](https://launchpad.net/awn)
AWN-Extras in LP: [https://launchpad.net/awn-extras](https://launchpad.net/awn-extras)
The developer's blog: [http://njpatel.blogspot.com/](http://njpatel.blogspot.com/)
Official AWN forums: [http://www.planetblur.org/hosted/awnforum/index.php](http://www.planetblur.org/hosted/awnforum/index.php)
Official AWN IRC channel: #awn on irc.freenode.net

**_Screenshots:_**

AWN (v0.2): 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=59682&stc=1&d=1203038515[/IMG]

[CENTER][COLOR="Red"]_**[SIZE="6"]Notes (please read!):[/SIZE]**_[/COLOR][/CENTER]

**AWN requires a compositor** (like beryl or compiz) to work properly. See the FAQ below for more information. 

If you have previously installed some other version of AWN, **you should remove it** before you begin. In most cases my guide will not have any trouble wiht a previous install, but odd bugs have been known to occur.

The instructions provided here install an **unstable, development** version of AWN. This means that you get new features and bugfixes much faster, but things may break without warning. There are stable packages of AWN available in universe and from getdeb.net. If you require absolute stability, it is recommended you use one of those sources instead.

**AWN is still under heavy development, and contains many bugs.** *Please* help development by reporting any bugs you find on Launchpad. Bugs in applets should be reported to the [awn-extras project](https://launchpad.net/awn-extras) instead of main AWN.

Terminal commands should be pasted in **one line at a time**, unless otherwise noted. The terminal is located in Applications->Accessories->Terminal.

[CENTER]_**[SIZE="6"]Installing:[/SIZE]**_[/CENTER]

**DISCLAIMER:** I do my best to keep the packages in this repo high-quality. However, 3rd party repositories such as this one are _completely_ unsupported by Ubuntu. Any problems caused by this repo should be reported to me in this thread, not to Ubuntu.

**IMPORTANT:** I support **only** Ubuntu Hardy (8.04) and Ubuntu Intrepid (8.10). This does not include derivative distros such as Mint. Though you are welcome to try using my packages under derivatives, I can provide no support for doing so.

Before we begin, **[COLOR="Red"]make sure you have all the needed ubuntu repositories[/COLOR]** installed, namely universe and ubuntu-updates. This can be done in System -> Administration -> Software Sources by enabling 'recommended updates' under the 'Updates' tab, and also enabling 'Community-maintained Open Source software' under the 'Ubuntu Software' tab.

Now open a terminal (Applications -> Accessories -> Terminal), we'll be pasting a lot of commands.  Remember, paste **[COLOR="Red"]only 1[/COLOR]** line at a time unless otherwise directed.

First, add my AWN repo by running the appropriate set of commands:

Hardy:
```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list
```

Intrepid:
```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main'  |  sudo tee -a /etc/apt/sources.list
```

Now update your software lists. If you are asked any questions during this, respond with 'y'.
```
sudo apt-get update
```

Then install AWN, again, answer 'y' to any questions.
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

That's it! You can now start AWN from Applications->Accessories->Avant Window Navigator.
If installation fails, go back to the beginning and make sure you followed all instructions correctly, and then check the FAQ section at the bottom of this guide.

_Available packages:_
[INDENT]avant-window-navigator-bzr - the latest development version of AWN.
awn-core-applets-bzr - extra applets for AWN (development version)
libawn0-bzr - applet library for AWN
libawn-bzr-dev - headers for the AWN applet library. Install this only if you need to compile applets from source.
python-awn-bzr - python bindings for libawn
[/INDENT]
All -bzr packages are updated periodically from AWN bzr.

[CENTER]_**[SIZE="6"]Updating:[/SIZE]**_[/CENTER]

The repository will automatically keep you up-to-date in the same manner that ubuntu updates the rest of your software. You can update manually with these commands:
```
sudo apt-get update
sudo apt-get upgrade
```

[CENTER]_**[SIZE="6"]Uninstalling:[/SIZE]**_[/CENTER]

```
sudo apt-get remove --purge avant-window-navigator-bzr awn-manager-bzr awn-core-applets-bzr libawn0-bzr
```

[CENTER]_**[SIZE="6"]FAQs:[/SIZE]**_[/CENTER]

**Q: Can I put AWN on another side of my screen?**
A: Not currently, but this is a planned feature for a future version of AWN.

**Q: When does the next version of AWN come out?**
A: When it's ready.

**Q: Can I use AWN as just a launcher, not a taskmanager?**
A: Not with my packages. There is an applet in development that will allow this, however it is written in Vala which I do not support in my repo. (See below for why.)

**Q: There's a big ugly black bar around AWN! How do I get rid of it?**
A: You need to be running a compositor like Beryl or Compiz. Other compositors such as xfwm4 and xcompmgr will also work, but are less tested and may exhibit bugs.

**Q: Why does AWN depend on so much of Gnome? I'm a kde/xfce/other user who doesn't want to be burdened by all that ******
A: The original developer chose to build on top of Gnome because it was what he was familiar with and could develop the fastest. However, there has been a lot of work poured into making a desktop-agnostic version of AWN that eliminates most of these dependencies. You will need to compile AWN from source to enable agnostic.

**Q: Some of the applets won't load! I only get a white line/nothing!**
A: Several of the applets are currently not functional in my builds. Others may not work without installing additional dependencies.

Broken: standalone taskmanager
Needs Deps: Affinity (tracker or beagle), TsClient (tsclient), Volume Control (python-alsaaudio), Mail (python-feedparser)

**Q: Why don't you support Vala applets?**
A: AWN requires a newer version of Vala than is available in Ubuntu. That means that I would have to package a newer version of Vala as well to be able to provide this, which is not only more effort than I am willing to expend, but also can interfere with Ubuntu's Vala packages. So, until such time as a suitable version of Vala becomes available in Ubuntu I cannot build in support for Vala applets.

**Q: I want my AWN to be curved like I see in all those screenshots!**
A: In gconf-editor, set apps->avant-window-navigator->bar->bar_angle to -1.

**Q: I heard Apple patented the dock! Does this mean AWN is illegal?**
A: No, see [https://answers.launchpad.net/awn/+question/47479](https://answers.launchpad.net/awn/+question/47479)

---

### Post by uschxc on 2008-04-22
> **reacocard said:**
> 
There are two ways to install AWN: from my apt repository, or from source. **If you are using Gutsy (7.10), using the repository is the recommended method of installation. For all other versions of Ubuntu, compiling from source is the recommended method.** You should use **only one** of these two methods to install AWN. If you decide to change which method you use, make sure to **completely remove** the previous AWN installation before following the guide. (see 'Uninstalling', below, for instructions)

even hardy?  even though you have a repository for it?  will this change in the next couple days?

---

### Post by reacocard on 2008-04-22
> **uschxc said:**
> even hardy?  even though you have a repository for it?  will this change in the next couple days?

sorry, forgot to remove that when I added the hardy repo. You should definitely prefer the repo over source when available.

EDIT: guide fixed

---

### Post by Hybrid86 on 2008-04-22
I've been using the shiny switcher app, but after finally updating my repos and updating awn, it now appears as a broken white bar. Aggravated, I attempted to simply disable the app, only to discover that I can no longer open up "preferences". Clicking on it yields no result.
Has anyone else had this problem/know how to solve it?

---

### Post by ubulap on 2008-04-22
Hybrid86, remove awn completely following the steps in this post for repository, then reinstall again.
It should solve your issue.

---

### Post by thunderwolf333 on 2008-04-22
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

im getting that error please help? :D

nevermind i restarted and it worked. lol

---

### Post by reacocard on 2008-04-22
> **thunderwolf333 said:**
> ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

im getting that error please help? :D

nevermind i restarted and it worked. lol

that error usually means you have another software management tool (like synaptic) open already. Since only one tool can access the software database at a time, it gives that error. Closing the other application will make this error go away without a reboot.

---

### Post by adult swim on 2008-04-23
great work reacocard!

---

### Post by techno-mole on 2008-04-23
hello.
i used this guide to install awn, which worked, well almost.
it seems for some reason i can either have launchers, or applets, but not both, if i have say a launcher for firefox it will work, but if i then add an applet the firefox launcher will disappear, and vice versa, i cant seem to get an applet and a launcher to work together.

i used this method for gutsy and it worked fine, any ideas as to what it might be ? ive tried removing everything and re-installing but i still get the same issue.
cheers

---

### Post by Hybrid86 on 2008-04-23
Uninstalled and reinstalled. Thanks.

---

### Post by reacocard on 2008-04-23
> **techno-mole said:**
> hello.
i used this guide to install awn, which worked, well almost.
it seems for some reason i can either have launchers, or applets, but not both, if i have say a launcher for firefox it will work, but if i then add an applet the firefox launcher will disappear, and vice versa, i cant seem to get an applet and a launcher to work together.

i used this method for gutsy and it worked fine, any ideas as to what it might be ? ive tried removing everything and re-installing but i still get the same issue.
cheers

Are you sure the launchers aren't just merging into your running tasks? Try adding a Firefox launcher when no firefox windows are open; does that then work when you add an applet?

---

### Post by Hybrid86 on 2008-04-23
Question about the affinity app:

1. is there a way to change the icon?
2. How do I make it index my system (or am I completely misunderstanding its purpose)?

---

### Post by reacocard on 2008-04-23
> **Hybrid86 said:**
> Question about the affinity app:

1. is there a way to change the icon?
2. How do I make it index my system (or am I completely misunderstanding its purpose)?

1. No

2. Affinity doesn't actually index your system itself. Instead, you have to install tracker or beagle to do the actual indexing, and then Affinity will allow you to search the index they generate.

---

### Post by Hybrid86 on 2008-04-23
> **reacocard said:**
> 1. No

2. Affinity doesn't actually index your system itself. Instead, you have to install tracker or beagle to do the actual indexing, and then Affinity will allow you to search the index they generate.

I see. Which would you suggest?

---

### Post by reacocard on 2008-04-23
> **Hybrid86 said:**
> I see. Which would you suggest?

I recommend tracker because it uses slightly less resources, but both work well.

---

### Post by techno-mole on 2008-04-24
ive got it sorted now, i did try what was suggested but had no luck.
in the end i removed awn, then removed the repos for it, reloaded synaptic, then added the repos again, reloaded synaptic and installed awn again, and it worked.
although the stacker applets didnt work (just showed up as a white line) this morning there was an update for the core applets, did that and the stackers work fine now.
cheers

---

### Post by martin saint martin on 2008-04-24
installed without a problem, thank you.  one problem post-install.  after a restart or shutdown the launchers on the dock will no longer be their.  how could i save my launchers from oblivion?

---

### Post by kgr132 on 2008-04-24
martin saint martin: You didn't say if AWN is working, just without applets and launchers, or if it's crashing on boot up. If it's crashing on boot up, is Compiz working after you reboot? On my Dell laptop (nVidea graphics card), Compiz apparently doesn't start up correctly with Hardy. If I try to run avant-window-navigator in a terminal, I get a message that the screen isn't composited (i.e. Compiz isn't working correctly.) If I restart the Compiz window manager after booting up, then load AWN, it works fine. Good Luck.

---

### Post by Janpreet on 2008-04-24
I just installed AWN without any hassle but unfortunately when I restart my computer or logoff,  AWN disappears and I have to manually start it.

Yes my compiz always works even after restarting the computer. I have made sure startup behavior is enabled.

Also I am not able to add any Launchers on AWN. So to sum up I have two problems : -

1. AWN doesn't start automatically
2. Not able to add any launchers like fire, skype, pidgin etc.


Any help would be appreciated. :)

---

### Post by Stormspireiv on 2008-04-25
> **Janpreet said:**
> I just installed AWN without any hassle but unfortunately when I restart my computer or logoff,  AWN disappears and I have to manually start it.

Yes my compiz always works even after restarting the computer. I have made sure startup behavior is enabled.

Also I am not able to add any Launchers on AWN. So to sum up I have two problems : -

1. AWN doesn't start automatically
2. Not able to add any launchers like fire, skype, pidgin etc.


Any help would be appreciated. :)

1. To start AWN automatically on logon, go to your session preferences System>Preferences>Sessions and click on New. Name it however you like and for the command:
```
avant-window-navigator
```

2. Your launchers will not appear immediately after adding them and the refresh button generally won't add them. Try closing out AWN and restarting it to get your new launchers to appear. You can then move them around and it will show the changes in real time.

---

### Post by martin saint martin on 2008-04-25
awn is working, but the launchers that i have added will not stay in/on the dock after a reboot/restart.  the applets will stay but no launchers will.  the way i add launchers maybe why things are acting up.  what i'll do is from the gnome menu i'll create a launcher on the desktop then drag/drop the launcher onto the dock.  if i leave the launchers on the desktop and the dock awn will have them on the dock after a restart, if i delete them from the desktop(but not the dock) the said launchers will stay until i do the old off/on. this is the only way i know how to ad a launcher, due to the fact that i'm not sure how to find the commands for the launchers that i want to add.

---

### Post by reacocard on 2008-04-25
> **martin saint martin said:**
> awn is working, but the launchers that i have added will not stay in/on the dock after a reboot/restart.  the applets will stay but no launchers will.  the way i add launchers maybe why things are acting up.  what i'll do is from the gnome menu i'll create a launcher on the desktop then drag/drop the launcher onto the dock.  if i leave the launchers on the desktop and the dock awn will have them on the dock after a restart, if i delete them from the desktop(but not the dock) the said launchers will stay until i do the old off/on. this is the only way i know how to ad a launcher, due to the fact that i'm not sure how to find the commands for the launchers that i want to add.

You can just drag/drop them from the menus in fact.  You can also drag from /usr/share/applications.

---

### Post by kaivalagi on 2008-04-25
Just upgraded from gutsy to hardy, uninstalled awn, changed the repo setting in source.list from gutsy to hardy, installed awn again.

Everything works, however, for some strange reason something triggers the tray icons to shift upwards? See screenshot

What do you suggest I do to remedy the issue? Any ideas?

Thanks

---

### Post by Nozem on 2008-04-25
I'm having a weird problem with AVN... some of my launchers won't start. 

For instance: I've added Firefox, Thunderbird, Pan and Audacious to my dock. When I try to start the first two, Ubuntu tries to load them, but seems to fail. Pan and Audacious however, do work.

The launchers were dragged from the desktop onto the dock. The desktop versions all work properly. Anyone an idea what causes this?

---

### Post by Payteer on 2008-04-25
On the old awn when I opened say mail or FF it would appear as an icon in AWN so if I minimised it was always there.  In this new version, this does not happen, can someone please tell me where I have gone wrong on this?
Hardy 8.04

---

### Post by JacksonDane on 2008-04-25
> **Nozem said:**
> I'm having a weird problem with AVN... some of my launchers won't start. 

For instance: I've added Firefox, Thunderbird, Pan and Audacious to my dock. When I try to start the first two, Ubuntu tries to load them, but seems to fail. Pan and Audacious however, do work.

The launchers were dragged from the desktop onto the dock. The desktop versions all work properly. Anyone an idea what causes this?

Having the same problem here, as well as the dock disappears when I make any changes in AWN manager which forces me to have to restart it.

---

### Post by CarpKing on 2008-04-25
> **Nozem said:**
> I'm having a weird problem with AVN... some of my launchers won't start. 

Same problem here.  It's inconsistent; launchers that work before a restart of AWN often don't work afterward.  Usually if I add a second launcher from the same place it will work; when I try to delete the duplicate from AWN manager AWN crashes and when it restarts I'm back to a mix of working and non-working launchers.  These were all dragged from the menu.  

I've deleted all the AWN config files that I could find and did a complete removal and installation of all AWN-related packages.  Now AWN seems to come by default with a single unremoveable Firefox launcher that doesn't work.

---

### Post by martin saint martin on 2008-04-25
did a drag/drop from the gnome-menu instead of creating a launcher on the desktop and my problem has been solved.  thank you reacocard for this how-to and for the help with setting up the dock.

---

### Post by keypox on 2008-04-25
how can i get windows to minimize to avant not to the bar on the bottom?  I thought i had it working last night but now it is not.  Im running 8.04, the manager has no option to do so?

---

### Post by martin saint martin on 2008-04-25
i was just wondering where i might find some themes for awn?  at this point it looks like all i've got is the default theme.

---

### Post by reacocard on 2008-04-25
> **keypox said:**
> how can i get windows to minimize to avant not to the bar on the bottom?  I thought i had it working last night but now it is not.  Im running 8.04, the manager has no option to do so?

You have to remove the other window list, avant is intended to replace that bar, not supplement it.

---

### Post by reacocard on 2008-04-25
> **martin saint martin said:**
> i was just wondering where i might find some themes for awn?  at this point it looks like all i've got is the default theme.
There's no central place to find them, so google's your best bet.

---

### Post by Payteer on 2008-04-25
My active tasks are not appearing in my AWN, what do I do.  I am on Hardy.

---

### Post by russianbandit on 2008-04-25
> **Payteer said:**
> My active tasks are not appearing in my AWN, what do I do.  I am on Hardy.

I'm also on Hardy and seeing some strange behavior.
I couldn't get the launchers to show up at first, after I got the launchers to show up I can't get active tasks to show now.

---

### Post by Nozem on 2008-04-25
Regarding the unresponsive launchers, I seem to have solved the problem by rerverting back to the 'standard' version of AWN. That is: the non-SVN version that is currently avaiable from Hardy's own repositories.

Although it doesn't have the -core package (and thus no applets etc. - but please correct me if I'm wrong) all the launchers -DO- work.

---

### Post by SoulSmasher on 2008-04-25
thanks for the guide :), but ive an styling issue

at your old guide, also the applications' positions were curved, now they don't at startup :(

i also have an issue, if a new application is opened, it stays a bit more top position from normal, i don't know if this is normal, but their position would be cool next to the applets

with this screenshot you can understand my issue better
[[IMG]http://img216.imageshack.us/img216/299/screenshotth8.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshotth8.png) [[IMG]http://img103.imageshack.us/img103/8815/screenshot1gc8.th.png[/IMG]](http://img103.imageshack.us/my.php?image=screenshot1gc8.png)

(firefox and amarok's positions are a bit more upper than normal applets, sometimes other applets go up , too. and mouse hover , or opening a new applicaiton doesn't fix the issue) 


when a bit more programs were opened , it ( with it, i mean the shape that applications' position generate) looks much more like a curve, but shouldn't it be a smooth curve at screenshot ? like i was using at your old guide

thanks for this great guide :)

---

### Post by russianbandit on 2008-04-25
To follow up on my post:
The launchers only launch one instance of the program. I cannot launch 2 firefox applications. Also the active tasks do show in an area separated from the launchers by a vertical bar, **however**, only the tasks that were started NOT from the launchers show up in active task list. The task that I start using the launchers do not show up anywhere.

I downloaded the AWN using the standard Hardy repository, not the BZR one.

---

### Post by keypox on 2008-04-25
> **reacocard said:**
> You have to remove the other window list, avant is intended to replace that bar, not supplement it.

Ok i removed the bottom bar but that didnt do anything but remove it.  Still windwos do not minimize to the avant thing.

---

### Post by reacocard on 2008-04-25
> **keypox said:**
> Ok i removed the bottom bar but that didnt do anything but remove it.  Still windwos do not minimize to the avant thing.

it may require a reboot to take full effect.

---

### Post by reacocard on 2008-04-25
> **SoulSmasher said:**
> thanks for the guide :), but ive an styling issue

at your old guide, also the applications' positions were curved, now they don't at startup :(

i also have an issue, if a new application is opened, it stays a bit more top position from normal, i don't know if this is normal, but their position would be cool next to the applets

with this screenshot you can understand my issue better
[[IMG]http://img216.imageshack.us/img216/299/screenshotth8.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshotth8.png) [[IMG]http://img103.imageshack.us/img103/8815/screenshot1gc8.th.png[/IMG]](http://img103.imageshack.us/my.php?image=screenshot1gc8.png)

(firefox and amarok's positions are a bit more upper than normal applets, sometimes other applets go up , too. and mouse hover , or opening a new applicaiton doesn't fix the issue) 


when a bit more programs were opened , it ( with it, i mean the shape that applications' position generate) looks much more like a curve, but shouldn't it be a smooth curve at screenshot ? like i was using at your old guide

thanks for this great guide :)

it's a known bug with curves, and one of the reason curve's isn't available via awn-manager yet. no fixes at this point.

---

### Post by Parlay on 2008-04-25
Thanks! I'd been trying to get AWN running for a while, and when I went Hardy I decided to give it another shot!

Thanks!  I got it running this time around.

---

### Post by SaddaGocaraRupa on 2008-04-25
Hey there,

got AWN up and running i amd it looks great, with one minor bug. There's a [white line]("http://i17.photobucket.com/albums/b94/gautsch/Screenshot-6.png") to the right of it I just can't get rid of since upgrading to HH this morning. Any idea how I could make it go away?
Cheers,

-SGR

---

### Post by CarpKing on 2008-04-26
> **SaddaGocaraRupa said:**
> Hey there,

got AWN up and running i amd it looks great, with one minor bug. There's a [white line]("http://i17.photobucket.com/albums/b94/gautsch/Screenshot-6.png") to the right of it I just can't get rid of since upgrading to HH this morning. Any idea how I could make it go away?
Cheers,

-SGR

That means that an applet is failing to start.  Run avant-window-navigator in a terminal to (hopefully) find out which one and why.  

As for my problem, it isn't going away.  If I have a taskbar as well, it has an entry saying "starting gnome terminal" or whatever while the icon is bouncing, but both go away without starting the program.  This is sporadic, though it seems that launching from the menu and then closing increases the chances of the launcher working for awhile.

---

### Post by SomeGuyDude on 2008-04-26
Did anyone else get a weird upgrade here? I suddenly have a whole slew of new packages and for some reason the "update" uninstalled the AWN-manager-bzr, but now there's "agnostic" packages?

---

### Post by reacocard on 2008-04-26
> **SomeGuyDude said:**
> Did anyone else get a weird upgrade here? I suddenly have a whole slew of new packages and for some reason the "update" uninstalled the AWN-manager-bzr, but now there's "agnostic" packages?

I've changed some things in the way the packages work, hopefully it'll fix the launcher issues people have been having. You were unlucky to get the bad awn-manager update, that's fixed now, after the next time you upgrade awn awn-manager will be installable again.

The -agnostic packages are currently broken, I'll post more about them once they're working. Just ignore them for now.

---

### Post by SoulSmasher on 2008-04-26
> **reacocard said:**
> it's a known bug with curves, and one of the reason curve's isn't available via awn-manager yet. no fixes at this point.

thanks for the info. and also thanks for your great tutorial :)

---

### Post by Dave in Tempe on 2008-04-26
EDIT: Nevermind, obsolete by the time I posted.

---

### Post by ayoli on 2008-04-26
I just got an update that have removed awn-manager and python-libawn-bzr.
And now, I can't run the manager (no such file) and have some applet issues.
The stack crashes at start with this error :
```
Traceback (most recent call last):
  File "/usr/lib/awn/applets/stacks/stacks_applet.py", line 27, in <module>
    import awn
ImportError: No module named awn
```
and plugger and trasher applet (with curved gui) show only a white line.

edit: I guess that the missing python-libawn-bzr is the cause of all this problems, apt-get report a dep issue :
```
Les paquets suivants contiennent des dépendances non satisfaites*:
  python-libawn-bzr: Dépend: libawn-bzr (= 0.3.1.bzr232.1~hardy) mais 0.3.1.bzr232.3~hardy devra être installé
E: Paquets défectueux
```

---

### Post by CarpKing on 2008-04-26
Update manager shows updates for avant-window-navigator-bzr, awn-manager-bzr, and libawn-bzr but says that they are not installable.

---

### Post by reacocard on 2008-04-26
ayoli, carpking: try completely removing all awn packages and reinstalling. I changed the names of a couple of packages and that might be messing with the dependency handling.

---

### Post by kaivalagi on 2008-04-26
Or in Synaptic, reload, mark all upgrades and apply, worked for me

Use customer filters, marked changes to see what's going to happen on applying

---

### Post by CarpKing on 2008-04-26
> **reacocard said:**
> ayoli, carpking: try completely removing all awn packages and reinstalling. I changed the names of a couple of packages and that might be messing with the dependency handling.

Thanks!  Worked like charm.

---

### Post by FoH on 2008-04-26
I've been using your PPA for a while now, and it's working great. It's very stable so far, I have no problems to report. I do miss one thing though, and that's a tidbit of information as to why I should upgrade every time I get an upgrade-advisory regarding the content in your PPA. As of now, I do every time and so far there's no problem, but I'm quite clueless about the improvements as well

So, short question: Where do I go to find information regarding the versions in your repository? I'm thinking of some sort of changelogs. Does your versions follow the AWN trunk so that I can check out their versioning system for bugfixes etc?

Thank you for all your effort!

Edit: Oops, my signature isn't right anymore. I'm using Hardy as of now :P

---

### Post by Dave in Tempe on 2008-04-26
> **reacocard said:**
> ayoli, carpking: try completely removing all awn packages and reinstalling. I changed the names of a couple of packages and that might be messing with the dependency handling.

Thanks, this worked for me.  Mudders are awesome.  Throwing the best parties in college, developing AWN...what can't Mudders do?

---

### Post by Thanh-BKK on 2008-04-27
Hello.

Please help me out here.... i am going thru hell and back to get a single feature working.

First tried to install "AWN Extras" the "manual way" (from source), only to find that after downloading over 300 MEGABYTES (!!!!!) dependencies the thing would still not install, giving me a "make" error............. 

Then i did it the way described here, so i got AWN working again and a bunch of applets available, too, however tjhe single one i'm after is not available AGAIN....

"Standalone Launcher", pleeeeeeease!! After i have wasted several straight DAYS trying to get this to work, i feel i deserve it...........

Also, how do i put a launcher there that opens a HDD partition? In an older AWN version (which also failed to ever get the "standalone launcher"!) there was an option "location" which is no longer prsent here, and dragging/dropping the drive icon does nothing....

Please help me.... before i set the whole house on fire for frustratuion.

Best regards......

Thanh

---

### Post by ayoli on 2008-04-27
> **reacocard said:**
> ayoli, carpking: try completely removing all awn packages and reinstalling. I changed the names of a couple of packages and that might be messing with the dependency handling.

Thanks for the hint, this has fixed the issue :)

---

### Post by SaddaGocaraRupa on 2008-04-27
> **CarpKing said:**
> That means that an applet is failing to start.  Run avant-window-navigator in a terminal to (hopefully) find out which one and why.  

As for my problem, it isn't going away.  If I have a taskbar as well, it has an entry saying "starting gnome terminal" or whatever while the icon is bouncing, but both go away without starting the program.  This is sporadic, though it seems that launching from the menu and then closing increases the chances of the launcher working for awhile.

cheers. I found something, but I'm not sure what it means. Here's what the terminal says:

```
gg@lappy:~$ avant-window-navigator
Screen is composited.
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/rhythmbox.desktop
LOADED : /usr/share/applications/nautilus-home.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/gthumb.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/affinity.desktop

** (awn-applet-activation:6299): WARNING **: This desktop file does not exist /usr/lib/awn/applets/affinity.desktop


```
:confused:

---

### Post by hessiess on 2008-04-27
trying to install awn-extras. cannot find a package and it wont configure. awn is already installed and working

```
checking for AWN... configure: error: Package requirements (awn) were not met:

No package 'awn' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by reacocard on 2008-04-27
> **hessiess said:**
> trying to install awn-extras. cannot find a package and it wont configure. awn is already installed and working

```
checking for AWN... configure: error: Package requirements (awn) were not met:

No package 'awn' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I take it you installed awn from the repo? the awn-core-applets-bzr package already contains most of awn-extras.

---

### Post by reacocard on 2008-04-27
> **Thanh-BKK said:**
> Hello.

Please help me out here.... i am going thru hell and back to get a single feature working.

First tried to install "AWN Extras" the "manual way" (from source), only to find that after downloading over 300 MEGABYTES (!!!!!) dependencies the thing would still not install, giving me a "make" error............. 

Then i did it the way described here, so i got AWN working again and a bunch of applets available, too, however tjhe single one i'm after is not available AGAIN....

"Standalone Launcher", pleeeeeeease!! After i have wasted several straight DAYS trying to get this to work, i feel i deserve it...........

Also, how do i put a launcher there that opens a HDD partition? In an older AWN version (which also failed to ever get the "standalone launcher"!) there was an option "location" which is no longer prsent here, and dragging/dropping the drive icon does nothing....

Please help me.... before i set the whole house on fire for frustratuion.

Best regards......

Thanh

Standalone launcher requires a newer version of Vala than is available in Ubuntu. You'll need to get that and compile it from source, then compile awn-extras from source as well. It's a somewhat long process, which is one reason why it's not in my repo.

---

### Post by robcarr2 on 2008-04-27
Thanks for that, I had a lot of trouble trying to get AWN working a while ago, and it seems *touch wood* to have actually worked with no problems this time.

Thanks a lot :)

---

### Post by hessiess on 2008-04-27
> **reacocard said:**
> I take it you installed awn from the repo? the awn-core-applets-bzr package already contains most of awn-extras.

I instaled it from the hardy repo, reinstaling it from the repo menitoned [here]("http://wiki.awn-project.org/DistributionGuides#Reacocard.27s_PPA") fixed it

---

### Post by martin saint martin on 2008-04-27
when i run my update manager it will tell me that not all update can be installed.  the following updates are the ones that can't be installed:  avant-window-navigator-bzr, avant-core-applets-bzr, and python-awn-bzr.  what's up with this/how can i fix it?

---

### Post by hessiess on 2008-04-27
now i have AWN working, can I remove gnome-panel?

---

### Post by yogo on 2008-04-27
Yes you can and I did but I find AWM buggy, it does not always add running programs back in and sometimes will add a program twice.

I added the gnome panel back as it will give more control and stability.

For example, I like to use Kate if I am working in terminal and many commands are necessary to enter in. b BUT in Kate I was not able to open the terminal part of app as where to click was underneath the AWN and other apps were opening on me instead of the terminal

Anyways, I find the Gnome panel useful to keep running, I even tried to minimize it as thin but you can not deviate too much as it is still about the same width. You can auto hide and expand the Gnome panel so it is not present but still have it for functionality.

---

### Post by moonbeam on 2008-04-27
> **Thanh-BKK said:**
> Hello.

Please help me out here.... i am going thru hell and back to get a single feature working.

First tried to install "AWN Extras" the "manual way" (from source), only to find that after downloading over 300 MEGABYTES (!!!!!) dependencies the thing would still not install, giving me a "make" error............. 

Then i did it the way described here, so i got AWN working again and a bunch of applets available, too, however tjhe single one i'm after is not available AGAIN....

"Standalone Launcher", pleeeeeeease!! After i have wasted several straight DAYS trying to get this to work, i feel i deserve it...........

Also, how do i put a launcher there that opens a HDD partition? In an older AWN version (which also failed to ever get the "standalone launcher"!) there was an option "location" which is no longer prsent here, and dragging/dropping the drive icon does nothing....

Please help me.... before i set the whole house on fire for frustratuion.

Best regards......

Thanh

You have two options.

1) Compiling from source :-)
2) Install from the awn-testing PPA.  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive) This will end up installing a few more deps than reacocard's/

---

### Post by henrikwl on 2008-04-27
What's the difference between the packages in your repo and the packages in the repo hosted by the AWN guys themselves at launchpad?

---

### Post by CarpKing on 2008-04-27
> **martin saint martin said:**
> when i run my update manager it will tell me that not all update can be installed.  the following updates are the ones that can't be installed:  avant-window-navigator-bzr, avant-core-applets-bzr, and python-awn-bzr.  what's up with this/how can i fix it?

I've still got this too.  Repository hasn't quite sorted itself out yet?

---

### Post by reacocard on 2008-04-27
> **henrikwl said:**
> What's the difference between the packages in your repo and the packages in the repo hosted by the AWN guys themselves at launchpad?

theirs has a slightly more unstable version of AWN, but they also include support for Vala applets which I do not. Aside form that there really isn't much difference.

---

### Post by ShdwNova on 2008-04-28
> **martin saint martin said:**
> when i run my update manager it will tell me that not all update can be installed.  the following updates are the ones that can't be installed:  avant-window-navigator-bzr, avant-core-applets-bzr, and python-awn-bzr.  what's up with this/how can i fix it?

I believe a ```
apt-get dist-upgrade
```in the terminal should fix your problem, run as the superuser of course.

---

### Post by Jammin80503 on 2008-04-28
Great guide. Any Mods want to sticky it?

---

### Post by henrikwl on 2008-04-28
> **reacocard said:**
> theirs has a slightly more unstable version of AWN, but they also include support for Vala applets which I do not. Aside form that there really isn't much difference.

Ok, thanks.

---

### Post by martin saint martin on 2008-04-28
> **ShdwNova said:**
> I believe a ```
apt-get dist-upgrade
```in the terminal should fix your problem, run as the superuser of course.

how could apt-get dist-upgrade help?  i'm already running hardy.

---

### Post by martin saint martin on 2008-04-28
> **martin saint martin said:**
> when i run my update manager it will tell me that not all update can be installed.  the following updates are the ones that can't be installed:  avant-window-navigator-bzr, avant-core-applets-bzr, and python-awn-bzr.  what's up with this/how can i fix it?

if you do the upgrade via synaptic package manager instead of your upgrade manager it will fix this problem.  once your in synaptic do a search for "avant".  then "mark for upgrade" the packages with the little yellow star.  click the apply and you should good to go after that.

---

### Post by ayoli on 2008-04-28
> **martin saint martin said:**
> how could apt-get dist-upgrade help?  i'm already running hardy.

apt-get dist-upgrade upgrade your system (as update-manager does) not the distribution version.

---

### Post by martin saint martin on 2008-04-28
> **ayoli said:**
> apt-get dist-upgrade upgrade your system (as update-manager does) not the distribution version.

this probably would've worked too, i fixed it using synaptic.  sorry i didn't understand what the dist-upgrade command would have done, but now i know thanks.

---

### Post by DarKobra on 2008-04-28
First time Ubuntu user here, got AWN running yesterday via Repos...

Is there any way to have AWN not display my currently running applications?

I would love to use it as a launcher and keep a panel around to keep track of the windows within my virtual desktop...

---

### Post by ayoli on 2008-04-28
> **martin saint martin said:**
> this probably would've worked too, i fixed it using synaptic.  sorry i didn't understand what the dist-upgrade command would have done, but now i know thanks.
Glad to have learn you something today, that was the purpose of my post :)

---

### Post by gareth9 on 2008-04-28
I think I have all the awn -bzr installed,and my awn is chosen to start up automatically but this does not happen.The only thing I can access is  System>preferences>Awn Manger. I also chose to Automatically start Awn on login but still does not work I am wondering what I am doing incorrect and why my awn wont show up at all. Any answers would be highly appreciated. Thanks. Oh , I am running the latest OS, 8.04

---

### Post by reacocard on 2008-04-28
> **DarKobra said:**
> First time Ubuntu user here, got AWN running yesterday via Repos...

Is there any way to have AWN not display my currently running applications?

I would love to use it as a launcher and keep a panel around to keep track of the windows within my virtual desktop...

Not with my packages. There is an applet in development that will allow this, however it is written in Vala which I do not support in my repo. (See the FAQ for why.)  The [awn-testing PPA](https://launchpad.net/~awn-testing/+archive) does have this applet, however I can provide no support for its installation and use.

---

### Post by ktulu1115 on 2008-04-28
Having small issue migrating to new avant.  Used old version on Feisty and Gusty fairly well, I just upgraded to the latest as described in this thread and it's worked great so far.

Only issue is a setting from previous configuration - I go into awn-manager and launchers setting and I see 5 items listed but without any text associated with them.  Trying to edit just brings the dialog without any information populated in it.  Also I'm unable to remove these from launchers.

I've seen these errors on Avant startup:

~$ avant-window-navigator 
Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/calendar.desktop
APPLET : /usr/lib/awn/applets/awnsystemmonitor.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/file-browser-launcher.desktop
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-10.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-14.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-11.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-12.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-13.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/awnnotificationdaemon.desktop
folder = /mnt/nfs

Those errors I'm assuming are the cause of the blank launcher entries.  I've checked and the files are not present, in fact nothing is there in the ~/.config/awn/launchers directory.

Where do I go to remove references to these missing files?  Is there a gconf entry for Avant?

---

### Post by drworm01 on 2008-04-28
AWN died for me with the last update and Synaptic wouldn't fix the problem, but I've got it working now. Here's what happened in hopes it'll be useful to others.

I told Synaptic during the update to just remove the programs figuring I could add/reinstall them later, but when I tried it said there were recursive unfulfilled dependencies (ie. avant-window-navigator could not be installed because it needed avant-window-manager which could not be installed because it needed avant-window-navigator). I then followed the suggestion posted earlier 

```

sudo apt-get dist-upgrade

```

but I've already upgraded to Hardy so it didn't do anything except to say this:

```

The following packages have been kept back:
  awn-core-applets-bzr

```

So,

```

sudo apt-get install awn-core-applets-bzr

```

That produced some messages, some recommended additions and then didn't install. So I repeated the command with the recommended additions:

```

sudo apt-get install awn-core-applets-bzr avant-window-navigator-bzr python-awn-bzr python-feedparser python-libgmail libawn0-bzr

```

And now AWN is back. One issue seemed to be the libawn0-bzr vs libawn-bzr:

```

dpkg: libawn-bzr: dependency problems, but removing anyway as you request:
 awn-core-applets-bzr depends on libawn-bzr.

```

came up during the process. The program works anyway so do with that what you will.

---

### Post by reacocard on 2008-04-29
> **ktulu1115 said:**
> Having small issue migrating to new avant.  Used old version on Feisty and Gusty fairly well, I just upgraded to the latest as described in this thread and it's worked great so far.

Only issue is a setting from previous configuration - I go into awn-manager and launchers setting and I see 5 items listed but without any text associated with them.  Trying to edit just brings the dialog without any information populated in it.  Also I'm unable to remove these from launchers.

I've seen these errors on Avant startup:

~$ avant-window-navigator 
Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/calendar.desktop
APPLET : /usr/lib/awn/applets/awnsystemmonitor.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/file-browser-launcher.desktop
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-10.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-14.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-11.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-12.desktop
FAILED : /home/adechiaro/.config/awn/launchers/awn_launcher-13.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/awnnotificationdaemon.desktop
folder = /mnt/nfs

Those errors I'm assuming are the cause of the blank launcher entries.  I've checked and the files are not present, in fact nothing is there in the ~/.config/awn/launchers directory.

Where do I go to remove references to these missing files?  Is there a gconf entry for Avant?

You can remove them in gconf-editor, the relevant key is apps->avant-window-navigator->window_manager->launchers

---

### Post by reacocard on 2008-04-29
> **drworm01 said:**
> AWN died for me with the last update and Synaptic wouldn't fix the problem, but I've got it working now. Here's what happened in hopes it'll be useful to others.

I told Synaptic during the update to just remove the programs figuring I could add/reinstall them later, but when I tried it said there were recursive unfulfilled dependencies (ie. avant-window-navigator could not be installed because it needed avant-window-manager which could not be installed because it needed avant-window-navigator). I then followed the suggestion posted earlier 

```

sudo apt-get dist-upgrade

```

but I've already upgraded to Hardy so it didn't do anything except to say this:

```

The following packages have been kept back:
  awn-core-applets-bzr

```

So,

```

sudo apt-get install awn-core-applets-bzr

```

That produced some messages, some recommended additions and then didn't install. So I repeated the command with the recommended additions:

```

sudo apt-get install awn-core-applets-bzr avant-window-navigator-bzr python-awn-bzr python-feedparser python-libgmail libawn0-bzr

```

And now AWN is back. One issue seemed to be the libawn0-bzr vs libawn-bzr:

```

dpkg: libawn-bzr: dependency problems, but removing anyway as you request:
 awn-core-applets-bzr depends on libawn-bzr.

```

came up during the process. The program works anyway so do with that what you will.

I've renamed several packages, so it's possible there may be rough edges when upgrading, however after a successful upgrade everything should be fine. At worst, removing and reinstalling all packages should fix any dependency problems.

---

### Post by kgr132 on 2008-04-29
> I've renamed several packages, so it's possible there may be rough edges when upgrading, however after a successful upgrade everything should be fine. At worst, removing and reinstalling all packages should fix any dependency problems.

I really didn't have any trouble using the Synaptic Package Manager to resolve this. In Synaptic I chose the avant-window-navigator-bzr package and selected the Mark For Upgade option. Synaptic then prompted me with all of the other package changes necessary, like removing libawn-bzr and installing libawn0-bzr, etc. I applied those changes and then ran the Update Manager one more time and it fetched an update for awn-core-applets-bzr. That was it. Thanks for great package.

---

### Post by rab4567 on 2008-04-29
I was wondering if I could easley transfer all my applet from the top launcher panel to awn.

---

### Post by reacocard on 2008-04-29
> **rab4567 said:**
> I was wondering if I could easley transfer all my applet from the top launcher panel to awn.

the applet format is incompatible. program launchers may be dragged to AWN, everything else cannot be and you'll have to find substitutes among the applets designed for AWN.

---

### Post by ayoli on 2008-04-29
@reacocard : Browsing some threads, and fall here (again).
Then my brain have been eaten (btw there wasn't much to eat there tonight !), after what I figured that you also got a deprecated link to your old repo in your sig.

Nothing better to say, maybe too lame or drunk :-P

Again big up for all your work and support :D

---

### Post by shawalli on 2008-04-29
i installed AWN 0.3.1 on Hardy.  after installing compiz-fusion, AWN disappeared, so i uninstalled fusion and reinstalled "Advanced Desktop Effects Settings." AWN was still gone.  I uninstalled it.  I then reinstalled it using this thread to no avail.  I then uninstalled it using the thread.  I can see AWN is unclicked under add/remove, but when i click it to install, it says:

"This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Any ideas? I can even figure out how to get the bottom panel back on my screen temporarily until i can fix AWN

---

### Post by ayoli on 2008-04-29
> **shawalli said:**
> i installed AWN 0.3.1 on Hardy.  after installing compiz-fusion, AWN disappeared, so i uninstalled fusion and reinstalled "Advanced Desktop Effects Settings." AWN was still gone.  I uninstalled it.  I then reinstalled it using this thread to no avail.  I then uninstalled it using the thread.  I can see AWN is unclicked under add/remove, but when i click it to install, it says:

"This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Any ideas? I can even figure out how to get the bottom panel back on my screen temporarily until i can fix AWN
I'm not sur eto exactly understand your issue. May be you haven't correctly uninstall, before installing using this thread.
Btw, to have your bottom panel back, you just need to create a new panel. Right click in an empty space of your top panel and pick "new panel" in the pop up menu. Where ever the panel is placed after its creation you can move it with a drag and drop.

---

### Post by GumbyX on 2008-04-29
Dude I appreciate you having a repository for AWN for us, but can you make give the agnostic tagged version of AWN a better description. I got confused thinking they were a new version, got rid of my old one, and installed them just to find out they are worthless. If not, can you bold the info about the agnostic packages on the main page. I didn't see it since it just mixed in with the normal text. If it stood out more, it would have saved me from having to go through 3+ pages on posts to find out what the hell was going on.

Also, the regular Trash applet is not working properly. It doesn't recognize that there are files in the trash. Affinity is not working also. I didn't see anyone post about it yet, so I might be the only one with this problem.

Anyway, keep up the good work. I hope you can straighten the repo out so its easier to figure out what is going on.

---

### Post by reacocard on 2008-04-29
> **ayoli said:**
> @reacocard : Browsing some threads, and fall here (again).
Then my brain have been eaten (btw there wasn't much to eat there tonight !), after what I figured that you also got a deprecated link to your old repo in your sig.

Nothing better to say, maybe too lame or drunk :-P

Again big up for all your work and support :D

oops, forgot to update the sig. fixed now. thanks for noticing that.

> **GumbyX said:**
> Dude I appreciate you having a repository for AWN for us, but can you make give the agnostic tagged version of AWN a better description. I got confused thinking they were a new version, got rid of my old one, and installed them just to find out they are worthless. If not, can you bold the info about the agnostic packages on the main page. I didn't see it since it just mixed in with the normal text. If it stood out more, it would have saved me from having to go through 3+ pages on posts to find out what the hell was going on.

Also, the regular Trash applet is not working properly. It doesn't recognize that there are files in the trash. Affinity is not working also. I didn't see anyone post about it yet, so I might be the only one with this problem.

Anyway, keep up the good work. I hope you can straighten the repo out so its easier to figure out what is going on.

the -agnostic packages are still VERY experimental, they'll get fixed when I have time (read: not this week). The trash applet doesn't work because hardy uses gvfs which the trash applet in the standard packages doesn't support yet. The agnostic packages do support it, but as I've said they're very experimental.

---

### Post by keeler1 on 2008-04-29
I installed from the repo with a fresh install of 8.04.  On both my laptop 32bit and my desktop 64 bit.  I am having the same problem on both.

For some odd reason, the docks icons dissappear at random times and the dock itself is unusable (you can not right click on it to tell it to quit or go to preferences)  the process is still running and the dock is viewable but unclickable.

Like I said all the icons are gone.  The only way I have found to fix this is kill the old process and restart awn.

Is there any other way?

---

### Post by Maupertus on 2008-04-30
I never really went for bling in my desktop, but I made the jump yesterday and installed AWM from the Tester repro's.

I'm loving it every second, I'm still fiddling with the look and feel, but up untill now, the only thing that annoys me is the workspace switcher applet (but after some playing around, it works great for me)

So I want to give credit to the developers, I've found that together with Gnome-DO, it isn't just great to look at, but greatly increases my feeling of control over my system.

If I can quickly make a feature request...

It would be great if the superb Media Control Applet could also be used to handle (in my case Rhythmbox's) place on the dock. Now you have to Icons when using your media player, but it would be great if the Applet could be used instead.

CUDOS!

---

### Post by MountainX on 2008-04-30
> **reacocard said:**
> I've renamed several packages, so it's possible there may be rough edges when upgrading, however after a successful upgrade everything should be fine. At worst, removing and reinstalling all packages should fix any dependency problems.

Hi reacocard - can you give us a better idea of exactly how to upgrade?

Here is what Synaptic is telling me now:
**_Not Authenticated:_**
libawn-bzr
**_To Be Removed:_**
python-libawn-bzr
awn-manager-bzr
avant-window-navigator-bzr

Should I let Synaptic remove those packages? Can you suggest some exact steps for proceeding? Thanks.

---

### Post by Vadi on 2008-04-30
That's fine. I've had that a couple of times, and AWN is still working after, so I guess it was just doing some cleaning.

---

### Post by vgrisham on 2008-04-30
I had to reinstall after the repo rearrangment and now the tsclient applet isn't working again. Andrew et, al. fixed the bug last week and pushed the fixed applet to the repository. Are the applets installable from a different deb now?

---

### Post by reacocard on 2008-04-30
> **vgrisham said:**
> I had to reinstall after the repo rearrangment and now the tsclient applet isn't working again. Andrew et, al. fixed the bug last week and pushed the fixed applet to the repository. Are the applets installable from a different deb now?

applets are still in awn-core-applets-bzr. I'm pushing up a newer version of that package later tonight, so perhaps that will fix your issue.

---

### Post by rjohnson on 2008-05-01
I just installed 8.04 and can't get awn to work. I followed the instructions to remove and reinstall...no joy

Excerpt:

@ubuntu-laptop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:196: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 203, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 130, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 98, in __init__
    self.setup_chooser(defs.APP, defs.ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 196, in setup_chooser
    raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)

Key: [app]active_png isn't set.
Restarting AWN usually solves this issue

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_awn-manager.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 203, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 130, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 98, in __init__
    self.setup_chooser(defs.APP, defs.ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 196, in setup_chooser
    raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)

Key: [app]active_png isn't set.
Restarting AWN usually solves this issue


Thanks

---

### Post by reacocard on 2008-05-01
> **rjohnson said:**
> I just installed 8.04 and can't get awn to work. I followed the instructions to remove and reinstall...no joy

Excerpt:

@ubuntu-laptop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:196: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 203, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 130, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 98, in __init__
    self.setup_chooser(defs.APP, defs.ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 196, in setup_chooser
    raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)

Key: [app]active_png isn't set.
Restarting AWN usually solves this issue

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_awn-manager.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 203, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 130, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 98, in __init__
    self.setup_chooser(defs.APP, defs.ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 196, in setup_chooser
    raise "\nKey: [%s]%s isn't set.\nRestarting AWN usually solves this issue\n" % (group, key)

Key: [app]active_png isn't set.
Restarting AWN usually solves this issue


Thanks

you need to run avant itself at least once before awn-manager will work.

---

### Post by darkwoofe on 2008-05-01
I can't get AWN to install from the repo. I get so far and then this error message: > Package avant-window-navigator-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avant-window-navigator-bzr has no installation candidate

---

### Post by darkwoofe on 2008-05-01
Never mind. It installed on the third try...

---

### Post by DJ_Peng on 2008-05-01
Is there a changelog that helps me keep up with what's in the nightly updates I seem to be getting? I'm also noticing that saving my password in the Clock/Calendar Applet seems to keep dumping me back at the login dialog, but I'll see about making sure a bug is filed for it in a little bit.

---

### Post by reacocard on 2008-05-01
> **DJ_Peng said:**
> Is there a changelog that helps me keep up with what's in the nightly updates I seem to be getting? I'm also noticing that saving my password in the Clock/Calendar Applet seems to keep dumping me back at the login dialog, but I'll see about making sure a bug is filed for it in a little bit.

I do not maintain my own changelog, however AWN bzr has one: [https://code.launchpad.net/~awn-core/awn/trunk](https://code.launchpad.net/~awn-core/awn/trunk)

Just look for the revision number matching the number in the bzrXXX part of my package's version. If you get an update and that number doesn't change, then it was just a packaging change.

---

### Post by vgrisham on 2008-05-01
> **reacocard said:**
> applets are still in awn-core-applets-bzr. I'm pushing up a newer version of that package later tonight, so perhaps that will fix your issue.

Okay. The tsclient applet is working again after updating this afternoon. The quit/logout applet is now dead however.

---

### Post by otrojake on 2008-05-01
My quit/logout applet died too with the latest updates.  I uninstalled the awn-core-applets-bzr package and went into the apt archives (/var/cache/apt/archives) and rolled it back to 0.3.1.bzr460.2 to get it working.

[Here]("http://www.filedropper.com/awn-core-applets-bzr031bzr4602hardyi386")'s the deb for the i386 version of Hardy if anyone's interested.

---

### Post by vgrisham on 2008-05-01
The quit applet bug was fixed today. I just updated via Synaptic, and it works again.

---

### Post by auslander1138 on 2008-05-02
Firstly, huge props to the developers--functional bling! :)

@reacocard

how can I get the warning messages about your repo being "unauthenticated" to go away??  Do you have a PGP key or something that I need to import?

Thanks for providing this service and especially taking the time to assist us in getting this working--nice!

Cheers!

aus

---

### Post by reacocard on 2008-05-02
> **auslander1138 said:**
> Firstly, huge props to the developers--functional bling! :)

@reacocard

how can I get the warning messages about your repo being "unauthenticated" to go away??  Do you have a PGP key or something that I need to import?

Thanks for providing this service and especially taking the time to assist us in getting this working--nice!

Cheers!

aus

bug the launchpad devs aout the unauthenticated errors. its a problem with the PPA system, nothing I can do about it.

---

### Post by Enlitend on 2008-05-02
Hi,

I just did an upgrade to the new build and the Quit applet is working correctly now. 
I didn't remove the old one, just do the apt-get upgrade, just to let you know and it works nicely.

Thanks for the hard work. :)

---

### Post by DJ_Peng on 2008-05-02
> **reacocard said:**
> I do not maintain my own changelog, however AWN bzr has one: [https://code.launchpad.net/~awn-core/awn/trunk]("https://code.launchpad.net/%7Eawn-core/awn/trunk")

Just look for the revision number matching the number in the bzrXXX part of my package's version. If you get an update and that number doesn't change, then it was just a packaging change.
Awesome info! I'll have to bookmark it, as well as the page for awn-extras. I just got the single update for the extras and it's great to be able to see what's changed.

I am seeing something that's confusing me a little. Launchpad says AWN is up to 0.2.6, but my awn-manager is reporting as 0.3.1. Am I missing something here? I know I probably need some more coffee, but I've been meaning to ask for a while and keep forgetting.

---

### Post by reacocard on 2008-05-02
> **DJ_Peng said:**
> Awesome info! I'll have to bookmark it, as well as the page for awn-extras. I just got the single update for the extras and it's great to be able to see what's changed.

I am seeing something that's confusing me a little. Launchpad says AWN is up to 0.2.6, but my awn-manager is reporting as 0.3.1. Am I missing something here? I know I probably need some more coffee, but I've been meaning to ask for a while and keep forgetting.

My packages are built straight from bzr, which is given the odd number 0.3.1 to mark it as the devel version. Before each official stable release, the code is branched off and given an even version like 0.2.6 to indicate its stability.

---

### Post by rausuar on 2008-05-02
I am trying to configure the AWN, I have Ubuntu Hardy 8.04 updated and AWN update to the latest (as explained in this howto).

Some icons do not appear in the notification area, and when they appear, the do it with a white squeare around, which makes the whole AWN look "not nice"... (consider the aforementioned color as the system default color for the panel)...

In the same way, I cannot make the volume control applet to work correctly... also, I use AMSN, and it doesn't load correctly in the AWN notification area (it usually "gets lost" - it is connected and operating but it doesnt appear in the AWN - )

Are those problems because AWN is not completely compatible with Hardy? or it is just the fault of my Ubuntu / AWN configuration?

Is there a way to make AWN move the icons in a carrousel like Cairo-dock?

Thanks and excuse my inexperience, I am new with AWN...

- Raul

---

### Post by reacocard on 2008-05-02
> **rausuar said:**
> I am trying to configure the AWN, I have Ubuntu Hardy 8.04 updated and AWN update to the latest (as explained in this howto).

Some icons do not appear in the notification area, and when they appear, the do it with a white squeare around, which makes the whole AWN look "not nice"... (consider the aforementioned color as the system default color for the panel)...

In the same way, I cannot make the volume control applet to work correctly... also, I use AMSN, and it doesn't load correctly in the AWN notification area (it usually "gets lost" - it is connected and operating but it doesnt appear in the AWN - )

Are those problems because AWN is not completely compatible with Hardy? or it is just the fault of my Ubuntu / AWN configuration?

Is there a way to make AWN move the icons in a carrousel like Cairo-dock?

Thanks and excuse my inexperience, I am new with AWN...

- Raul

the systray applet for AWN just sucks right now. I suggest you use a different systray, either the one in gnome-panel or a standalone one like trayer. There are plans to improve the one in AWN but it's not a simple problem so it will be a while before it gets fixed.

as for the carrousel thing, no.

---

### Post by rausuar on 2008-05-02
Thanks reacocard! your answer has been very useful! - Raul

---

### Post by sdhog2002 on 2008-05-03
> **reacocard said:**
> You can remove them in gconf-editor, the relevant key is apps->avant-window-navigator->window_manager->launchers

Reacocard, thank you SO much for a wonderful app. I am having the same problem, but when I look for the key as mentioned, I have, under the apps/avant-window-navigator key, just 'applets'. AWM is definitely installed, however. Suggestions?

---

### Post by NOLU on 2008-05-03
Hi.

I've installed AWN but when I click on AWN in accessories, something tries to open in the top left of the screen but it flashes away so fast that I have no idea what it is.

Basically AWN doesn't open for me. I've installed 7.10 today after having issues with Heron.

---

### Post by DJ_Peng on 2008-05-03
> **reacocard said:**
> My packages are built straight from bzr, which is given the odd number 0.3.1 to mark it as the devel version. Before each official stable release, the code is branched off and given an even version like 0.2.6 to indicate its stability.
Cool. I should have realized it was something like this. Thanks for the quick answer.

---

### Post by fermin on 2008-05-03
Thanks for the guide :). But i have a problem and cant run AWN ](*,). I had a previous installation of AWN for gutsy, but wanted to try this new one. So i followed your uninstall guide plus i removed from synaptic everything that related to "awn", "libawn" or "avant-window-mananger". Then i followed your guide for the Hardy Heron repository version and all went well, apparently, but i cant start AWN, nothing happens when i call it, either from the menu or terminal. With the latter i get this output:

```
fermin@fermin-laptop:~$ avant-window-navigator 
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_vfs_init

```

Any ideas what could be the problem? I unistalled and installed again and didnt solve the problem. I also followed another install guide from this page:

[]("http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml")

unistalling first and i get the same problem (same output) :(

Please help me [-o<, now i cant get AWN to work at all :cry:

---

### Post by threetwozero on 2008-05-03
I'm having this exact problem.  Everything worked fine before "upgrading" to Heron.  What gives?


> **NOLU said:**
> Hi.

I've installed AWN but when I click on AWN in accessories, something tries to open in the top left of the screen but it flashes away so fast that I have no idea what it is.

Basically AWN doesn't open for me. I've installed 7.10 today after having issues with Heron.

---

### Post by reacocard on 2008-05-03
> **fermin said:**
> Thanks for the guide :). But i have a problem and cant run AWN ](*,). I had a previous installation of AWN for gutsy, but wanted to try this new one. So i followed your uninstall guide plus i removed from synaptic everything that related to "awn", "libawn" or "avant-window-mananger". Then i followed your guide for the Hardy Heron repository version and all went well, apparently, but i cant start AWN, nothing happens when i call it, either from the menu or terminal. With the latter i get this output:

```
fermin@fermin-laptop:~$ avant-window-navigator 
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_vfs_init

```

Any ideas what could be the problem? I unistalled and installed again and didnt solve the problem. I also followed another install guide from this page:

[]("http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml")

unistalling first and i get the same problem (same output) :(

Please help me [-o<, now i cant get AWN to work at all :cry:

what does 
```
which avant-window-navigator
```
output?

---

### Post by fermin on 2008-05-03
Thanks for the reply, Reacocard. I typed the code you gave me and the output is as follows:

```
fermin@fermin-laptop:~$ which avant-window-navigator
/usr/bin/avant-window-navigator
```

I had previosly deleted this commands in the bin folder with your unistall procedure.

By the way, the page i followed alternatively to install AWN is
[URL="http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml"]
http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml[/URL]

wich, basically has another AWN repository that claims to have also the latest AWN upgrades and be relatively stable at the same time.

Thanks in advance for the help :D

---

### Post by shawalli on 2008-05-04
I posgted this a few days ago and still have no solution:

i installed AWN 0.3.1 on Hardy. after installing compiz-fusion, AWN disappeared, so i uninstalled fusion and reinstalled "Advanced Desktop Effects Settings." AWN was still gone. I uninstalled it. I then reinstalled it using this thread to no avail. I then uninstalled it using the thread. I can see AWN is unclicked under add/remove, but when i click it to install, it says:

"This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Any ideas? I can even figure out how to get the bottom panel back on my screen temporarily until i can fix AWN

---

### Post by threetwozero on 2008-05-04
> **threetwozero said:**
> I'm having this exact problem.  Everything worked fine before "upgrading" to Heron.  What gives?

So, after installing xgl (which is a no no with my ati card) awn does render and function as normal - albeit brutally slow.  There are other threads about ati drivers and compiz not playing nice.  As soon as I removed xgl awn stopped loading.

---

### Post by Penguinu$$$ on 2008-05-04
!!!Help!!! whe I try to install AWN it says unable to find (or identify) package avant-window-navigator-0.2.6 !!! PLEASE HELP!!! S.O.S.!!!

---

### Post by 565Customz on 2008-05-04
....here we goo  again...

so awn decides that now it doesnt want to display running applets...so basically when i minimize a window i have no way of getting it back...any ideas

---

### Post by lvanderree on 2008-05-08
I had awn running below my maximized applications, and made it pop-up as soon as my mouse-cursor touched the bottom of my screen. However since a while awn will not come back on top any more. 

Has anyone else experienced this same problem? and are there any known solutions to solve this issue? 
I currently have this issue with both awn-bzr and awn 0.2.1

I really loved awn, but now it isn't very useful... There where only two features I'd really like to see someday (after this bug has been fixed) and that are:
1. Be able to set a delay to make awn pop-up once you hit the bottom of your screen with the mouse cursor (awn sometimes came up too soon).
2. Make it possible to re-arrange the icons within the taskmanager

---

### Post by GumbyX on 2008-05-08
Wow, looks like I'm not the only one having issues with AWN. Sadly, with all the changes that seem to have happened between 7.10 and 8.04, looks like awn might need a *small* overhall. :( Hopefully it comes soon.

Anyway, I am having a problem with the weather applet all of a sudden. I no longer get weather updates; It just keeps "fething weather data". Anyone else run into this problem?

---

### Post by lvanderree on 2008-05-08
yep have that issue as well, can't get any weather updates anymore in awn, while is does work in my gnome-systray where it is integrated in the clock.

---

### Post by moonbeam on 2008-05-08
> **GumbyX said:**
> Wow, looks like I'm not the only one having issues with AWN. Sadly, with all the changes that seem to have happened between 7.10 and 8.04, looks like awn might need a *small* overhall. :( Hopefully it comes soon.

Anyway, I am having a problem with the weather applet all of a sudden. I no longer get weather updates; It just keeps "fething weather data". Anyone else run into this problem?

I don't use Ubuntu myself but it sounds like WM behavior may have changed.  Possible configurable....  I'll try and do a bit of research.  compiz or metacity?  I'll assume compiz unless told otherwise.

The weather applet was affected by some changed weather.com made.  

Bug:

[https://bugs.edge.launchpad.net/awn-extras/+bug/227419](https://bugs.edge.launchpad.net/awn-extras/+bug/227419)

Fix Committed:

[http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477)

The awn-testing PPA has been updated with the patch.  I'm not sure if Reacocard has had a chance to update yet.

---

### Post by NOLU on 2008-05-08
I'm still on 7.10. Will the tutorial on page one be up to date now?

---

### Post by reacocard on 2008-05-08
> **moonbeam said:**
> I don't use Ubuntu myself but it sounds like WM behavior may have changed.  Possible configurable....  I'll try and do a bit of research.  compiz or metacity?  I'll assume compiz unless told otherwise.

The weather applet was affected by some changed weather.com made.  

Bug:

[https://bugs.edge.launchpad.net/awn-extras/+bug/227419](https://bugs.edge.launchpad.net/awn-extras/+bug/227419)

Fix Committed:

[http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477)

The awn-testing PPA has been updated with the patch.  I'm not sure if Reacocard has had a chance to update yet.

New version uploading now, should be built within an hour.

> **NOLU said:**
> I'm still on 7.10. Will the tutorial on page one be up to date now?

It's up-to-date.

---

### Post by NOLU on 2008-05-09
Thanks. Got it working straight away.

---

### Post by DJ_Peng on 2008-05-09
The Weather Applet issue has been fixed. As of this morning's updates I'm once again showing Malden's weather on my dock. Thanks for the quick work on pushing out the patch!

---

### Post by GumbyX on 2008-05-09
> **reacocard said:**
> New version uploading now, should be built within an hour.

Thanks for getting it out so fast!! Weather works perfectly now.

Got a question for ya reacocard: Do you have any information about the changes to the trash bin in 8.04? You mentioned they changed some stuff about it and that is why the applet doesn't work anymore. Just wanted to take a look and see if I *might* be able to do minor coding changes to fix it.

---

### Post by reacocard on 2008-05-09
> **GumbyX said:**
> Thanks for getting it out so fast!! Weather works perfectly now.

Got a question for ya reacocard: Do you have any information about the changes to the trash bin in 8.04? You mentioned they changed some stuff about it and that is why the applet doesn't work anymore. Just wanted to take a look and see if I *might* be able to do minor coding changes to fix it.

it's already fixed... in the -agnostic branch. Unfortunately, mainline AWN hasn't changed over yet since many other distros still don't use the GVFS backend. However if you could find a way to make it auto-detect which method was appropriate and use the correct one I'm sure it'd be a welcome patch. You should talk to the devs in #awn for more information.

---

### Post by maddentim on 2008-05-11
@kaivalagi,
Did you find out how to fix this? I have the same issue.  it seems to be related to turning on the setting maximized windows to not cover the bar in the preferences.  when i turn it off it goes away. although, i would prefer to be able to set it on.  I worked ok in gutsy.

Edit: By this i mean the thing where the icons float too high above the bar.

---

### Post by say2sky on 2008-05-11
This howto is great and easy to follow. Thank you for this wonderful app and it let my hardy installation looks much more attractive. 

Hope all these packages will enter ubuntu repository soon and more users can enjoy  it.

Now I find AWN already stable enough and I can use it replacing gnome-panel. I try to disable gnome-panel by 

1. killall -9 gnome-panel
2. use gconf editor
3. use session manager
4. delete panel

but all these cannot let gnome-panel disappear and let desktop simpler and no other object except AWN on it. Any method I can use to disable gnome-panel?

---

### Post by reacocard on 2008-05-11
> **say2sky said:**
> This howto is great and easy to follow. Thank you for this wonderful app and it let my hardy installation looks much more attractive. 

Hope all these packages will enter ubuntu repository soon and more users can enjoy  it.

Now I find AWN already stable enough and I can use it replacing gnome-panel. I try to disable gnome-panel by 

1. killall -9 gnome-panel
2. use gconf editor
3. use session manager
4. delete panel

but all these cannot let gnome-panel disappear and let desktop simpler and no other object except AWN on it. Any method I can use to disable gnome-panel?

Here's how I got rid of gnome-panel:
1) In session manager's Current Session tab, set the style of gnome-panel to Trash.
2) In terminal, killall -9 gnome-panel
3) In terminal, sudo apt-get remove gnome-panel

---

### Post by say2sky on 2008-05-11
> **reacocard said:**
> Here's how I got rid of gnome-panel:
1) In session manager's Current Session tab, set the style of gnome-panel to Trash.
2) In terminal, killall -9 gnome-panel
3) In terminal, sudo apt-get remove gnome-panel

Thanks a lot for help.
I worked as your way and now I use only AWN to control everything. It's great and very good looking. 

Some small bugs there but it does not prevent me from using it. hope this great app become better everyday!:popcorn:

---

### Post by GumbyX on 2008-05-13
> **reacocard said:**
> it's already fixed... in the -agnostic branch. Unfortunately, mainline AWN hasn't changed over yet since many other distros still don't use the GVFS backend. However if you could find a way to make it auto-detect which method was appropriate and use the correct one I'm sure it'd be a welcome patch. You should talk to the devs in #awn for more information.

Thanks for the info. I will talk to the devs sometime soon. I have a few programming projects going on right now between school and work, so I might not be able to work on it. Will do the research about an auto-detect patch at least.

PS I would use the -agnostic branch, but it didn't seem to work on my box. None of my settings or icons from the main AWN "branch" from your repo show up. Is that normal and if it is, how can I get my "old" settings and icons into the -agnostic build?

---

### Post by reacocard on 2008-05-13
> **GumbyX said:**
> Thanks for the info. I will talk to the devs sometime soon. I have a few programming projects going on right now between school and work, so I might not be able to work on it. Will do the research about an auto-detect patch at least.

PS I would use the -agnostic branch, but it didn't seem to work on my box. None of my settings or icons from the main AWN "branch" from your repo show up. Is that normal and if it is, how can I get my "old" settings and icons into the -agnostic build?

-agnostic uses a flat-file backend instead of mainline's gconf backend. There's no automated conversion, the only way is to move your settings is to do it by hand.

---

### Post by aidave on 2008-05-13
Hi, this is really quite an impressive program, I like it alot!  Great work!

Some ideas:

- Allow the Avant bar to be moved up, by an arbitrary amount of pixels.  This would be useful because it overlaps any panels you might have at the bottom of the screen.  

- Allow user to set animation speed.

---

### Post by maculata on 2008-05-13
There was a desktop switcher that work liked the awn terminal applet (simple popup style), will this again be available? I find the 2 included to be large and intrusive, imho. Besides that, awn is a required app on my systems.

M

---

### Post by reacocard on 2008-05-13
> **aidave said:**
> Hi, this is really quite an impressive program, I like it alot!  Great work!

Some ideas:

- Allow the Avant bar to be moved up, by an arbitrary amount of pixels.  This would be useful because it overlaps any panels you might have at the bottom of the screen.  

- Allow user to set animation speed.

1) AWN is not intended to be used on a side of the screen that has a panel. 

2) Will be done, but it's not high priority.

> **maculata said:**
> There was a desktop switcher that work liked the awn terminal applet (simple popup style), will this again be available? I find the 2 included to be large and intrusive, imho. Besides that, awn is a required app on my systems.

M

It was removed due to licensing issues. There's nothing stopping the original author from updating it to be compatible, or for someone else to rewrite it, it's just that neither of these things has happened yet.

---

### Post by Rever75 on 2008-05-14
I am having an issue with the latest AWN-bzr. Sometimes when I close a window on my desktop, AWN will crash. This happened to me today when I was doing updates and a config window for ssh popped up. When I closed it my AWN quit. I have had this happen also when I close a gnome-rdesktop session.

---

### Post by nomentero on 2008-05-14
> **Rever75 said:**
> I am having an issue with the latest AWN-bzr. Sometimes when I close a window on my desktop, AWN will crash. This happened to me today when I was doing updates and a config window for ssh popped up. When I closed it my AWN quit. I have had this happen also when I close a gnome-rdesktop session.
Same insue here with Latest bzr.

---

### Post by MountainX on 2008-05-14
Which version of AWN is the most stable? I can't use the Ubuntu repo version because it doesn't support applets (extras pkg). But I don't want a cutting edge version either. I just want a stable version. Which one should I use? Thanks.

---

### Post by reacocard on 2008-05-14
> **MountainX said:**
> Which version of AWN is the most stable? I can't use the Ubuntu repo version because it doesn't support applets (extras pkg). But I don't want a cutting edge version either. I just want a stable version. Which one should I use? Thanks.

This one and the testing PPA are usually similar. This one has slightly more stable code but there isn't very much difference most of the time. However, both this and -testing are considered unstable versions. AFAIK, there are no stable packages outside those available in the ubuntu repos, so if you want the stable version you may just have to use that and compile the applets from source yourself.

---

### Post by MountainX on 2008-05-14
> **reacocard said:**
>  so if you want the stable version you may just have to use that and compile the applets from source yourself.

Thank you. Would you be kind enough to point me to step by step instructions for compiling the applets from source?

---

### Post by reacocard on 2008-05-14
> **MountainX said:**
> Thank you. Would you be kind enough to point me to step by step instructions for compiling the applets from source?

The AWN wiki has a comprehensive guide: [http://wiki.awn-project.org/Awn_Extras:Installation#Building_From_Source](http://wiki.awn-project.org/Awn_Extras:Installation#Building_From_Source)

EDIT: note that you'll need to install the libawn-dev package from the ubuntu repos as well as the deps listed on the wiki.

---

### Post by RiTarDid on 2008-05-14
works good, thanks for this post

---

### Post by reacocard on 2008-05-14
> **Rever75 said:**
> I am having an issue with the latest AWN-bzr. Sometimes when I close a window on my desktop, AWN will crash. This happened to me today when I was doing updates and a config window for ssh popped up. When I closed it my AWN quit. I have had this happen also when I close a gnome-rdesktop session.

> **nomentero said:**
> Same insue here with Latest bzr.

I've uploaded packages to the PPA that should fix this. Many thanks to moonbeam for patching this so quickly.

---

### Post by Jesus_Valdez on 2008-05-14
Im having a problem with libawn-bzr with the updates, when my system updates gives me a error of autentification with the package.

Its happening since upgrade to Hardy Heron.

---

### Post by dccrens on 2008-05-15
> **Jesus_Valdez said:**
> Im having a problem with libawn-bzr with the updates, when my system updates gives me a error of autentification with the package.

Its happening since upgrade to Hardy Heron.

I haven't upgraded to Hardy but it is happening here too. Also have the issue above where AWM crashes sometimes when I close a window.

---

### Post by Rever75 on 2008-05-15
Update works perfectly for me thanks.

---

### Post by reacocard on 2008-05-15
> **dccrens said:**
> I haven't upgraded to Hardy but it is happening here too. Also have the issue above where AWM crashes sometimes when I close a window.

the authentication stuff is a bug in the PPA system, nothing I can do about it. The window closing bug should be fixed in the most recent update.

---

### Post by holmrun on 2008-05-15
> **reacocard said:**
> the authentication stuff is a bug in the PPA system, nothing I can do about it. The window closing bug should be fixed in the most recent update.

Is this something where we should just keep trying and eventually we'll get through - or what other options do we have to get to the latest version? Complete uninstall/reinstall?

---

### Post by ayoli on 2008-05-15
> **dccrens said:**
> I haven't upgraded to Hardy but it is happening here too. Also have the issue above where AWM crashes sometimes when I close a window.

before updating to a new ubuntu version, ppl should disable third party repositories I think.

---

### Post by holmrun on 2008-05-15
> **holmrun said:**
> Is this something where we should just keep trying and eventually we'll get through - or what other options do we have to get to the latest version? Complete uninstall/reinstall?

Nevermind - uninstall/reinstall worked to get the update. Hope this fixes the close on minimize bug. :guitar:

---

### Post by Jesus_Valdez on 2008-05-16
Same here, uninstall/reinstall worked.

Thanks a lot.

---

### Post by MMMan on 2008-05-16
I get the following message when I try to install AWN:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: python-gnome2-desktop but it is not going to be installed
                              Depends: python-gnome2-extras but it is not going to be installed
E: Broken packages

```

I am running a new installation Kubuntu 8.04


Ok, I fixed it.  I enabled Pre-released updates in Adept Manager and did a full upgrade.  (I'm not really sure if that was a good idea or not.)  I also had to install dbus-x11.

---

### Post by RebelwithoutaClue on 2008-05-17
> **threetwozero said:**
> I'm having this exact problem.  Everything worked fine before "upgrading" to Heron.  What gives?

Same as.
I've been trawling for days to find an answer to this.  Is there hope?:confused:

After lots of time spent, I got awn mostly working.  I did the upgrade and had to get many libraries updated before it happened.  Now I get the top left flash and nothing.  When I check in processes awn is sleeping but I can't wake the b*gger up!

When I do the remove, either with the package manager or through the terminal the app stays in the menu, it doesn't go away.  So I'm not convinced any reinstall actually does anything.

I've done every step at the start and all of the suggestions with and without reboots throughout the 16 pages, someone must have a fix for this?

---

### Post by Rever75 on 2008-05-17
Have you tried to apt-get purge all the files for awn?

---

### Post by moonbeam on 2008-05-18
> **RebelwithoutaClue said:**
> Same as.

After lots of time spent, I got awn mostly working.  I did the upgrade and had to get many libraries updated before it happened.  Now I get the top left flash and nothing.  When I check in processes awn is sleeping but I can't wake the b*gger up!



Sounds like a classic case of no compositor (we really should popup a error dialog when that happens.. but we don't yet).

Try running 

avant-window-navigator

in a terminal and paste the output here.

---

### Post by keeler1 on 2008-05-18
I cannot update awn from the repositories.  When the update manager runs it asks to do a partial upgrade because the bzr can not be installed.  Is this fixable?

---

### Post by reacocard on 2008-05-18
> **keeler1 said:**
> I cannot update awn from the repositories.  When the update manager runs it asks to do a partial upgrade because the bzr can not be installed.  Is this fixable?

use synaptic to upgrade, it's smarter about handling the dependencies.(System->Administration->Synaptic Package Manager, "mark all upgrades", "apply")

---

### Post by nhamze on 2008-05-19
Moonbeam, when I type that into the terminal I get the message Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

How can I fix it, I am running Hardy on CD macbook via parallels build 5600

Thanks

---

### Post by pmaconi on 2008-05-19
Does anyone have the "keep below maximized window when not in use" function working correctly? Or does it not work with the current build?

[EDIT]: Nevermind. It seems like it just corrected itself after a restart. *shrug*

---

### Post by aidave on 2008-05-23
> **reacocard said:**
> 1) AWN is not intended to be used on a side of the screen that has a panel.

I realize that is the intention.  However, personally, I love having a panel at the bottom of the screen.  Having AWN at the bottom, causes headaches due to the overlapping.  If there was a way to move AWN up, by 32 pixels or whatever, it would be perfect!  :)

---

### Post by gamont on 2008-05-25
Using Hardy.
When i try to toggle to Auto-start AWN in awn-manager appears this in console:

> 
Delete autostarter for Avant-Window-Navigator.
rm: imposível remover `/home/gamont/.config/autostart//awn.desktop': Arquivo ou diretório inexistente
toggled
Couldn't create autostarter for AWN
toggled


"Impossible to remove path : file or directory not found."
This path (autostart//awn.desktop) really dont exist.
What i can do ?
Thanks.

---

### Post by reacocard on 2008-05-25
> **gamont said:**
> Using Hardy.
When i try to toggle to Auto-start AWN in awn-manager appears this in console:


"Impossible to remove path : file or directory not found."
This path (autostart//awn.desktop) really dont exist.
What i can do ?
Thanks.

this should have the same effect as checking that box:
```

mkdir -p ~/.config/autostart/
cp /usr/share/applications/avant-window-navigator.desktop ~/.config/autostart/

```

---

### Post by gamont on 2008-05-25
> **reacocard said:**
> this should have the same effect as checking that box:
```

mkdir -p ~/.config/autostart/
cp /usr/share/applications/avant-window-navigator.desktop ~/.config/autostart/

```

Thanks ! Worked.

---

### Post by Tux_Johannes on 2008-05-26
hi reacocard,
Since Ubuntu Hardy there is a small bug with the trash applet; the applet try to use the path ~/.trash but it has been changed, so now the nautilius trash is in /home/johannes/.local/share/Trash/files. Could you fix this small bug, please.

---

### Post by reacocard on 2008-05-26
> **Tux_Johannes said:**
> hi reacocard,
Since Ubuntu Hardy there is a small bug with the trash applet; the applet try to use the path ~/.trash but it has been changed, so now the nautilius trash is in /home/johannes/.local/share/Trash/files. Could you fix this small bug, please.

first off, I'm not an AWN dev, I just package it, so I can't actually fix it.

Second, this is a known bug. Malept is working on it, I believe, so hopefully it'll be fixed soon. (in fact this is fixed in -agnostic, but that's too unstable for general use)

---

### Post by trondhuso on 2008-05-27
Just want to inform that I have installed the avant window manager under Hardy with the trunk-repo that is described on page 1. 
Got all the applets up and the manager seems very stable.

Suggestion to the developer of the desktopswitcher:
[delete]It should have some configuration-settings. I would like to have it smaller than it is right now, and maybe I would only like to have two and not four. For instance.
Just a suggestion.[/delete]

Found out about the size configuration a few hours after posting. I must have been unfocused. Thanks for the feedback btw.

to the avant team:
Keep up the great work!

---

### Post by moonbeam on 2008-05-27
> **trondhuso said:**
> 

Suggestion to the developer of the desktopswitcher:
It should have some configuration-settings. I would like to have it smaller than it is right now, and maybe I would only like to have two and not four. For instance.
Just a suggestion.


If you're referring to shinyswitcher there are several configuration options.  Unfortunately there isn't a nice preferences dialog yet so you need to start gconf-editor and then navigate to /apps/avant-window-navigator/applets/shinyswitcher

You can use the applet_scale key to change the size of the applet.

Assuming you're NOT using compiz you can change the layout using the rows and columns keys.  If you are using compiz you need to change the desktop layout in compiz.

---

### Post by ehron on 2008-05-27
First, thanks for packaging this.  I really like it.  

I just reinstalled Hardy.  Before I reinstalled when I got an IM (using Pidgin 2.4.1) the person's buddy icon would bounce up and down.  After the reinstall, using the same version of AWN, the icons no longer bounce up and down.

I have played with various settings, but I can't seem to find the cause of this behavior.  Any tips?

Thanks.

---

### Post by reacocard on 2008-05-27
> **ehron said:**
> First, thanks for packaging this.  I really like it.  

I just reinstalled Hardy.  Before I reinstalled when I got an IM (using Pidgin 2.4.1) the person's buddy icon would bounce up and down.  After the reinstall, using the same version of AWN, the icons no longer bounce up and down.

I have played with various settings, but I can't seem to find the cause of this behavior.  Any tips?

Thanks.

set icon effects to 'Classic', and enable "Alert when application window updated"

---

### Post by ehron on 2008-05-27
I shouldn't have been so vague.  I already selected that option.  I have disabled, and re-enabled it to see if that made a difference.  It didn't.  Do you think I need to reinstall?

Ehron

---

### Post by sorrowstyr on 2008-05-27
Hi!
I just installed Awn-bzr and I love it.

I do have one question which I cant seem to find by searching on the ubuntu forums.. or on the awn website.

Is there a way to group up applications?
I usually have like 10 terminals open, and I would love them to appear as one icon or some sort of stack like menu.

Can I do this already, if so how ?

Thanks!

Note::
Ehron -- You might want to try closing all running copies of awn, and restarting it.  I found that sometimes the preferences dont always take effect until after the application restarts.

---

### Post by reacocard on 2008-05-28
> **sorrowstyr said:**
> Hi!
I just installed Awn-bzr and I love it.

I do have one question which I cant seem to find by searching on the ubuntu forums.. or on the awn website.

Is there a way to group up applications?
I usually have like 10 terminals open, and I would love them to appear as one icon or some sort of stack like menu.

Can I do this already, if so how ?

Thanks!

Note::
Ehron -- You might want to try closing all running copies of awn, and restarting it.  I found that sometimes the preferences dont always take effect until after the application restarts.

No, it's not possible at this time.

---

### Post by Tux_Johannes on 2008-05-28
> Second, this is a known bug. Malept is working on it, I believe, so hopefully it'll be fixed soon. (in fact this is fixed in -agnostic, but that's too unstable for general use)
Ok, thank you. Next time I will look at Launchpad first.:)

---

### Post by Arthur Archnix on 2008-05-28
As of Hardy it should be possible to run AWN with metacity, though that's not one of the window managers listed. You just need to go into gconf-editor and turn on the "compositing_manager" setting, which is disabled by default. While using metacity as the default "window_manager" of course.

Just tossing it out there in case someone wants to confirm or refute that thought.

---

### Post by reacocard on 2008-05-28
> **Arthur Archnix said:**
> As of Hardy it should be possible to run AWN with metacity, though that's not one of the window managers listed. You just need to go into gconf-editor and turn on the "compositing_manager" setting, which is disabled by default. While using metacity as the default "window_manager" of course.

Just tossing it out there in case someone wants to confirm or refute that thought.

It works, but has issues. It's easier to just use xfwm4 or compiz instead, both of which work very well.

---

### Post by moonbeam on 2008-05-29
> **reacocard said:**
> It works, but has issues. It's easier to just use xfwm4 or compiz instead, both of which work very well.

I second this.  Several awn devs use recent xfwm4 versions and are very happy with it. In our experience xfwm4 is less flaky than metacity at this time.

---

### Post by DancemasterGlenn on 2008-05-30
Fighting with my graphics drivers has kept me away from avant for far too long... but a reformat put me back on track, and it's nice to see some of the improvements that have happened since I left. Lame that the trash is still not working, but it's good to know it's still being worked on.

Also, Pandora sorta kinda works! When I click it, it pops up a bubble in a sort of stacks fashion, which I think is trying to take me to a particular site. However, the page is not recognized by pandora. After it tells me so, I am able to click the link that takes me to the main pandora page, and music works fine... clicking other windows hides the bubble, which is a nice feature. Is this how it's supposed to work (besides the having to be redirected), or am I supposed to go to a specific page? I've noticed that it's a little weird trying to navigate pandora within the bubble, simply because the page is bigger than the bubble and thus requires scrolling around. Is it supposed to take me to a smaller stand-alone, perhaps? Just curious.

Very glad to be using avant again! Thanks so much for packaging it.

EDIT: Is it trying to load the mini version of the player? Because that would be great...

---

### Post by Old Marcus on 2008-05-30
Would it be possible for awn to be hidden when I have a window in full screen, but reappear when I mouse over where the dockbar is?

EDIT: No problem, found it in the manager

---

### Post by srt4lifez on 2008-05-30
im having a problem running awn, I installed it following the repository way on kubuntu hardy, but when i run avant-window-navigator in terminal it outputs...


(avant-window-navigator:13722): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

(avant-window-navigator:13722): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

** (avant-window-navigator:13722): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (avant-window-navigator:13722): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:13722): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:13722): WARNING **: There was an error requesting the name:
*** glibc detected *** avant-window-navigator: double free or corruption (fasttop): 0x081a1118 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76bfa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76c34f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb79198b1]
/usr/lib/libglib-2.0.so.0(g_error_free+0x29)[0xb7902a79]
avant-window-navigator[0x804eb81]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb766a450]
avant-window-navigator[0x804dc61]

it also has a memory map: and lists a bunch of stuff but i wasnt sure if should post all of it or not...

please let me know if you know how to fix this...

---

### Post by reacocard on 2008-05-30
> **srt4lifez said:**
> im having a problem running awn, I installed it following the repository way on kubuntu hardy, but when i run avant-window-navigator in terminal it outputs...


(avant-window-navigator:13722): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

(avant-window-navigator:13722): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

** (avant-window-navigator:13722): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (avant-window-navigator:13722): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:13722): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:13722): WARNING **: There was an error requesting the name:
*** glibc detected *** avant-window-navigator: double free or corruption (fasttop): 0x081a1118 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76bfa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76c34f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb79198b1]
/usr/lib/libglib-2.0.so.0(g_error_free+0x29)[0xb7902a79]
avant-window-navigator[0x804eb81]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb766a450]
avant-window-navigator[0x804dc61]

it also has a memory map: and lists a bunch of stuff but i wasnt sure if should post all of it or not...

please let me know if you know how to fix this...

looks like its having trouble connecting to DBUS, which doesn't surprise me since you're on kubuntu. make sure dbus is installed and working properly.

---

### Post by srt4lifez on 2008-05-31
didnt notice that last night, installed kdbus and x11-dbus and it seemed to of fixed it... i still get the 'clearlooks' errors though?...

---

### Post by reacocard on 2008-05-31
> **srt4lifez said:**
> didnt notice that last night, installed kdbus and x11-dbus and it seemed to of fixed it... i still get the 'clearlooks' errors though?...

the clearlooks errors probably mean you don't have a GTK theme set. It shouldn't affect the functionality of anything.

---

### Post by kmanpwnudwn on 2008-05-31
I copied and pasted the lines exactly as they were for installing AWN on Hardy under the repository instructions, and I keep getting this error:

E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list

I can't access add/remove programs without getting this error:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

If anyone knows how to fix this, PLEASE HELP!
It would be greatly appreciated!!

---

### Post by srt4lifez on 2008-05-31
> **kmanpwnudwn said:**
> I copied and pasted the lines exactly as they were for installing AWN on Hardy under the repository instructions, and I keep getting this error:

E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list

I can't access add/remove programs without getting this error:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

If anyone knows how to fix this, PLEASE HELP!
It would be greatly appreciated!!

sounds like you copied the repository line that your supposed to copy and paste into a terminal into the /etc/apt/sources.list file.

the word 'echo' shouldnt be in that file... open it up in a text editor and remove w/e is on line 56.

---

### Post by kmanpwnudwn on 2008-06-01
> **srt4lifez said:**
> sounds like you copied the repository line that your supposed to copy and paste into a terminal into the /etc/apt/sources.list file.

the word 'echo' shouldnt be in that file... open it up in a text editor and remove w/e is on line 56.

Even under root access I dont have permissions to edit the file. I tried copying it to the desktop, editing it, and replacing it, but it still wont let me. 

I'm sure that there is some sudo command I can type in the terminal, but I'm really new to this, what exactly would I type?

---

### Post by reacocard on 2008-06-01
> **kmanpwnudwn said:**
> Even under root access I dont have permissions to edit the file. I tried copying it to the desktop, editing it, and replacing it, but it still wont let me. 

I'm sure that there is some sudo command I can type in the terminal, but I'm really new to this, what exactly would I type?

```
sudo gedit /etc/apt/sources.list
```

---

### Post by kmanpwnudwn on 2008-06-01
> **reacocard said:**
> ```
sudo gedit /etc/apt/sources.list
```

Wow, that makes sense. I was trying to make thing's a lot harder than they needed to be. Thanks!

---

### Post by barbedsaber on 2008-06-01
as soon as this works with windows managment, and launchers, you will make me very happy, for now I will have to alt tab, and fall in love with gnome-do

---

### Post by Rowanmf on 2008-06-03
I would like to find out how to sort out a problem i am having with awn , i have a fresh install of HH 8.04 , and i followed instructions to add the awn repo's from an earlier post , and i have added and now using awn properly , however there are no aplets , launchers or themes to choose from , i have read every single post here from page 1 to page 20 , i have tried to follow and correct my problem but the synaptic manager refuses to add awn extra's because of dependancies , i have tried an apt-get update and a few other things but i still cant add the extra's , is there something that i have missed , should i be trying to uninstall and reinstall .

Thanks

Rowan

---

### Post by yogo on 2008-06-03
Go to the AWN site and add the extras, just google adding applets for AWN and there are specific directions for doing so. [http://wiki.awn-project.org/index.php?title=Awn_Extras](http://wiki.awn-project.org/index.php?title=Awn_Extras)

Just wanted to add,  I am not able to drag programs into the dock like before and I have my dock to start at start-up but it goes thru a bit of ugliness first, I get a white box at top left and another one at the bottom but after a few seconds, it looks as it should.

Not sure what tweaks gOS applied to it but it runs perfect at start-up in gOS

---

### Post by reacocard on 2008-06-03
> **Rowanmf said:**
> I would like to find out how to sort out a problem i am having with awn , i have a fresh install of HH 8.04 , and i followed instructions to add the awn repo's from an earlier post , and i have added and now using awn properly , however there are no aplets , launchers or themes to choose from , i have read every single post here from page 1 to page 20 , i have tried to follow and correct my problem but the synaptic manager refuses to add awn extra's because of dependancies , i have tried an apt-get update and a few other things but i still cant add the extra's , is there something that i have missed , should i be trying to uninstall and reinstall .

Thanks

Rowan

make sure you have ubuntu-updates enabled, that's most often the source of dependency issues.

---

### Post by micsame on 2008-06-03
Hi,

I can't get active applets to work. The icons don't show, but running aps are appearing. See attach for more details.

I have done apt-get update and installed all updates. 


/Michael

---

### Post by reacocard on 2008-06-03
> **micsame said:**
> Hi,

I can't get active applets to work. The icons don't show, but running aps are appearing. See attach for more details.

I have done apt-get update and installed all updates. 


/Michael

you appear to be running an older version, please completely remove both repository and source installs according to the guide and FAQ, then reinstall following the guide.

---

### Post by Snappo on 2008-06-04
I go to launch it and nothing happens... infact it messed up my top bar...

---

### Post by reacocard on 2008-06-04
> **Snappo said:**
> I go to launch it and nothing happens... infact it messed up my top bar...

can you be more specific? in what way is your top bar messed up? How did you launch it?

---

### Post by denilson3 on 2008-06-05
> **ehron said:**
> First, thanks for packaging this.  I really like it.  

I just reinstalled Hardy.  Before I reinstalled when I got an IM (using Pidgin 2.4.1) the person's buddy icon would bounce up and down.  After the reinstall, using the same version of AWN, the icons no longer bounce up and down.

I have played with various settings, but I can't seem to find the cause of this behavior.  Any tips?

Thanks.

i have the same problem.. the suggested fix in this thead didnt work for me either.

---

### Post by moonbeam on 2008-06-05
> **denilson3 said:**
> i have the same problem.. the suggested fix in this thead didnt work for me either.

I don't use pidgin myself but I do know pidgin does need to be properly configured for this...  taking a quick look I'm thinking you need to load the "Message Notification" plugin and in the plugin configuration under "Notification Methods" make sure to "set Window manager Urgent hint"

Just a guess...

---

### Post by micsame on 2008-06-05
> **reacocard said:**
> you appear to be running an older version, please completely remove both repository and source installs according to the guide and FAQ, then reinstall following the guide.

Hi,

Thank for you're quick reply. I did what you said uninstall/install but that didn't work and i am not an Linux expert, so i removed the OS and then installed it and know it work fine..


/Michael

---

### Post by Snappo on 2008-06-05
> **reacocard said:**
> can you be more specific? in what way is your top bar messed up? How did you launch it?

I launched it from the program menu & that was it.

---

### Post by azizzle on 2008-06-06
I'm trying to get awn curves, but the setting for bar angle won't accept -1. It states that the key is not writable. What should I do?

---

### Post by denilson3 on 2008-06-06
> **moonbeam said:**
> I don't use pidgin myself but I do know pidgin does need to be properly configured for this...  taking a quick look I'm thinking you need to load the "Message Notification" plugin and in the plugin configuration under "Notification Methods" make sure to "set Window manager Urgent hint"

Just a guess...

thanks...i think that plugin used to be enabled by default..not sure.  whatever the case, that fixed it. thanks.

---

### Post by nickdbliss on 2008-06-06
Hi thanks for this howto. i just finished installing AWN and everything is working fine. :)

---

### Post by mhedges48 on 2008-06-06
Thanks to all, just upgraded to AWN 0.3.1 and loving it.

One question: is there a way to customize a particular launcher so that its default setting on launch is "Always on Visible Workspace"? There are certain launchers that I always need on whatever workspace I am on, and just wondered if there was a way to change the configuration for them so their setting is "Always on Visible Workspace" as opposed to manually changing it each time I start the computer.


thanks and best wishes

---

### Post by WeEatVista on 2008-06-06
Okay, no I haven't read every post in these 3 forums that cover AWM, so I'm not sure if this question was asked and answered. My question is, is AWM move-able? Can I move it to the right of my screen and not the bottom? 

Thanks in advance,

We Eat Vista

---

### Post by ayoli on 2008-06-06
> **WeEatVista said:**
> Okay, no I haven't read every post in these 3 forums that cover AWM, so I'm not sure if this question was asked and answered. My question is, is AWM move-able? Can I move it to the right of my screen and not the bottom? 

Thanks in advance,

We Eat Vista
No, not at the moment. This is maybe a planned feature.

---

### Post by gfern on 2008-06-06
This is an authentic question, since I'm a true newbie, just installed Linux for the first time last Thursday, so please don't take me wrong: How is it getting your version of AWN better than getting the stable one from Hardy Universe? I mean, it says on your FAQ that many of the applets currently don't work with this compilation of AWN, would they work with the one in Hardy? Is yours more, let's say... modern, cutting edge? I'm just trying to understand how this works.... differences in releases and so on... 

Other than that, I understand that I can help the project by using this version and reporting bugs, but would that go back to the stable version at some point? I guess the bottom line is: how different of a project is this from the stable compilation? 

Thanks you!

---

### Post by reacocard on 2008-06-07
> **gfern said:**
> This is an authentic question, since I'm a true newbie, just installed Linux for the first time last Thursday, so please don't take me wrong: How is it getting your version of AWN better than getting the stable one from Hardy Universe? I mean, it says on your FAQ that many of the applets currently don't work with this compilation of AWN, would they work with the one in Hardy? Is yours more, let's say... modern, cutting edge? I'm just trying to understand how this works.... differences in releases and so on... 

Other than that, I understand that I can help the project by using this version and reporting bugs, but would that go back to the stable version at some point? I guess the bottom line is: how different of a project is this from the stable compilation? 

Thanks you!

Mine is built straight out of revision control, meaning you get new features and fixes as they're added rather than having to wait months for an update (on the flip side you also get bugs as they're added :) ).  Also the standard ubuntu packages do not currently supply any applets, so if you want an easy way to get applets this repository is currently a better option.

As for your question about bugs, I don't actually modify the code myself, I just package what the main AWN devs provide. Since my packages are generally closely in line with the latest AWN developments, reporting bugs found is in fact very useful to the developers and any fixes will be placed into the next stable release. If you need more information on testing and reporting bugs in AWN I suggest you talk to some devs in #awn on freenode.

Hope that clears things up!

---

### Post by gfern on 2008-06-07
> **reacocard said:**
> Mine is built straight out of revision control, meaning you get new features and fixes as they're added rather than having to wait months for an update (on the flip side you also get bugs as they're added :) ).  Also the standard ubuntu packages do not currently supply any applets, so if you want an easy way to get applets this repository is currently a better option.

As for your question about bugs, I don't actually modify the code myself, I just package what the main AWN devs provide. Since my packages are generally closely in line with the latest AWN developments, reporting bugs found is in fact very useful to the developers and any fixes will be placed into the next stable release. If you need more information on testing and reporting bugs in AWN I suggest you talk to some devs in #awn on freenode.

Hope that clears things up!
It sure does! Thanks for the explanation! : )

---

### Post by Irwin J. Finster on 2008-06-08
Hi,

I followed your excellent instructions, and installed AWN just fine, and love it !

There is but on issue I have. I use a dual monitor setup, and when I first startet awn, it appeard on my bottom monitor, which is just what I want. After my first reboot however, AWN insists on appearing on my top monitor which is annoying. I don't have the least clue why, or how I could move it down again. I tried to switch around the monitor priority in the nvidia-settings, but no matter which monitor I designate as main, AWN still appears on the top monitor,....

Any help would be highly apricciated... Thanks

---

### Post by scope on 2008-06-08
Hi, I was looking for a brightness applet for awn, so I can change the screen brightness of my laptop. Is there any one?

This is not related to this thread but I'll ask, I deleted all the gnome panels to exclusively use awn but now alt + f2 doesnt load the window to execute commands. I guess the main gnome-panel enabled that, but now that I removed it I cannot use it.
Is there any alternative to that?

Thanks

---

### Post by gamont on 2008-06-08
My AWN bar appears when started. I configured to autohide.
But after 4 or 5 clicks the bar dont appear more.

Launching from terminal appears an error:
FAILED : /home/gamont/.config/awn/launchers/awn_launcher.desktop

Im using Ubuntu 8.04, 1024-768 resolution, dont delete the Gnome panels.

What can i do to keep the bar?
Thanks,

---

### Post by reacocard on 2008-06-08
> **Irwin J. Finster said:**
> Hi,

I followed your excellent instructions, and installed AWN just fine, and love it !

There is but on issue I have. I use a dual monitor setup, and when I first startet awn, it appeard on my bottom monitor, which is just what I want. After my first reboot however, AWN insists on appearing on my top monitor which is annoying. I don't have the least clue why, or how I could move it down again. I tried to switch around the monitor priority in the nvidia-settings, but no matter which monitor I designate as main, AWN still appears on the top monitor,....

Any help would be highly apricciated... Thanks

it is possible to force AWN to open at a specific place. To do so, press alt+f2 and enter 'gconf-editor'. In this window select apps->avant-window-navigator. Make sure the 'force_monitor' option is checked, and then set monitor_height to the *combined* height of your monitors, and monitor_width to the width of the lower monitor. The next time AWN starts it should now be placed in the correct position.

---

### Post by reacocard on 2008-06-08
> **scope said:**
> Hi, I was looking for a brightness applet for awn, so I can change the screen brightness of my laptop. Is there any one?

This is not related to this thread but I'll ask, I deleted all the gnome panels to exclusively use awn but now alt + f2 doesnt load the window to execute commands. I guess the main gnome-panel enabled that, but now that I removed it I cannot use it.
Is there any alternative to that?

Thanks

There is no screen brightness applet at present.

For alt+f2, I suggest using gmrun instead. You can install it with
```

sudo apt-get install gmrun

```
run it with 'gmrun'. It does not take care of binding alt+f2 for you, but compiz (and most other window managers) allows you to run arbitrary commands on a keycombo so it's trivial to do that yourself. (In ccsm, the settings are in General->Commands)

---

### Post by scope on 2008-06-08
Thanks! Only lacking the brightness applet, but I dont need gnome-panel anymore.

While I was downloading the gmrun packet the systray applet got a bit crazy:

[[IMG]http://img294.imageshack.us/img294/8636/pantallazo5gq4.th.png[/IMG]](http://img294.imageshack.us/my.php?image=pantallazo5gq4.png)

(The systray icon of synaptic appeared a lot bigger than normal)

---

### Post by nickdbliss on 2008-06-08
cheers it is working.

---

### Post by Vadi on 2008-06-08
> **scope said:**
> 
While I was downloading the gmrun packet the systray applet got a bit crazy:

(The systray icon of synaptic appeared a lot bigger than normal)

I've seen that happen once in the gnome panel with the pidgin icon, so I don't think it's awn's fault here.

---

### Post by scope on 2008-06-09
Is there any way to "refresh" awn or its applets?
I'm having problems with all the main menu applets (awn main menu, cairo main menu, cairo main menu classic), if I install an application, the icon won't appear on them until I go to awn manager and deactivate-re-activate the applet.

---

### Post by Irwin J. Finster on 2008-06-09
> **reacocard said:**
> it is possible to force AWN to open at a specific place. To do so, press alt+f2 and enter 'gconf-editor'. In this window select apps->avant-window-navigator. Make sure the 'force_monitor' option is checked, and then set monitor_height to the *combined* height of your monitors, and monitor_width to the width of the lower monitor. The next time AWN starts it should now be placed in the correct position.

Great, thank you very much that worked like a charm - height and width were already correctly enterd, All I had to do was check 'force monitor' and presto.....

THANKS! Keep up the good work with AWN -> it's one of the coolest things I've seen in a while!

---

### Post by detroit/zero on 2008-06-09
When I had AWN running on Gutsy, I found and downloaded something that provided additional control to the AWN animations. It allowed me to select different animations for each function, i.e.: spin the icon when the mouse hovers on it, squish when you click it, fade when the application closes, etc.

I've been searching for this download (or a link to it) both in these forums and at the AWN sites, and can't seem to dig it up.

Anybody else know what one I'm talking about and where to get it?

---

### Post by scope on 2008-06-09
I know what you are talking about and that feature comes bundled in the AWN standard installation as fas as I know.
I didnt install any aditional plugin or program and in the general tab i can change the icons to zoom, squish, rotate, glow, rotate+glow, or custom (choose the animation depending on the event).

---

### Post by detroit/zero on 2008-06-09
Ha! Yeah, that's how it's done. I seem to remember downloading something to do that last fall for Gutsy, but I could be wrong.

Anyways, I got it going. Thanks..

---

### Post by zeta on 2008-06-09
Hi,
I installed AWN through reacocards repository, and everything works really great - except the trash can. The functionality is there, it links to wherever .trash is located under hardy, but there is no icon. This problem is consistent with both the "Tracks Applet" and the "Stacks Trasher". :( 
I tried around quite a bit with the icon set (running Human), set links to the human-trash-icon but to no avail. 
Any idea how to fix this?!

---

### Post by pmaconi on 2008-06-09
Its a known bug in the way that the applets access the trash can. They are linked to the wrong one (~/.Trash) instead of ~/.local/share/Trash. I expect that they will be updated soon enough to fix the problem. If you use the Trash Applet and click to open, it will take you to the correct folder. However, it won't show if there is anything in the trash and you can't right click to empty. But going to the folder and using the empty button there works fine.

---

### Post by zeta on 2008-06-10
Hi pmaconi,
thanks for your reply. I was under the impression that this bug affects the functionality, not the appearance. Plus - the trash applet works on my laptop and it even worked on my main machine - right after bootup, and only as long as I didn't click on it. Then it changed back to the whitish rectangular you see below (Screenshot with both trash applets) :confused:

[[IMG]http://img120.imageshack.us/img120/5262/screenshot1tu6.th.png[/IMG]](http://img120.imageshack.us/my.php?image=screenshot1tu6.png)

---

### Post by pmaconi on 2008-06-10
I guess that I misunderstood your first post. I thought that you meant the full trash can wouldn't change icons. Both of the applets appear consistent with the icon from my current theme. I don't know what the problem is with yours.

---

### Post by Brian96 on 2008-06-17
I have successfully installed and use AWN using this how-to on other machines, but on my latest setup I can install and run it fine, but I can't run awn-manager.

When I right-click on the dock and select "Dock Preferences" nothing happens.

When I run awn-manager in terminal, I get this:

```

brian@ubuntu:~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 46, in <module>
    from awnApplet import awnApplet
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 38, in <module>
    from xdg.DesktopEntry import DesktopEntry
ImportError: No module named xdg.DesktopEntry

```

Any ideas?

---

### Post by reacocard on 2008-06-17
> **Brian96 said:**
> I have successfully installed and use AWN using this how-to on other machines, but on my latest setup I can install and run it fine, but I can't run awn-manager.

When I right-click on the dock and select "Dock Preferences" nothing happens.

When I run awn-manager in terminal, I get this:

```

brian@ubuntu:~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 46, in <module>
    from awnApplet import awnApplet
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 38, in <module>
    from xdg.DesktopEntry import DesktopEntry
ImportError: No module named xdg.DesktopEntry

```

Any ideas?

install python-xdg is my guess

---

### Post by DancemasterGlenn on 2008-06-18
I just wanted to say that the latest update has completely fixed pandora for me. The applet is working amazingly! Thanks so much for this.

---

### Post by Tiede on 2008-06-18
Hello all.
I am having a most shameful problem here.
I just installed awn and I am trying to get affinity to work correctly.
I have tracker enabled, but I could not use the search function in affinity. Therefore, I am not able to use any programs and my "Favorites" section is completely empty.
I am using ubuntu hardy, latest updates, with all the bells and whistles and I am using avant-window-navigator-bzr from reacocard's launchpad repo.

I am thinking that my problem stems from not having affinity-tracker (or affinity-tracker-svn) installed.
But I have searched *everywhere* for them and cannot seem to find those packages. There not in ubuntu's repos (not even universe), not in reacocard's repo neither, and a quick google search for affinity-tracker.deb gave me nothing.
I seem to be drawing blanks here. Can someone point me to the proper way of doing this? Thanks :confused:

---

### Post by PRGUY85 on 2008-06-19
I have installed AWN various times but I can never consistently get applets to work at boot (right now I have the Stacks applet active...get the usual white line and no way to get into Dock Preferences)....it works on my laptop...any ideas?

Update:

Only way to get everything to work is when I uninstall and reinstall everything again.  After that, if I restart the system, I get same problem.  I removed the Stacks applet and left only the AWN manager and still got the same problem.

---

### Post by Tiede on 2008-06-19
What is the problem you are having exactly. Which applets? Sounds weird that restarting the system would break anything... Maybe I am reading your post wrong?

---

### Post by PRGUY85 on 2008-06-22
AWN won't show applets or allow me to access the Dock Preferences when I click it.  Only way to have it appear is uninstall and reinstalling it.  On another note my Deskbar applet also doesn't work on startup...

These 2 issues do not occur on my laptop running Hardy 32-bit (same as desktop...)

---

### Post by jramoyo on 2008-06-23
Hi I've got 2 questions actually. Coming off 7.10, AWN is working great for me, however when I upgraded to 8.04 (fresh install), the AWN terminal applet and trash stacker applets are no longer working. Are there known bugs/issues concerning these 2 applets?

Also, when I use the curved bar (setting the bar angle to -1) the icons are not aligned--I understand that they are supposed to be placed like an arch, but for me, some icons are placed oddly higher and some lower. Any of you guys experience this?

---

### Post by reacocard on 2008-07-09
quick notice: the latest AWN update has made an API change that will require you to remove and re-add all your applets.

for more information: [http://ubuntuforums.org/showthread.php?p=5351476](http://ubuntuforums.org/showthread.php?p=5351476)

---

### Post by eternalnewbee on 2008-07-09
Thanks **Stormspireiv** for the tip for adding awn to the start-up programs

---

### Post by DJ_Peng on 2008-07-10
Thanks for the update, reacocard. When I fired up my comp this morning I noticed the issue with my applets but there was the answer sitting in my email. I love first thing in the am fixes that are so easy to find and implement. :)

---

### Post by SomeGuyDude on 2008-07-12
All the applets are gone after an update. It's not like last time, they're just gone. Not even showing up in the manager. Whuzzup?

---

### Post by ayoli on 2008-07-12
> **SomeGuyDude said:**
> All the applets are gone after an update. It's not like last time, they're just gone. Not even showing up in the manager. Whuzzup?

I guess that the fix for your issue is 3 posts above.

---

### Post by PRGUY85 on 2008-07-12
Hmm Im having the same issue.  There are not Applets available to Add anymore and I can't see how to fix it after the most recent update.  Will this get fixed on future updates?

---

### Post by SomeGuyDude on 2008-07-12
> **ayoli said:**
> I guess that the fix for your issue is 3 posts above.

No, that was just for when the applets stopped working. You'd open up the manager, deactivate the applets, and the activate 'em again. Now they can't be activated because there aren't any in the manager.

---

### Post by JayTee on 2008-07-12
I'm having the same problem. All the applets in the AWN Manager have disappeared except for Launcher/TaskManager since I applied the update to AWN this morning. The previous update to AWN created the white line problem many people were having but deactivating and then reactivating the applets fixed that however the list of applets were "jumpy" (the list would display erratically) and most of the icons for the applets were the default gears icon. Now I just have only the one applet in the list. I'm running Gutsy 7.10. I know they made alot of code changes recently and although the applets aren't in the list AWN is running with the applets that I'd already activated.

 I'm sure this will be fixed shortly.

---

### Post by PRGUY85 on 2008-07-12
> **SomeGuyDude said:**
> No, that was just for when the applets stopped working. You'd open up the manager, deactivate the applets, and the activate 'em again. Now they can't be activated because there aren't any in the manager.

Exactly, now I cannot add any applet.

---

### Post by SomeGuyDude on 2008-07-12
For reference, here's what the applet menu looks like now:

---

### Post by reacocard on 2008-07-12
I'm rebuilding awn-core-applets against the new awn now, hopefully that'll fix the issue with applets not being shown.

---

### Post by SomeGuyDude on 2008-07-12
And so it did!

Damn I love open-source. The devs are always so amazingly responsive.

---

### Post by JayTee on 2008-07-12
yep, that last update fixed the applet showing up in the list in the Awn Prefernces but it broke the taskbar function. Launchers won't display and any running task no longer shows up on the bar when minimized. I've tried a complete removal and deleted all traces then reinstalled with Synaptic but it still fails to show running programs and launchers. I'm running Ubuntu 7.10.

---

### Post by Ruazinn on 2008-07-13
I'm also having the problem of the applets not being shown in awn-manager.  I installed an update to awn-core-applets-bzr this morning via update manager.  I was hoping the update would fix the problem, but it didn't.  Here's a post I made about the topic a few minutes ago to another thread:

[http://ubuntuforums.org/showthread.php?t=858338&highlight=no+applets+awn-manager](http://ubuntuforums.org/showthread.php?t=858338&highlight=no+applets+awn-manager)

---

### Post by moonbeam on 2008-07-13
Some of the current issues are also being tracked at  [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true)

---

### Post by moonbeam on 2008-07-13
Anyone having an issue with the taskmanager please do the following.

1) Start awn-manager.
2) Close awn.
3) Remove the Launcher/Taskmanager applet from the applet list.
4) Add the Launcher/Taskmanager applet to the applet list.
5) Start awn.

If that doesn't work then please post a bug at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn)

Thanks.

---

### Post by SomeGuyDude on 2008-07-13
"avant-window-navigator-bzr: subprocess post-installation script returned error exit status 2"

New update, just did that. Lost my MiMenu and Quit applets.

---

### Post by reacocard on 2008-07-13
> **SomeGuyDude said:**
> "avant-window-navigator-bzr: subprocess post-installation script returned error exit status 2"

New update, just did that. Lost my MiMenu and Quit applets.

sorry you caught that update, it was only up for a few minutes. new version with the fix is available now.

---

### Post by SomeGuyDude on 2008-07-14
> **reacocard said:**
> sorry you caught that update, it was only up for a few minutes. new version with the fix is available now.

Two problems. 

1) Terminal applet is now a big X icon.

2) Those two applets are still broken. Running in terminal gives me this:

```
(awn-applet-activation:19632): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1715: handler `37' of instance `0x81f6008' is not blocked
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 131, in <module>
    applet = App (awn.uid, awn.orient, awn.height)
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 43, in __init__
    self.set_awn_icon('quit-applet', uid, 'application-exit')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/mimenu/mimenu.py", line 212, in <module>
    applet = App                  (awn.uid, awn.orient,awn.height)
  File "/usr/share/avant-window-navigator/applets/mimenu/mimenu.py", line 54, in __init__
    self.set_awn_icon('MiMenu', uid, 'gnome-main-menu')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)

```

---

### Post by Ruazinn on 2008-07-14
Just installed the latest updates, but still only have the taskman applet listed.  I ran avant-window-navigator from the command line and didn't get any error messages.  

In the directory /usr/local/lib/awn/applets, the only file is taskman.desktop.  I installed awn-core-applets-bzr.

Thanks for the quick responses.  Hope I don't sound too whiny.

---

### Post by Ruazinn on 2008-07-14
I'm not a python programmer, but I scanned through the file awnApplet.py. It looks to me like the load_applets function scans through a number of applet directories for ".desktop" files.  I found applet .desktop files on my system in the directory /user/share/avant-window-navigator.  But this directory is not one of the ones that load_applets scans.  load_applets appears to only scan through:

/usr/lib/awn/applets,
/usr/local/lib/awn/applets,
/usr/lib64/awn/applets,
/usr/local/lib64/awn/applets,
~/.config/awn/applets

---

### Post by nomentero on 2008-07-14
sorry double post

---

### Post by nomentero on 2008-07-14
latest update fail:```

Configurando awn-core-applets-bzr (0.3.1.bzr699.1~hardy) ...
(gconftool-2:15131): GConf-WARNING **: Falló al escribir «/etc/gconf/gconf.xml.defaults/%gconf-tree.xml»: Falló al mover el archivo temporal «/etc/gconf/gconf.xml.defaults/%gconf-tree.xml.new» a la ubicación final «/etc/gconf/gconf.xml.defaults/%gconf-tree.xml»: No existe el fichero ó directorio

```
I purge and reinstall awn-bzr but not work always same problem.

---

### Post by DJ_Peng on 2008-07-14
> **SomeGuyDude said:**
> Two problems. 

1) Terminal applet is now a big X icon.

2) Those two applets are still broken. Running in terminal gives me this:

```
(awn-applet-activation:19632): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1715: handler `37' of instance `0x81f6008' is not blocked
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 131, in <module>
    applet = App (awn.uid, awn.orient, awn.height)
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 43, in __init__
    self.set_awn_icon('quit-applet', uid, 'application-exit')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/mimenu/mimenu.py", line 212, in <module>
    applet = App                  (awn.uid, awn.orient,awn.height)
  File "/usr/share/avant-window-navigator/applets/mimenu/mimenu.py", line 54, in __init__
    self.set_awn_icon('MiMenu', uid, 'gnome-main-menu')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)

```
I hate to say this but I'm glad I'm not the only one with big red X's on his dock today. I snagged the waiting updates when I fired up my comp about half an hour ago, restarted AWN, and found the attached image waiting for me. The three applets affected are Cairo Main Menu (I don't think it's the classic version but I may be wrong), Places and AWN Terminal. It's funny because they show up alright in the Applet Preferences window. The three applets work as expected, despite getting this when I run it in a terminal window:
> peng@############:~$ avant-window-navigator
Screen is composited.
LOADED : /home/peng/.config/awn/launchers/awn_launcher-3.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-10.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-4.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-6.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-14.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-7.desktop
LOADED : /home/peng/.config/awn/launchers/awn_launcher-8.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/cairo_main_menu.desktop
APPLET : /usr/share/avant-window-navigator/applets/places.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnterm.desktop
APPLET : /usr/share/avant-window-navigator/applets/trash.desktop

** (awn-applet-activation:8218): WARNING **: Places: XDG_DESKTOP_DIR is not set... defaulting to "~/Desktop"

---

### Post by reacocard on 2008-07-14
I think the icon problems are due to the move to the new awn-icons framework. There's some more fixes for this upstream, I'll build new packages after I get back from work today.

---

### Post by DJ_Peng on 2008-07-14
Awesome, reacocard. Thanks for the prompt response. I look forward to to the next update from the PPA.

---

### Post by PRGUY85 on 2008-07-14
I have install this on several computers and they all work, however, on my main computer the Stacks applet never appears...it only shows the white line and never lets me access Dock Preferences once that happens.  The only way to get it to work just once is to reinstall the packages.  Once I reboot, it goes back to showing the white line...

Considering this only happens on my main desktop, could it be a startup program or anything else that is not letting the Stacks applet start showing the white line?

---

### Post by DJ_Peng on 2008-07-14
Have you tried accessing the prefs panel via System > Preferences > Awn Manager? Also what version of AWN are you running? I know the latest PPA updates have had some issues due to upstream changes but I suspect it will be easier to help you if we know which version you're running. (That's available in Synaptic if you can't get into the Dock Preferences.)

---

### Post by Ruazinn on 2008-07-14
Reacord, 

I edited the code in /usr/local/share/avant-window-navigator/awn-manager/awnApplet.py and added a line to load_applets to make it include "/usr/share/avant-window-navigator/applets" in the scan.  (That is, I added that line to the array named "dirs".)  When I ran awn-manager, lots and lots of applets were listed.  So I moved the comics applet to the active applets list.  I got the white line and this error message in the terminal:

ruazinn@a1888c:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
Creating new applet :/usr/share/avant-window-navigator/applets/comics.desktop uid:1216045344

** (awn-applet-activation:7762): WARNING **: This desktop file does not exist /usr/share/avant-window-navigator/applets/comics.desktop

Again, from my previous post, it appears that all of my applet desktop files except taskman.desktop are in a directory which load_applets does not scan.

---

### Post by brandroid on 2008-07-14
I followed the method in this how-to, and I've reinstalled several times in an attempt to solve my problem, but it doesn't seem to be helping.
My problem is this: everything works but two things, the gnome related buttons on awn (show desktop, main menu, and shutdown) and the separators/back(or top, depending on your point of view) of the bar seem to have disappeared.

When running in terminal, the pertinent information is this
```
APPLET : /usr/share/avant-window-navigator/applets/quit-applet.desktop
Traceback (most recent call last):
  File "/usr/share/awn/applets/showdesktop/showdesktop.py", line 64, in <module>
    applet = ShowDesktopButton (awn.uid, awn.orient, awn.height)
  File "/usr/share/awn/applets/showdesktop/showdesktop.py", line 44, in __init__
    self.set_awn_icon("showdesktop", uid, "desktop")
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)
['/usr/share/awn/applets/calendar', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0', '/usr/share/awn/applets/calendar/google']
Traceback (most recent call last):
  File "/usr/share/awn/applets/mimenu/mimenu.py", line 212, in <module>
    applet = App                  (awn.uid, awn.orient,awn.height)
  File "/usr/share/awn/applets/mimenu/mimenu.py", line 54, in __init__
    self.set_awn_icon('MiMenu', uid, 'gnome-main-menu')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 131, in <module>
    applet = App (awn.uid, awn.orient, awn.height)
  File "/usr/share/avant-window-navigator/applets/quit-applet/quit-applet.py", line 43, in __init__
    self.set_awn_icon('quit-applet', uid, 'application-exit')
TypeError: AwnAppletSimple.set_awn_icon() takes exactly 2 arguments (3 given)



```

I also attached a screenshot of what my bar currently looks like.

---

### Post by moonbeam on 2008-07-14
A few comments regarding various issues:

1) If awn-manager is not looking in /usr/share/avant-window-navigator/applets for applet then the awn-manager installed is not the correct version.

2) Yes some applets are broken.  Two reasons:  moving of files under share and introduction of awn-icons.

3) For those of you seeing an X in place of a normal icon in an applet it means that awn-icons is unable to find icon in the installed gtk icon theme.  The solution is to drag and drop the desired icon onto the applet.  For references the terminal applet looks for an icon called "terminal"  and cairo menu (and most other menus) us "gnome-main-menu".   But you can drag and drop whatever icon you want into the applet (Not all of the applets have been converted yet).  The goal with this is to have applets use gtk icon theme icons by default and thus visually mesh with the rest of the desktop... obviously some icon themes are a lacking certain names :-)

---

### Post by DJ_Peng on 2008-07-14
Thanks for the update, moonbeam. I take it the icons for the prefs window has a different info source than on the dock itself, since I'm seeing the icons in the manager but not on the dock.

---

### Post by moonbeam on 2008-07-14
> **DJ_Peng said:**
> Thanks for the update, moonbeam. I take it the icons for the prefs window has a different info source than on the dock itself, since I'm seeing the icons in the manager but not on the dock.

Yeah the awn-manager gets its icons in a slightly different manner.  I expect that over the next little bit we'll make sure the applets install a fallback icon that gets used if there's nothing else available.  It may not end up being the highest priority as it's just a matter of draggin and dropping a desired icon at the moment.  Though I am surprised at some of the icons that are missing in the themes.

---

### Post by hollowhead on 2008-07-14
Yep I have the same problems.  48 hours ago I updated avant amongst a host of other things.  It was broken when I used the machine again tonight. No applets visible, including in preferences. I checked for upgrades and there were loads including avant and its applets.  Upgraded this restored the applets in prefs although I had to set them back up in prefs including my stacker (lost stacked files).  However, no programme icons for running programmes appear on the taskbar which makes it difficult to get back to a programme window you have minimised.  Its annoying since I put up with the glitchs in gutsy to have them solved in hardy and as far as I was concerned it was working perfectly to 48 hours ago.  It amazing how much you rely on it.....NH Hardy with avant 0.3.1

---

### Post by hollowhead on 2008-07-14
By the way brandroid I love your dock (as I should have called it above) what theme is it?  NH

---

### Post by hollowhead on 2008-07-14
Thanks moonbeam I followed your method for restoring icons to the dock it worked, the Launcher/Taskmanager wasn't added back when I put all my applets back in after they disappeared between upgrades.  I was unaware of its function sorry..... NH

---

### Post by PRGUY85 on 2008-07-15
> **DJ_Peng said:**
> Have you tried accessing the prefs panel via System > Preferences > Awn Manager? Also what version of AWN are you running? I know the latest PPA updates have had some issues due to upstream changes but I suspect it will be easier to help you if we know which version you're running. (That's available in Synaptic if you can't get into the Dock Preferences.)

I am using version 0.3.1.bzr405.1~hardy...had an update a few minutes ago.  The Stacks applet worked after the update but when I reboot the same stuff occurs.  I cannot access AWN Manager through Preferences or through Dock Preferences and Stacks Applet doesn't show, just the White line.

---

### Post by DJ_Peng on 2008-07-15
*Yooouge* thanks to reacocard and moonbeam. I got the latest update this am and my dock is working normally again. 

@PRGUY85:
I don't know why you can't access the prefs panel. What happens if you type ```
awn-manager
``` in a Terminal? I can't help with Stacks as I haven't used that applet yet but hopefully someone will be around soon that is smarter than me when it comes to Stacks. :)

---

### Post by PRGUY85 on 2008-07-15
When I type awn-manager I get:

```
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 45, in <module>
    from awnTheme import AwnThemeManager
  File "/usr/share/avant-window-navigator/awn-manager/awnTheme.py", line 25, in <module>
    import awn
  File "/usr/lib/python2.5/site-packages/awn/__init__.py", line 31, in <module>
    from awn import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

```

---

### Post by brandroid on 2008-07-15
> **hollowhead said:**
> By the way brandroid I love your dock (as I should have called it above) what theme is it?  NH

I'm just using the "default" theme, but I the iconset is Black & White 2. [http://www.gnome-look.org/content/show.php?content=72619](http://www.gnome-look.org/content/show.php?content=72619)


> **moonbeam said:**
> A few comments regarding various issues:
1) If awn-manager is not looking in /usr/share/avant-window-navigator/applets for applet then the awn-manager installed is not the correct version.


I've recently updated, so I'm not sure how I don't have the correct version. Is there a way I can force it to look in the correct spot for those two or three applets it's having problems with? 
At the moment I'm using a temporary fix for the issue. I just copied the folders for the applets that I wanted to the spot where awn was looking for them...so it could find the newer, better, working versions.

---

### Post by hollowhead on 2008-07-15
Cheers moonbeam never could get that theme to install but I'll have another go.....

---

### Post by PRGUY85 on 2008-07-16
Any ideas on my issue?

```
~$ avant-window-navigator
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/emesene.desktop
LOADED : /usr/share/applications/transmission.desktop
LOADED : /usr/share/applications/banshee-1.desktop
LOADED : /usr/share/applications/totem.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/f-spot.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/synaptic.desktop
LOADED : /usr/share/applications/gnome-system-monitor.desktop
LOADED : /usr/share/applications/update-manager.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/stacks/stacks_applet.py", line 27, in <module>
    import awn
  File "/usr/lib/python2.5/site-packages/awn/__init__.py", line 31, in <module>
    from awn import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

```

and this when I call the manager or Dock Preferences:

```
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 45, in <module>
    from awnTheme import AwnThemeManager
  File "/usr/share/avant-window-navigator/awn-manager/awnTheme.py", line 25, in <module>
    import awn
  File "/usr/lib/python2.5/site-packages/awn/__init__.py", line 31, in <module>
    from awn import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

```

I went into usr/lib/awn/applets and didn't see any Stacks folder there along with other applets.

---

### Post by PRGUY85 on 2008-07-16
I think this has to do with me using OSS as a sound solution to use my X-FI card.  Saw someone using oss-linux deb package that had same error for another completely different thing.

UPDATE:

Solved from other thread:

> **janfsd said:**
> A better way is:
```
sudo apt-get install libesd0
```
OSSv4 is great!

---

### Post by ubukool on 2008-07-17
I'm really sorry if this has been posted a million times.  My AWN is broken at the moment.  I'm using the latest version from reacocard's repository.  When I got my last update I didn't know about the applet problem but I removed and replaced all my applets and they work fine now.   The only problem is that only the applets work!  My launchers do not appear.  I tried removing all my launchers and replacing them, but if I drag a launcher icon to the AWN bar from the menu, I get the little '+' sign to indicate that it will be added and then nothing appears!  The only other alternative would be to set them up manually from AWN manager and that's a massive task that I'd rather avoid if possible.

Can someone please help?  What's gone wrong and how do I fix it?  If this has been covered before please post a link to the post with the relevant answer.  Thanks in advance! :)

---

### Post by bossa on 2008-07-17
> **ubukool said:**
> I'm really sorry if this has been posted a million times.  My AWN is broken at the moment.  I'm using the latest version from reacocard's repository.  When I got my last update I didn't know about the applet problem but I removed and replaced all my applets and they work fine now.   The only problem is that only the applets work!  My launchers do not appear.  I tried removing all my launchers and replacing them, but if I drag a launcher icon to the AWN bar from the menu, I get the little '+' sign to indicate that it will be added and then nothing appears!  The only other alternative would be to set them up manually from AWN manager and that's a massive task that I'd rather avoid if possible.

Can someone please help?  What's gone wrong and how do I fix it?  If this has been covered before please post a link to the post with the relevant answer.  Thanks in advance! :)

I got this problem too, also some of icons have changed in particular the quit icon.Normally I would have the Mac for Lin quit icon but it has reverted to a door with a red arrow.:confused:
Any advice much appreciated .

---

### Post by moonbeam on 2008-07-17
> **ubukool said:**
> I'm really sorry if this has been posted a million times.  My AWN is broken at the moment.  I'm using the latest version from reacocard's repository.  When I got my last update I didn't know about the applet problem but I removed and replaced all my applets and they work fine now.   The only problem is that only the applets work!  My launchers do not appear.  I tried removing all my launchers and replacing them, but if I drag a launcher icon to the AWN bar from the menu, I get the little '+' sign to indicate that it will be added and then nothing appears!  The only other alternative would be to set them up manually from AWN manager and that's a massive task that I'd rather avoid if possible.

Can someone please help?  What's gone wrong and how do I fix it?  If this has been covered before please post a link to the post with the relevant answer.  Thanks in advance! :)

[http://ubuntuforums.org/showpost.php?p=5380262&postcount=259](http://ubuntuforums.org/showpost.php?p=5380262&postcount=259)

---

### Post by Bruynz on 2008-07-17
I Installed AWN exactly as instructed in the first post but whenever I try to start the program I just see a line on the bottom that disappears almost immediately. Probably it's the dock that just starts and shuts soon after.

Anybody knows why and what I can do.?

---

### Post by lamborghiniwang on 2008-07-17
Thanks for the great tutorial. 
I am having a small problem with the bzr version that I installed from ppa.
In awn-manager, I am trying to disable the option "Automatically start AWN on login", but I found that by doing so, it will also automatically disable the option "Tasks have arrows". It seems both options point to the same gconf-editor key "/apps/avant-window-navigator/app/tasks_have_arrows". 

Besides that, the pynot applet seems to have stability problem, and sometime if I close and then restart awn, pynot wouldn't display the notification tray appropriately. Although killing the python process and then restart awn would fix the problem.

---

### Post by ubukool on 2008-07-17
Dear moonbeam, thank you so much!  I didn't realize that the launchers were themselves managed by an applet and that I hadn't added it.  Dohhhhh!

It's great to have my AWN working again!  Yay! :)

---

### Post by reacocard on 2008-07-17
> **Bruynz said:**
> I Installed AWN exactly as instructed in the first post but whenever I try to start the program I just see a line on the bottom that disappears almost immediately. Probably it's the dock that just starts and shuts soon after.

Anybody knows why and what I can do.?

you need to be running compiz (or some other compositor) for awn to work.

---

### Post by Bruynz on 2008-07-17
I have compiz fushion but it still won't work. Is compiz fushion good?

---

### Post by bossa on 2008-07-17
Still having a problem with the dock icons .The quit icon is not the Mac4lin its the open door with the red arrow and now the calender applet is huge .
Any ideas ?

---

### Post by moonbeam on 2008-07-17
> **bossa said:**
> Still having a problem with the dock icons .The quit icon is not the Mac4lin its the open door with the red arrow and now the calender applet is huge .
Any ideas ?

The calendar applet was briefly broken in trunk.  The ppa must have been refreshed at that time.  It was fixed almost immediately and should be fine on the next ppa refresh.


Quit applet now uses whatever icon is in the gtk icon  theme that is configured.  If you want a different icon then just drag and drop the desired icon into the applet.

---

### Post by bossa on 2008-07-17
> **moonbeam said:**
> The calendar applet was briefly broken in trunk.  The ppa must have been refreshed at that time.  It was fixed almost immediately and should be fine on the next ppa refresh.


Quit applet now uses whatever icon is in the gtk icon  theme that is configured.  If you want a different icon then just drag and drop the desired icon into the applet.

Terrific that did the trick thanks moonbeam :-D

---

### Post by hedrian on 2008-07-20
i have installed and opened AWN..but when i change the colours and stuff nothing happens..how can i make a mac like dock using AWN?

---

### Post by Raistlin82 on 2008-07-20
hi all,  I insstalled awn from snaptic and all seems to be fine but i cannot seem to add the desktop switcher, could anyone help?

---

### Post by vgrisham on 2008-07-21
During the last updates, I lost the logout icon for the logout applet.

I've dragged a stock icon over it, and it works fine, but I miss that shiny black logout icon. Where can I find it? I assume it must be somewhere on my computer because when I go to dock preferences, I see it used to activate the applet. 

Anybody know where our shiny black logout icon went?

---

### Post by moonbeam on 2008-07-21
> **vgrisham said:**
> During the last updates, I lost the logout icon for the logout applet.

I've dragged a stock icon over it, and it works fine, but I miss that shiny black logout icon. Where can I find it? I assume it must be somewhere on my computer because when I go to dock preferences, I see it used to activate the applet. 

Anybody know where our shiny black logout icon went?

You will probably find it somewhere in /usr/share/avant-window-navigator/applets/quit-applet/icons/

---

### Post by vgrisham on 2008-07-21
Thanks! That's exactly where it was.

---

### Post by williamson389 on 2008-07-23
i tried the steps listed, all worked fine( or seemed to), but awn will not run.   when i go to applications- accesories- awn, nothing happens.  not sure why but on a different install guide i deleted my bottom taskbar.  dont know if that has anything to do with it.  i have unistalled and reinstalled.

thanks in advance

---

### Post by Richard9795 on 2008-07-23
Can you get AWN to zoom like the Mac OS X Dock?

---

### Post by Richard9795 on 2008-07-23
Oh And williamson389, do you have compiz enabled?

---

### Post by Islington on 2008-07-23
> **williamson389 said:**
> i tried the steps listed, all worked fine( or seemed to), but awn will not run.   when i go to applications- accesories- awn, nothing happens.  not sure why but on a different install guide i deleted my bottom taskbar.  dont know if that has anything to do with it.  i have unistalled and reinstalled.

thanks in advance

could you run it through a terminal and post any output?

---

### Post by moonbeam on 2008-07-23
> **Richard9795 said:**
> Can you get AWN to zoom like the Mac OS X Dock?

Short answer no, not at this time.  And not in the near future.  And possibly longer :-)

For a little discussion of why see: [http://moon-shiny.blogspot.com/2008/03/why-things-are-way-they-are.html](http://moon-shiny.blogspot.com/2008/03/why-things-are-way-they-are.html)

---

### Post by Islington on 2008-07-24
> **moonbeam said:**
> Short answer no, not at this time.  And not in the near future.  And possibly longer :-)

For a little discussion of why see: [http://moon-shiny.blogspot.com/2008/03/why-things-are-way-they-are.html](http://moon-shiny.blogspot.com/2008/03/why-things-are-way-they-are.html)

good post! thanks for explaining.:)

---

### Post by ajhtiredwolf on 2008-07-24
Hey, I installed the avant windows manager. But I expected that when I open a new window, it would not create a new icon on the avant panel, instead there would be one icon and you would click it to see a list of the same windows, like in the mac os, can this be done? Also is there a way to get rid of the fact that when you minimize and then reopen a window some times it will dissapear and then move to the first window on the right? I dont think this is a bug, it seems to be a feature since there is an animation for it. If so thanks.

---

### Post by Maverick88 on 2008-07-24
AWN BREAKS GIMP!!

If you install AWN from this rep "deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main", AWN will break gimp in Ubuntu hardy Heron 8.04.1.

See [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

You can easily verify that this is the problem.

1. Boot off the Hardy Heron 8.04.1 Live CD.
2. Add the repos:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

3. sudo apt-get update

4. sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

5. Try to run gimp. It will not run. If you run gimp from the terminal, you will see the following error:

symbol lookup error: undefined symbol: gimp_micro_version

Now try to get gimp to run again. I can't!
I tried to COMPLETELY uninstall the following:

awn (using the instructions on the [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363))
gimp
gimp-data
libgimp.

I even manually deleted the .gimp-2.4/ folder in my home directory. Then deleted the AWN third party rep sources and reinstalled gimp. I still see the error.

This bug is VERY annoying. I would really like to get gimp running again. Please HELP!

Rob

---

### Post by Maverick88 on 2008-07-24
I figured out the problem and the solution!!

The latest version of AWN does appear to break the Gimp 2.4.5 in Hardy Heron 8.04.1.

To get the gimp working again, you need to uninstall AWN. And then Uninstall BOTH gimp and gimpshop (if gimpshop is also installed). Then install gimp and afterwards install gimpshop.

Here are the details.

1. Uninstall AWN using the instructions from [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

2. Make sure you remove the third party AWN repos (as described in [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) ) and do a "sudo apt-get update"

3. Completely uninstall gimp, gimp-data, gimp-data-extras, libgimp2.0, xsane, xsane-common AND gimpshop. (This will also uninstall ubuntu-desktop, gimp-gnomevfs and gnome-python).

4. Reinstall the following:

gimp
gimp-data
gimp-data-extras
gimp-gnomevfs
gimp-python
libgimp2.0
ubuntu-desktop
xsane
xsane-common

5. If you want to re-install gimpshop, go for it BUT ONLY after you have first installed gimp.

6. Pray. Both gimp and gimpshop should work.

P.S. You might be able to get away with uninstalling fewer packages but this works!

---

### Post by Richard9795 on 2008-07-24
How Strange, nothing Happened to my Gimp with the exact rep....

---

### Post by DJ_Peng on 2008-07-24
Same here. AWN from reacocard's repo and GIMP from Ubuntu's repo with nary an issue, right out of the box.

---

### Post by Maverick88 on 2008-07-24
The issue definitely appears if you have both the gimp and gimpshop installed.  Then you install AWN.  

You can easily reproduce this by booting off the Ubuntu Hardy Heron LiveCD and installing gimpshop and AWN (from the third party repos).

To install gimpshop, visit the gimpshop home page and download the Debian package.  Then install using "sudo dpkg -i (package name)"

Then install AWN (from the third party repos listed in the beginning of this thread).

The minute you install AWN, the Gimp breaks.  (But you can still run gimpshop).

If you want to get the Gimp back, you will need to uninstall gimp, gimpshop and awn and then reinstall (using the instructions I posted above OR the following slightly easier instructions):

EASIER WAY TO GET THE GIMP WORKING AGAIN:

1. Uninstall AWN using the instructions from [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

2. Make sure you remove the third party AWN repos (as described in [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) ) and do a "sudo apt-get update"

3. COMPLETELY uninstall gimpshop.  (not just an uninstall)

4. Reinstall gimp amd libgimp2.0.  (You do not need to do a complete uninstall followed by an install).  

5. Optional -- reinstall gimpshop

6. Pray..  Now The Gimp and gimpshop work.

---

### Post by moonbeam on 2008-07-24
> **DJ_Peng said:**
> Same here. AWN from reacocard's repo and GIMP from Ubuntu's repo with nary an issue, right out of the box.

well according to the bug:  [https://bugs.launchpad.net/awn/+bug/251596](https://bugs.launchpad.net/awn/+bug/251596)

It appears Debian packages were used for gimpshop.  I'll leave it for the rest of you to determine if awn should be saddled with the blame in this case :-)

---

### Post by moonbeam on 2008-07-24
Following up on the gimpshop issue I'l paste the thoughts of awn dev malept which were prepared for the bug opened on our bugtracker ( [https://bugs.launchpad.net/awn/+bug/251596](https://bugs.launchpad.net/awn/+bug/251596) ).  It is fair to say, this is the consensus among those of us who have looked at the issue.

-----

As I understand it, the gimpshop package is for Debian, not Ubuntu.  What I would do is look for someone who is knowledgeable about building on PPAs and ask them to build a version.  Apparently someone has been attempting to build it for intrepid, not hardy.

Additionally, said PPA package should replace the gimp package(s).  Installing both gimp and gimpshop at the same time creates problems because they both install libraries with the same name, albeit in different locations.  However, when gimp is loaded, due to the way that the executable loads libraries, the gimpshop libraries are loaded for it.  This breaks gimp loading partially because the gimpshop debian package is 2.2.x and the hardy version of gimp is 2.4.x, and I assume that the gimp broke binary library compatibility between 2.2.x and 2.4.x.  So, since the gimp can't find functions/variables that were in 2.4.x but not in 2.2.x.

I think the reason that you're seeing this behavior *after* Awn is installed is because the Awn packages regenerate the library cache, whereas I doubt that the gimpshop package does this (especially when you use dpkg to install it).

I'm marking this invalid because I believe that this doesn't have anything to do with Awn, but rather, it's a problem with installing gimpshop.

---

### Post by Maverick88 on 2008-07-24
Well, Gimp, gimpshop and AWN all coexisted and worked perfectly until the latest AWN update a few days ago.  

I suspect that something in the last AWN update overwrote a shared library that broke the Gimp.

I would be very cautious with the latest version of AWN.  It may break other packages as well.

Rob

---

### Post by Maverick88 on 2008-07-24
After more testing and investigation, it looks like AWN is not to blame. It was just mere coincidence (since installing AWN via Synaptic or apt-get also did a ldconfig whivh regenerated the library cache).

I booted off the Ubuntu Hardy Heron Live CD and installed gimpshop via dpkg -i. Both gimp and gimpshop worked perfectly. If you did a "ldd `which gimp-2.4`", you would see that the gimp only loaded libraries in /lib and /usr/lib and NOT any libraries installed by Gimpshop in /usr/local/lib.

But then I did a "sudo ldconfig". Then gimp stopped working. (But gimpshop still worked). If you did a "ldd `which gimp-2.4`", you would see the gimp loading some (but not all) libraries from /usr/local/lib where gimpshop installed libraries.  

So it does look like a packaging issue. The gimpshop package should be modified to show a conflict with gimp. But since the gimpshop project appears to be dead that is not likely to happen.

---

### Post by moonbeam on 2008-07-24
> **Maverick88 said:**
> Well, Gimp, gimpshop and AWN all coexisted and worked perfectly until the latest AWN update a few days ago.  

I suspect that something in the last AWN update overwrote a shared library that broke the Gimp.

I would be very cautious with the latest version of AWN.  It may break other packages as well.

Rob

Edited out my response due to the previous post.

Added the following.

I would request that in the future that you please verify the source of issues before making such claims.  We are very pleased with our build and packaging people and they tend to be very concientious (as does reacocard who while not an official member of awn has been packaging it for a long, long time).  

Regards,

---

### Post by Perow on 2008-07-25
Hey,
Thanks for this nice thread. I installed it and played around with the settings, but I still don't get to see my open applications (Firefox, Pidgin...) on the dock. Does anybody know what causes this?
Thanks.

EDIT-
Ugh. Clearly I hadn't played around with it enough. I just had to enable the main awn applet. Stupid. :)

---

### Post by diego898 on 2008-07-25
> **Perow said:**
> Hey,
Thanks for this nice thread. I installed it and played around with the settings, but I still don't get to see my open applications (Firefox, Pidgin...) on the dock. Does anybody know what causes this?
Thanks.

EDIT-
Ugh. Clearly I hadn't played around with it enough. I just had to enable the main awn applet. Stupid. :)

I have the same problem. How did you enable the main awn applet? what is it called?

---

### Post by reacocard on 2008-07-25
> **diego898 said:**
> I have the same problem. How did you enable the main awn applet? what is it called?

Launcher/Task Manager

---

### Post by ajhtiredwolf on 2008-07-25
I am having a few problems in AWN, works fairly well so far. When a new window is opened, some of the applet icons will get a white bar over them until the animation for the new icon appearing in the awn panel is done. Then the bars disappear. Also I am still wondering, when i minimize and then re maximize a window it will disappear and then re add itself to the right most position on the awn panel. Can this be disabled?

here is my output for running it in the panel
[http://pastebin.ca/1083010](http://pastebin.ca/1083010)

---

### Post by RealG187 on 2008-07-25
I have Ubuntu 8.04 and installed AWN but there is no trash.

Where can I get the trash applet? I have been googling forever and found nothing.

---

### Post by diego898 on 2008-07-26
Does anyone have the problem where when they start their computer, the bar starts empty, centered and an applet starts all the way to the left and moves slowly till it meets with the bar. It looks like an animation. Is it normal?

---

### Post by diego898 on 2008-07-26
Also, how do I add launchers? I cant seem to find the ",exe" for firefox (I know it isnt a .exe but whats the executable? What do I add?

---

### Post by keeler1 on 2008-07-26
As far as creating the firefox launcher go to add launcher in awns menu.  Then it will ask for a name for the launcher and description (put whatever you feel like for these two).  In the third box which asks for the command type firefox.  It is not an exe, it is simply firefox.  Then click on the photo area and navigate to usr/share/pixmaps.  Find the firefox logo and click on it.  Then click ok to create the launcher and you are finished.

I have a question as well.  Is there a gkrellm applet for awn?

---

### Post by keeler1 on 2008-07-26
If awn doesnt have a gkrellm applet does it have an applet that uses the dell i8kutils to control fan speeds based on cpu temperatures?

---

### Post by diego898 on 2008-07-26
> **keeler1 said:**
> As far as creating the firefox launcher go to add launcher in awns menu.  Then it will ask for a name for the launcher and description (put whatever you feel like for these two).  In the third box which asks for the command type firefox.  It is not an exe, it is simply firefox.  Then click on the photo area and navigate to usr/share/pixmaps.  Find the firefox logo and click on it.  Then click ok to create the launcher and you are finished.

I have a question as well.  Is there a gkrellm applet for awn?

What are the "commands" for the rest of the programs I want to add? Is there some kind of convention?

---

### Post by reacocard on 2008-07-26
> **diego898 said:**
> Does anyone have the problem where when they start their computer, the bar starts empty, centered and an applet starts all the way to the left and moves slowly till it meets with the bar. It looks like an animation. Is it normal?

that's normal

> **diego898 said:**
> What are the "commands" for the rest of the programs I want to add? Is there some kind of convention?

easiest thing to do is to open /usr/share/applications and just drag them to the doc. otherwise. most applications have a path of /usr/bin/name-of-application, but there are exceptions.

---

### Post by reacocard on 2008-07-26
> **keeler1 said:**
> If awn doesnt have a gkrellm applet does it have an applet that uses the dell i8kutils to control fan speeds based on cpu temperatures?

not so far as I'm aware, sorry.

---

### Post by RealG187 on 2008-07-26
how can I make awn startup with the system? (and still need trash applet?)

---

### Post by ajhtiredwolf on 2008-07-27
> **diego898 said:**
> Does anyone have the problem where when they start their computer, the bar starts empty, centered and an applet starts all the way to the left and moves slowly till it meets with the bar. It looks like an animation. Is it normal?

I just turned the fps up and it happens fast enough that it isn't noticable anymore. The Zoom effect still looks good with fast animations.

---

### Post by sputnikkk on 2008-07-27
> **ajhtiredwolf said:**
> I just turned the fps up and it happens fast enough that it isn't noticable anymore. The Zoom effect still looks good with fast animations.

Thank you ... how do you increase the fps?

---

### Post by sn0m on 2008-07-27
Hi mate, thanks for this great application.
I had the old version and worked great. However after the last update. when I run a new application, let say bash, it dosen't jump and appear on the awn dock, and i have completely removed my bottom pannel relying in awn to keep track of them when collapsing.
Is there anyway that I could return this feature again or at least return to the old version...
Apologise if this has been answered allready.
Regards
Sokol

---

### Post by zephyrus17 on 2008-07-28
Hey, thanks very much for the wonderful guide. Everytime I install Ubuntu for a friend, this is one of the first things I install, and it's always from your guide. Major kudos to you. :D

However, there's a very annoying thing that I noticed: There's this space above the dock that doesn't allow mouse interaction. It's about the area of the dock up to the words that pop up when you highlight the launchers. It's pretty annoying, as that means that, effectively, you lose desktop workspace. Is there a way to make that area smaller?

---

### Post by reacocard on 2008-07-28
> **zephyrus17 said:**
> Hey, thanks very much for the wonderful guide. Everytime I install Ubuntu for a friend, this is one of the first things I install, and it's always from your guide. Major kudos to you. :D

However, there's a very annoying thing that I noticed: There's this space above the dock that doesn't allow mouse interaction. It's about the area of the dock up to the words that pop up when you highlight the launchers. It's pretty annoying, as that means that, effectively, you lose desktop workspace. Is there a way to make that area smaller?

this is due to the fact that AWN has to reserve that space to draw itself, there's not any way to eliminate that fact. You can set the bar to auto-hide or to keep itself below maximized windows as a sort of workaround, but the problem itself has no fix currently.

---

### Post by reacocard on 2008-07-28
> **sputnikkk said:**
> Thank you ... how do you increase the fps?

in gconf-editor, set the /apps/avant-window-navigator/app/frame_rate option. the default is 25.

---

### Post by sn0m on 2008-07-28
Mate i think there's some sort of a bug/conflict when 'Cairo Main Menu' applet is activated. I did that and active programs would not dock, appear on the AWN dock.
Purging configuration files and re-installing AWN resolved the problem. However should I activate the cairo menu, it will go funny again.
Kind regards
Sokol

---

### Post by moonbeam on 2008-07-28
> **sn0m said:**
> Mate i think there's some sort of a bug/conflict when 'Cairo Main Menu' applet is activated. I did that and active programs would not dock, appear on the AWN dock.
Purging configuration files and re-installing AWN resolved the problem. However should I activate the cairo menu, it will go funny again.
Kind regards
Sokol

Are you using metacity? 

This really is new one though there are some cairo-menu places issues under metacity.  I've spoken with a metacity dev about them and will be filing a bug.

Can you please confirm that you have the Launcher/Taskmanager applet loaded?  And if you do... try removing it and activating it again as the behaviour you described really sounds like an issue on that side of things.

---

### Post by zephyrus17 on 2008-07-28
> **reacocard said:**
> this is due to the fact that AWN has to reserve that space to draw itself, there's not any way to eliminate that fact. You can set the bar to auto-hide or to keep itself below maximized windows as a sort of workaround, but the problem itself has no fix currently.
Yeah.. I thought as much. Thanks again for the comfirmation of doom, though. :)

---

### Post by MrM002 on 2008-08-05
Hello together,

hope my english is good enough to understand what i'm talking about ;)

I've pulled the main panel (from top) to bottom, because i like it as more as on top. Now there is a problem with onTop / ofTop:

[IMG]http://c.imagehost.org/0707/awn.png[/IMG]

How can i tell the panel to stay in the back? or other way round, how can i tell the AWN to stay ontop if i click on the panel?

Greetings
MrM

---

### Post by reacocard on 2008-08-05
> **MrM002 said:**
> Hello together,

hope my english is good enough to understand what i'm talking about ;)

I've pulled the main panel (from top) to bottom, because i like it as more as on top. Now there is a problem with onTop / ofTop:

[IMG]http://c.imagehost.org/0707/awn.png[/IMG]

How can i tell the panel to stay in the back? or other way round, how can i tell the AWN to stay ontop if i click on the panel?

Greetings
MrM

this is not currently possible I'm afraid. AWN is not intended to be used on the same screen edge as a panel.

---

### Post by Clappy on 2008-08-05
Hi, thanks for making such a cool app! I have one issue, and that is it opens on the wrong display and I can't find an option to change this. 

here are some of my specs, I'm not sure what's relevant:
ubuntu version: Hardy 8.04
video card: Nvidia (installed via Edgy)
window manager: Compiz

I am using twinview, and my second display is a TV (to my left). I need it to open on my Samsung (main screen) instead of the TV. Any help is appreciated, thanks again.

---

### Post by reacocard on 2008-08-05
> **Clappy said:**
> Hi, thanks for making such a cool app! I have one issue, and that is it opens on the wrong display and I can't find an option to change this. 

here are some of my specs, I'm not sure what's relevant:
ubuntu version: Hardy 8.04
video card: Nvidia (installed via Edgy)
window manager: Compiz

I am using twinview, and my second display is a TV (to my left). I need it to open on my Samsung (main screen) instead of the TV. Any help is appreciated, thanks again.

close AWN

open gconf-editor (alt+f2, enter gconf-editor)

navigate to apps->avant-window_navigator

enable force_monitor
set monitor_height to the height of your main monitor
set monitor_width to the COMBINED width of your monitors
set monitor_xoffset to the width of your TV monitor

start AWN, it should now be it the correct position

---

### Post by Clappy on 2008-08-05
reacocard, you are a genius. I just finished doing this and was going to post the workaround in the thread but you beat me to it!

Thanks so much, have a great day!

---

### Post by Drone4four on 2008-08-16
How do I eliminate the gnome panel?

---

### Post by Maupertus on 2008-08-16
> **Drone4four said:**
> How do I eliminate the gnome panel?

Except for the top panel, you can just rightclick on it and 'delete' it.

---

### Post by thehkv on 2008-08-16
> **Maupertus said:**
> Except for the top panel, you can just rightclick on it and 'delete' it.

Or make it Autohide.

---

### Post by Macdelaney on 2008-08-19
> **russianbandit said:**
> To follow up on my post:
The launchers only launch one instance of the program. I cannot launch 2 firefox applications. Also the active tasks do show in an area separated from the launchers by a vertical bar, **however**, only the tasks that were started NOT from the launchers show up in active task list. The task that I start using the launchers do not show up anywhere.


I'm having this same problem, and been looking through many pages to see if a solution was posted but couldn't find one.
Any help would be much appreciated, and thanks for this great how to!

---

### Post by reacocard on 2008-08-19
> **Macdelaney said:**
> I'm having this same problem, and been looking through many pages to see if a solution was posted but couldn't find one.
Any help would be much appreciated, and thanks for this great how to!

When you start a task from a launcher the launcher becomes the task's icon. Middle-clicking this icon will launch another copy of the app.

---

### Post by Macdelaney on 2008-08-19
Thanks for the quick reply!

---

### Post by d0nut on 2008-08-20
How do I go about creating a Launcher?  I select "Application", then type in the name "Pidgeon".  If I want to put pidgeon on it, what do I put in for the command?  I'm new to linux still and trying to figure this all out.  Thanks.

---

### Post by reacocard on 2008-08-20
> **d0nut said:**
> How do I go about creating a Launcher?  I select "Application", then type in the name "Pidgeon".  If I want to put pidgeon on it, what do I put in for the command?  I'm new to linux still and trying to figure this all out.  Thanks.

Here's an easier way: just drag the launcher from the menu to AWN.  (Alternatively you can also drag from /usr/share/applications).

---

### Post by d0nut on 2008-08-20
That works much easier.  Thanks for the help!:)

---

### Post by d0nut on 2008-08-21
Another question.  

Is there a way to just keep it as a task launcher?  Because whenever I open a new Browser window, it gets added to the list.  Sometimes I'll have a few browsers open and it gets annoying...anyway to make it not get added to the avant?  

Also, does anyone know any links to get themes and patterns for avant?

Thanks.

---

### Post by reacocard on 2008-08-21
> **d0nut said:**
> Another question.  

Is there a way to just keep it as a task launcher?  Because whenever I open a new Browser window, it gets added to the list.  Sometimes I'll have a few browsers open and it gets annoying...anyway to make it not get added to the avant?  

That is not currently possible. A rewrite of the system that would enable this is planned, but it will likely be a long time before that comes.

---

### Post by d0nut on 2008-08-21
Ok, np.  Thanks for the reply.

---

### Post by fabounet on 2008-08-22
you can try out Cairo-Dock. you can deactivate the task-bar or group the applis in sub-docks ;-)
or even put the applis in a separate dock.

---

### Post by moore.bryan on 2008-08-23
so, uh... any word on the agnostic packages? i get a non-existent reply on installing avant-window-navigator-agnostic. 
;-)
thanks!

---

### Post by reacocard on 2008-08-24
> **moore.bryan said:**
> so, uh... any word on the agnostic packages? i get a non-existent reply on installing avant-window-navigator-agnostic. 
;-)
thanks!

they're broken and are going to stay that way, as I don't have the resources to support them in addition to the regular packages.

---

### Post by moore.bryan on 2008-08-24
that's a shame... there's lot of us out here who dislike both gnome and kde. :-(

---

### Post by acesneights08 on 2008-09-02
So, i think everything seemed to install just fine, but I try loading up the avant window manager and I don't see anything. Awn manager loads up, added a few applets tried again and still nothing. Check the system processes and is shows is running. Anyone know whats going on?

I am running a fresh installed and updated copy of 8.04

---

### Post by cptr13 on 2008-09-02
can we please get a sticky for this?

---

### Post by reacocard on 2008-09-10
I've updated the PPA with intrepid packages. I am also now dropping gutsy support, though the current packages will remain available for those who want them. I've also removed the instructions for compiling from source, as they were outdated.

---

### Post by munchy4444 on 2008-09-15
when i try to install this happens
tanner@Munchy:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr482.1~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
                        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                        Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                        Depends: libvte9 (>= 1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
                        Depends: libxcb-render-util0 but it is not installable
                        Depends: libxi6 (>= 2:1.1.3-1ubuntu1) but 2:1.1.3-1 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages
tanner@Munchy:~$ DO,IT,NOW!
bash: DO,IT,NOW!: command not found, are you retarded? Y/N

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

### Post by Maupertus on 2008-09-15
I haven't found an answer on the forums or Google, but that's partly because I don't really know how to describe it. But when I open a new window (Firefox, evolution etc) a small slab in the system colour covers the most left icon (in my case the trash applet). I've tried changing the applet, but it doesn't matter. I've tried making a screenshot, but it happens pretty fast. 

Anybody an idea why it's happening?

---

### Post by reacocard on 2008-09-15
> **munchy4444 said:**
> when i try to install this happens
tanner@Munchy:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr482.1~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
                        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                        Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                        Depends: libvte9 (>= 1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
                        Depends: libxcb-render-util0 but it is not installable
                        Depends: libxi6 (>= 2:1.1.3-1ubuntu1) but 2:1.1.3-1 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages
tanner@Munchy:~$ DO,IT,NOW!
bash: DO,IT,NOW!: command not found, are you retarded? Y/N

make sure you have ubuntu-updates enabled, as detailed in the guide. also make sure you're using the right deb lines for your version of ubuntu.

---

### Post by munchy4444 on 2008-09-15
> **reacocard said:**
> make sure you have ubuntu-updates enabled, as detailed in the guide. also make sure you're using the right deb lines for your version of ubuntu.
Yeah, I have the everything up to date. I think it might be something wrong with compiz. =\

---

### Post by ThinkMud on 2008-09-18
Thanks for the info!  This worked perfect, but since I've installed it, Blender won't work properly.  What happens is that Blender (either windowed or full screen) will open, then disappear, like maybe when the icons refresh or something, it makes Blender disappear.  I'm using the ATI graphics driver that ubuntu "warns" you about too...  this could be a compiz issue too maybe?  Any advice?

p.s. new to ubuntu, long time suse user off and on, but finally made the "windows free" jump a few days ago, so all my pc's are now ubuntu!

---

### Post by reacocard on 2008-09-18
> **ThinkMud said:**
> Thanks for the info!  This worked perfect, but since I've installed it, Blender won't work properly.  What happens is that Blender (either windowed or full screen) will open, then disappear, like maybe when the icons refresh or something, it makes Blender disappear.  I'm using the ATI graphics driver that ubuntu "warns" you about too...  this could be a compiz issue too maybe?  Any advice?

p.s. new to ubuntu, long time suse user off and on, but finally made the "windows free" jump a few days ago, so all my pc's are now ubuntu!

compiz and blender dont get along well, and won't until the GEM/DRI2 mess gets sorted out upstream. For now it's best simply to disable compiz when you want to work with blender, and turn it back on when you're done.

---

### Post by ThinkMud on 2008-09-19
> **reacocard said:**
> compiz and blender dont get along well, and won't until the GEM/DRI2 mess gets sorted out upstream. For now it's best simply to disable compiz when you want to work with blender, and turn it back on when you're done.

That totally worked!  Thanks!  I love how much help there is for Ubuntu out there.  I feel so free now with no full windows box running, except for my work pc, but can't swap that out b/c I'm a .NET developer...

---

### Post by LoSt180 on 2008-09-20
Any chance on adding a key so I can stop getting the "Unable to Verify Software" warning every time an update comes out?

---

### Post by reacocard on 2008-09-20
> **LoSt180 said:**
> Any chance on adding a key so I can stop getting the "Unable to Verify Software" warning every time an update comes out?

this is a problem in the PPA system, there's nothing I can do about it. take it up with the launchpad devs if it really bothers you.

---

### Post by davis.matthewjames on 2008-09-20
For intrepid users, the typical "gnome-session" manager method of disabling the gnome-panel doesn't work. Please try running gconf-editor and going to desktop>gnome>session>required components and deleting "gnome-panel" from the panel key.

---

### Post by rlsimpso on 2008-09-24
Thanks, this is a better solution then what I was doing.

---

### Post by davidryder on 2008-09-26
This is the most amazing thing I have found regarding eye candy. WOW!!!!!!!!!

---

### Post by ilovehinhua on 2008-09-28
Anyone out there.... My apologies if this question was raised a thousand times before...
How should I install the GNOME Main Menu into AWN 0.2.1? Main Menu referring to the applications places systemthat stuff. Thank you in advance for the step-by-step information provided.

---

### Post by davidryder on 2008-09-28
> **ilovehinhua said:**
> Anyone out there.... My apologies if this question was raised a thousand times before...
How should I install the GNOME Main Menu into AWN 0.2.1? Main Menu referring to the applications places systemthat stuff. Thank you in advance for the step-by-step information provided.

Go to System|Preferences|Awn Manager then click on the Applets theme then you will find a few Main Menu applets there. Select the one you want and click "Activate".

[img]http://www.phpstory.net/graphics/ss_Sep_28_2008_0652.png[/img]

---

### Post by ilovehinhua on 2008-09-28
well there isnt anything in my applets theme unfortunately...Where can I download the other applets? I only have "Launcher/TaskManager" in my applets theme. Thank YOu

---

### Post by davidryder on 2008-09-28
> **ilovehinhua said:**
> well there isnt anything in my applets theme unfortunately...Where can I download the other applets? I only have "Launcher/TaskManager" in my applets theme. Thank YOu

Can you paste the results of ```
ls /usr/share/avant-window-navigator/applets/
```?

That's where all the available applets should be. If they aren't there, we should try to get them there.

---

### Post by reacocard on 2008-09-29
> **ilovehinhua said:**
> well there isnt anything in my applets theme unfortunately...Where can I download the other applets? I only have "Launcher/TaskManager" in my applets theme. Thank YOu

install the awn-core-applets-bzr package.

---

### Post by Tadhg on 2008-09-29
Does anyone know how to change the folder icons used in the Stacks and Menu applets? It uses an ugly brown folder icon by default, and I'd like to be able to change it.

Also, I can't get the notification applet working. It appears, but doesn't show any running programs.

---

### Post by reacocard on 2008-09-29
> **Tadhg said:**
> Does anyone know how to change the folder icons used in the Stacks and Menu applets? It uses an ugly brown folder icon by default, and I'd like to be able to change it.

Also, I can't get the notification applet working. It appears, but doesn't show any running programs.

you need to remove any already running notification area from gnome-panel (or other panel) before you add one to AWN.

---

### Post by Zachx65 on 2008-10-01
I had installed AWN a different way before, but I couldn't find the applets. So I removed it and did it the way in the OP. Now it works great except that my tasks are on the left and launchers are on the right. The first time it was Launchers/right Tasks/left. Any way I can make it like it was before?

---

### Post by davidryder on 2008-10-01
[img]http://img371.imageshack.us/img371/2968/ssoct0120082340nw5.png[/img]

Just move the blue launcher to the opposite side.

---

### Post by vgrisham on 2008-10-03
I just upgraded to Intrepid (nice!). AWN is working great (the trash applet now works!). The shutdown command has apparently changed in 8.10 however. When I click the shutdown button on the dock, I get a screen asking if I want to Log out or Switch User, but there is no option to shutdown or restart. When I shutdown from the System menu, I get the option to shutdown or restart. 

I know I can edit the command that is issued when I click the shutdown button. My question is, what command do I need to change it to?

---

### Post by DancemasterGlenn on 2008-10-04
Oh man, trash is going to work again?? That's going to be great, I'm very excited to try Intrepid out now...

---

### Post by vgrisham on 2008-10-04
> **DancemasterGlenn said:**
> Oh man, trash is going to work again?? That's going to be great, I'm very excited to try Intrepid out now...

Yeah! I was pretty surprised by that as well. 

Now if we can just get the Quit button to offer shutdown or restart, AWN and Intrepid will be an even better match.

Here's a picture of Intrepid and AWN...

_[[IMG]http://img171.imageshack.us/img171/778/desktoplg4.th.png[/IMG]](http://img171.imageshack.us/my.php?image=desktoplg4.png)_
[IMG]http://img171.imageshack.us/my.php?image=desktoplg4.png[/IMG]

---

### Post by vgrisham on 2008-10-05
I just filed a [bug report]("https://bugs.launchpad.net/awn/+bug/278732") on the Quit-Logoff applet's inability to shut down or restart the computer.

---

### Post by Locutus_of_Borg on 2008-10-05
is it possible to get a list of the bare necessary required dependencies for avant-window-navigator on a fresh install of ubuntu 8.04?

I have an installation of said operating system that is unconnected to the internets for an assortment of reasons and am wishing to put this dock onto it.  

My current operating system has it installed already, but i compiled it from source and needed no additional packages.  Trying to reproduce such steps in Ubuntu is complaining of needs for various python headers and libraries  (why are the headers/libraries dissociated from the python package?) So I would very much like to simply download whatever dependencies are needed on this computer, then transfer them to that one afterwards.  As opposed to the lengthy process of discovering that with each potentially resolved dependency, a new one emerges.


Thanks.

---

### Post by reacocard on 2008-10-06
> **Locutus_of_Borg said:**
> is it possible to get a list of the bare necessary required dependencies for avant-window-navigator on a fresh install of ubuntu 8.04?

I have an installation of said operating system that is unconnected to the internets for an assortment of reasons and am wishing to put this dock onto it.  

My current operating system has it installed already, but i compiled it from source and needed no additional packages.  Trying to reproduce such steps in Ubuntu is complaining of needs for various python headers and libraries  (why are the headers/libraries dissociated from the python package?) So I would very much like to simply download whatever dependencies are needed on this computer, then transfer them to that one afterwards.  As opposed to the lengthy process of discovering that with each potentially resolved dependency, a new one emerges.


Thanks.

that's really a lot more difficult than it sounds at first. while I could produce a list of the top-level deps easily, some of those have sub-deps and some of those have more sub-deps.... you get the idea. Probably the simplest way would be to boot up an ubuntu livecd on a computer that has an internet connection, and follow the guide in the first post to install AWN on it via apt. after that install, all needed packages should now be in /var/cache/apt/archives so you can just copy those to a flash drive and install them by hand on the target computer. If you want to be able to compile from source on the target computer you should also do a "sudo apt-get build-dep avant-window-navigator-bzr" before you copy all the packages.

---

### Post by CAPLinux on 2008-10-06
Hey Reacocard, thanks for the great How-To.  I have AWM installed and set up my Compaq laptop to look just like a Mac.  Besides just looking cool, that "eye-candy" is truly functional and benifical from a productivity stand-point.  Thanks again.

---

### Post by Locutus_of_Borg on 2008-10-06
> **reacocard said:**
> that's really a lot more difficult than it sounds at first. while I could produce a list of the top-level deps easily, some of those have sub-deps and some of those have more sub-deps.... you get the idea. Probably the simplest way would be to boot up an ubuntu livecd on a computer that has an internet connection, and follow the guide in the first post to install AWN on it via apt. after that install, all needed packages should now be in /var/cache/apt/archives so you can just copy those to a flash drive and install them by hand on the target computer. If you want to be able to compile from source on the target computer you should also do a "sudo apt-get build-dep avant-window-navigator-bzr" before you copy all the packages.

i never even thought of that, thanks a lot

---

### Post by tclark___ on 2008-10-08
Hi
im new to this stuff
im getting an error when i type

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

its says that the packeges has some dependences not found or something like that

and says in the end that will not intall, broken packages

any one can help?

---

### Post by reacocard on 2008-10-08
> **tclark___ said:**
> Hi
im new to this stuff
im getting an error when i type

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

its says that the packeges has some dependences not found or something like that

and says in the end that will not intall, broken packages

any one can help?

As the guide says, you need to have ubuntu-updates enabled,

---

### Post by DancemasterGlenn on 2008-10-08
[http://yro.slashdot.org/yro/08/10/08/1224224.shtml](http://yro.slashdot.org/yro/08/10/08/1224224.shtml)

In short, Apple has patented the "dock". What does this mean, if anything, for awn development? Should I be worried?

... will my kids be safe?

---

### Post by tclark___ on 2008-10-08
> **reacocard said:**
> As the guide says, you need to have ubuntu-updates enabled,

i do have
i followed every single step on the intallation

---

### Post by cbrigstocke on 2008-10-08
I get the following message when trying to run awn-manager:

"Could not load the "gtk-preferences" icon.  Make sure that the SVG loader for Gtk+ is installed. It usually comes with librsvg, or a package similarly named."

I've reinstalled librsvg2-2 and using librsvg2-2bin and it still doesn't work.  Any thoughts?  I'm running Hardy btw.

Thanks.

---

### Post by DJ_Peng on 2008-10-09
I'm looking at the Stacks Applet to finally give it a try but when I don't really have a good folder to use the Folder backend. I see there's an option to use a File backend but I can't find any docs on how to set that up. Is this a flat file that I create or is there some info I'm missing?

---

### Post by reacocard on 2008-10-09
> **DancemasterGlenn said:**
> [http://yro.slashdot.org/yro/08/10/08/1224224.shtml](http://yro.slashdot.org/yro/08/10/08/1224224.shtml)

In short, Apple has patented the "dock". What does this mean, if anything, for awn development? Should I be worried?

... will my kids be safe?

the developer response can be found here: [https://answers.launchpad.net/awn/+question/47479](https://answers.launchpad.net/awn/+question/47479)

---

### Post by DancemasterGlenn on 2008-10-09
Thanks for the reply, that puts me much more at ease. I'd hate to see the project taken down over something like that...

---

### Post by boxxy27 on 2008-10-10
i got this crazy kinda like error, guessing its either on my side or you have moved the dependency or something

anyway when i try to fetch the file it says a lot of stuff then this

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr482.1~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu4 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed

any idea what it means?

---

### Post by Scott-271 on 2008-10-10
This is a great app!!! Thanks for the guide!!!

I have a few questions though. How do I increase the size of the dock icons? I can't seem to get the volume control to work, I'm missing "alsaaudio" and it doesn't seem to be in the repo. Any ideas?

Thanks again,
Scott

---

### Post by Zachx65 on 2008-10-10
I've installed AWN using this tutorial, and I was wondering if there is a way to change the icons of the launchers. It allows me to change the icons of tasks, but no go when I right click the launchers.

Also, I see in the OP the question 'Q: Can I use AWN as just a launcher, not a taskmanager?'

This is probably already known but you can do that by deactivating the Launcher/Taskmanager applet in AWN manager. When you do this AWN closes down but after you launch it again it works fine. The exception being you can't drag and drop stuff from say, GnomePanel, to the dock. You have to add new launchers through the applets window in AWN Manager.

Thanks!

---

### Post by Scott-271 on 2008-10-10
Howdy Zachx65,

I just got this setup myself also! One of the things I found is you can drag and drop from /usr/share/applications to AWN Manager->Launchers.

*'Q: Can I use AWN as just a launcher, not a taskmanager?'*

From what I read a few (dozen) pages back, no you can't use it as just a launcher at this time.

Hope that helps.

---

### Post by Zachx65 on 2008-10-10
Scratch what I said about launchers. I was mixing up launchers and applets. So I just want to know if changing applet icons is possible.

---

### Post by Scott-271 on 2008-10-10
I just darg and drop them on the dock itself, and them a pop-up asks to confirm or something like that. Just go to /usr/share/pixmaps or /usr/share/gnome to get icons.

Scott

---

### Post by reacocard on 2008-10-10
> **Scott-271 said:**
> This is a great app!!! Thanks for the guide!!!

I have a few questions though. How do I increase the size of the dock icons? I can't seem to get the volume control to work, I'm missing "alsaaudio" and it doesn't seem to be in the repo. Any ideas?

Thanks again,
Scott

the package name is python-alsaaudio iirc.

---

### Post by edboyww on 2008-10-11
I have a little problem with curved gui:
If I set bar angle to -1 in gconf-editor, the curved gui is visible for a moment, but then the bar angle (and the look of the dock) jumps back at 0, flat.

Can anyone help me? Thanks in advance!

(Ubuntu 8.04, bzr repo)

---

### Post by SomeGuyDude on 2008-10-11
Tried to install in Intrepid. Hit this:

"Depends: libgnome-desktop-2  but it is not installable"

Que?

---

### Post by reacocard on 2008-10-11
> **SomeGuyDude said:**
> Tried to install in Intrepid. Hit this:

"Depends: libgnome-desktop-2  but it is not installable"

Que?

intrepid packages need some dependency fixing, I'm working on it.

---

### Post by airtonix on 2008-10-11
/etc/apt/sources.list
```

deb http://au.archive.ubuntu.com/ubuntu/ hardy restricted main universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy restricted main universe multiverse

deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ hardy-security restricted main universe multiverse

deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates restricted main universe multiverse

# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner


## CUSTOM REPOS ##

 deb http://ppa.launchpad.net/compiz/ubuntu hardy main
 deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main

# deb http://redmoonstudios.org/~aszlig/toribash/debian/apt/ toribash main
# deb-src http://redmoonstudios.org/~aszlig/toribash/debian/apt/ toribash main

#avant-window-navigator (testing)
#deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
#deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

#avant-window-navigator (reacocard)
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

#cairo-dock
#deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

# deb http://ppa.launchpad.net/m-buck/ubuntu hardy main

# deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
# deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main

# deb http://ppa.launchpad.net/spring/ubuntu hardy main
# deb-src http://ppa.launchpad.net/spring/ubuntu hardy main

# deb http://www.getdropbox.com/static/ubuntu hardy main
# deb-src http://www.getdropbox.com/static/ubuntu hardy main

#XBox Media Centre
#deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
#deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main

#transmission
#deb http://ppa.launchpad.net/bortis/ubuntu hardy main
#deb-src http://ppa.launchpad.net/bortis/ubuntu hardy main

```

```

~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libgnome-desktop-2-7 but it is not installable
E: Broken packages

```

```

~$ sudo apt-get install libgnome-desktop-2-7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgnome-desktop-2-7 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnome-desktop-2-7 has no installation candidate

```

any ideas

---

### Post by sbjesse on 2008-10-12
> **reacocard said:**
> intrepid packages need some dependency fixing, I'm working on it.

apparently now the fixed dependency only works for intrepid, it breaks awn on hardy bitterly...
awn-bzr version:0.3.1.bzr483.1~hardy

---

### Post by reacocard on 2008-10-12
> **sbjesse said:**
> apparently now the fixed dependency only works for intrepid, it breaks awn on hardy bitterly...
awn-bzr version:0.3.1.bzr483.1~hardy

oops, it was supposed to use the new one only for intrepid, will be fixed momentarily.

UPDATE: should be fixed now

---

### Post by DJ_Peng on 2008-10-12
> **edboyww said:**
> I have a little problem with curved gui:
If I set bar angle to -1 in gconf-editor, the curved gui is visible for a moment, but then the bar angle (and the look of the dock) jumps back at 0, flat.

Can anyone help me? Thanks in advance!

(Ubuntu 8.04, bzr repo)
I just saw that the curved GUI was included in the main awn (Thanks reacocard!) but it still looks rather flat once you get past the outer edges. Is this intended? Plus my Stacks plugin is now sitting lower than the applets on either side of it. I'm attaching a screenie to show what I mean.

---

### Post by Tryfon on 2008-10-12
A little question. How can I configure the avant bar to hide and appear smoothly? (Come up smoothly not fade)

---

### Post by reacocard on 2008-10-13
> **DJ_Peng said:**
> I just saw that the curved GUI was included in the main awn (Thanks reacocard!) but it still looks rather flat once you get past the outer edges. Is this intended? Plus my Stacks plugin is now sitting lower than the applets on either side of it. I'm attaching a screenie to show what I mean.

Those are both normal for curves, it doesnt quite have all its bugs ironed out yet.

> **Tryfon said:**
> A little question. How can I configure the avant bar to hide and appear smoothly? (Come up smoothly not fade)

Check the "Auto hide bar when not in use" option in AWN Manager.

---

### Post by Tryfon on 2008-10-13
I've already checked the "Auto hide bar when not in use" option. My question is not how to make it appear and disappear, but how to make it appear and disappear **smoothly**. Like in MAC OS if you know what I mean.
And something else. I have already checked the "Alert when application window updated" option, but I want it also to appear if it is hidden and an update occurs. Is this possible?

---

### Post by DJ_Peng on 2008-10-14
[quote=reacocard;5959740]Those are both normal for curves, it doesnt quite have all its bugs ironed out yet.
Thanks. I think the Stacks needed to finish refreshing or something because the problem went away on its own.

---

### Post by Tux_Johannes on 2008-10-14
Hi, there is a bug with the Applet *AWN Main Menu* in Intrepid, I would like to write a bug report. The Applet crashes down, if I select a entry in the Menu or click back. Could you help me to write a good bug report, please?

---

### Post by reacocard on 2008-10-14
> **Tryfon said:**
> I've already checked the "Auto hide bar when not in use" option. My question is not how to make it appear and disappear, but how to make it appear and disappear **smoothly**. Like in MAC OS if you know what I mean.
And something else. I have already checked the "Alert when application window updated" option, but I want it also to appear if it is hidden and an update occurs. Is this possible?

the animation is smooth for me, so I really dont know what the issue is.

for the alerting, no that isnt possible yet.

---

### Post by reacocard on 2008-10-14
> **Tux_Johannes said:**
> Hi, there is a bug with the Applet *AWN Main Menu* in Intrepid, I would like to write a bug report. The Applet crashes down, if I select a entry in the Menu or click back. Could you help me to write a good bug report, please?

just submit one as clearly as you can to [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn), they'll ask if they need clarification. If you really want help writing the report, finding someone in #awn on freenode is probably your best chance to find someone.

---

### Post by e_labranche on 2008-10-16
Hi!

I had some bugs with awn and wanted to re-install from scratch. In doing so, I realised that even after purging all installs, when re-installing, awn kept my preferences?

I looked inside my /home/user account (hidden folders) to find out were I could just delete te related file?

does anyone know where awn stores it's user preferences and settings?

thanks

---

### Post by reacocard on 2008-10-16
> **e_labranche said:**
> Hi!

I had some bugs with awn and wanted to re-install from scratch. In doing so, I realised that even after purging all installs, when re-installing, awn kept my preferences?

I looked inside my /home/user account (hidden folders) to find out were I could just delete te related file?

does anyone know where awn stores it's user preferences and settings?

thanks

most of AWN's prefs are stored inside gconf, you can reset them by closing AWN and running
```
gconftool-2 --recursive-unset /apps/avant-window-navigator
```

---

### Post by vgrisham on 2008-10-18
> **vgrisham said:**
> I just filed a [bug report]("https://bugs.launchpad.net/awn/+bug/278732") on the Quit-Logoff applet's inability to shut down or restart the computer.

Here's how to get your quit applet working in Intrepid.

Right click the quit button and choose preferences. Replace the word --kill with --shutdown-dialog

Now you can quit in style once again. :guitar:

---

### Post by oshouip on 2008-10-19
After installing AWN, I disable the lower panel.

but AWN not Displaying my opened application.

is there is any applet to display the opened application?

---

### Post by osabr22000 on 2008-10-19
I'm trying to do this on Gutsy but keep getting the error "Broken packages".  I know that the standard response to this is that I need to have the updates set, but I do and always did.  Screenshots to prove it.  Any other ideas?  Thanks

---

### Post by deeesseee on 2008-10-19
> **oshouip said:**
> After installing AWN, I disable the lower panel.

but AWN not Displaying my opened application.

is there is any applet to display the opened application?

You want to add the "Launcher/Taskmanager" applet. The icon looks like the AWN icon (blue bar that you can only see the left end of).




> **osabr22000 said:**
> I'm trying to do this on Gutsy but keep getting the error "Broken packages".  I know that the standard response to this is that I need to have the updates set, but I do and always did.  Screenshots to prove it.  Any other ideas?  Thanks

Just so you know, from the first page:

> IMPORTANT: I support only Ubuntu Hardy (8.04) and Ubuntu Intrepid (8.10). This does not include derivative distros such as Mint. Though you are welcome to try using my packages under derivatives, I can provide no support for doing so.

Sorry I couldn't help you more.

---

### Post by osabr22000 on 2008-10-19
Not a problem, I figured it's worth a shot since Gutsy is supported in the link to the previous tutorial...

---

### Post by reacocard on 2008-10-20
> **osabr22000 said:**
> Not a problem, I figured it's worth a shot since Gutsy is supported in the link to the previous tutorial...

Gutsy used to be supported, but as the packages haven't been updated in a long time it's likely that subsequent updates to gutsy have broken the packages. There are two solutions:

1) recompile AWN for gutsy yourself (the awn wiki has a guide to compiling: [http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource))
2) upgrade to hardy or intrepid

sorry I can't be of more help, but I really dont have the resources to support more than two releases at a time.

---

### Post by deeesseee on 2008-11-02
> **vgrisham said:**
> Here's how to get your quit applet working in Intrepid.

Right click the quit button and choose preferences. Replace the word --kill with --shutdown-dialog

Now you can quit in style once again. :guitar:

I want to try your solution, but I can't bring up the preferences window for the quit button. If I right click it all it does is open the Log Out of the Session window in the background.

---

### Post by vgrisham on 2008-11-02
> **deeesseee said:**
> I want to try your solution, but I can't bring up the preferences window for the quit button. If I right click it all it does is open the Log Out of the Session window in the background.
 
That's strange. That's not what happens when I right click the quit button on the AWN Dock. I get this:
[IMG]http://i255.photobucket.com/albums/hh145/vgrisham/Screenshot.png[/IMG]

---

### Post by bigbri on 2008-11-02
More of a gnome issue, but here goes:

I recently upgraded to intrepid, but I'm having some issues disabling the gnome-panel now.  In Hardy, I used to be able to do it by opening the gnome-session-properties dialog, going to the current session tab, and killing the gnome-panel.  Then I clicked on "Save Session" and it was a done deal.  AWN was all I needed.  

After my upgrade, the "Current Sessions" tab is gone from gnome-session-properties!  I can use "killall gnome-panel" from the terminal, but first I need to change the properties on the session so that it doesn't automatically restart.  Does anyone know the command line trickery for this feat?  I've been scouring the web for hours.

---

### Post by rt2002 on 2008-11-02
Yeah, I noticed that too.  Since the upgrade, my gnome-panels have been relaunched.  All the directions here involve settings for the "current session".  Help please to find a new way.

---

### Post by deeesseee on 2008-11-02
> **bigbri said:**
> More of a gnome issue, but here goes:

I recently upgraded to intrepid, but I'm having some issues disabling the gnome-panel now.  In Hardy, I used to be able to do it by opening the gnome-session-properties dialog, going to the current session tab, and killing the gnome-panel.  Then I clicked on "Save Session" and it was a done deal.  AWN was all I needed.  

After my upgrade, the "Current Sessions" tab is gone from gnome-session-properties!  I can use "killall gnome-panel" from the terminal, but first I need to change the properties on the session so that it doesn't automatically restart.  Does anyone know the command line trickery for this feat?  I've been scouring the web for hours.

I had the same problem and used a solution from further back in the thread.

Basically:
Open gconf-editor. Navigate to desktop > gnome > session > required components. Delete the entry "gnome-panel" for the panel key. I didn't delete the whole key, just left it blank, and this worked for me. You have to restart for the change to take effect. And like with the other solution you can't you the Alt-F2 shortcut anymore, although the shortcut to open a terminal window still works fine.

---

### Post by mihir786 on 2008-11-03
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr483.2~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                        Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                        Depends: libvte9 (>= 1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
                        Depends: libxcb-render-util0 but it is not installable
                        Depends: libxi6 (>= 2:1.1.3-1ubuntu3) but 2:1.1.3-1 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages


```

i got this output can u tell me whts the pro ?

---

### Post by reacocard on 2008-11-03
> **mihir786 said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr483.2~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                        Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                        Depends: libvte9 (>= 1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
                        Depends: libxcb-render-util0 but it is not installable
                        Depends: libxi6 (>= 2:1.1.3-1ubuntu3) but 2:1.1.3-1 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages


```

i got this output can u tell me whts the pro ?

make sure you are using the right repository for your version of ubuntu, and that you have ubuntu-updates enabled.

---

### Post by mihir786 on 2008-11-03
Still i cannot get the :(

tell me wht can i do 

i update my pc linux still i ddidnt get

---

### Post by mihir786 on 2008-11-03
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr483.2~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                              Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                              Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                              Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                              Depends: libxcb-render-util0 but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
                        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
                        Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
                        Depends: libvte9 (>= 1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
                        Depends: libxcb-render-util0 but it is not installable
                        Depends: libxi6 (>= 2:1.1.3-1ubuntu3) but 2:1.1.3-1 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages

```

i think the packages r moved ???

---

### Post by reacocard on 2008-11-03
> **mihir786 said:**
> Still i cannot get the :(

tell me wht can i do 

i update my pc linux still i ddidnt get

I stand by my first post to you. If neither of those fixes your issue, then I honestly have no idea why your system is the only one broken, as were it an issue in my packages I'd have expected someone else to have confirmed your issue by now.

---

### Post by Scott-271 on 2008-11-03
First and foremost Reacocard, thanks for this!!!!!! This, and all the help you've given to everyone is great!

Moving right along............I just did a fresh install of 8.10, followed the guide 100% and have it up and running sweetly! The only issue I seem to be having, is that I lost the drag/drop functionality of 8.04. I cannot d/d from */usr/share/applications* to the launchers window of awn-manager. I didn't find anything offering a solution, and I don't know if I just need to tweak something in gconf-editor.

Is anyone else experiencing this?

Thanks again!
Scott

---

### Post by reacocard on 2008-11-03
> **Scott-271 said:**
> First and foremost Reacocard, thanks for this!!!!!! This, and all the help you've given to everyone is great!

Moving right along............I just did a fresh install of 8.10, followed the guide 100% and have it up and running sweetly! The only issue I seem to be having, is that I lost the drag/drop functionality of 8.04. I cannot d/d from */usr/share/applications* to the launchers window of awn-manager. I didn't find anything offering a solution, and I don't know if I just need to tweak something in gconf-editor.

Is anyone else experiencing this?

Thanks again!
Scott

It's working just fine for me. Can you add them via awn-manager?

---

### Post by deeesseee on 2008-11-03
Are there supposed to be less extra applets or did I do something wrong in my upgrade to Intrepid? For example I am now missing the Pandora applet.

---

### Post by Scott-271 on 2008-11-03
> **reacocard said:**
> It's working just fine for me. Can you add them via awn-manager?

Yes. I have been able to put them in with the *Add* option, under **Launchers** window, and putting in the command. When I had AWN running under 8.04, I was able to drag/drop them into the Launchers window, now I can't. It's not a big deal, just that I didn't run across anyone else having the same issue.

BTW, fresh install of 8.10, not an upgrade; otherwise everything so far is running smooth.

Scott

---

### Post by fluhartz on 2008-11-07
Hello,

I am having a heck of a time since I updated to 8.10.  I have posted this in the installation section since I have had other problems too. I have been trying to fix this for two days and can't get it right, so I thought I would try here.

Every time I reboot I have two AWN docks running at the same time. I can totally remove AWN from my PC. Then reinstall is and the same thing happens..  I try to totally remove all off the applets and launchers from the top awn and close it down.  Then when I go to the AWN manager again the launchers that are on the dock don't show in there.

I am also getting some errors during the install and I don't know what they mean.. I have added a screen shot, I hope you can see it....

Any help with this will be greatly appreciated....

Thanks,
Flu

---

### Post by dccrens on 2008-11-07
> **fluhartz said:**
> Hello,

I am having a heck of a time since I updated to 8.10.  I have posted this in the installation section since I have had other problems too. I have been trying to fix this for two days and can't get it right, so I thought I would try here.

Every time I reboot I have two AWN docks running at the same time. I can totally remove AWN from my PC. Then reinstall is and the same thing happens..  I try to totally remove all off the applets and launchers from the top awn and close it down.  Then when I go to the AWN manager again the launchers that are on the dock don't show in there.

I am also getting some errors during the install and I don't know what they mean.. I have added a screen shot, I hope you can see it....

Any help with this will be greatly appreciated....

Thanks,
Flu

Try checking System ->Preferences ->Sessions. See it You may have two entries there. See if "Avant Window Manager Bar" is listed twice.

---

### Post by fluhartz on 2008-11-07
dccrens,

that did it..... I tried everything So simple, yet so far away......
THANK YOU very much............ I am still learning every day using this OS....

Thanks Again,
Flu

---

### Post by dccrens on 2008-11-07
fluhartz,
Super! Glad I could help. Many folks have helped me.

---

### Post by jtdgrz on 2008-11-07
> **martin saint martin said:**
> i was just wondering where i might find some themes for awn?  at this point it looks like all i've got is the default theme.

Looks like there are a bunch here: [http://wiki.awn-project.org/index.php?title=Themes](http://wiki.awn-project.org/index.php?title=Themes)

---

### Post by prizrak on 2008-11-08
I got a clean install of Ibex and the "stock" AWN that comes with it. I don't seem to be able to find the "notification area" applet in any of the applet packs. Anyone know where I can get that particular applet without going to the "trunk" branch of PPA?

---

### Post by reacocard on 2008-11-08
> **prizrak said:**
> I got a clean install of Ibex and the "stock" AWN that comes with it. I don't seem to be able to find the "notification area" applet in any of the applet packs. Anyone know where I can get that particular applet without going to the "trunk" branch of PPA?

No idea. I do not use and therefore cannot support either of those forms of installing AWN. If you have the awn-applets-* packages installed (there are four of them), and its still not available then it probably just isn't available in the ubuntu version.

---

### Post by prizrak on 2008-11-08
Yeah I have all 4 packages, I really hope that this is remedied cuz its a bit annoying to say the least.

---

### Post by megadroog on 2008-11-08
Ok, so I followed the instructions 2 times and I still can't get it to work. When I click Accessories->Avant Window Navigator there's a white bar that appears where the dock is supposed to be (it's there just for a second, then disappears) :(

---

### Post by reacocard on 2008-11-09
> **megadroog said:**
> Ok, so I followed the instructions 2 times and I still can't get it to work. When I click Accessories->Avant Window Navigator there's a white bar that appears where the dock is supposed to be (it's there just for a second, then disappears) :(

Do you have compiz enabled? If that's not it, try running
```
avant-window-navigator
```
in a terminal and post the output.

---

### Post by DJ_Peng on 2008-11-09
> **prizrak said:**
> I got a clean install of Ibex and the "stock" AWN that comes with it. I don't seem to be able to find the "notification area" applet in any of the applet packs. Anyone know where I can get that particular applet without going to the "trunk" branch of PPA?
I use reacocard's PPA on launchpad and I've only had the rare glitch when things got changed. I hardily (and intrepidly ;) ) recommend using them. I also get updates pretty quickly when they get built so I'm no more than a day behind the fixes.

---

### Post by megadroog on 2008-11-09
> **reacocard said:**
> Do you have compiz enabled? If that's not it, try running
```
avant-window-navigator
```
in a terminal and post the output.


How do I enable it??? Sorry I'm new at this

pc@pc-desktop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Thanx

---

### Post by reacocard on 2008-11-09
> **megadroog said:**
> How do I enable it??? Sorry I'm new at this

pc@pc-desktop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Thanx

Yep, you're missing compiz. You can enable it by going to System->Preferences->Appearance and selecting "normal" or "extra" on the Visual Effects tab.

---

### Post by dkev on 2008-11-09
Been using Avant now for several days and it works great. I find I don't get screen glitches once I disabled backgrounds. I do have a question. Why is it that the tray sits on the task bar and not above it? If I have a few apps open, they disappear behind the Avant tray. Not a huge deal, I just moved the task bar to the top. But its there a setting I don't see that moves it up?

---

### Post by reacocard on 2008-11-09
> **dkev said:**
> Been using Avant now for several days and it works great. I find I don't get screen glitches once I disabled backgrounds. I do have a question. Why is it that the tray sits on the task bar and not above it? If I have a few apps open, they disappear behind the Avant tray. Not a huge deal, I just moved the task bar to the top. But its there a setting I don't see that moves it up?

Avant is not intended to be used on the same side of the screen as a regular panel. You can futz with the monitor settings in gconf to trick it into being higher, but its not designed to be able to do that.

---

### Post by megadroog on 2008-11-10
> **reacocard said:**
> Yep, you're missing compiz. You can enable it by going to System->Preferences->Appearance and selecting "normal" or "extra" on the Visual Effects tab.

Hmm... I can't get it to work I get "Visual effects could not be enabled" Does it work with old video cards?

Thanx

---

### Post by reacocard on 2008-11-11
> **megadroog said:**
> Hmm... I can't get it to work I get "Visual effects could not be enabled" Does it work with old video cards?

Thanx

You need proper 3d drivers for your card for it to work. Most intel, nvidia and ati cards have such drivers available. If you cannot find appropriate drivers you may need to use some other compositiong manager, such as xcompmgr, or cairo composite manager. Unfortunately I've not used either of those so I don't know how to set them up.

---

### Post by broneo on 2008-11-11
does anyone have this problem ?

[http://ubuntuforums.org/showthread.php?t=977291](http://ubuntuforums.org/showthread.php?t=977291)

---

### Post by DJ_Peng on 2008-11-11
As I responded on that topic it looks like a misbehaving applet.

---

### Post by mem on 2008-11-12
mem@laptop:/media/disk/$ sudo aptitude install avant-window-navigator-data 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  avant-window-navigator-data 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/203kB of archives. After unpacking 1311kB will be used.
Writing extended state information... Done
(Reading database ... 106699 files and directories currently installed.)
Unpacking avant-window-navigator-data (from .../avant-window-navigator-data_0.2.6-7ubuntu1_all.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/avant-window-navigator-data_0.2.6-7ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/active/spotlight1.png', which is also in package avant-window-navigator-bzr
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/avant-window-navigator-data_0.2.6-7ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



getting errors trying to install. narrowed it down to avant-window-navigator constantly failing because of this file. I've removed the file from my system and it still errors with the same problem.

not sure what else to do at this point. its a brand new install of 8.10 64bit. any help would be appreciated.

---

### Post by reacocard on 2008-11-13
> **mem said:**
> mem@laptop:/media/disk/$ sudo aptitude install avant-window-navigator-data 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  avant-window-navigator-data 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/203kB of archives. After unpacking 1311kB will be used.
Writing extended state information... Done
(Reading database ... 106699 files and directories currently installed.)
Unpacking avant-window-navigator-data (from .../avant-window-navigator-data_0.2.6-7ubuntu1_all.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/avant-window-navigator-data_0.2.6-7ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/active/spotlight1.png', which is also in package avant-window-navigator-bzr
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/avant-window-navigator-data_0.2.6-7ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



getting errors trying to install. narrowed it down to avant-window-navigator constantly failing because of this file. I've removed the file from my system and it still errors with the same problem.

not sure what else to do at this point. its a brand new install of 8.10 64bit. any help would be appreciated.

avant-window-navigator-data is not one of my packages, You'll need to remove it before you install my packages (all of which have a -bzr suffix)

---

### Post by Pinocheckio on 2008-11-13
Since I upgraded to intrepid, I get this error when starting AWN:

> avant-window-navigator: error while loading shared libraries: libgnome-desktop-2.so.2: cannot open shared object file: No such file or directory


after searching for this package it seems broken or renamed or something....

---

### Post by reacocard on 2008-11-13
> **Pinocheckio said:**
> Since I upgraded to intrepid, I get this error when starting AWN:




after searching for this package it seems broken or renamed or something....

Did you switch to the intrepid version of my repo when you upgraded? If not, edit /etc/apt/sources.list and replace all occurrences of hardy with intrepid, then check for updates.

---

### Post by eltrutgnik on 2008-11-13
can someone help me out, i keep getting this error:



Errors were encountered while processing:
 /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr489.1~intrepid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)





im running intrepid, btw.

---

### Post by mem on 2008-11-13
> **reacocard said:**
> avant-window-navigator-data is not one of my packages, You'll need to remove it before you install my packages (all of which have a -bzr suffix)

just following the guide to the T:
```
mem@laptop:~$ sudo aptitude search avant*
p   avant-window-navigator                                                         - A MacOS X like panel for GNOME                                                           
p   avant-window-navigator-bzr                                                     - Avant Window Navigator                                                                   
p   avant-window-navigator-data                                                    - Common files for avant-window-navigator                                                  
p   xavante                                                                        - Lua HTTP 1.1 Web server                                                                  
p   xavante-doc                                                                    - Documentation files for the Xavante web server                                           
mem@laptop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages were automatically installed and are no longer required:
  avant-window-navigator-data[/B]
Use 'apt-get autoremove' to remove them.
[B]The following extra packages will be installed:
  avant-window-navigator-data[/B] libawn0-bzr python-awn-bzr
Recommended packages:
  awn-manager
**The following NEW packages will be installed:**
  avant-window-navigator-bzr **avant-window-navigator-data** awn-core-applets-bzr awn-manager-bzr libawn0-bzr python-awn-bzr
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 4689kB of archives.
After this operation, 20.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

I'm all ears... it would see that somewhere -data is listed as a dependency because i sure as hell didn't tell the thing to install on its own. somethings screwy and its not my fault. after the initial install failed i removed the package. as you can see its no longer listed as installed (see first search in dump).

:lolflag:

---

### Post by gilir on 2008-11-13
reacocard : you should add a Replaces/Conflicts on avant-window-navigator-data for avant-window-navigator-bzr, there is more and more bugs on launchpad about this problem.

---

### Post by reacocard on 2008-11-14
> **gilir said:**
> reacocard : you should add a Replaces/Conflicts on avant-window-navigator-data for avant-window-navigator-bzr, there is more and more bugs on launchpad about this problem.

done. you'd think apt would be able to handle this sort of thing without my having to edit stuff whenever upstream makes changes. *grumble grumble*

note: for bugs on my packages just subscribe me or assign them to me or something, otherwise I have no idea they've been reported until someone tells me in this thread.

EDIT: also added a note to the guide that users should remove prior installations before they begin.

---

### Post by Irwin J. Finster on 2008-11-14
Hi,

since switching to Ibex, and installing AWN again, I get a strange white fragment behind the awn bar when opening and closing windows. Any idea anyone what could caus this, and how to get rid of it?

I attached a screenshot so one can see what I mean.

Thanks for any help!

P.S. it isn't specifc to the desktop switcher, it also happens when it is disabled.

---

### Post by reacocard on 2008-11-14
> **Irwin J. Finster said:**
> Hi,

since switching to Ibex, and installing AWN again, I get a strange white fragment behind the awn bar when opening and closing windows. Any idea anyone what could caus this, and how to get rid of it?

I attached a screenshot so one can see what I mean.

Thanks for any help!

P.S. it isn't specifc to the desktop switcher, it also happens when it is disabled.

I've had that occasionally too, but never more than 1-2 times a week and only for a second or two. No idea what's causing it, I assume some difference in the graphics drivers. Are you also on an intel graphics chip?

---

### Post by vgrisham on 2008-11-14
> **reacocard said:**
> I've had that occasionally too, but never more than 1-2 times a week and only for a second or two. No idea what's causing it, I assume some difference in the graphics drivers. Are you also on an intel graphics chip?

After upgrading to Intrepid 64-bit, I'm getting the white lines too. They disappear when I mouse over them. My video card is an Nvidia geforce 7600 gs. I'm seeing the white lines multiple times per day on this PC.

I'm also running 32-bit Intrepid on my laptop which has an Intel video card and I haven't encountered any problems.

---

### Post by keeler1 on 2008-11-15
The white bar happens behind mine to but is specific to the shiny application switcher.

It does not happen on my laptop with an ati x1400 but it does on my desktop with my nvidia 7600gt

---

### Post by Irwin J. Finster on 2008-11-15
No I have an Nvidia 6800 GT and I also run ibex 64.

---

### Post by keeler1 on 2008-11-15
It seems like its an issue with the nvidia driver, if only those of us who have nvidia graphics cards are affected.

---

### Post by reacocard on 2008-11-15
> **keeler1 said:**
> It seems like its an issue with the nvidia driver, if only those of us who have nvidia graphics cards are affected.

note my post, I have on intel just considerably less so. It happened just earlier today on the weather applet.

---

### Post by PRGUY85 on 2008-11-16
Hey:

I've followed instructions and got the following:

Could not load the "gtk-preferences" icon.  Make sure that the SVG loader for Gtk+ is installed. It usually comes with librsvg, or a package similarly named.

I've installed librsvg2-common, librsvg2, librsvg2-dev and everything else related.  The only way to open AWN-manager is through terminal with Sudo but the stuff I do are not reflected on the dock.

---

### Post by Mr.Pants on 2008-11-20
in hardy xubuntu i was fine till today, fired up the laptop and now the applets all have reflections.  everything is doubled. i wasn't able to find anything in the settings managr about it so im stuck. the only open ap is firefox.  Im a NEWB so take it easy on me.

---

### Post by Mr.Pants on 2008-11-20
Wierd, just did a re-start and now it cool...

---

### Post by fluhartz on 2008-11-20
Mr Pants,

I had this same problem.  If it happens again, go to System/Preferences/Sessions and see if AWN is in there twice.

When I had this problem this is what Dccrens told me to do and it was the problem, there was two of them.  He actually helped me earlier in this thread.....

Have a good day,
Flu

---

### Post by Mr.Pants on 2008-11-21
> **fluhartz said:**
> Mr Pants,

I had this same problem.  If it happens again, go to System/Preferences/Sessions and see if AWN is in there twice.

When I had this problem this is what Dccrens told me to do and it was the problem, there was two of them.  He actually helped me earlier in this thread.....

Have a good day,
Flu

thanks Flu I'll check it out

---

### Post by fluhartz on 2008-11-21
Your welcome.... This forum is great.....
I am still somewhat new to Linux myself,but if i can help I am happy to....

You can almost always get the help you need on this forum..........

Have a good day....
Flu

---

### Post by vgrisham on 2008-11-22
> **reacocard said:**
> note my post, I have on intel just considerably less so. It happened just earlier today on the weather applet.

Should I file a bug report on the white lines thing? It doesn't seem to be resolving itself.

---

### Post by reacocard on 2008-11-22
> **vgrisham said:**
> Should I file a bug report on the white lines thing? It doesn't seem to be resolving itself.

Might as well, it can't hurt at any rate.

Also I figured out that mine happens only when the weather applet is busy trying to update itself, so my issue might be unrelated. :(

---

### Post by lime4x4 on 2008-11-22
is it possible to move the min,max and close buttons to the right side of the title bar?

---

### Post by reacocard on 2008-11-23
> **lime4x4 said:**
> is it possible to move the min,max and close buttons to the right side of the title bar?

That is not a question relevant to AWN and thus has no place in this thread. Please make your own thread for this issue.

---

### Post by lime4x4 on 2008-11-23
sorry i was veiwing 2 threads and posted to the wrong one

---

### Post by trendyabinash on 2008-11-23
There is a problem with my AWN.

It shows some white patches at regular intervals, and get fixed once I move my mouse over the AWN again. I think It is not getting automatically refreshed

I am giving a screenshot of my problem here so that you can understand
I am using ubuntu 8.10

---

### Post by Changturkey on 2008-11-23
Why does Compiz/AWN not work well with playing 3D games? Ex. I had AWN running, then I launched Tremulous, and X crashed.

---

### Post by reacocard on 2008-11-24
> **Changturkey said:**
> Why does Compiz/AWN not work well with playing 3D games? Ex. I had AWN running, then I launched Tremulous, and X crashed.

That's a compiz bug. I won't go into detail as there are countless other sources of information for it (use google!), but you should always turn off compiz before you start a 3d application to avoid this sort of conflict. (note that nvidia users do not have this bug and can safely run 3d under compiz.) This bug is slated to be fixed in the near future, hopefully in time for Jaunty.

---

### Post by trendyabinash on 2008-11-24
Sir tell me about the white patches, what should I do to remove them????

---

### Post by reacocard on 2008-11-24
> **trendyabinash said:**
> Sir tell me about the white patches, what should I do to remove them????

If you have an nvidia card, it's suspected to be a bug in the nvidia drivers. No known fix at this point. (See the last couple pages in this thread for a discussion of it.) If you do not have an nvidia card, then this is a bug I am not familiar with and you should file a bug against AWN on launchpad.

---

### Post by Tryfon on 2008-11-24
The AWN works almost perfectly for me, but this "almost" is pretty big. Here are the most important issues I am facing and if you could give me a solution to at least on of them (especially the first two ones really irritate me) I would be grateful:

- All the workspace switcher applets I have tried are presenting serious graphical issues. Fragments of previous windows, or just stupid white (or other colors) stripes remain attached to them for no obvious reason and remain there no matter what I do. It really ruins the image of the whole bar. All the rest applets don't have any similar graphical problems.

-aMSN starts on system startup on the AWN instead of the upper Notification Area (system tray) as it should.

-Open windows change places on the AWN when I am maximizing or minimizing them.

---

### Post by vgrisham on 2008-11-24
I went to file a bug report on the nvidia/awn conflict and a bug report already exists [here]("https://bugs.launchpad.net/awn/+bug/273326").

A workaround is to move the applets to the left side of the dock and the launcher bar to the right. I haven't tried it yet, but I will this evening.

EDIT: Apparently the workaround is very temporary and the "artifacts" begin showing up again at some point down the road. The bug report then degenerates into an argument as to whose problem this is (AWN's or nvidia's).

---

### Post by Changturkey on 2008-11-24
> **reacocard said:**
> That's a compiz bug. I won't go into detail as there are countless other sources of information for it (use google!), but you should always turn off compiz before you start a 3d application to avoid this sort of conflict. (note that nvidia users do not have this bug and can safely run 3d under compiz.) This bug is slated to be fixed in the near future, hopefully in time for Jaunty.

For Intel GFX?

---

### Post by trendyabinash on 2008-11-25
This is the output when I am trying to install AWN extras

What is the solution to this? Which packages I am missing.

```
trendyabinash@abinash-desktop:~$ su
Password: 
root@abinash-desktop:/home/trendyabinash# cd awn
root@abinash-desktop:/home/trendyabinash/awn# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for python... /usr/bin/python
checking for a version of Python >= 2.1.0... yes
checking for the distutils Python package... yes
checking for Python include path... -I/usr/include/python2.5
checking for Python library path... -L/usr/lib/python2.5 -lpython2.5
checking for Python site-packages path... ${exec_prefix}/lib/python2.5/site-packages
checking python extra libraries...  -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions
checking consistency of all components of python development environment... no
configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================
           
root@abinash-desktop:/home/trendyabinash/awn# make
make: *** No targets specified and no makefile found.  Stop.
root@abinash-desktop:/home/trendyabinash/awn# 

```

---

### Post by reacocard on 2008-11-25
> **Changturkey said:**
> For Intel GFX?

All Intel cards and also ATI cards that run on the open-source drivers, if I recall correctly.

---

### Post by reacocard on 2008-11-25
> **trendyabinash said:**
> This is the output when I am trying to install AWN extras

What is the solution to this? Which packages I am missing.

<snip>

Looks like you're missing python-dev.

---

### Post by trendyabinash on 2008-11-25
> **reacocard said:**
> Looks like you're missing python-dev.
now it is saying
```
No package 'pycairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYCAIRO_CFLAGS
and PYCAIRO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by vgrisham on 2008-11-25
I just updated my the driver for my nvidia geforce 7600gs to version 180.06 (beta) and I can report that the problems I had with AWN artifacts are gone. My windows are drawing correctly now as well. 

The driver was very easy to install. Just download the driver from [here]("http://www.nvidia.com/Download/Find.aspx?lang=en-us")__ and logout. Ctrl-Alt-F4 into your tty terminal and shut down the x server (code: sudo /etc/init.d/gdm stop). Then navigate to the directory where you saved the driver and code "sudo sh (name of file).run" I answered yes to every question and didn't run into any difficulties.

---

### Post by moore.bryan on 2008-11-25
no matter what i do, i can't seem to get rid of a white vertical line coming through the middle of awn; any ideas?

EDIT:
nevermind... i was silly and didn't look around the forums enough; found a post detailing it was an applet not loading.

---

### Post by reacocard on 2008-11-25
> **trendyabinash said:**
> now it is saying
```
No package 'pycairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYCAIRO_CFLAGS
and PYCAIRO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

python-cairo-dev. Note that the AWN wiki has a full list of the needed packages here: [http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix](http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix)

---

### Post by vgrisham on 2008-11-26
Is the line always in the same spot? If so you may have a broken applet. Take note of where the line is and then fire up the AWN manager (key Alt-F2 and type awn-manager). Click the Applets icon and try removing the applet that seems to be causing the problem. Close the dock and reopen it and see if the line persists. 

If the line is jumping around and you have an NVIDIA graphics card, you'll need to install the beta driver (180.06) from nvidia's site to correct the problem. See [this]("http://ubuntuforums.org/showthread.php?t=980081") thread for more info or post #503 above.

---

### Post by moore.bryan on 2008-11-26
yeah, already fixed this one... it was an applet not loading, not nvidia.

---

### Post by arniepoo on 2008-11-27
Hi,

Does anyone know how to run AWN without the AWN Taskmanager applet being visible. If I remove it the whole dock disappears. I still want the tasks visible but not the extra icon.

Any ideas?

Arnie

---

### Post by trendyabinash on 2008-11-29
The white patches problem has been resolved with the new nvidia drivers.

Man I love LINUX and over that UBUNTU is the BEST

---

### Post by karankrn on 2008-11-30
Help i cant install AWN

wheni give the command sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

it says
E: Couldn't find package avant-window-navigator-bzr

what am i doing wrong?

---

### Post by reacocard on 2008-11-30
> **karankrn said:**
> Help i cant install AWN

wheni give the command sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

it says
E: Couldn't find package avant-window-navigator-bzr

what am i doing wrong?

You must have missed one of the first two commands. Try doing
```
sudo apt-get update
```
and then reissuing the install command. If that doesn't resolve it, start over from the beginning of the guide. If you still can't get it to work, post the full output of each command you ran and the contents of the file /etc/apt/sources.list.

---

### Post by karankrn on 2008-11-30
thanks but that got solved

i had not successfully put in the repositories

once i did that i successfully installed and launched AWN

but now, i cannot update the system. it keeps showing this long error

> Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Translation-en_IN    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Translation-en_IN   
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN 
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release                              
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Packages                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages          
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Packages                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources           
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Sources                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Packages 
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Sources  
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


now what have i done wrong?

---

### Post by reacocard on 2008-12-01
> **karankrn said:**
> thanks but that got solved

i had not successfully put in the repositories

once i did that i successfully installed and launched AWN

but now, i cannot update the system. it keeps showing this long error



now what have i done wrong?

not sure what you did, but try using Software Sources (in the System->Administration menu) to choose a different mirror; that might resolve it.

---

### Post by deGz0rx on 2008-12-01
hey guys, i got a tiny problem thats kinda annoying
i can keep my eyes closed, but apparently not for long enough :)
so, theres a small gray space between the weather and the trash can applet
when i move my cursor above the trash can it disappears, and returns when a new process gets opened (in which case the trash can moves right and creates that "gray gap")
any advices on solving this issue?

thanks

[ATTACH]94894[/ATTACH]

---

### Post by trendyabinash on 2008-12-02
> **deGz0rx said:**
> hey guys, i got a tiny problem thats kinda annoying
i can keep my eyes closed, but apparently not for long enough :)
so, theres a small gray space between the weather and the trash can applet
when i move my cursor above the trash can it disappears, and returns when a new process gets opened (in which case the trash can moves right and creates that "gray gap")
any advices on solving this issue?

thanks

[ATTACH]94894[/ATTACH]
Hey I think u need to update your graphics card driver.

I was having the same issue but it got solved as soon I downloaded the 180.0 version of NVIDIA card.

Try it out.

---

### Post by deGz0rx on 2008-12-02
hey, thanks buddy
i did the update about 20 minutes ago, and havent seen a single "gap" so far
its working like a charm!
180.0 for the win! :mad:

---

### Post by jdorenbush on 2008-12-02
I got it installed, but it's so buggy I can't even use it. The dock keeps disappearing and closing and doing weird stuff.

Bummer. I thought this would be neat to have.

---

### Post by deGz0rx on 2008-12-03
thats strange, i installed mine a few days ago and its working awesome
now with the latest nvidia drivers, its working perfect

---

### Post by lime4x4 on 2008-12-04
is it possible to have avant-window-navigator appear on all lcd panels?
I run 5 lcd panels each as a seperate x-screen. Currently it only appears on my main lcd panel display 0

---

### Post by TheHybrid520 on 2008-12-04
I like to have custom icons for my dock but every time I shut down my computer and turn it back on the icons go back to it it's default set. How do I solve this issue?

---

### Post by jdorenbush on 2008-12-04
I am trying to remove Avant from my computer, but it doesn't recognize it as being installed in both Add/Remove and also Synaptic. What do I do?

---

### Post by reacocard on 2008-12-04
> **jdorenbush said:**
> I am trying to remove Avant from my computer, but it doesn't recognize it as being installed in both Add/Remove and also Synaptic. What do I do?

read the guide's uninstalling section.

---

### Post by jdorenbush on 2008-12-04
> **reacocard said:**
> read the guide's uninstalling section.

You = Win
Me = Fail

Lol.

I'll watch Avant and wait for a more stable release to show up. Cool software, it just isn't playing nicely with me.

---

### Post by KEE on 2008-12-06
Thanks

---

### Post by vgrisham on 2008-12-15
After this morning's update of the awn applets (from the reacocard ppa repo) the Cairo Clock applet is not loading. Any ideas?

EDIT: This is a bug and a fix is in the works.

---

### Post by vgrisham on 2008-12-18
I just realized that the tsclient applet is gone from AWN. I tried reinstalling the awn extras library, but no joy. Does anyone know what happened to the tsclient applet? Is anyone else experiencing this?

EDIT: I guess [this]("https://blueprints.launchpad.net/awn-extras/+spec/remove-tsclient-applet") explains it. Bummer.

---

### Post by Fiste788 on 2008-12-21
is there a awn plugin for banshee-1??
now the plugin is up to date and work with older version of banshee:(

---

### Post by F411en on 2008-12-22
Thanks ! Guide was very useful !

---

### Post by reahjw6 on 2009-01-01
THis guide has really helped thankyou.

---

### Post by pappfer on 2009-01-14
Hi!

My only problem with AWN was that when I had Firefox open and wanted to click on a link which was in the very bottom of the page, I couldn't cause AWN was covering it.

So I set AWN to autohide when not used, but then I missed it, I like to see AWN all the time and there are only a few sites which has links in the very bottom.

So I'm wondering if there's an applet or some key combination or something with which I could hide AWN with just a click and then make it come back again simply.

---

### Post by Usufruct on 2009-01-14
I'd like to upgrade from AWN 0.2.6.

I have [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main and src in my software sources, but it still won't update, nor does it show up in synaptic.

Any ideas?

---

### Post by lime4x4 on 2009-01-15
is it possible to have open on multi panels? Currently running 4 lcd panels each as a seperate xscreen. I would like to have awn running on all 4 screens?

---

### Post by Symbolis on 2009-01-16
> **pappfer said:**
> Hi!

My only problem with AWN was that when I had Firefox open and wanted to click on a link which was in the very bottom of the page, I couldn't cause AWN was covering it.

So I set AWN to autohide when not used, but then I missed it, I like to see AWN all the time and there are only a few sites which has links in the very bottom.

So I'm wondering if there's an applet or some key combination or something with which I could hide AWN with just a click and then make it come back again simply.

I use the 'Maximized windows don't cover the bar' setting, myself.(It's under the General preference). Needs a restart of AWN, but works well for me.

---

### Post by pappfer on 2009-01-16
> **Symbolis said:**
> I use the 'Maximized windows don't cover the bar' setting, myself.(It's under the General preference). Needs a restart of AWN, but works well for me.
Well, I'd prefer a "hide dock for 5 seconds" applet, but this is a solution as well.
Thanks for the idea! ;)

---

### Post by pappfer on 2009-01-17
> **pappfer said:**
> Well, I'd prefer a "hide dock for 5 seconds" applet, but this is a solution as well.
Thanks for the idea! ;)
"Keep below maximized windows when not in use" option seems to do exactly what I needed: it only hides the dock when a window (like Firefox) is maximized. Great! :)

---

### Post by lime4x4 on 2009-01-17
when i use the command below to auto start awn on a second monitor it never appears but yet i can go to that screen and manually start it

DISPLAY=:0.1 avant-window-navigator

---

### Post by Maupertus on 2009-01-25
Annoyingly, I've stopped using AWN after I upgraded to Intrepid as it gave me a couple of ugly glitches and as it is eyecandy, I didn't want to be annoyed by such a thing ;)

However, I noticed that the new install from the ppa didn't give these glitches, and re-installed as it still remains one of my favorite desktop apps.

Only now: I get strange borders between icons! 

Compiz is enabled, although I have a HDRadeon2600XP which may be at issue. But is this really a bug, or can I do something about it?

Screenshot attached.

---

### Post by deeesseee on 2009-01-25
The white lines are applets that didn't load. You can look at the order of your applets to figure out what they should be, or run AWN in terminal and post the errors you get.

---

### Post by Maupertus on 2009-01-26
> **deeesseee said:**
> The white lines are applets that didn't load. You can look at the order of your applets to figure out what they should be, or run AWN in terminal and post the errors you get.

Thanks, you've got it in one. I have no idea what the applets where, they called themselves "Awn applets" which didn't really give anything away.

You are hereby thanked.

---

### Post by deeesseee on 2009-01-28
If I remember correctly the same thing happened to me when I upgraded. I would guess it is because they got removed from the repository so AWN can't use them anymore because their files were lost. I'm not a dev or repo manager though so I'm not positive.

---

### Post by tstack77 on 2009-01-28
> **deeesseee said:**
> The white lines are applets that didn't load. You can look at the order of your applets to figure out what they should be, or run AWN in terminal and post the errors you get.

My problem is the same but it's not from applets that didn't load. I get these lines ALL the time whenever a new window opens (the dock expands/moves). 

If I run my mouse over them they immediately disappear and everything looks great...very annoying

[IMG]http://img136.imageshack.us/img136/6858/screenshotkw6.png[/IMG]

[IMG]http://img136.imageshack.us/img136/7324/screenshot1vx7.png[/IMG]

---

### Post by vgrisham on 2009-02-04
> **tstack77 said:**
> My problem is the same but it's not from applets that didn't load. I get these lines ALL the time whenever a new window opens (the dock expands/moves). 

If I run my mouse over them they immediately disappear and everything looks great...very annoying

[IMG]http://img136.imageshack.us/img136/6858/screenshotkw6.png[/IMG]

[IMG]http://img136.imageshack.us/img136/7324/screenshot1vx7.png[/IMG]

If you have an NVIDIA graphics card, the issue is with the driver. Please search this thread for 'NVIDIA' for an earlier workaround.

---

### Post by RealG187 on 2009-02-05
I have Ubuntu 8.10 and there finally is a trash icon (in 8.04 there wasn't). Is there a way I can make it so I can unmount removable media or eject CDs by dragging them onto the trash?

---

### Post by fabounet on 2009-02-06
only Cairo-Dock can do that I think ;-)

---

### Post by VeeDubb on 2009-02-06
fabounet, you are my hero again.  I always wished I could do that, and even though I've been using cairo dock for a while now, I never realized it's trash applet would do that.

Excellent.

---

### Post by RealG187 on 2009-02-06
> **fabounet said:**
> only Cairo-Dock can do that I think ;-)

There is no applet like that for AWN? I will try Cairo when I get time...

---

### Post by VeeDubb on 2009-02-06
> **RealG187 said:**
> There is no applet like that for AWN? I will try Cairo when I get time...

Cairo will also let you separate just about any plugin from the dock and use it as a desklet, AND let you have multiple instances of the same outlet, with one on the doc, and one on the desktop.  I use the clock this way.

---

### Post by xbanex on 2009-02-11
Hello i installed awn and tryed to start it and i get this error and not 100% sure to what to do next the error is (Error:Screen isn't composited. Please run compiz (-fusion) or another compositing manger)

Anyone know what it means and how to fix it?

---

### Post by lime4x4 on 2009-02-11
awn needs compiz to work i beleive.Check system-preferences-appearance-visual effects and c if normal or extra is checked

---

### Post by xbanex on 2009-02-11
> **lime4x4 said:**
> awn needs compiz to work i beleive.Check system-preferences-appearance-visual effects and c if normal or extra is checked

yeah i did and none is checked

---

### Post by vgrisham on 2009-02-11
> **xbanex said:**
> Hello i installed awn and tryed to start it and i get this error and not 100% sure to what to do next the error is (Error:Screen isn't composited. Please run compiz (-fusion) or another compositing manger)

Anyone know what it means and how to fix it?

Have you enabled desktop effects? Go to System>Preferences>Appearance. Click the Visual Effects tab and make sure that it's set to Normal or Extra. Allow it to install any video drivers needed and you should be good to go.

---

### Post by xbanex on 2009-02-11
> **vgrisham said:**
> Have you enabled desktop effects? Go to System>Preferences>Appearance. Click the Visual Effects tab and make sure that it's set to Normal or Extra. Allow it to install any video drivers needed and you should be good to go.

Yeah when i try to click on it it say Desktop effect could not be enable

---

### Post by vgrisham on 2009-02-11
> **xbanex said:**
> Yeah when i try to click on it it say Desktop effect could not be enable
 
You'll need to resolve that before you can get AWN running then. If I were you, I'd find out what kind of video card you have and search these forums for how to get that card to be able to composite (if possible).

---

### Post by xbanex on 2009-02-11
> **vgrisham said:**
> You'll need to resolve that before you can get AWN running then. If I were you, I'd find out what kind of video card you have and search these forums for how to get that card to be able to composite (if possible).

Yeah i got something kinda old its an nvida fx 5600

---

### Post by DJ_Peng on 2009-02-12
> **lime4x4 said:**
> awn needs compiz to work i beleive.Check system-preferences-appearance-visual effects and c if normal or extra is checked
I've had AWN working with only [Xcompmgr]("http://packages.ubuntu.com/intrepid/xcompmgr") while I was waiting for Nvidia to update their drivers for 8.10. You can also add [Gcompmgr]("http://sourceforge.net/projects/gcompmgr/"), which adds a GUI control window to Xcompmgr to make it a little easier to configure. It's not as pretty as Compiz Fusion but it will let you run AWN until you get Compiz's issues resolved.

---

### Post by xbanex on 2009-02-12
> **DJ_Peng said:**
> I've had AWN working with only [Xcompmgr]("http://packages.ubuntu.com/intrepid/xcompmgr") while I was waiting for Nvidia to update their drivers for 8.10. You can also add [Gcompmgr]("http://sourceforge.net/projects/gcompmgr/"), which adds a GUI control window to Xcompmgr to make it a little easier to configure. It's not as pretty as Compiz Fusion but it will let you run AWN until you get Compiz's issues resolved.

yeah i tryed what you said and it wont install the Xcompmgr

---

### Post by DJ_Peng on 2009-02-13
That's odd. I didn't have a problem installing xcompmgr. Not sure what could be the problem.

---

### Post by xbanex on 2009-02-13
> **DJ_Peng said:**
> That's odd. I didn't have a problem installing xcompmgr. Not sure what could be the problem.

Nevermind i had a bad driver for my graphic card everything is work 100% now.Thanks for trying to help.

---

### Post by DJ_Peng on 2009-02-13
No problem. I had that type of thing before, which is why I made a point of getting a new(-ish) video card for Chrismukkuh. Glad you were able to get it working.

---

### Post by blackrockzig on 2009-02-18
I am trying to make the curve look, but it won't let me set the bar at -1. When I type -1 it goes to 0.

---

### Post by AlejandroDelLoco on 2009-02-23
> **blackrockzig said:**
> I am trying to make the curve look, but it won't let me set the bar at -1. When I type -1 it goes to 0.

I am having the exact same problem!

---

### Post by hollyjester on 2009-02-24
How can I use the AWN on the right side of my screen.

---

### Post by deeesseee on 2009-02-25
Not possible at this time. Sorry.

---

### Post by barkhat on 2009-03-03
I am trying the jaunty jackalope vers of Xubuntu and I would like to install the AWN. When I follow the guide here (I am a novice), I get:

emichelle@Xubuntu:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr489.3~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Recommends: python-awn-bzr but it is not going to be installed
                        Recommends: vala-awn-bzr but it is not going to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages


I don't know how to fix this. Can someone advise me, please?

Thank you.

---

### Post by vgrisham on 2009-03-05
I recently installed an application and added a launcher for it in AWN (the app was virtualbox-ose fwiw). I then decided to remove the application and install a new one (the proprietary virtualbox fwiw). I tried to add a new launcher to the new app, but it won't take--once I enter all of the info, it won't accept OK and I have to cancel. In the launcher creation area, there are two dead launchers show (gears), but I can't remove them. When I open them their contents are empty. If I add info, AWN won't let me save the changes. 

How can I fix this?

---

### Post by francisco204 on 2009-03-08
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
-fusion

i got this error if you can tell me what is it :):popcorn::D

---

### Post by chezzo on 2009-03-08
> **francisco204 said:**
> Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
-fusion

i got this error if you can tell me what is it :):popcorn::D

it means exactly what it says - you need to be running a compositing manager such as compiz-fusion. go back and actually read the first post in this thread.

---

### Post by lime4x4 on 2009-03-22
will u be adding a jaunty repo as well?

---

### Post by BatPenguin on 2009-03-22
Are there any debs of the latest 0.3.2 version of Awn? I noticed it was relased about a month or two ago, but the repo mentioned here only has 0.3.1. I'm a pretty happy user of AWN but bug fixes would sound great to me =). Thanks.

---

### Post by DancemasterGlenn on 2009-03-29
Looks like reacocard has discontinued this ppa (check out the edited first post). Thanks for all your work reacocard, we'll miss you!

I switched over to the awn testing team ppa to get a newer version, you guys can find it here:

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

SO, what happens to this forum now? Are any of the awn devs (moonbeam, perhaps) keeping an eye on this forum? Should we post bugs and other stuff somewhere else?

---

### Post by reacocard on 2009-03-29
> **DancemasterGlenn said:**
> Looks like reacocard has discontinued this ppa (check out the edited first post). Thanks for all your work reacocard, we'll miss you!

I switched over to the awn testing team ppa to get a newer version, you guys can find it here:

[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

SO, what happens to this forum now? Are any of the awn devs (moonbeam, perhaps) keeping an eye on this forum? Should we post bugs and other stuff somewhere else?

I would say to use the [AWN forum](http://www.planetblur.org/hosted/awnforum/index.php) and [launchpad](https://bugs.launchpad.net/awn) instead.

---

### Post by moonbeam on 2009-04-01
> **reacocard said:**
> I would say to use the [AWN forum](http://www.planetblur.org/hosted/awnforum/index.php) and [launchpad](https://bugs.launchpad.net/awn) instead.

And if you know it's an applet bug [awn-extras](https://bugs.launchpad.net/awn-extras)

---

### Post by connorh123 on 2009-04-13
I did all of this, and the program is in applications/accessories. When I try to run a black screen pops up, then goes away. Making it so I can't run it.

---

### Post by kiprit on 2009-04-25
I am using simple launcher from the extras. When i set the launcher icon to something that does not appear under "stock/in theme" option, the icon does not change at all. 

A similar thing goes with the stdanard launch/taskmanager applet: when i use a different icon,the original launcher it is ok... it shows my chice. But further instances of the same application come with the default theme icon.

Can anyone suggest a way to solve this problem?

---

### Post by lavs on 2009-04-29
> **barkhat said:**
> I am trying the jaunty jackalope vers of Xubuntu and I would like to install the AWN. When I follow the guide here (I am a novice), I get:

emichelle@Xubuntu:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr489.3~intrepid) but it is not going to be installed
                              Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libgnome-desktop-2-7 (>= 1:2.23.90) but it is not installable
                        Recommends: python-awn-bzr but it is not going to be installed
                        Recommends: vala-awn-bzr but it is not going to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages


I don't know how to fix this. Can someone advise me, please?

Thank you.

same problem for me too ..... since i updated to jautny this happened.... cant get a way through .... help plzzzzzzzzzz

---

### Post by kiprit on 2009-04-29
> **lavs said:**
> same problem for me too ..... since i updated to jautny this happened.... cant get a way through .... help plzzzzzzzzzz

Did you add 
```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main 
```
to your third party sources?

And you may try to add the awn-manager-trunk and awn-extras-applets-trunk version... I think the install is easier and it contains additional stuff

---

### Post by boddhisatva on 2009-05-22
I wonder why bother with AWN when Cairo-Dock seems to be so much better in every way?

---

### Post by vgrisham on 2009-05-22
> **boddhisatva said:**
> I wonder why bother with AWN when Cairo-Dock seems to be so much better in every way?

IMHO, AWN's design elements are much nicer. I tried Cairo-Dock, but it didn't quite look right with my desktop. Now if Gnome-DO's Docky would go 3D, I might have to go shopping.

---

### Post by fabounet on 2009-05-22
GLX-Dock has gone 3D, so you can "go shopping" :)
(and after all, AWN is just a subset of Cairo-Dock now)

---

### Post by moonbeam on 2009-05-22
> **fabounet said:**
> 
(and after all, AWN is just a subset of Cairo-Dock now)

I have no idea what this is supposed to mean.  Sounds like meaningless marketing speak to me.  


Anyway, some meaningful marketing speak follows :-)  Those who are fond of AWN's fundamentally sound architecture and belief in a focus on usability (with a bit of shiny thrown in) are encouraged to post questions/thoughts on our forums at [http://awn.planetblur.org/](http://awn.planetblur.org/) and report bugs on [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) and [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras).  There is also planet AWN at [http://planet.awn-project.org/](http://planet.awn-project.org/) and our irc channel (#awn) on freenode.net.  Please note that AWN devs rarely browse the Ubuntu forums so if you'd like ensure we see a comment please keep this in mind :-)

And for those who are using the awn-testing PPA,0.4 is progressing and testing packages should appear within a few weeks.  It's a fundamental rewrite where we have taken the tenets of stability, usability and ease of applet development and extended these even further to provide a basis for many cool (and usable) features, both in this upcoming release and future releases.

---

### Post by vgrisham on 2009-05-23
> **moonbeam said:**
> I have no idea what this is supposed to mean.  Sounds like meaningless marketing speak to me.  


Anyway, some meaningful marketing speak follows :-)  Those who are fond of AWN's fundamentally sound architecture and belief in a focus on usability (with a bit of shiny thrown in) are encouraged to post questions/thoughts on our forums at [http://awn.planetblur.org/](http://awn.planetblur.org/) and report bugs on [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) and [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras).  There is also planet AWN at [http://planet.awn-project.org/](http://planet.awn-project.org/) and our irc channel (#awn) on freenode.net.  Please note that AWN devs rarely browse the Ubuntu forums so if you'd like ensure we see a comment please keep this in mind :-)

And for those who are using the awn-testing PPA,0.4 is progressing and testing packages should appear within a few weeks.  It's a fundamental rewrite where we have taken the tenets of stability, usability and ease of applet development and extended these even further to provide a basis for many cool (and usable) features, both in this upcoming release and future releases.

Moonbeam, what is up with the Trash applet? Will it be fixed in .4? Thanks.

---

### Post by moonbeam on 2009-05-23
> **vgrisham said:**
> Moonbeam, what is up with the Trash applet? Will it be fixed in .4? Thanks.

According to malept "Most definitely" :-)

---

### Post by fwc67 on 2009-07-07
Any word on when one will be able to orient the dock to other sides of the screen than the bottom?

---

### Post by moonbeam on 2009-07-07
> **fwc67 said:**
> Any word on when one will be able to orient the dock to other sides of the screen than the bottom?

It's in the 0.4 branch.  Which will be hitting the awn-testing ppa real soon now and will be seeing an official release within a couple months (if all goes well)

---

### Post by dasbooter on 2009-07-25
Sorry if this is asked already (googling brought me here). I saw in a bug thread that 0.4 might have some accommodation for people using "focus follows mouse" in Compiz. I realize there is a global key but I haven't gotten the behavior to work for me(perhaps some applets not obeying that key). I google for an update everyonce in awhile ... I really liked focus follows mouse but gave it up for this panel. Any word on how this accommodation would work (something to do with the ctrl button I think)

---

### Post by moonbeam on 2009-07-25
> **dasbooter said:**
> Sorry if this is asked already (googling brought me here). I saw in a bug thread that 0.4 might have some accommodation for people using "focus follows mouse" in Compiz. I realize there is a global key but I haven't gotten the behavior to work for me(perhaps some applets not obeying that key). I google for an update everyonce in awhile ... I really liked focus follows mouse but gave it up for this panel. Any word on how this accommodation would work (something to do with the ctrl button I think)

I don't think there is any intent to use the ctrl key.  I'll ask around to see if any of the other devs has such an intent.

I'm will nag some more applet devs into paying attention to the shared key once we merge.  It's a medium priority item.

So, the degree to which we'll be compatible with focus follows mouse is still somewhat up in the air for 0.4.  I hope it's fairly good by release day.

---

### Post by badenov on 2010-08-13
Brightness applet for AWN
=========================

version 0.1.2
[http://www.larpfort.pl/linux/brightness-0.1.2.tar.gz]("http://larpfort.pl/linux/brightness-0.1.2.tar.gz")

Installation:

1. Unpack to: ~/.config/awn/applets
2. Add applet: awn-settings

Dependencies:
- python
- awn-extras
- gnome-power-manager

Other info:
- tested only with awn-bzr on my laptop

---

### Post by pol2005 on 2010-08-20
i installed the mac theme and everything was good until reboot my computer.A message appeared in my screen and from then the ubuntu starts but i am getting a black screen with the cursor only appearing.I tried to uninstall the theme but didn't work.Any ideas how to restore my desktop?

---

### Post by juil on 2010-08-30
I'm a real noob here so I have some important questions. I installed AWN a while back. Didn't use it for several months and started using it again. Currently 0.4.0. When I tried installing applets i ran into TWO issues

**1**)I added the below to the /etc/apt/sources.list
#FILE: /etc/apt/sources.list
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) lucid main

then, in the terminal
$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr

unfortunately it gave me this message:
Failed to fetch [http://ppa.launchpad.net/reacocard-a...86/Packages.gz](http://ppa.launchpad.net/reacocard-a...86/Packages.gz) 404 Not Found

2)While investigating this problem, i ran into a topic by reacocard on how to install the applets in this link: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
The terminal instruction was:

$sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

The weird thing is that software centre says that AWN is installed but synaptic shows that the 3 packages above is NOT installed (white box).

Can someone help me out?

Also, this post says that he only suppots hardy and intrepid. Does that mean i can't get these applets for lucid?

---

### Post by techno-mole on 2010-08-30
You should add this repo, it will give you the latest version, it's a testing ppa, so there maybe some unstable behaviour.

I've run packages from this ppa on lucid and at present maverick and I haven't had any issues.
Remove any awn related repo's ppa's you have installed before adding this one.

Here's the link to the launchpad ppa page.

[https://launchpad.net/~awn-testing/+archive/ppa]("https://launchpad.net/~awn-testing/+archive/ppa")

---

### Post by defue on 2012-02-23
Brightness applet for AWN
=========================

version 0.1.3 attached
I've tacken badenov's version and enhanced it to work with gnome3 shell

Installation:

1. Unpack to: ~/.config/awn/applets
2. Add applet: awn-settings

Dependencies:
- python
- awn-extras
- gnome-power-manager

---

