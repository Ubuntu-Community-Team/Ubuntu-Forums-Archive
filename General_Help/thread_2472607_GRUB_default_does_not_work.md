---
title: "GRUB default does not work"
date: 2022-03-05
forum: General Help
---

### Post by mikeubell on 2022-03-05
I needed to downgrade to 5.10. I loaded up the files on my /boot and set /etc/default/grub to:
```
[COLOR=#000000][FONT=Menlo]GRUB_DEFAULT="gnulinux-5.10.0-051000-generic-recovery-d0309aa8-c61f-44ad-870a-273a43578bd9"
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]GRUB_TIMEOUT_STYLE=countdown[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_TIMEOUT=3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_CMDLINE_LINUX=""[/FONT][/COLOR]
```
I ran update-grub.

I can see the 3 second countdown when it boots, so I know my changes were installed in /boot.  But it still boots to 5.13 unless I interrupt GRUB and select the 5.10 release. I don't see anyway to get GRUB to say what it is doing, e.g. "verbose" or "debug".  

What next?

---

### Post by him610 on 2022-03-05
> I don't see anyway to get GRUB to say what it is doing, e.g. "verbose" or "debug".

In */etc/default/grub*. change this line 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to read > GRUB_CMDLINE_LINUX_DEFAULT="text"
Save the file then  run *update-grub* afterwards to update /boot/grub/grub.cfg

---

### Post by oldfred on 2022-03-05
Grub default has to be an exact menu entry, not a kernel. 
[https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub](https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub)
> **GRUB_DEFAULT="xxxx"** An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter.

You may need to add your own boot stanza to 40_custom.
But did not a sudo update-grub find you kernel?

cat /boot/grub/grub.cfg  | grep menuentry

---

### Post by grahammechanical on 2022-03-06
Perhaps this page from the Grub 2 manual will help get the protocol right.

[https://www.gnu.org/software/grub/manual/grub/grub.html#default](https://www.gnu.org/software/grub/manual/grub/grub.html#default)

Regards

---

### Post by mikeubell on 2022-03-06
[COLOR=#000000]*GRUB_CMDLINE_LINUX_DEFAULT="text"*[/COLOR] will show Linux boot messages, not grub.  I am trying to figure out why grub is ignoring the GRUB_DEFAULT configuration.

---

### Post by mikeubell on 2022-03-06
> **grahammechanical said:**
> Perhaps this page from the Grub 2 manual will help get the protocol right.

[https://www.gnu.org/software/grub/manual/grub/grub.html#default](https://www.gnu.org/software/grub/manual/grub/grub.html#default)

Regards

that is where I got the change I made.  Did you spot a mistake?

---

### Post by mikeubell on 2022-03-06
> **oldfred said:**
> Grub default has to be an exact menu entry, not a kernel. 
[https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub](https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub)


You may need to add your own boot stanza to 40_custom.
But did not a sudo update-grub find you kernel?

cat /boot/grub/grub.cfg  | grep menuentry

I did update-grub, as I said.  It found the kernel.  What do you mean by "add your own boot stanza to 40_custom"?  I am using what looks like the standard method to specify the default kernel.

The kernel is in /boot.  If it were not there and GRUB was trying to boot it, the boot would fail.  I verified this by removing the kernel that GRUB tries to boot.

---

### Post by oldfred on 2022-03-06
What did this show?
cat /boot/grub/grub.cfg  | grep menuentry

---

### Post by tea for one on 2022-03-06
> **mikeubell said:**
> I needed to downgrade to 5.10.

There is another way to do this.
Assuming that kernel 5.10 is the second of two kernels installed, you can try:-

```
GRUB_DEFAULT="[COLOR="#0000FF"]1[/COLOR]>[COLOR="#FF0000"]2[/COLOR]"
```

Grub counts from 0 hence GRUB_DEFAULT=0 is the first line of the Grub menu, which will boot the latest installed kernel.
The 1 in blue is the second line of the Grub menu
The 2 in red is the third option from the second line.

I have two kernels installed, therefore:-
5.13.0-30 is represented by 1>0
5.13.0-30 Recovery is represented by 1>1
5.13.0-28 is represented by 1>2
5.13.0-28 Recovery is represented by 1>3

Don't forget to run [COLOR="#0000FF"]sudo-update grub[/COLOR] after you have edited the file.

---

### Post by grahammechanical on 2022-03-06
In addition to what tea for one says, if the desired kernel is in the Grub submenu called Advanced options for Ubuntu then that submenu has to be referenced by its title in the GRUB_DEFAULT= line. That is my understanding of the instructions of the Grub 2 manual. 

Regards

---

### Post by mikeubell on 2022-03-06
> **grahammechanical said:**
> In addition to what tea for one says, if the desired kernel is in the Grub submenu called Advanced options for Ubuntu then that submenu has to be referenced by its title in the GRUB_DEFAULT= line. That is my understanding of the instructions of the Grub 2 manual. 

Regards

Ah!  I read the "6.1 Simple configuration handling" section first.  Then looking at section 15.1.10, it did not occur to me that there were submenus in the script.  A previously read "How To" just say to grep the .cfg file to find the id of the desired kernel.

Thanks all for the pointers.

---

