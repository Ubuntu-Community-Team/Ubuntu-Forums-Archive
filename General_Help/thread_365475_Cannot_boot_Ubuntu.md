---
title: "Cannot boot Ubuntu"
date: 2007-02-19
forum: General Help
---

### Post by liviubero on 2007-02-19
Hy,
I have two problems:
The first one is that I try to download from the Ubuntu website the server version but all I get is always the desktop version. Is there actually a difference between the two? Or should I just install the desktop version and then a Lampp? As I understood from the site, the is this server flavour with a server included (Lampp).

Second:
I installed Ubuntu on a laptop and I like it a lot.
But now, when I try to boot from the same cd or even from a new burned one, I get only the progress bar and then a black screen with the followin message:

[COLOR="Blue"][17179699.960000] Buffer I/O error on device hda, logical block 1
Buffer I/O error on device hda, logical block 2
[/COLOR]
And then after a few minutes the list goes on with logical block 3 and so on.

Why is that? I have no idea how to go further.
I have a
[COLOR="SeaGreen"]Pentium 4 2,80Ghz
512 Ram
a lot of disk space and a
Radeon 9100 IGP graphics card (on bord).[/COLOR]
On the disk there is only one partition, with Windows on it. Windows is set up with a login password.
Could this password be the problem?
I can disable the login screen, but the administrator pass I cannot disable (I should then reinstall Windows, which should not be the way to do things).

Please, anyone can help?

---

### Post by alyoung on 2007-02-19
It sounds like a hard drive physical error, unfortunately.

Best get a second opinion, though.

---

### Post by pgilmon on 2007-02-19
I don't understand very well your problem:

Are you trying to install ubuntu or have you installed it already? You say that you have installed it but then you say something about booting from a CD...

---

### Post by liviubero on 2007-02-20
I installed it, but on another PC.
On this PC, it doesn't even want to boot.
I have no idea why. I don't think that the hard disk is damaged somehow.
I tried with other Linux distros, but it is alway the same.

Could it be an interfering of the Windows?
And what's with the server edition? I tried to download it but I get the desktop edition: ubuntu-6.10-[COLOR="DeepSkyBlue"]desktop[/COLOR]-i386

---

### Post by liviubero on 2007-02-20
I removed any windows user passwords and Ubuntu doesn't boot.
I get crazy.
Does anyone have any idea?

---

### Post by liviubero on 2007-02-21
Hey,
No one has any idea why I cannot boot Ubuntu?
I really need help.

It is about a computer who already has windows on it, with only one partition. I would love to install (not only to boot) Ubuntu on this computer, but unfortunately I cannot even boot Ubuntu.

---

### Post by kellsens on 2007-02-21
Hi livubero !

   You have windows installed and you are trying to boot from a live cd ?
   That's it ?

Kellsens

---

### Post by liviubero on 2007-02-21
Yes.
I do have Windows installed. And I try to boot from the live cd. My aim is to install Ubuntu on this computer, I mean to make a dual-boot system with XP, but I cannot get Ubuntu booted.
I only get those errors.
And I have no idea what they mean.

---

### Post by kellsens on 2007-02-21
Hi liviubero,

   Well, the problem it's not with the passwors on your installed windows. Did you use this same CD to install ubuntu in other machine ? If so, are you having some problem with your windows before ? Cause if you're having, it could be some hardware problem. 

Kellsens

---

### Post by liviubero on 2007-02-22
The CD is ok. I just installed Ubuntu on another machine and is working (I am just using it right now). With Windows I didn't had any problems, just with Windows Installer.
What does it mean logical drive 0?
And why should I have any problems with the hard disk drive if Ubuntu doesn't need the hard disk in order to boot?

And where do I find the Server Edition of Ubuntu? On the web site I just find the desktop edition.
On the machine on which I cannot boot Ubuntu and also on other machines I use, I have installed Xampp for Windows.
Could I just install Xammp in Ubuntu?
Does anone tried to install it?
I mean... perhaps I don't need any server edition, I just install Xampp for Linux.

---

### Post by kellsens on 2007-02-22
Hi liviubero !

    I look for some thread like yours in Launchpad support and foun this [https://answers.launchpad.net/ubuntu/+ticket/3451](https://answers.launchpad.net/ubuntu/+ticket/3451) , maybe this can help you with your problem

Kellsens

P.S.: Sorry my english...

---

### Post by liviubero on 2007-02-24
So... should I understand that no one knows what that error message is? Because I don't want to wait anymore for replies.
But thanks sincerely to all who answered.
I just installed Ubuntu on one more machine and it works great. I am becoming in fact a great fan of Ubuntu, but I would love to know if that kind of error is a hardware error or what?
The cd I used is ok.

---

### Post by JohnPhys on 2007-02-24
Do you get the errors when you try to boot to windows on the laptop, or from the ubuntu livecd on the laptop?  It's possible that hda (the drive you're getting the errors from) is the cdrom drive, and that your disk might be bad (even though it installed fine elsewhere).

If you can boot windwos fine, then it's *probably* not a hard drive issue.  You might want to download the ubuntu image again, run an md5sum check on it, and make sure to burn it to a cd at the slowest speed your burner will go at.

---

### Post by liviubero on 2007-02-24
The cd is OK.
I already installed two times Ubuntu with this CD. I also used that application on booting "check the cd for errors" or something like this and got no errors.
On my laptop, I didn't got any errors. Only on the comp whose configuration I gave at the beginning. And on that one Windows works fine.
I think that the hard disk of that comp is broken somehow.  I abandon that ship. I don't know anymore what to do.
That last thing, if I don't get any other suggestions, is to try to boot a windows cd. If this doesn't work also, then.... either I have a MBR virus, or.. the disk is about to die.

---

### Post by JohnPhys on 2007-02-24
So, on the one computer, windows boots fine, but the livecd won't?

---

### Post by pgilmon on 2007-02-24
You can also try the solution suggested by kellsens, but substituting "pci=noacpi" with "acpi=off" (I mean, follow the instructions on kellsens's link but with those changes).

---

### Post by liviubero on 2007-02-25
JohnPhys:
Yes, that's right.
Windows boots alright and have only a few windows-installer problems with it.
Only the live cd doesn't boot.

And, as what the other methods, with that F6 thing, it is not clear to me.
You know, I am really a newbie.

One more thing:
Even when I try to check the cd for errors, from within the main boot menu, (which menu is the only thing that appears), I get the same errors.

Bios recognizes the hdd alright.

---

### Post by liviubero on 2007-02-25
I just tried what kellsens and pgilmon suggested and namely:
at boot menu press F6
then write:
[COLOR="Green"]acpi=off ide=nodma ide=reverse[/COLOR]
enter
and I only got a black screen. Ubuntu seamed to boot, but then it just friezed in a black screen.
I tried to press ctrl alt backspace but the comp beeped a few times and then Ubuntu showed me the exit screen (shuting down).

Other suggestions?

---

### Post by JohnPhys on 2007-02-25
What kind of windows-installer problems?

Also, is it a sata or ide hard drive?  If it's an ide hard drive, can you tell us whether it's on the primary or secondary controller?  You can find this info in the bios if you're not sure where to look.

---

### Post by liviubero on 2007-02-26
Some hp software is not installing correctly. And also I cannot uninstall a some hp software.

The bios shows this data about the hard disk:

[COLOR="Green"]Primary IDE Master   :[HL-DT-ST DVDRAMGS]
Primary IDE Slave    :[Not Detected]
Serial ATA Master     :[ST3160827AS][/COLOR]

>>>That is, it is a sata disk

This is uneditable:

[COLOR="Blue"]Device: Hard Disk
Vendor: ST3160827AS
Size: 160.0 GB
LBA Mode: Supported
Block Mode: 4
Async DMA: MultiWord DMA-2
Ultra DMA: Ultra DMA-6
Smart Monitoring:Supported[/COLOR]

This is editable:

[COLOR="Blue"]Type                                        [Auto]
LBA/Large Mode                        [Auto]
Block (Multi-Sector Transfer) M   [Auto]
PIO Mode                                  [Auto]
DMA Mode                                 [Auto]
SMART Monitoring                      [Auto]
32Bit Data Transfer                   [Disabled][/COLOR]

---

