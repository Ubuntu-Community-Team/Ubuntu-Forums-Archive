---
title: "Purge Google Ghrome"
date: 2017-07-22
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-07-22
What command do I use to purge Google Chrome?  I want to unintall the entire package including add ons and bookmarks and reinstall it.

```
$ sudo apt-get purge google chrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google
E: Unable to locate package chrome
bubba@bubba-110-194:~$ sudo apt-get purge google_chrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google_chrome
bubba@bubba-110-194:~$ sudo apt-get purge google
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google
bubba@bubba-110-194:~$ 

```

---

### Post by wildmanne39 on 2017-07-22
It depends how you installed it, please tell as how and from where.

Thanks

---

### Post by deadflowr on 2017-07-22
```
sudo apt-get purge google-chrome-stable
```
is the command to purge the default chrome. 
Change stable to unstable or beta if running either of those

Also, for a complete purge
remove the chrome folders in
/home/you/.config/google-chrome
and /home/you/.cache/google-chrome
(change you to your username)

The /home/you/.config/google-chrome folder is you profile folder which holds your settings such as addons and bookmarks.
The .cache folder is just a cached folder and is more optional to remove, but if you want to start fresh, clear that too.

Edit: 
To Add, since you already have chrome installed and have the google repositories enabled for your system.
You can reinstall using apt-get.
(Instead of downloading a new copy from the Chrome website)
Simple reverse the above command, replacing purge with install.

---

### Post by shane_faulkinbury2 on 2017-07-22
Thanks!  I installed with a .deb file.

---

### Post by vasa1 on 2017-07-22
You haven't explained why you want to completely remove the browser. When you re-install it, if you sign-in to your Google account, a lot of stuff will get synced and reappear in your profile including possibly whatever seems to have prompted you to purge.

---

### Post by shane_faulkinbury2 on 2017-07-22
Hmm?
[ATTACH=CONFIG]276108[/ATTACH]
I don't have a Google account.  I just transfer my Firefox bookmarks over to it.  I'm just purging to try to fix a Lastpass problem that didn't work with uninstallling Chrome and reinstalling the .deb so just figured I'd have to purge it.

---

### Post by deadflowr on 2017-07-22
Did you run an update after you originally installed chrome?

---

### Post by vasa1 on 2017-07-23
@bubba, please don't convey terminal output using images. Just copy the content and paste it here using code tags.

Also, please post the output from```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```and from```
apt list --installed | grep -i chrome
```

---

### Post by shane_faulkinbury2 on 2017-07-23
```
~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/appgrid-stable-xenial.list:deb http://ppa.launchpad.net/appgrid/stable/ubuntu xenial main
/etc/apt/sources.list.d/appgrid-stable-xenial.list.save:deb http://ppa.launchpad.net/appgrid/stable/ubuntu xenial main
/etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main
/etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main
/etc/apt/sources.list.d/damien-moore-ubuntu-codeblocks-stable-xenial.list:deb http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu xenial main
/etc/apt/sources.list.d/damien-moore-ubuntu-codeblocks-stable-xenial.list.save:deb http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu xenial main
/etc/apt/sources.list.d/enpass.list:deb http://repo.sinew.in/ stable main
/etc/apt/sources.list.d/enpass.list.save:deb http://repo.sinew.in/ stable main
/etc/apt/sources.list.d/flexiondotorg-ubuntu-hal-flash-xenial.list:deb http://ppa.launchpad.net/flexiondotorg/hal-flash/ubuntu xenial main
/etc/apt/sources.list.d/flexiondotorg-ubuntu-hal-flash-xenial.list.save:deb http://ppa.launchpad.net/flexiondotorg/hal-flash/ubuntu xenial main
/etc/apt/sources.list.d/heyarje-ubuntu-makemkv-beta-xenial.list:deb http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu xenial main
/etc/apt/sources.list.d/heyarje-ubuntu-makemkv-beta-xenial.list.save:deb http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu xenial main
/etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-xenial.list:deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial main
/etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-xenial.list.save:deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial main
/etc/apt/sources.list.d/opera-stable.list:deb https//:deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/spotify.list:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/spotify.list.save:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/unit193-ubuntu-encryption-xenial.list:deb http://ppa.launchpad.net/unit193/encryption/ubuntu xenial main
/etc/apt/sources.list.d/unit193-ubuntu-encryption-xenial.list.save:deb http://ppa.launchpad.net/unit193/encryption/ubuntu xenial main

```

```
$ apt list --installed grep -i chrome
Listing... Done
grep/xenial-updates,now 2.25-1~16.04.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```

Running an up date now!

---

### Post by vasa1 on 2017-07-23
A better command may be```
dpkg --get-selections | grep -i google
```

I'm sorry I forgot to include the "|" previously :( I've edited that post so it now has```
apt list --installed | grep -i chrome
```

On my system, I get```
google-chrome-stable/stable,now 59.0.3071.115-1 amd64 [installed]
```

If you had installed google-chrome-stable in the normal way, you should have```
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```in your sources but it seems to be absent.

It's possible that you still have the .deb in */var/cache/apt/archives* if you haven't run *sudo apt-get clean* in a while. Whether it will install properly if it's not referenced in your sources, I don't know.

---

### Post by shane_faulkinbury2 on 2017-07-23
```
$ dpkg --get-selections | grep -i google
account-plugin-google                install
libaccount-plugin-google    
```

```
$ apt list --installed | grep -i chrome

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

```

---

### Post by vasa1 on 2017-07-23
Okay, then if you want to reinstall google-chrome-stable, the easiest way is to download the deb from [https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html) and install it using gdebi (which you may need to install in case you don't have it).

---

### Post by shane_faulkinbury2 on 2017-07-23
I have gcebi installed and the deb downloaded from Google Chrome and will install when I get back from church!  Thanks for your help!

---

### Post by deadflowr on 2017-07-23
Basically at this point how you reinstall is far less important overall to the need to nuke the google-chrome profile folder.


Also, as a sidenote, at this point in time you can get rid of the hal-flash packages, as the only thing that ever needed them was flash and flash on linux no longer supports the feature that hal-flash brought.

(it only worked on Firefox anyway (that's a generalization, it did work on more than firefox like movie players and such, but did not work on many other browsers like chrome,opera, vivaldi; those require the pepper flash flash plugin which  don't support the feature hal provided) 

And if you have the flash plugin version (11.2)  that could use it, your system is very susceptible to exploits at this point and should be immediately updated to a new version.

And that's not counting that the hal-flash packages is even more out-of-date and has not had maintenance in years, and it too may have serious flaws in it. It was useful for it's use, but since it no longer has a use, then there is no need to still have it, in my opinion.)

---

### Post by shane_faulkinbury2 on 2017-07-23
Well I uninstalled Chrome, ran an update and even deleted every folder listed under Google Chrome.  The freaking bookmarks and bookmarks title bar were still there!  Even my installed extensions were listed.  So it looks like tomorrow I'm going to have to purge it again and rm -r everything Google related!  I'm off to bed.

---

### Post by shane_faulkinbury2 on 2017-07-24
Hmm, I did the purge and deleted everything listed under Google and when I open Chrome my bookmarks and extensions are still here!  Should I do a search for something else besides Google?

---

### Post by deadflowr on 2017-07-24
Did you remove the profile folder?
Either
```
rm -rf ~/.config/google-chrome
```
or
```
mv ~/.config/google-chrome ~/.config/google-chrome.old
```
The first command will outright remove it, the second will simply move it so it can be restored later if you want.

---

### Post by shane_faulkinbury2 on 2017-07-24
I sure did and everything is still in it!

```
$ sudo apt-get remove google-chrome-stable[sudo] password for bubba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.8.0-53 linux-headers-4.8.0-53-generic linux-headers-4.8.0-54
  linux-headers-4.8.0-54-generic linux-headers-4.8.0-56
  linux-headers-4.8.0-56-generic linux-image-4.8.0-53-generic
  linux-image-4.8.0-54-generic linux-image-4.8.0-56-generic
  linux-image-extra-4.8.0-53-generic linux-image-extra-4.8.0-54-generic
  linux-image-extra-4.8.0-56-generic linux-signed-image-4.8.0-53-generic
  linux-signed-image-4.8.0-54-generic linux-signed-image-4.8.0-56-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  google-chrome-stable
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 239 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'account-plugin-google' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaccount-plugin-google' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-scope-virtualbox' missing; assuming package has no files currently installed
(Reading database ... 348369 files and directories currently installed.)
Removing google-chrome-stable (59.0.3071.115-1) ...
update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/x-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group x-www-browser) doesn't exist
update-alternatives: using /usr/bin/opera to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/gnome-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group gnome-www-browser) doesn't exist
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
bubba@bubba-110-194:~$ sudo su
root@bubba-110-194:/home/bubba# rm -rf ~/.config/google-chrome
root@bubba-110-194:/home/bubba# 



```

---

### Post by deadflowr on 2017-07-24
Are you logging (signing) into your google account when it starts?
Also, don't sudo su to remove the config folder, it's your folder so no need to remove as root.

---

### Post by shane_faulkinbury2 on 2017-07-24
No, I am not logging in and I won't remove as sudo su this time.

---

### Post by shane_faulkinbury2 on 2017-07-24
Finally!!!  Thanks a lot deadflowr!  It worked this time.  ;):D:p

---

### Post by vocx on 2017-07-24
> **shane_faulkinbury2 said:**
> I sure did and everything is still in it!

```

bubba@bubba-110-194:~$ **sudo su**
**root**@bubba-110-194:/home/bubba# rm -rf ~/.config/google-chrome
root@bubba-110-194:/home/bubba# 

```

The tilde symbol in the terminal is expanded to the user's home directory. If you are under your normal user, the "~" is expanded to "/home/bubba", so "~/.config" is actually "/home/bubba/.config"

If you enter single user mode with "su", you become root, so now the "~" expands to "/root", which is the home folder of the root user. Therefore "~/.config" is actually "/root/.config". That is, you should be deleting "/home/bubba/.config", but instead you are deleting "/root/.config"; you are trying to delete a configuration file in the wrong directory.

Try to understand Linux permissions. Do not use "sudo" indiscriminately. It does not only make you more "powerful" to edit system files, and install or remove packages, but it also slightly changes the environment of the terminal. In other words, you should use "sudo" sparingly, when performing specialized tasks, but for operating files under your own control, you should do this with your normal user.

> **deadflowr said:**
> Are you logging (signing) into your google account when it starts?
Also, **don't sudo su** to remove the config folder, it's your folder so no need to remove as root.

---

