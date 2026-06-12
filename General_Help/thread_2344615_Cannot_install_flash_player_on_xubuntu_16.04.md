---
title: "Cannot install flash player on xubuntu 16.04"
date: 2016-11-26
forum: General Help
---

### Post by krulmariosz on 2016-11-26
Hi everybody!

I am new xubuntu user, I am slowly getting with new things like commands, apps and other stuff, and I am glad to use xubuntu. However there is one thing that I cannot do. It is installation of Flash Player. I have searched different topics to tried to get it with different methods, but everytime installation fails, or flash is not working.

I tried installing pepperflash, but it was not working with Firefox or Chromium (I am using the second one at the moment). Installing Chrome is not really an option because I have 32bit laptop. When I try to install pepperflash from terminal this is the result:

```
mariosz@mariosz-Studio-1537:~$ sudo apt-get install pepperflashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iucode-tool mypaint-data python-numpy thermald
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  ttf-dejavu ttf-xfree86-nonfree
The following NEW packages will be installed:
  pepperflashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/11,2 kB of archives.
After this operation, 42,0 kB of additional disk space will be used.
Selecting previously unselected package pepperflashplugin-nonfree.
(Reading database ... 197575 files and directories currently installed.)
Preparing to unpack .../pepperflashplugin-nonfree_1.8.2ubuntu1_i386.deb ...
Unpacking pepperflashplugin-nonfree (1.8.2ubuntu1) ...
Setting up pepperflashplugin-nonfree (1.8.2ubuntu1) ...
E: No packages found
E: No packages found
E: No packages found
E: No packages found
E: No packages found
E: No packages found
dpkg-deb: error: --extract needs a target directory.
Perhaps you should be using dpkg --install ?
```


Any ideas? Thanks very much for all help!

---

### Post by Bashing-om on 2016-11-26
krulmariosz; Hello:

As of 2015-05, the old "pepperflashplugin-nonfree" is deprecated in favor of an official, maintained, one-step package called adobe-flashplugin, which works for Firefox and Chromium and derivatives.
Terninal commands:
```

sudo apt update
sudo apt install adobe-flashplugin

```
to install .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2016-11-26
There is alternatives but to install flash player, first thing you need to do is enable the Canonical Partner Repository.

Open Software & Updates> Switch to ‘Other Software‘ tab>Click/check the ‘Canonical Partners’ repository then refresh your software sources when prompted.

Search for the adobe flash plugin in Ubuntu Software (by searching for adobe flash), or in the terminal:
```
sudo apt install adobe-flashplugin
```
Reboot

---

### Post by wildmanne39 on 2016-11-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by krulmariosz on 2016-11-26
Thanks a lot guys, flash is working! :)

---

### Post by wildmanne39 on 2016-11-26
Your welcome! please use thread tools at the top of the page to mark thread solved.

---

