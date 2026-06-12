---
title: "GRUB2 menu not displayed"
date: 2023-01-04
forum: General Help
---

### Post by daanheuvelbeuk on 2023-01-04
My new system has 'fast boot' in its UEFI booting it ultra fast to Windows11. This means it is almost impossible to choose to boot into Ubuntu. I am now so far I have configured my UEFI to first boot Ubuntu on my Kingston SSD, and as second choice boot Windows boot manager on the Kingston SSD. I thought to be able to choose between Ubuntu and Windows in the Grub menu, but that is not shown. I boots directly to Ubuntu. Now I have a difficult to boot Windows.

According to grub-probe my GRUB2 is installed on dev/sdb3. That is the WD harddrive containing my Ubuntu installation. Do I understand correctly that my GRUB2 should be on the Kingston SSD so I can use the Grub menu to choose what OS to run?

---

### Post by tea for one on 2023-01-04
The UEFI setting of Fast Boot can be disabled.
It will simply boot the OS configured to boot as priority.
Jump into UEFI settings and disable it.

You previously asked this question here [https://ubuntuforums.org/showthread.php?t=2481709&p=14122195#post14122195](https://ubuntuforums.org/showthread.php?t=2481709&p=14122195#post14122195)

---

### Post by yancek on 2023-01-04
If you have both windows and Ubuntu on the same SSD and they are both UEFI, you should not have a problem booting them from Grub.  Do you have a chainloader entry for windows in the /boot/grub/grub.cfg file?

>  Do I understand correctly that my GRUB2 should be on the Kingston SSD so I can use the Grub menu to choose what OS to run? 		 

Grub has files in different locations.  On an EFI install, there will be grub files on the EFI partition as well as in the /boot/grub directory of the system partition where Ubuntu is installed.  I'm not sure from your post if you have both Ubuntu and windows on the same drive (SSD)?.

---

### Post by grahammechanical on 2023-01-04
You say this:

> I have configured my UEFI to first boot Ubuntu on my Kingston SSD

But you also say this:

> According to grub-probe my GRUB2 is installed on dev/sdb3. That is the WD harddrive containing my Ubuntu installation

Do you have two installs of Ubuntu? One Ubuntu on a Kingston SSD and one Ubuntu on a WD hard drive? 

> I boots directly to Ubuntu.

If you can boot into Ubuntu, which Ubuntu is it? If it is the Ubuntu on the Kingston SSD then run this command and see what the printout shows and if that fixes the problem.

```
sudo update-grub
```

If that gives you a Grub menu with Ubuntu (on SSD), Windows and Ubuntu (on WD hard drive) then load into the Ubuntu on WD hard drive and update the OS and then run 

```
sudo update-grub
```

In this way if the boot priority is set to the SSD you should get a Grub boot menu and if it is set to the WD hard drive you should also get a Grub boot menu that will offer to load every OS including Windows

Regards

---

### Post by ajgreeny on 2023-01-04
Something else you can do is follow the instructions in my signature below for **Boot-Repair** to run the Boot-Info-Script.	 **Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more detailed information about the boot system of your computer.

It is used to diagnose problems of dual boots where it is impossible to boot one of the two OSs that should be available from grub.  I am no expert in reading and understanding these reports but some other forum members most certainly are and may be able to figure out your problem in detail.

---

### Post by daanheuvelbeuk on 2023-01-07
> **grahammechanical said:**
> You say this:
<SNIP>
Do you have two installs of Ubuntu? One Ubuntu on a Kingston SSD and one Ubuntu on a WD hard drive?


No. I have one installation. I thought I was talking about installing the grub2 menu script to the SSD.

> **ajgreeny said:**
> Something else you can do is follow the instructions in my signature below for **Boot-Repair** to run the Boot-Info-Script.     **Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more detailed information about the boot system of your computer.


You can find the pastebin on [https://paste.ubuntu.com/p/Bq45vWfDwB/](https://paste.ubuntu.com/p/Bq45vWfDwB/)

Let me lay out my problem again. My new system (one SSD, and 2 HD's from my old sytstem, one containing Ubuntu) boots without a splash screen so I do not know when to press the appropriate key (F11 to choose where to boot from, F12 to change the BIOS/UEFI settings). By putting my system to sleep I can boot the old OS, but have a hart time switching to the other system. Yesterday I had my system configured to boot the SSD with Windows, I changed that in the BIOS to boot from the HD/sdb, and had a hard time booting to Ubuntu. During boot I saw the Ubuntu splash screen on my right terminal. After boot the left terminal which should display the Ubuntu log in screen stayed black. I finally got it working again by pulling the plug for my right terminal.

What I was hoping for by choosing to boot from the HD was that a Grub2 menu would show, which would let me choose which OS to start. But most of the times I see no Grub2 menu during boot.

Do I make sense?

---

### Post by tea for one on 2023-01-07
> **daanheuvelbeuk said:**
> My new system (one SSD, and 2 HD's from my old sytstem, one containing Ubuntu) boots without a splash screen so I do not know when to press the appropriate key (F11 to choose where to boot from, F12 to change the BIOS/UEFI settings)
Did you disable Fast Boot in the UEFI settings?

If you have, then:-
Power off the PC.
Only have your main monitor connected.
Power on and _immediately_ tap (at one second intervals) the F11 or F12 dedicated key.
Any luck?

---

### Post by tea for one on 2023-01-07
Next question:-
Line 5 - Windows 7/8/10/11/2012 is installed in the MBR of /dev/nvme0n1
Line 19 - /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 

These two lines allude to the Windows installation.
Line 5 indicates that it is a legacy installation (although no mention of legacy in the boot-repair report).
Line 19 displays the Windows boot file for UEFI installation.

Can you boot into Windows and double check?
System Information > System Summary > BIOS mode > UEFI?

---

### Post by tea for one on 2023-01-07
Notwithstanding my earlier comments/questions, your Grub2 menu needs a little alteration:-

Can you boot into Ubuntu, open a terminal and enter:-
```
sudo nano /etc/default/grub
```
Replace hidden with menu
```
GRUB_DEFAULT=0
[s]GRUB_TIMEOUT_STYLE=hidden[/s]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
```
sudo update-grub
```
Does Grub appear when you boot your Ubuntu disk?

---

### Post by maglin2 on 2023-01-07
Sorry to intrude - but should 
sudo nano /etc/defaultgrub
be
sudo nano /etc/default/grub

---

### Post by tea for one on 2023-01-07
> **maglin2 said:**
> Sorry to intrude - but should 
sudo nano /etc/defaultgrub
be
sudo nano /etc/default/grub
Yes, it should.
Thank you - I'll change it now.

---

### Post by daanheuvelbeuk on 2023-01-09
I hate a system that boots in a different way seemingly on a whim. This morning waking up my computer my keyboard did not work. I rebooted, and was surprised by the GRUB menu appearing. Just now, after reading your posts, and making some notations, I booted, and was presented with a black window. Only after the third reboot Ubuntu started, without a GRUB menu.This is frustrating!

So I can not answer your questions. The only thing I can tell is that I commented the line with:
```
GRUB_TIMEOUT_STYLE=hidden
```

Edit:
I rebooted, and got black terminals a few times. At one try I got a GRUB menu, booted Windows, and could not answer if my Windows is a 'Legacy installation'. I can only tell Windows 11 was installed by the company I bought the system from. In Windows, after a reboot I came in the GRUB menu, choose the option of the UEFI, and got a black terminal again. Some reboots later Ubuntu started without passing the GRUB menu.

---

### Post by MAFoElffen on 2023-01-09
These are the lines I add and/or change on almost all Ubuntu Installs I do (and I have done over 3000 installs of Ubuntu Linux alone)...
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]---[/COLOR] splash"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]## UnComment next line to enable OS Prober
GRUB_DISABLE_OS_PROBER=false[/COLOR]
## More...

```
If you have questions on any of that, just ask me...

Another option for GRUB_TIMEOUT_STYLE is countdown...

---

### Post by daanheuvelbeuk on 2023-01-10
> **MAFoElffen said:**
> These are the lines I add and/or change on almost all Ubuntu Installs I do (and I have done over 3000 installs of Ubuntu Linux alone)...
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]---[/COLOR] splash"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]## UnComment next line to enable OS Prober
GRUB_DISABLE_OS_PROBER=false[/COLOR]
## More...

```
If you have questions on any of that, just ask me...

Another option for GRUB_TIMEOUT_STYLE is countdown...

Thanks all for the input. After the change suggested by @MAFoElffen I rebooted my system twice and was presented by a GRUB2 menu twice. So, based on n=2 this problem is licked (famous last words?).

---

### Post by ajgreeny on 2023-01-10
Great news! 
Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction.
It is a great help to other users searching the forum.

---

### Post by daanheuvelbeuk on 2023-01-11
Sorry to say, I am looking to much at a black terminal window after reboot, requiring me to reboot until I see an OS booting. I now boot to a black terminal, directly to Ubuntu, or to the GRUB2 menu. ;'-|

---

### Post by MAFoElffen on 2023-01-12
I don't understand your last post. Is this 'Solved' or is there a problem?

---

