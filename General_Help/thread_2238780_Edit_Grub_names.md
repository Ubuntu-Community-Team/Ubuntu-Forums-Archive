---
title: "Edit Grub names?"
date: 2014-08-10
forum: General Help
---

### Post by Mike_Walsh on 2014-08-10
Morning, everybody.

Quite a simple query, this one.

I've just installed several of the Ubuntu family variants onto small partitions on an external hard drive, for experimenting and testing purposes.

The only problem with this, of course, is that the Grub menu now shows several "Ubuntu" entries, and so I have to look carefully at the individual listed partitions, to make sure I'm booting up the one I actually want.

Is it possible to edit the individual entry names within the Grub screen that is shown on start-up? I would like to simply make it so that I have "(K)ubuntu", "(L)ubuntu", "(X)ubuntu".....rather than "Ubuntu", "Ubuntu", "Ubuntu", etc.

I don't wish to alter the Grub configuration, or ANYTHING that makes Grub perform its job. I merely want to edit the actual names.

Can the file in question BE edited? I'm guessing it probably can, since most things in Linux CAN be modified (carefully, of course!) Where do I locate the specific file needed?

I'm still quite new to Linux, although I'm feeling my way around, and slowly getting the hang of everything. ANY advice would be appreciated.


Regards,

Mike.

---

### Post by ajgreeny on 2014-08-10
Very easy to do!

In each of the OSs open /etc/default/grub with ```
sudo nano -B /etc/default/grub
``` and edit the line
```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```
or similar, to read, for example
```
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
```
Note the change from a single back-tick to double quote marks in the changed part of the line.  Finally run ```
sudo update-grub
``` in each OS for the chnnges to take effect.

To edit files with nano, a simple command line text editor, use cursor keys to navigate (the mouse does not work, or not in a normal manner) and when finished use Ctrl+O to save and Ctrl+X to close.  The -B option I showed will make sure that a backup of the file is made when you save it called /etc/default/grub~ so you can always restore that version if things go totally wrong; not that they should.

---

### Post by Mike_Walsh on 2014-08-10
Thanks for that, AJ!

Does 'nano' HAVE to be used, or can it be any of the text editors (leafpad, gedit, etc.)?

I only ask because some distros have one enabled by default, some have another. I don't want to have to install something that's only likely to be used once.


Regards,

Mike.

---

### Post by ajgreeny on 2014-08-10
Any text editor will do it but you need to run it with root permissions, and as gksu/gksudo is no longer installed by default it can be more involved telling you how to start a text editor as root in order to make the changes.

**sudo nano** is the simplest way to do the job, hence my recommendation, and I know that all the *ubuntu family have it by default.

Try it; it is not something to fear and if you know how to use it there are times when it can get you out of a scrape if you can't get a DE up and running for any reason.

---

### Post by Mike_Walsh on 2014-08-10
Okay, AJ; thanks for that.

That's something I've learnt today; I didn't even know about 'nano', much less that they ALL have it by default!

I'll let you know how I get on.


Regards,

Mike.

---

### Post by Mike_Walsh on 2014-08-10
Hi again, AJ.

Just tried your suggestion in each of the O/ss, and it hasn't produced the desired result, unfortunately.

I still have a list of several Ubuntus, I'm afraid!

Is there anything else that I should try?


Regards,

Mike.

---

### Post by Rev2010 on 2014-08-10
On my system (12.04), not sure if it's still the same on 14.04, I run: sudo gedit /boot/grub/grub.cfg

Then I just edit the menuentry for whatever listing I want to change and rename it to whatever I want, save the file, and reboot. Example: 

ORIGINAL
menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {

EDITED
menuentry 'Ubuntu Installation' --class ubuntu --class gnu-linux --class gnu --class os {

Works perfectly. I also need to edit the Grub file after every kernel update since I have a dual boot with Windows and it readds a listing for every prior kernel and readds the Memtest entry. So I remove all those again so I just have three entries, Ubuntu, Ubuntu Recovery, and Windows 7.


Rev.

---

### Post by Mike_Walsh on 2014-08-10
Hallo, Rev2010.

Well, it's worth a try. I'm finding my way around Linux fairly well after a few months.....but I'm (understandably) a wee bit wary when it comes to altering critical system stuff. I don't care if I mess up my test distros, 'cos that's what they're for.....but I'd rather not muck up Ubuntu itself (or Zorin) since they're my main dual-boot installations!

Will give your suggestion a try, and let you know how I get on. Thanks for that.


Regards,

Mike.

---

### Post by ajgreeny on 2014-08-10
> **Mike_Walsh said:**
> Hi again, AJ.

Just tried your suggestion in each of the O/ss, and it hasn't produced the desired result, unfortunately.

I still have a list of several Ubuntus, I'm afraid!

Is there anything else that I should try?


Regards,

Mike.
Did you make sure that you ran the ```
sudo update-grub
``` in ALL the OSs including the *ubuntu OS which manages grub, even if you did not edit the file in that OS, after editing the /etc/default/grub file in each one?

And also, did you ensure that the new contents of the line were enclosed in quotation marks, as shown?  If that still does not work I am totally baffled as it is working fine here for me in both 12.04 and 14.04, in all the *ubuntu OSs I have (Ubuntu, Xubuntu and Lubuntu 12.04 and 14.04).

What is it that you are not doing? Think very carefully; there must be something!

Try again, then run ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-85
``` in your main OS which manages grub, to see exactly what your grub menu contains.

PS:
Do **NOT** edit /boot/grub/grub.cfg.
You will find it difficult to edit anyway, as it is a read-only file, so you will first need first to change its permissions. But why bother?
As Rev2010 says, it will be changed back after a kernel update, and it is completely unnecessary.  My method will change it once and for all, so will not need repeating every time a new kernel appears.

---

### Post by Mike_Walsh on 2014-08-10
Hallo, AJ.

Hm. Well, I haven't yet tried REV2010's suggestion; I've looked at the file, but was put off that method by 2 things:-

1) The enormous length, and complexity of the file, and

2) The fact that it clearly says, in VERY large letters, right at the top, "DO NOT EDIT THIS FILE"..!!

So; you say this DOES work for you in Trusty, as well as Precise? Mmm....

I suspect the sticking point may well be 'nano'. I had a job figuring out just how you save with it, despite your instructions; it didn't seem to want to do what you said.

I'll have another go at it. As grahammechanical says in his signature, "It's only a machine. It's more stupid than we are..." I've never let one of these things beat me yet, and hey! it's all additional knowledge, especially if it's earned the hard way. Like I said, I don't really care if I mess THESE distros up.....that's what they're there for. Make, or break...I'll get there eventually!

If the worst comes to the worst, I'll just re-install. That's one thing I like about Linux; installation is a snap compared to Windows. :D While MS is still installing, I'm halfway through configuring my Linux distro...*lol*

I shall retrace my steps, and see what happens this time!


Regards,

Mike.

---

### Post by ajgreeny on 2014-08-10
If you prefer to use a GUI text editor in place of nano, do so, but all means, but you will need to open each as root to edit the default/grub file.

You should not use **sudo** for GUI applications, however, but **gksu** (or **kdesu** if using kde) instead, but as I said gksu/gksudo is no longer installed by default so will need to be installed first; no big problem but one annoying extra step.  It's your choice! That way you will, I suppose be certain that the file has saved as necessary.

As I said, remember to enclose the new text in the file in quotation marks, as "new text here" and delete the old text, of course, and do not forget to run **sudo update-grub** in all OSs after making the edits.

---

### Post by Dennis N on 2014-08-10
Another option to consider is to create a custom menu:

I used this excellent guide:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Rev2010 on 2014-08-10
> **Mike_Walsh said:**
> 2) The fact that it clearly says, in VERY large letters, right at the top, "DO NOT EDIT THIS FILE"..!!

All you're editing is a portion of text in the menuentry portion. If that's all you edit then save the file you aren't going to botch anything up. I've been editing the file manually for years with no issue but since you're not too familiar with the file just be sure not to touch anything else other than the named part in menuentry. I'll show again how simple it is: 

Open a terminal windows and type: sudo gedit /boot/grub/grub.cfg

Locate and find the entries you wish to change. Example: menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os { 

Simply edit only the text inside the ' marks. So for example change that to: menuentry 'Whatever you want' --class ubuntu --class gnu-linux --class gnu --class os {


Rev.

---

### Post by ajgreeny on 2014-08-10
> **Rev2010 said:**
> All you're editing is a portion of text in the menuentry portion. If that's all you edit then save the file you aren't going to botch anything up. I've been editing the file manually for years with no issue but since you're not too familiar with the file just be sure not to touch anything else other than the named part in menuentry. I'll show again how simple it is: 

Open a terminal windows and type: [COLOR=#ff0000]sudo gedit[/COLOR] /boot/grub/grub.cfg

Locate and find the entries you wish to change. Example: menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os { 

Simply edit only the text inside the ' marks. So for example change that to: menuentry 'Whatever you want' --class ubuntu --class gnu-linux --class gnu --class os {


Rev.
Sorry, but you are suggesting something else which is not advised, ie, sudo gedit.

I know a lot of people suggest it, and use it that way, but as I said above in post #11, you should never use sudo for GUI applications; you should be using **gksu gedit **(see Root-Sudo in my signature for the details of this and reasons why).

You do not mention the read-only permissions of that file either, and as far as I'm aware it will not be possible to edit it and save the changes without changing the files permissions first.  But why bother when it is a great deal easier to make the edit, or edits, to /etc/default/grub, run **sudo update-grub** and that is all that is needed.

---

### Post by Rev2010 on 2014-08-10
I don't recall ever needing to change permissions to the config file to do what I suggested and I've done it many many times. Not disputing your way is better however, just trying to help him get it done. 

Rev.

---

