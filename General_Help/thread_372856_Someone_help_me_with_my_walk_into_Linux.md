---
title: "Someone help me with my walk into Linux"
date: 2007-02-28
forum: General Help
---

### Post by lsutiger on 2007-02-28
I hope someone can become a friend here. I have tried the IRC channels, but you are looked down upon and treated badly. 
I have searched the forums, tried several 'instructions' on how to do some things, but a lot of it jumps ahead of itself.
I have no idea where to start.
To give you an example, I am trying to get the wireless card to function. I am following the the instructions from [this documentation. ]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check"). But when I try to save a file to the to the /etc/modprobe.d/ folder, I am told I do not have the permissions to write to that folder. So I check the permissions and root is the owner, and I can not change this. But, why in the instructions, does it state as this would not be the case? 
I am the only user and this is an install from about 3 hours ago.
Someone point me in the right direction....please...
Thanx

---

### Post by ~LoKe on 2007-02-28
In order to make modifications to files you don't have the permission to modify, you must act as root.  Using sudo, you can do this:
> gksudo /etc/modprobe.d/file
Remember: gksudo is used when something has a graphical interface (gedit, nautilus, etc) and sudo is used for things done via the command line (nano, mv, mkdir, etc).

---

### Post by christhemonkey on 2007-02-28
I presume you are trying this bit of the howto?
> For example, if you own a D-Link DWL-G520+ card which uses the ACX111 chipset, and you plan to use the ndiswrapper module, you have to blacklist the acx module, by creating the file /etc/modprobe.d/blacklist-acx with a single line inside which states :
 [I]blacklist acx
[/I]

To edit this file, you need to temporarily gain root priviliges, to do this use *sudo*.
If you edit the file with a terminal editing program (such as vi or nano) you need to type this:
```
sudo nano /etc/modprobe.d/blacklist-acx 
```
This will create a new file that you can insert that line into.

If you prefer a graphical editor (its only 1 line of code though....) you need to use *gksudo*.
```
gksudo gedit /etc/modprobe.d/blacklist-acx 
```

---

### Post by CocoAUS on 2007-02-28
One of the problems with the Ubuntu community is the lack of organization and common sense.  On ubuntuforums.org, you'll find too many how-to's that are disorganized, bloated, inaccurate, etc.  Too many people say things without explanation, add unnecessary instructions, etc.  With the IRC channels, there are way too many people asking for information that could easily be found on Google.  The result is that the volunteers on the IRC channels don't bother responding, and they're too flooded to respond to the questions that should be dealt with.

Sorry for your bad experiences.  I know how frustrating it is trying to get started with Linux and not having any real help.

---

### Post by lsutiger on 2007-02-28
ok I tried what you told me and it worked. Now I am trying the mdiswrapper thing, but I get an error:
./ndiswrapper_setup: command substitution: line 44: unexpected EOF while looking for matching `"'
./ndiswrapper_setup: command substitution: line 45: syntax error: unexpected end of file
./ndiswrapper_setup: command substitution: line 44: unexpected EOF while looking for matching `"'
./ndiswrapper_setup: command substitution: line 45: syntax error: unexpected end of file
Dapper final release detected.
Installing ndiswrapper-utils...
Done...
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
You appear to have an i386 system...installing the i386 drivers...
Done...
Adding drivers to ndiswrapper...
Done...
Gathering wireless card information...
Done...

??? I have no idea what to do.

---

### Post by ofek on 2007-02-28
I'll suggest posting a new thread with ur new problem, this would get more attention.

---

