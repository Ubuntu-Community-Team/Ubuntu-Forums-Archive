---
title: "Ubuntu for family"
date: 2007-06-22
forum: General Help
---

### Post by Kzap333 on 2007-06-22
Hi it's me again I have been around these forums alot latly looking for help mainly (well always).
I have just installing Ubuntu on my main computer and my dad wants me to install it on the home one when I have got it all worked out.
But I have run into afew problems installing it on my PC and want to get it fixed for the real deal.
Okay the computer will be used by the whole family (apart from me abd my sister we have our own)

My Mum and Dad will only use it for internet and word prosessing so I got that sorted (I will just have to teach them a new program)

My brother will use it for playing Warcraft 3 and internet and my little sister will just use it for internet.

Now the things I am worried about.
[LIST]
[*]Wireless my I cant find any linux drivers for my wireless card so I need to know where I can get a simple program to work it or find a cheap wirelessw card or USB devise that is supported by Linux.
[*]All my HDDs are showing as read only and when I try to change them to Read and Wight it come up with an error.** I really need help on this one.**
[*]And lastly internet is the Orange/Freeserve/Wanadoo brodband modem sopported in linux I have internet on my computer when connect it to the family computer with a cross over cable.
[/LIST]

Thank you for your help and sorry for my spelling.

---

### Post by weblordpepe on 2007-06-22
Ok.
Wireless:
Check out **ndiswrapper**. It is a program which will allow you to use a Windows driver for your wireless.
HDDs:
Fiesty Fawn should prompt you for a password to allow write-access, however check out **ntfs-3g**. You will be able to mount Windows directorys with write-access and save the configuration to /etc/fstab.
Also, do not use ntfs-compression on the NTFS drives. Thats about the only thing ntfs-3g/linux can't handle yet.

Broadband modem:
No clue. :P

---

### Post by stevebakerj on 2007-06-22
> **Kzap333 said:**
> [*]And lastly internet is the Orange/Freeserve/Wanadoo brodband modem sopported in linux I have internet on my computer when connect it to the family computer with a cross over cable.
[/LIST]

Thank you for your help and sorry for my spelling.

What Modem is it? (Make Model) or is it a modem/router?(Make Model) are you connected to it via ethernet or USB or WiFi? how are your Mom,Dad, Brother, Sister connected to it?

---

### Post by Kzap333 on 2007-06-22
> **stevebakerj said:**
> What Modem is it? (Make Model) or is it a modem/router?(Make Model) are you connected to it via ethernet or USB or WiFi? how are your Mom,Dad, Brother, Sister connected to it?
We have a wireless network at home the main computer is the host or what ever it has a broundband modem I'm at school at the moment so I can't tell you the name on the box.

---

### Post by Kzap333 on 2007-06-22
> **weblordpepe said:**
> Ok.
Wireless:
Check out **ndiswrapper**. It is a program which will allow you to use a Windows driver for your wireless.
HDDs:
Fiesty Fawn should prompt you for a password to allow write-access, however check out **ntfs-3g**. You will be able to mount Windows directorys with write-access and save the configuration to /etc/fstab.
Also, do not use ntfs-compression on the NTFS drives. Thats about the only thing ntfs-3g/linux can't handle yet.

Broadband modem:
No clue. :P
I can't acess the HDDs in Fiesty Fawn it just comes up with an error it does not ask me for a password

---

### Post by r0ck80y on 2007-06-22
Please post your /etc/fstab file. 
You're probably using ntfs drives or you have to be root to write onto these drives. If its the former case, install 'ntfs-3g' as weblordpepe suggested

---

### Post by Old Pink on 2007-06-22
> **Kzap333 said:**
> [LIST]
[*]And lastly internet is the Orange/Freeserve/Wanadoo brodband modem sopported in linux I have internet on my computer when connect it to the family computer with a cross over cable.[/LIST] Plug it in and try and connect. If no luck, open a terminal, type dmesg and post the last lines of output (the relevant ones) here. :)

---

### Post by Kzap333 on 2007-06-22
> **r0ck80y said:**
> Please post your /etc/fstab file. 
You're probably using ntfs drives or you have to be root to write onto these drives. If its the former case, install 'ntfs-3g' as weblordpepe suggested
Okay I'm confussed I'll check when I get home I'm at school at the moment.
I cannot write to ANY drives AT ALL not even file system I have save every thing on the desktop.
I have given my user all admin rights.
*@Old Pink*If no one is on it I'll check with the live CD at home.

---

### Post by Kzap333 on 2007-06-22
> **weblordpepe said:**
> Ok.
Wireless:
Check out **ndiswrapper**. It is a program which will allow you to use a Windows driver for your wireless.
HDDs:
Fiesty Fawn should prompt you for a password to allow write-access, however check out **ntfs-3g**. You will be able to mount Windows directorys with write-access and save the configuration to /etc/fstab.
Also, do not use ntfs-compression on the NTFS drives. Thats about the only thing ntfs-3g/linux can't handle yet.

Broadband modem:
No clue. :P
I got **ndiswrapper** but could not get it to work so I uninstalled it.
*EDIT: thats because it was a makefile I'll install it on sunday hopefully.*

---

### Post by r0ck80y on 2007-06-22
Haven't u heard of apt-get ot aptitude to install software? Google and u'll find lotsa topics on them. Or use this guide and learn about the ubuntu system:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Chk this to install ndiswrapper: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

And see my earlier post if your hard disk problem is still not sorted out

---

### Post by Kzap333 on 2007-06-22
> **r0ck80y said:**
> Please post your /etc/fstab file. 
You're probably using ntfs drives or you have to be root to write onto these drives. If its the former case, install 'ntfs-3g' as weblordpepe suggested
```
bash: /etc/fstab: Permission denied
```

---

### Post by orb9220 on 2007-06-22
gksudo gedit /etc/fstab

---

### Post by christhemonkey on 2007-06-22
The reason you cannot write to the root of your filesystem is because your not the admin (root user) of your system.

It is very very very bad practice to run as this user (like you do by default in windows) the only place you can save files to by default is /home/YOURUSRENAME/ and any subdirectories within that.

If you *really need* to write to higher in the directory tree go to a terminal and type:
```
sudo *insertrealcommand* 
```


For example replacing insertrealcommand with 'gedit /etc/fstab' which allows you to edit the file /etc/fstab in gedit (the text editor).


To get a graphical browser that will give you root acces ***(Dangerous***)  type:
```
gksudo nautilus / 
```

---

### Post by Motoxrdude on 2007-06-22
For the ntfs drives try out NTFS CONFIGURATION TOOL.
Go to Applications>>Add/Remove Programs
Search NTFS, check the NTFS configuratoin tool and press ok. Once that is done, go to Applications>>System Tools>>NTSF Configuration tool.
The check both boxs, press ok, restart your computer, and see if you can write to those drives.

---

### Post by Kzap333 on 2007-06-23
Okay I have not got an internet conection at the moment (in Ubunut).
Just to fill you in I was showing of all the linux Beryl effects to my dad and showed him how it neaver crashed and could actually run some windows program (it has come along was sence he was raving about it in the late 70s it was called Unix then) my dad has been out of the Linux loop for a long time now and as he was saying "well if you can find all the...." I opened up the aplications menu and showed him open office "and what about internet and e-mail does it us netscape" I told him it came with firefox which he already uses and the e-mail program that comes with Ubuntu. "So can I test it on my work laptop? If it works I'll use it permently" I gave him the LiveCD. So I just need to know how to get the wireless working on roaming mode working and that should be good. My dad used to be a techy but now he manages and cluster of the PACs program (thats digital X-Rays so that any doctor any where in the countory can acess the digital images). He will just want it on his work laptop because it keeps crashing when he's browsing the internet and doing databases and stuff.

---

### Post by Kzap333 on 2007-06-23
Well that justed pooed my whole system I CAN"T LOIGIN at all now. I'm going to have to re-install every thing again. How do you remove Ubuntu from the boot menu (I don't realy want 2 of them there.)

---

### Post by Kzap333 on 2007-06-23
> **Motoxrdude said:**
> For the ntfs drives try out NTFS CONFIGURATION TOOL.
Go to Applications>>Add/Remove Programs
Search NTFS, check the NTFS configuratoin tool and press ok. Once that is done, go to Applications>>System Tools>>NTSF Configuration tool.
The check both boxs, press ok, restart your computer, and see if you can write to those drives.
HOW OFTEN DO I HAVE TO SAY THE DRIVE IS NOW NTFS IT IS EX3 OR WHAT EVER IT IS CALLED!!!!

---

### Post by muguwmp67 on 2007-06-23
> **Kzap333 said:**
> HOW OFTEN DO I HAVE TO SAY THE DRIVE IS NOW NTFS IT IS EX3 OR WHAT EVER IT IS CALLED!!!!
I believe that christhemonkey's response explains whats happening with the root file system.  You can only write files to your home directory (including desktop) unless you have su rights.

If you are having trouble accessing other hard drives besides the root file system, post your /etc/fstab  using the command orb9220 provided earlier.

No offense intended, but I think you should wait a little while before you install on your family's system.  The questions you are asking indicate that you are very new to Linux.  Give yourself a month after you have set up your system and it is running the way you want.  This will help you get over a large portion of the learning curve.

---

### Post by Kzap333 on 2007-06-23
> **muguwmp67 said:**
> I believe that christhemonkey's response explains whats happening with the root file system.  You can only write files to your home directory (including desktop) unless you have su rights.

If you are having trouble accessing other hard drives besides the root file system, post your /etc/fstab  using the command orb9220 provided earlier.

No offense intended, but I think you should wait a little while before you install on your family's system.  The questions you are asking indicate that you are very new to Linux.  Give yourself a month after you have set up your system and it is running the way you want.  This will help you get over a large portion of the learning curve.
Okay I shall but I did think the point of Ubuntu was that it just worked and any old person could install it and I found my self using all my knolage just to setup a basic system and its not working properly.
Any way pressing isue is that I cannot log in any more!!!!
Help please!!!
I just need to know how to uninstall Ubuntu without loging in so I can start again from scratch. Or at least how to REMOVE it from the boot menu.

---

### Post by stevebakerj on 2007-06-23
You don't need to uninstall, just do a new install over the broken one, GRUB will sort out the boot.

Before you do this though **[COLOR="Red"]BACKUP[/COLOR]** all of your working data.

It might be a good idea to install something like VirtualBox on your Win setup and practice various Ubuntu installs/setups/.conf edits/sudo/gksudo/terminal use/different desktops Xface or KDE before committing to a working Install.

Ubuntu does work out of the box first time, but remember people control how it installs

Virtual Machine Software:

[http://virtualbox.org/](http://virtualbox.org/)
[http://microsoft.com/virtualpc/](http://microsoft.com/virtualpc/)
[http://vmware.com/products/player/](http://vmware.com/products/player/)
[http://parallels.com/products/workstation/](http://parallels.com/products/workstation/)

And when you are happy with your newly installed setup you can install VirtualBox on your Ubuntu setup and create Ubuntu setups for the various members of your family so they can see what they will be getting and can change things before they finally commit to the working install on their machines, and earn yourself a lot of brownie points and in the process you will gain invaluable Linux experience and it wont matter if your screw up when using any of the Virtual Machines as it will not effect any of your/their working data..

---

### Post by Kzap333 on 2007-06-24
> **stevebakerj said:**
> You don't need to uninstall, just do a new install over the broken one, GRUB will sort out the boot.

Before you do this though **[COLOR="Red"]BACKUP[/COLOR]** all of your working data.

It might be a good idea to install something like VirtualBox on your Win setup and practice various Ubuntu installs/setups/.conf edits/sudo/gksudo/terminal use/different desktops Xface or KDE before committing to a working Install.

Ubuntu does work out of the box first time, but remember people control how it installs

Virtual Machine Software:

[http://virtualbox.org/](http://virtualbox.org/)
[http://microsoft.com/virtualpc/](http://microsoft.com/virtualpc/)
[http://vmware.com/products/player/](http://vmware.com/products/player/)
[http://parallels.com/products/workstation/](http://parallels.com/products/workstation/)

And when you are happy with your newly installed setup you can install VirtualBox on your Ubuntu setup and create Ubuntu setups for the various members of your family so they can see what they will be getting and can change things before they finally commit to the working install on their machines, and earn yourself a lot of brownie points and in the process you will gain invaluable Linux experience and it wont matter if your screw up when using any of the Virtual Machines as it will not effect any of your/their working data..

I done it now. I've re-installed everything. I also gave my self some swap memory this time (I hade none last time).
I think the idea of being only to acess you're own directory in Ubuntu is crap because I was showing off Ubuntu to my Dad the other day and it would not let me save any thing to my memory stick as I was not the root user.

---

### Post by rax_m on 2007-06-24
That doesn't happen to me.. I can save stuff onto my USB as a normal user. 
Could it be you created a directory on the USB as root rather than the normal user ?
Also what filesystem format (NTFS, FAT32, Ext3??) is your USB in?

---

### Post by Kzap333 on 2007-06-25
> **rax_m said:**
> That doesn't happen to me.. I can save stuff onto my USB as a normal user. 
Could it be you created a directory on the USB as root rather than the normal user ?
Also what filesystem format (NTFS, FAT32, Ext3??) is your USB in?

FAT I don't know which one

---

