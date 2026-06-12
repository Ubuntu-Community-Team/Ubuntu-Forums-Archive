---
title: "Recently installed Fluxbox, but..."
date: 2005-06-10
forum: General Help
---

### Post by Paul Panks on 2005-06-10
...there's no default desktop background that I can see, only a bright square dot in the left hand corner of the screen, Clicking on the mouse shows a small menu (Apps, Games, etc.), but how do I install some sort of background desktop for Fluxbox?

Also, how do I get Firestarter (the firewall) working on Fluxbox? I can easily get it working by going to "Applications" -> "System Tools" -> "Firestarter", but on Fluxbox I don't see it under "Apps"?

Paul

---

### Post by Seti on 2005-06-11
You will have to do two things when using fluxbox:

1) Prepare to use the console a lot more; flux is stripped-down. It is a window manager, not a desktop-enviromnent like Gnome or Xfce.

2) You must edit your /home/username/.fluxbox/init file so that your /home/username/.fluxbox/menu file is used for the menu. You can then edit this ~/.fluxbox/menu file so that you can have the apps you want in the menu. The syntax of the file is straighforward, simple and effective. Be sure you make a backup of your orginal, just in case you fubar it.

You should find a menu of fluxbox styles in the menu somewhere. These are a good start.

To set backgrounds, you will probably need a program called feh so that your pictures are correctly rendered as backgrounds.
```
sudo apt-get install feh
``` 

Now, to set a pic as your background, cd to the folder where you keep backgrounds.
For example, I like to keep all of mine in a folder called bkrnds. 
So in a console (I like xterm, tho aterm is nice in fluxbox)

```
cd pictures/bkrnds
``` 

and then:
```
fbsetbg filename
``` 

remember to include the file extension in the file name if it is there!

To start Firestarter, just open a console and type:
```
nohup firestarter
``` 

Fluxbox is great!

---

### Post by Paul Panks on 2005-06-11
Didn't work. Here is the output:

# sudo apt-get install feh

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  giblib1 libimlib2 libltdl3 libungif4g
The following NEW packages will be installed:
  feh giblibl libimlib2 libltdl3 libungif4g
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 185kB/690kB of archives.
After unpacking 1495kB of additional disk apce will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libimlib2 1.1.2-2.1 [185kB]
Fetched 185kB in 2s (88.9kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb)   MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

# 

Any ideas? It had me insert my Ubuntu 5.04 install CD into the drive during the middle of the process.

When I just tried to place a background regardless of the presence of feh, fluxbox balked and said that it couldn't find a program to put a background image up. It suggested "eterm", which I also tried to "apt-get", but with the same failed results.

Paul

---

### Post by Seti on 2005-06-11
You probably have to go into Synaptic and add the Universe repository to your sources.list so that it can install it. Sorry, I should have told you that in the first place.

Just add the repositories, I know feh is in there.

---

### Post by claydoh on 2005-06-11
I am getting the same error when tring to istall other applications, as it happens they are all icewm related:

 > ~$ sudo apt-get install icewm
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  icewm-common
Suggested packages:
  icewm-gnome-support icewm-themes icepref iceme
The following NEW packages will be installed:
  icewm icewm-common
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 812kB of archives.
After unpacking 3817kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe icewm-common 1.2.18-1ubuntu1 [350kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe icewm 1.2.18-1ubuntu1 [462kB]
Fetched 812kB in 4s (186kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/i/icewm/icewm-common_1.2.18-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/i/icewm/icewm-common_1.2.18-1ubuntu1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 

So I guess there is a problem on the repository?

---

### Post by gil-galad on 2005-06-11
You probably shouldn't use fluxbox unless you have a good reason too.

---

### Post by claydoh on 2005-06-11
I have a good reason to: **it's there **:)

---

### Post by void_false on 2005-06-11
[QUOTE=gil-galad]You probably shouldn't use fluxbox unless you have a good reason too.[/QUOTE]

LOL. Why? It's as great as other WMs.  :wink:

---

### Post by simple on 2005-06-11
[QUOTE=gil-galad]You probably shouldn't use fluxbox unless you have a good reason too.[/QUOTE]
after installing fluxbox for the hell of it, my alsa config went poof and sound card wasn't detected anymore, got rid of fluxbox since i didn't even need it and had to recompile/configure alsa, so yeah i would say it could 'cause more problems than it's worth

---

