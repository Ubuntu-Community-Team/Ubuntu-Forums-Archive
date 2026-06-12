---
title: "I cant make ACPI=OFF permanent in grub"
date: 2013-08-25
forum: General Help
---

### Post by ash772 on 2013-08-25
Hi folks, i'm a beginner on Ubuntu and i'm experiencing some dificulties.

I have installed Ubuntu 12.043. LTS on an Asus Laptop with a live cd.

board: X71SL (Pegatron corporation ATI)
bios: 09/24/2008 American Megatrends Inc version 204
proc: 2x Intel Core 2 Duo T5800 @ 2.00GHz 1999.00MHz
gc: geforce 9300M GS (Que je ne vois pas dans le report systinfo)

I've made some research on different forums and it turns out that i can only make Ubuntu works by adding the command ACPI=OFF into the grug during the boot. In this case Ubuntu works nicely.
Turning on the pc without modifying the ACPI results in a black or purple screen.

Now i want to edit definitively the /etc/default/grub file, but none of the commands i've found works. (Editing and updating grub is ok and when i restart, the grub display the changes)

Heres the command i have tryied so far:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi"

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" (this one works only when i do it manualy)

I may need a bit of help here.

If you need any imformation, just ask.

Thanks in advance.

---

### Post by Quackers on 2013-08-25
After you included acpi=off after the qiet splash entry did you then run
```
sudo update-grub
```
in the terminal?
That should make the change permanent.

---

### Post by Boab1993 on 2013-08-25
Try editing the line in the etc/default/grub 

note: This is not the line 'GRUB_CMDLINE_LINUX_DEFAULT'

GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX= "acpi=off"

Then do as above in a terminal

sudo update-grub

hope this helps

---

### Post by ash772 on 2013-08-25
Yes, i have done the updating grub command. I'm making another try now.

Thx for answering anyway.

---

### Post by ash772 on 2013-08-25
I will try again with a fresh install. I am messing with the etc/default/grub file for two days now and may have accidentaly change something wrong.

---

### Post by Quackers on 2013-08-25
That's possible - it gets difficult to remember what was original and what you've changed.
Good luck!

---

### Post by Boab1993 on 2013-08-25
It can be changed via command line on boot. No need for a fresh install.

Either hold down shift on boot to edit the grub before start up or when in a position of black screen after startup try pressing ctrl+alt+f1 and login via your details.

Then just type : gksudo gedit /etc/default/grub

And you can edit the grub

---

### Post by ash772 on 2013-08-25
good to know, thx.

---

### Post by wildmanne39 on 2013-08-25
Did you try nomodeset first because acpi=off turns of several things, it is different from computer to computer but in many cases the fans and wireless will not work.

---

### Post by Boab1993 on 2013-08-25
> **Wild Man said:**
> Did you try nomodeset first because acpi=off turns of several things, it is different from computer to computer but in many cases the fans and wireless will not work.

This is actually a good time to ask because you seem to know what your doing.

Disabling acpi in this way, does that just disable it for the period of booting or is it permanent?

One person says one thing, the other says another, just wondering if you had a clear answer.

---

### Post by mcduck on 2013-08-25
It's permanent.

Also you should make sure to do the edit in both GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE_LINUX.

The later is the one that actually has effect on your boot, but the first one is the one that's maintained through kernel updates, so if you forget to make the chance in it as well as the actual boot line, your chances will disappear during the next kernel update and you'll have to do the editing again...

Also I agree with Wild Man about trying nomodeset first before acpi=off. Also it's a good idea to save a backup of any system files before editing them. Just add something like ".backup" to the end of the file name, and you'll always be able to get back to the default file without having to do a reinstall or search Google to find the default file contents. ;))

---

### Post by wildmanne39 on 2013-08-25
Boab1993 no I am not an expert with booting issues, I mainly work with wireless issues these days.

---

### Post by Boab1993 on 2013-08-25
@mcduck

Thank you, ill remember that for future thoughts before diving in to problems.

@Wild Man

Ah. Well either way, you have more experience than i do, can never go wrong with asking for a bit of insight. Thank you anyway

---

### Post by ash772 on 2013-08-26
@Wildman Yes i tryied the nomodeset option, in this case too nothing  starts (either fans or HD) and it displays: "cannot allocate resource  for eisa slot" 1 2 3 etc... thats why i was trying the acpi off option.

Anyway the pc owners just told me that even with windows xp, he was unable to put it  in sleep mode. Its maybe an hardware/bios issue after all.

Thanks to all again for answering even with the bugs its a pleasure to see such a reactive community.

Edit: I tryied again with the nolapic boot option and it worked too, but i'm still unable to edit the grub file to make the change permanent. I think i'm close to an end here.

---

### Post by Quackers on 2013-08-26
You can't edit the grub file? Do you mean /etc/default/grub? 
Please paste the contents of /etc/default/grub file in your next post and state which boot options you wish to make permanent.

---

### Post by ash772 on 2013-08-26
I dont understand why **sudo update-grub **dont work anymore. I'm the only user registered so i have admin rights by default, right? Does this command is supposed to ask the password?

Havent seen your msg, will do.

---

### Post by Quackers on 2013-08-26
It will normally ask for the password, yes. What does it do?

---

### Post by ash772 on 2013-08-26
The grub update command dont ask me the password like other commands do.

Heres my grub file thats i want to be updated. (a reboot grub still displays "quiet splash" instead of the "nolapic")

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nolapic"
GRUB_CMDLINE_LINUX="nolapic"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by Quackers on 2013-08-26
Were there no other entries in the 
GRUB_CMDLINE_LINUX_DEFAULT=
line? Or have you deleted them?

And what happens when you run sudo update-grub ?

---

### Post by ash772 on 2013-08-26
i have deleted the "quiet slash"

When i run sudo update-grub, no password is asked and the monitor close himself. And at reboot the grub is still on "quiet splash" mode (i've also tryied with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic". Same result.

---

### Post by Quackers on 2013-08-26
Woah! Something is wrong there. Running sudo update-grub should ask for your password and then show certain lines of text which represent the operating systems installed and end with the word done.
It certainly shouldn't close the monitor! Do you mean it closes the terminal window or does it make the screen go black?

---

### Post by ash772 on 2013-08-26
only closes the terminal window.

---

### Post by Quackers on 2013-08-26
I have not heard of that before. Something is definitely wrong if update-grub closes the terminal window.
Sadly I have no idea what that might be.

---

### Post by ash772 on 2013-08-26
Ok thanks for your time, i will reinstal xp for now. Ubuntu seems fine throught, i will try it on one of my pc.

Is there a "closed tag" to add to the post?

Bye

---

### Post by Quackers on 2013-08-26
You could mark the thread as solved using thread tools near the top of the page but as it isn't solved I'd probably leave it.

---

### Post by ash772 on 2013-08-26
ok

---

