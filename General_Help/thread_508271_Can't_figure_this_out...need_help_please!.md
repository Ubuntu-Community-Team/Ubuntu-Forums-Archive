---
title: "Can't figure this out...need help please!"
date: 2007-07-24
forum: General Help
---

### Post by herrma29 on 2007-07-24
I am at a loss for solutions. I have been scouring for some time now searching for any bit of information as to how to resolve this issue.

I recently tried following [these]("http://vorian.org/?p=82") instructions to install compiz fusion, and ended up breaking things.

Update Manager is giving me this :> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I type sudo apt-get update I get this:

```
Reading package lists... Done
W: GPG error: http://ftp.musicbrainz.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3A39A02A92132F7B
W: You may want to run apt-get update to correct these problems

```

sudo apt-get -f install gives me:

```
root@chris-laptop:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz compiz-gtk
The following NEW packages will be installed:
  compiz compiz-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 60.0kB/122kB of archives.
After unpacking 254kB of additional disk space will be used.
Do you want to continue [Y/n]? y      
Get:1 http://us.archive.ubuntu.com feisty/main compiz 1:0.3.6-1ubuntu13 [26.9kB]
Get:2 http://us.archive.ubuntu.com feisty/main desktop-effects 0.7.1-0ubuntu4 [33.1kB]
Fetched 60.0kB in 0s (82.2kB/s)       
Selecting previously deselected package compiz-gtk.
(Reading database ... 134725 files and directories currently installed.)
Unpacking compiz-gtk (from .../compiz-gtk_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.3.6-1ubuntu13_all.deb) ...
Selecting previously deselected package desktop-effects.
Preparing to replace desktop-effects 0.7.1-0ubuntu4 (using .../desktop-effects_0.7.1-0ubuntu4_i386.deb) ...
Unpacking replacement desktop-effects ...
Setting up compiz-gtk (0.3.6-1ubuntu13) ...

Setting up compiz (0.3.6-1ubuntu13) ...
Setting up desktop-effects (0.7.1-0ubuntu4) ...

(update-desktop-database:16172): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing desktop-effects (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 desktop-effects
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, I have tried various solutions on my own before asking for some help which has probably done more to harm than to help, but I could really use a hand on this one. Thanks a ton in advance.

---

### Post by zanglang on 2007-07-24
You were missing the GPG key for Musicbrainz picard or tagger.

If you've installed picard, do this step:
> wget [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key) -O- | sudo apt-key add -
and then
> sudo aptitude update

Edit: oops, you do have something broken. Let's see...
Try
> sudo update-desktop-database

If that doesn't work, try removing all compiz packages including desktop-effects, then
> sudo aptitude clean
sudo aptitude update
and reinstall following this guide:
[http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)

---

### Post by herrma29 on 2007-07-24
Alright, I ended up removing all packages related to compiz, it seemed to work. Thanks for the help!

---

### Post by herrma29 on 2007-07-24
Ok, I thought I had the problem fixed...but I don't. I couldn't remove desktop-effects and now it's spitting this out at me:

```
root@chris-laptop:~# apt-get remove desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  desktop-effects
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 557kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133855 files and directories currently installed.)
Removing desktop-effects ...

(update-desktop-database:32395): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing desktop-effects (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 desktop-effects
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried going into aptitude and removing the broken package from there, but it gives me an error message.

I then tried just fixing the file and it asked to install a bunch of compiz stuff. I said ok and it gave me this error message:

> E: desktop-effects: subprocess post-installation script returned error exit status 139



I've since removed all of the compiz stuff again, the only thing holding me up is desktop-effects

---

### Post by yorkie on 2007-07-24
You could try open synaptic search for compiz some files may still be installed if so mark for complete removal .
 hope this helps

---

### Post by zanglang on 2007-07-24
Hmm, seems to be a known bug in the desktop-file-utils package:
[https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939](https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939)
Would you like to reopen the bug and submit as much info as possible?

Another one on Launchpad is this.. maybe you can try contacting Mr Cesare directly for help.
[https://answers.launchpad.net/ubuntu/+question/7335](https://answers.launchpad.net/ubuntu/+question/7335)

---

### Post by herrma29 on 2007-07-24
Anyone have any more ideas for me? I'm kind of stuck where I am right now...

---

