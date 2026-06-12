---
title: "Noob needs help. Desktop icons gone, PCManFM not working"
date: 2015-08-05
forum: General Help
---

### Post by kickflipsnnollies on 2015-08-05
Hi there. Running Lubuntu 14.04.

 So I'm sitting here browing the internet (Youtube in specific) and I decided to watch a video located on my desktop. I minimize my browser (had a window open with PCManFM) and all of a sudden I have no desktop icons. Weird, but I figured not a big deal, I'll go to the file through the file manager and just play it that way. Nope. It's frozen. So I kill it manually.

 I click the icon on my taskbar for PCManFM and nothing happens. I go through the menu and nothing happens. I reboot and no icons reappear. PCManFM still does nothing, either through the taskbar or the menu. I did just let an upgrade run, so I'm guessing that's it. I was half-asleep and didn't see what the upgrade actually was, but it said something about the Lubuntu base.

Any ideas? Need more info? Just let me know where the output logs are and I'll post whatever you need. Right now I just want to smash this thing.

---

### Post by Bucky Ball on 2015-08-05
Boot and then try this in a terminal, one command at a time:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Post any and all errors. See if it makes it through that much and if not, might give some clues. :)

---

### Post by kickflipsnnollies on 2015-08-05
Ok, got one error on the update command:

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886

W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Dist-upgrade didn't exactly give me an error, but ended with:

```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'll reboot now and see what happens.

---

### Post by kickflipsnnollies on 2015-08-05
Nothing has changed. Still no PCManFM, still no desktop icons. Going through the terminal and using ls shows me that they're still there, I just can't get to them through the GUI.

---

### Post by Bucky Ball on 2015-08-05
That has told us one thing: the spotify repo is either down or dead or the wrong one. Disable that for the moment in Software and Updates> Other Software.

I'll think on this, but for now, to bed! :)

---

### Post by howefield on 2015-08-05
Won't fix the underlying problem, but for the spotify error,  try this thread [http://ubuntuforums.org/showthread.php?t=2285155](http://ubuntuforums.org/showthread.php?t=2285155)

For the underlying problem, have a look in /var/log/apt/history.log to get an idea of what packages were updated recently. Are you using the default theme or had you changed it ?

---

### Post by kickflipsnnollies on 2015-08-05
I don't even care about Spotify. My friend installed that when he was staying with me for a few months so he could use his account on my system. I have copies of everything I want.

Pretty sure I'm on the default theme, but it's been so long I'm not 100% sure. I did tweak a few things like resolution (I use a 50" TV for a monitor) and the size of the icons, fonts, etc, so I can see it across the room. I definitely didn't install any other themes.

Under the history.log I have:

```
Start-Date: 2015-08-05  12:17:01
Commandline: aptdaemon role='role-commit-packages' sender=':1.55'
Upgrade: apt:i386 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10), oxideqt-codecs-extra:i386 (1.7.9-0ubuntu0.14.04.1, 1.8.4-0ubuntu0.14.04.2), libapt-pkg4.12:i386 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10), base-files:i386 (7.2ubuntu5.2, 7.2ubuntu5.3), apt-utils:i386 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10), libapt-inst1.5:i386 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10), apt-transport-https:i386 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
End-Date: 2015-08-05  12:19:37

Start-Date: 2015-08-05  13:55:59
Commandline: apt-get autoremove
Remove: libglew1.10:i386 (1.10.0-3), libcg:i386 (3.1.0013-1), linux-image-extra-3.13.0-24-generic:i386 (3.13.0-24.47), linux-headers-3.13.0-24:i386 (3.13.0-24.47), libcggl:i386 (3.1.0013-1), linux-image-3.11.0-19-generic:i386 (3.11.0-19.33), linux-image-extra-3.11.0-19-generic:i386 (3.11.0-19.33), linux-headers-3.13.0-24-generic:i386 (3.13.0-24.47), linux-image-3.13.0-24-generic:i386 (3.13.0-24.47)
End-Date: 2015-08-05  13:57:21

Start-Date: 2015-08-05  13:59:09
Commandline: apt-get upgrade
Upgrade: bsdutils:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), libgtk-3-bin:i386 (3.10.8-0ubuntu1.5, 3.10.8-0ubuntu1.6), libmount1:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), libblkid1:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), libgtk-3-0:i386 (3.10.8-0ubuntu1.5, 3.10.8-0ubuntu1.6), ubuntu-drivers-common:i386 (0.2.91.9, 0.2.91.11), mount:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), util-linux:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), gir1.2-gtk-3.0:i386 (3.10.8-0ubuntu1.5, 3.10.8-0ubuntu1.6), uuid-runtime:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), libgail-3-0:i386 (3.10.8-0ubuntu1.5, 3.10.8-0ubuntu1.6), libuuid1:i386 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6), libgtk-3-common:i386 (3.10.8-0ubuntu1.5, 3.10.8-0ubuntu1.6)
End-Date: 2015-08-05  14:00:05
```

So any ideas? I'm not even sure exactly what all this is.

---

### Post by CantankRus on 2015-08-06
Does pcmanfm run from terminal?
```
pcmanfm
```

---

### Post by kickflipsnnollies on 2015-08-06
Nope. I tried that. I appreciate the super-noob suggestions, and keep them coming. But I have used Linux for several years now, just never got much into the command line or inner workings. I mostly just need a media box. I know how to navigate around my folders, launch a program, use various ls commands, etc. But don't assume I know anything at all cause I've been lazy with it and there's a decent chance I don't know whatever you're wanting to suggest.

On an semi-related note, is there a good book I can pick up on basic Linux that won't cost a lot? I get too ADHD online trying to read.

---

### Post by kickflipsnnollies on 2015-08-06
It's really more the desktop icons being gone that is bothering me. While I can get to all my programs and folder and files and such through the terminal, it's 1000x easier to do it with a GUI.

---

### Post by CantankRus on 2015-08-06
When you start a thread with "Noob needs help" expect the most basic.
I asked to start in terminal to see errors if any.
It's not clear whether you can run any programs from a menu?

Don't use Lubuntu, but doesn't pcmanfm draw the desktop as does nautilus in ubuntu.
```
pcmanfm --desktop-pref
```

---

### Post by Bucky Ball on 2015-08-06
You should be able to type 'pcmanfm' in the terminal and it will launch. If not, something's amiss, possibly the window manager. Not sure what Lubuntu uses. :-k

lxsession, openbox-menu, lxpanel may be the culprit. But try this in a terminal:

```
/etc/init.d/lxdm start
```

From [here]("http://superuser.com/questions/671169/starting-and-stopping-x11-and-lxde-from-command-line").

---

### Post by vasa1 on 2015-08-06
> **Bucky Ball said:**
> ... If not, something's amiss, possibly the window manager. Not sure what Lubuntu uses. :=k
Openbox.

---

### Post by kickflipsnnollies on 2015-08-07
Sorry, I didn't mean to come off as ungrateful or anything in my last post. I had been drinking a bit and this is frustrating me to no end.

```

/etc/init.d/lxdm start
```

Got me nothing. Don't have the lxdm folder.

Just noticed that right-clicking on the desktop also does nothing. Maybe related?

```

pcmanfm --desktop-pref
```

Also seemingly did nothing.

---

### Post by kickflipsnnollies on 2015-08-08
Desparate bump

---

### Post by kickflipsnnollies on 2015-08-08
Any more ideas?

---

### Post by Bucky Ball on 2015-08-08
None here, really. Have we tried completely removing pcmanfm and shoving it in again? Something odd here, though, cos reading your first post again, seems like a pcmanfm window was up behind Firefox, you minimised Firefox and the machine froze? Is that it? After that, no icons, etc.?

---

### Post by kickflipsnnollies on 2015-08-08
Yep, that's exactly what happened.

---

### Post by kickflipsnnollies on 2015-08-09
I followed all the advice here. Removing and reinstalling PCManFM left me with nothing. I get to the login screen, I log in, I tet 0 options for logins except Openbox which gets me a grey screen and nothing else. Any ideas? Maybe ask for some output before

---

### Post by kickflipsnnollies on 2015-08-09
Before having me do random ****? Im stuck on my phone now, which is way more awful than my computer. My conputer is bricked as far as I can tell.

---

### Post by tea for one on 2015-08-09
> **kickflipsnnollies said:**
> Before having me do random ****? Im stuck on my phone now, which is way more awful than my computer. My conputer is bricked as far as I can tell.

Do you have a back-up of your data? 

Have you tried to boot from a live CD or USB?

If your PC has been unresponsive for 3 days, I would consider re-installing Lubuntu.

3 days of frustration can not be compared to 30 - 60 mins of re-installation time?

Please make sure that you have a copy of your data first.

---

### Post by CantankRus on 2015-08-09
Not the best advice to remove pcmanfm, as core components depend on it in lubuntu.
Removing pcmanfm would have also removed  lubuntu-core lubuntu-default-session lubuntu-default-settings
If you're able to log in to a terminal run...
```
sudo apt-get install lubuntu-desktop
```
lubuntu-desktop is a [**_[COLOR="#B22222"]metapackage[/COLOR]_**]("https://help.ubuntu.com/community/MetaPackages") which should pull in all those packages along with pcmanfm.

---

### Post by kickflipsnnollies on 2015-08-09
I have a backup of my media and such. Don't have a live version of anything. I'd reinstall if I could. My laptop screen is also broken, making it even harder.

Can't find a way to get to the terminal. Is there a way from the login screen? That's all I have. I think I'm just gonna have to buy a new computer. I could use one anyway, I just don't really have the money.

---

### Post by CantankRus on 2015-08-09
> **kickflipsnnollies said:**
> I have a backup of my media and such. Don't have a live version of anything. I'd reinstall if I could. My laptop screen is also broken, making it even harder.

Can't find a way to get to the terminal. Is there a way from the login screen? That's all I have. I think I'm just gonna have to buy a new computer. I could use one anyway, I just don't really have the money.
At the login screen hit ctrl+alt+F1 to take you to a terminal.
Might not work because of what's happened.

ctrl+alt+F7 will take you back to the greeter.

---

### Post by kickflipsnnollies on 2015-08-09
OK, I got my desktop back! That's awesome. Any more ideas on the original problem though? PCManFM still isn't working.

---

### Post by lzeimet on 2015-08-09
do you have unity tweak tool installed?  try this and see what it does, no guarantee tho  
$ unity --reset-icons   

you should also try this aswell,  itll clean up your system  

$ echo "Cleaning Up" && 
> sudo apt-get -f install &&
>sudo apt-get autoremove && 
>sudo apt-get -y autoclean && 
>sudo apt-get -y clean

---

### Post by kickflipsnnollies on 2015-08-09
Actually, I let my laptop die and when I plugged it back in all my icons were back, PCManFM is working properly again and all seems to be good. Thanks a lot, guys!

---

### Post by CantankRus on 2015-08-09
Good. ):P
First task download an iso and create a live usb or cd. ;)

---

