---
title: "Can't boot Ubuntu from grub??"
date: 2007-09-04
forum: General Help
---

### Post by Wintergreen on 2007-09-04
Hi all,

I am totally new at this Linux thing. I spent most of the day trying to install Ubuntu and to dual boot it with windows xp. At first, I had a live cd. I put it in and hit the first install option, and it just went to a screen where, on the bottom, it said something like "kernel active, kernel direct mapping......" some numbers. I looked around the forums for an answer. I rebooted and when the screen came up for Ubuntu, I pressed F6 and typed "acpi=off" in the box at the bottom, and it worked.

I now have it installed, but there is a problem when i boot up and enter grub. I select the option to start ubuntu normally. But it just goes to that "kernel alive...." screen again, the same one i saw at install. The acpi=off command doesnt work here. 

I have seen people with this problem while using the live cd, but no one seems to have it when booting Ubuntu with grub. I am going to update my BIOS tomorrow and see if that helps, but any other suggestions?

Thanks!

---

### Post by Wintergreen on 2007-09-04
Anyone have an answer?

---

### Post by logos34 on 2007-09-04
> **Wintergreen said:**
> I select the option to start ubuntu normally. But it just goes to that "kernel alive...." screen again, the same one i saw at install. The acpi=off command doesnt work here.

You should be able to add it to the end of the 'kernel' line:

Before it boots the main ubuntu hit 'e' key to edit.  Hit 'e' again on the kernel line and add the option to the end.  'Enter' to save and 'b' to boot.  If it gets you into ubuntu then make the change permanent:

**gksudo gedit /boot/grub/menu.lst**

---

### Post by Wintergreen on 2007-09-04
I can boot into Ubuntu now, but there is a problem though. WHen I try to change menu.lst, it won't let me because it is a read-only file. The owner is "root", and the option the change the owner is greyed out. How do I make the changes permanent.

Edit: it seems that I am not the owner of any folder or file in the "System Files" directory... is this normal? How do I get around this? 

P.S. I already checked the help section of the official documentation and didnt find anything...

---

### Post by confused57 on 2007-09-04
> **Wintergreen said:**
> There is a problem though. WHen I try to change menu.lst, it won't let me because it is a read-only file. The owner is "root", and the option the change the owner is greyed out. How do I make the changes permanent.

Edit: it seems that I am not the owner of any folder or file in the "System Files" directory... is this normal? How do I get around this? 

P.S. I already checked the help section of the official documentation and didnt find anything...

You can make the changes permanent by opening a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
copy & paste one line at a time, press "enter" after each line

Make your changes to the kernel line...also, add the option to the line with #kopt(kernel options):
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)
this way, the acpi=off will automatically be added when you have a kernel update

When you've finished, quit & save.

---

### Post by Wintergreen on 2007-09-04
Slight problem. I have done everything you said, but I still cannot make changes to the file. Am I doing something wrong?

---

### Post by Wintergreen on 2007-09-04
Anyone know?

---

### Post by confused57 on 2007-09-04
You can try changing your menu.lst in Nautilus...press "Alt+F2", enter:
```
gksudo nautilus
```

You'll then be prompted to enter your password that you created when you installed Ubuntu, then you should be able to make changes to your menu.lst in Nautilus.

---

### Post by strabes on 2007-09-04
> **Wintergreen said:**
> I can boot into Ubuntu now, but there is a problem though. WHen I try to change menu.lst, it won't let me because it is a read-only file. The owner is "root", and the option the change the owner is greyed out. How do I make the changes permanent.

Edit: it seems that I am not the owner of any folder or file in the "System Files" directory... is this normal? How do I get around this? 

P.S. I already checked the help section of the official documentation and didnt find anything...

Yes, it is normal that all the "system files" (meaning anything not in your home directory) are owned by root. This is a security feature. It protects you from breaking things and also from malicious software being installed on your system without your explicit consent.

In ubuntu, you can temporarily become root to edit system files by using the "sudo" command. So, to edit the menu.lst file you could run the following command:```
sudo gedit /boot/grub/menu.lst
```

Before saving, make sure you did not make any mistakes when editing because it will take a bit of work (nothing impossible, though) to restore grub if you break it.

By the way, opening nautilus as root (as confused57 told you to do) is generally a very very bad idea. It is very easy to do large amounts of damage with one wrong keystroke.

For more information, read [this page](http://www.psychocats.net/ubuntu/permissions).

---

### Post by confused57 on 2007-09-05
It's actually better to use gksudo, as logos34 mentioned earlier:
```
gksudo gedit /boot/grub/menu.lst
```
there's an excellent explanation of why in this guide:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> By the way, opening nautilus as root (as confused57 told you to do) is generally a very very bad idea. It is very easy to do large amounts of damage with one wrong keystroke.
He had already tried from the terminal, using the instructions I gave in my last reply...I realize it is potentially a bad idea(kind of like running Windows as administrator), but on a new install I thought it may be worth trying.

---

