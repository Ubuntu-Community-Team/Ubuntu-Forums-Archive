---
title: "[SOLVED] Help! Changed GRUB settings, can't login!"
date: 2008-06-25
forum: General Help
---

### Post by drjonze on 2008-06-25
Hello,

I went into Start Up manager under Administration and I changed the settings to only display 1 kernel, I just wanted to clean up the Grub menu. The problem is that I have kernel 19 which I use and kernel 19 RT which I was advised to try for another problem I was having. The RT kernel freezes my system at the splash screen so I can't login. Now the only option I have in the GRUB menu for Ubuntu is the RT kernel! How can I get back to 19 and change the setting back?!?!?

ubuntu hardy amd 64

---

### Post by hariprs on 2008-06-25
Did you try login using recovery mode?

---

### Post by drjonze on 2008-06-25
Yes. I have RT and RT recovery and both just freeze my pc at the splash page.

Can I open a terminal from the GRUB screen? Is there a command I can run to boot the 19 generic kernel?

---

### Post by VMC on 2008-06-25
> **drjonze said:**
> Yes. I have RT and RT recovery and both just freeze my pc at the splash page.

Can I open a terminal from the GRUB screen? Is there a command I can run to boot the 19 generic kernel?

Hit the ESC key when you see the Grub message. Then you will see all the selections. If that's what you were asking. Also you can use the 'e' to edit inside the Grub menu, then go back and use the 'b' for boot.

---

### Post by drjonze on 2008-06-25
> **VMC said:**
> Hit the ESC key when you see the Grub message. Then you will see all the selections. If that's what you were asking. Also you can use the 'e' to edit inside the Grub menu, then go back and use the 'b' for boot.

I esc and I still only get the options to login into kernel rt (and rt recovery)and both freeze my PC. I need loginto kernel 19 generic.


I had that option before I changed the setting on how many kernels to display in Start Up Manager.

What I am asking is how to I boot into kernel 19 generic if its not list on GRUB?

---

### Post by drjonze on 2008-06-26
Bump. Help!

---

### Post by mcduck on 2008-06-26
Boot into recovery mode, run "nano /boot/grub/menu.lst", undo the changes you made & hit ctrl-x to exit (select 'yes' when nano asks you if you wish to save the file). Then run 'reboot' to restart the machine.

---

### Post by drs305 on 2008-06-26
If kernel 19 is still on your machine, I think you can run:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
sudo update-grub
```
which will restore the kernel 19 option. I don't know if it overrides the 'display option 1' or not but it's an easy try.

Read about 'update-grub' by typing 'man update-grub' in terminal.

---

### Post by drjonze on 2008-06-26
> **mcduck said:**
> Boot into recovery mode, run "nano /boot/grub/menu.lst", undo the changes you made & hit ctrl-x to exit (select 'yes' when nano asks you if you wish to save the file). Then run 'reboot' to restart the machine.

I can't boot in at all. I only have the options of kernel 19 RT and RT recovery and when I boot either option, my system freezes.

---

### Post by drjonze on 2008-06-26
> **drs305 said:**
> If kernel 19 is still on your machine, I think you can run:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
sudo update-grub
```
which will restore the kernel 19 option. I don't know if it overrides the 'display option 1' or not but it's an easy try.

Read about 'update-grub' by typing 'man update-grub' in terminal.

I can't login so I can't access a terminal.

---

### Post by drs305 on 2008-06-26
Assuming the 19 kernel is still installed:

Boot to the livecd.
Open a terminal.
Run the following (replace /dev/sdaX with your ubuntu partition):
```

sudo mkdir /temp
sudo mount **/dev/sdaX** /temp
sudo cp /temp/boot/grub/menu.lst /temp/boot/grub/menu.lst-bak1
sudo gedit /temp/boot/grub/menu.lst

```

Find the line that says:
```
# howmany=1
```
and change it to:
```
# howmany=all
```

Save, close, and reboot.

If there are other settings which you may have changed and you would prefer, you can post the results of your menu.lst here and we can check it.

---

### Post by drjonze on 2008-06-26
> **drs305 said:**
> Assuming the 19 kernel is still installed:

Boot to the livecd.
Open a terminal.
Run the following (replace /dev/sdaX with your ubuntu partition):
```

sudo mkdir /temp
sudo mount **/dev/sdaX** /temp
sudo cp /temp/boot/grub/menu.lst /temp/boot/grub/menu.lst-bak1
sudo gedit /temp/boot/grub/menu.lst

```

Find the line that says:
```
# howmany=1
```
and change it to:
```
# howmany=all
```

Save, close, and reboot.

If there are other settings which you may have changed and you would prefer, you can post the results of your menu.lst here and we can check it.

Thanks, I will give this a try. I just have to thimngs to clarify:

-When you say 'boot to the live cd', do you mean to run ubuntu from the disc, right?

- I don't know what you mean when you say "replace /dev/sdaX with your ubuntu partition". Would I be typing something like "/dev/sda04" or whatever number my ubuntu partition is? Am I just replacing the letter 'X'?

Sorry, I am a complete noob, I know very little about computers and even less about linux. I'm in a little over my head here.

---

### Post by drs305 on 2008-06-26
> **drjonze said:**
> Thanks, I will give this a try. I just have to thimngs to clarify:

-When you say 'boot to the live cd', do you mean to run ubuntu from the disc, right?

- I don't know what you mean when you say "replace /dev/sdaX with your ubuntu partition". Would I be typing something like "/dev/sda04" or whatever number my ubuntu partition is? Am I just replacing the letter 'X'?

Sorry, I am a complete noob, I know very little about computers and even less about linux. I'm in a little over my head here.

Yes, booting from the LiveCD is running ubuntu from the disk.

Your ubuntu system is located on a specific partition on your computer. If you don't know which one it is on, when you boot into ubuntu from the LiveCD, run "sudo fdisk -l"  (small L) and it will list your partition information. You should see something like:

```
/dev/sda8           30288       38191    63488848+  83  Linux
/dev/sda9           38192       38913     5799433+  82  Linux swap / Solaris

```

In this example, my linux system is located on /dev/sda8. So you would put "/dev/sda8" in place of "/dev/sdaX". Note it could also say "**h**daX", in which case that is what you would enter.

Just keep asking questions until we get it fixed. :)

If just changing the "howmany" line doesn't work (preferred), here is another way to get your kernel 19 option back. Copy and paste this into menu.lst, putting it just above the kernel 19RT lines. You will have to change 2 things: the (hd1,0) entry and the UUID number. Copy them from what is listed in the 19RT entry.  You can also get the UUID by running yet another command - "sudo blkid": 
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		**(hd1,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=**cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccdx** ro 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		**(hd1,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=**cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccdx** ro single
initrd		/boot/initrd.img-2.6.24-19-generic

```

I'll just mention it here in case you get everything solved. Using StartUp-Manager was a great choice since it prevents you from messing up your grub menu. In your case, you just made an unfortunate choice of selecting to see only 1 kernel. Once you have your system working correctly, you can go back to SUM and reset the number or kernels to view (instead of "all"). Just don't select 1 ;-)  For more information on options available in SUM, here's a link:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by drjonze on 2008-06-26
> **drs305 said:**
> Yes, booting from the LiveCD is running ubuntu from the disk.

Your ubuntu system is located on a specific partition on your computer. If you don't know which one it is on, when you boot into ubuntu from the LiveCD, run "sudo fdisk -l"  (small L) and it will list your partition information. You should see something like:

```
/dev/sda8           30288       38191    63488848+  83  Linux
/dev/sda9           38192       38913     5799433+  82  Linux swap / Solaris

```

In this example, my linux system is located on /dev/sda8. So you would put "/dev/sda8" in place of "/dev/sdaX". Note it could also say "**h**daX", in which case that is what you would enter.

Just keep asking questions until we get it fixed. :)


Thank you, my friend! I truly believe the best part of ubuntu is the community - there's always someone glad to help. 

I remember seeing my partitions before and they do start with the letter 'h'. I will try this out, I feel confident I know what I'm doing now. I am at work so I won't be able to try it until later tonight. I will let everyone know how it goes.

---

### Post by drs305 on 2008-06-26
I've added some more to my last post since you responded so just read through it again for some additional information. 

If it works, please mark it solved with the thread tools. If it doesn't, come on back and we'll keep working on it until we get it fixed.

---

### Post by drjonze on 2008-06-26
> **drs305 said:**
> 

Just keep asking questions until we get it fixed. :)

If just changing the "howmany" line doesn't work (preferred), here is another way to get your kernel 19 option back. Copy and paste this into menu.lst, putting it just above the kernel 19RT lines. You will have to change 2 things: the (hd1,0) entry and the UUID number. Copy them from what is listed in the 19RT entry.  You can also get the UUID by running yet another command - "sudo blkid": 
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		**(hd1,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=**cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccdx** ro 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		**(hd1,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=**cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccdx** ro single
initrd		/boot/initrd.img-2.6.24-19-generic

```

I'll just mention it here in case you get everything solved. Using StartUp-Manager was a great choice since it prevents you from messing up your grub menu. In your case, you just made an unfortunate choice of selecting to see only 1 kernel. Once you have your system working correctly, you can go back to SUM and reset the number or kernels to view (instead of "all"). Just don't select 1 ;-)  For more information on options available in SUM, here's a link:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")


I'm back up and running! The 19 generic kernel is back. I actually had to use the second option as the first one didn't do it. I only had the 19 RT kernel in the file (even though I also have 16,18,19) so I think it only had one option to choose from. I just copied and pasted the RT kernel info just below it and changed all the 'rt's to 'generic'. When I rebooted generic was there. I went into start up manager and restored my original settings. All was fine when I rebooted again.

Thank you for your help and your patience!! :)

---

