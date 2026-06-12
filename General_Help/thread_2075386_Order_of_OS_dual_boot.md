---
title: "Order of OS dual boot"
date: 2012-10-23
forum: General Help
---

### Post by lwalper on 2012-10-23
Is there any way to change the order of boot sequence in the boot loader. I've got a dual-boot Vista / Ubuntu system that I would like to change the boot order to load Vista by default instead of Ubuntu.

---

### Post by dr1094 on 2012-10-23
One way is to run Live CD, open software center, search 'grub' install 'StartUp-Manager'. 

This program does not work well (or at all) for ubuntu 11.04. You will have to find out from the net on how to properly use this program, also, the user comments in software center may help somewhat.

hope it helps, report back if it works for you.

---

### Post by aabed91 on 2012-10-23
You can do this using grub customizer tools in ubuntu

To download this tool Type these commands:

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```

By this tool you can reorder the boot list or remove some elements from it

it's easy to use and small

---

### Post by Dennis N on 2012-10-23
To change which grub menu entry boots without human intervention,

Edit the file [B]/etc/default/grub
[/B]
Find the line GRUB_DEFAULT=0 and change 0 to 1 to boot the second grub menu entry as default (counting starts at 0 here); change 0 to 2 to boot the third grub menu entry, and so on.

This will not visibily change the menu order, only the entry which automatically boots.

Last, run the command **sudo update-grub** to generate a new grub menu.

---

### Post by Mark Phelps on 2012-10-24
Do NOT install startup-manager.  Does not work with recent Ubuntu versions primarily due to GRUB changes.

+1 for Grub-Customizer. Offers a lot more options than just changing the boot order.

---

### Post by lwalper on 2012-10-24
**Dennis N**
OK, I located / opened the grub file with gedit, made the appropriate change and tried to save the file, but get the error that I don't have privileges to change the file. Guess I need to do some SUDO command to edit in terminal?

---

### Post by Dennis N on 2012-10-24
> **lwalper said:**
> **Dennis N**
OK, I located / opened the grub file with gedit, made the appropriate change and tried to save the file, but get the error that I don't have privileges to change the file. Guess I need to do some SUDO command to edit in terminal?

Yes, any changes made to system files need root privileges. There are text editors that work inside the terminal - I use nano, which is installed in Ubuntu by default and easy to use.

In the terminal, navigate to **/etc/default**.

Then, **sudo nano grub** will open the file for editing in the terminal. Use arrow keys to navigate to the desired line **GRUB_DEFAULT=0**. Backspace over 0 and change to desired number.

There are keys to commands on the bottom but in brief, (^O means CTRL-O)

CTRL-O will write the file out.
CTRL-X will exit.

Next, type **sudo update-grub** to create the new grub menu file.

Done.

---

### Post by lwalper on 2012-10-25
OK, thanks a bunch. That fixed it.

Curious use of language - "write out" as opposed to the more commonly used (at least for me) "save" and then prompting for "overwrite".

---

