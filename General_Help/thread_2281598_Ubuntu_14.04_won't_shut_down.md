---
title: "Ubuntu 14.04 won't shut down"
date: 2015-06-08
forum: General Help
---

### Post by zoidberg2 on 2015-06-08
I have installed Ubuntu 14.04 on my Desktop & have encrypted the hard drive, when I reboot the computer I have no issues but when I try to shut it down it hangs on the page where it is stopping services. It hangs on this screen for hours & doesn't power, does anyone have any ideas as to what my issue is. 

My uneducated hunch is that there is an issue with the disk encryption as it says FAIL next to it. 




[IMG]http://i57.tinypic.com/msyi47.png[/IMG]

---

### Post by Aidan_St.Louis on 2015-06-08
This website can help as long as you know to how use the terminal. [http://askubuntu.com/questions/460095/ubuntu-14-04-not-shutting-down-completely](http://askubuntu.com/questions/460095/ubuntu-14-04-not-shutting-down-completely)

---

### Post by QDR06VV9 on 2015-06-08
> **zoidberg2 said:**
> I have installed Ubuntu 14.04 on my Desktop & have encrypted the hard drive, when I reboot the computer I have no issues but when I try to shut it down it hangs on the page where it is stopping services. It hangs on this screen for hours & doesn't power, does anyone have any ideas as to what my issue is. 

My uneducated hunch is that there is an issue with the disk encryption as it says FAIL next to it. 




[IMG]http://i57.tinypic.com/msyi47.png[/IMG]
can you post back the contents of 
```
gksu gedit /etc/default/grub
```
Regards

---

### Post by zoidberg2 on 2015-06-11
[FONT=Liberation Serif][SIZE=3]I ran this command to update [/SIZE][/FONT]

[FONT=Liberation Serif][SIZE=3]sudo apt-get update && sudo apt-get upgrade [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]and it updated the system. [/SIZE][/FONT]

[FONT=Liberation Serif][SIZE=3] I then tried to shut down from the terminal trying these commands [/SIZE][/FONT]

[FONT=Liberation Serif][SIZE=3]sudo shutdown now[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]then[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]sudo init 0[/SIZE][/FONT]
 


 [FONT=Liberation Serif][SIZE=3]However the same thing happens though and it just stalls on the screen I posted a picture above. [/SIZE][/FONT] 


[FONT=Liberation Serif][SIZE=3]This is the contents of the gksu gedit /etc/default/grub file [/SIZE][/FONT]


 [FONT=Liberation Serif][SIZE=3]# If you change this file, run 'update-grub' afterwards to update[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# /boot/grub/grub.cfg.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# For full documentation of the options in this file, see:[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#   info -f grub -n 'Simple configuration'[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]GRUB_DEFAULT=0[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_HIDDEN_TIMEOUT=0[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_HIDDEN_TIMEOUT_QUIET=true[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_TIMEOUT=10[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]GRUB_CMDLINE_LINUX=""[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# Uncomment to enable BadRAM filtering, modify to suit your needs[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# This works with Linux (no patch required) and with any kernel that obtains[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# Uncomment to disable graphical terminal (grub-pc only)[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_TERMINAL=console[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# The resolution used on graphical terminal[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# note that you can use only modes which your graphic card supports via VBE[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]# you can see them in real GRUB with the command `vbeinfo'[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_GFXMODE=640x480[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_DISABLE_LINUX_UUID=true[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# Uncomment to disable generation of recovery mode menu entries[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_DISABLE_RECOVERY="true"[/SIZE][/FONT]
 

 [FONT=Liberation Serif][SIZE=3]# Uncomment to get a beep at grub start[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]#GRUB_INIT_TUNE="480 440 1"[/SIZE][/FONT]

---

### Post by QDR06VV9 on 2015-06-11
I almost forgot all about you.
Find the line"[FONT=Liberation Serif][SIZE=3]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
And Comment that out by putting # in front so it would look like this "#[FONT=Liberation Serif][SIZE=3]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off""
Without the Quotes of course. And just below that line add this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios"
```
Save and then update Grub
```
sudo update-grub
```
Hopefully you should be able to reboot and shutdown again,
Cheers[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by zoidberg2 on 2015-06-11
Thanks alot that sorted my problem, I can shut down without any issues now, so what was my issue? 

Thanks again.

---

### Post by QDR06VV9 on 2015-06-11
It was just that grub entry more or less making other things fighting to do other things.(Or Lost in the Loop)
That's my story and I'm sticking to it.):P
But the Important thing is you got sorted out YEAH!!
Good Job
Kind Regards

---

