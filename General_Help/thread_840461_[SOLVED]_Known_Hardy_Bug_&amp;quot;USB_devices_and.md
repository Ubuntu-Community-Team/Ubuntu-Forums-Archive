---
title: "[SOLVED] Known Hardy Bug: &amp;quot;USB devices and permissions&amp;quot;"
date: 2008-06-25
forum: General Help
---

### Post by Cotopaxi on 2008-06-25
System: Kubuntu 8.04
Printer: Brother MFC-5440CN connected via USB.

Under Gutsy, I was proposed an upgrade to Hardy, which I accepted, and everything went fine.

But, after a few system updates, I could not print anymore!

The printer is recognized by the printer manager, but when I want to print a test page nothing happens. When I go to &#8220;System Settings&#8221; - &#8220;Printers&#8221; and choose &#8220;Add Printer/Class&#8221;, the &#8220;Add Printer Wizard&#8221; comes up and, on the second screen, the clickable option &#8221;Local printer (parallel, serial, USB)&#8221; is just whitened out, so I can't choose it.

I have been dealing for over a fourtnight with this problem and I have been reading everything I could within these forums and, after reading in "Known Hardy Bugs" - "USB devices and permissions" I am sure that:

1) I am not the only one who has this problem,
2) The same bug could also be affecting network printers (although they are, logically, not USB connected).

Now to the point: I read the Bug Description and the Workaround, but I am an absolute beginner in Kubuntu and I do not understand HOW TO DO IT.

Can anyone please give me a "tutorial for dummies"? :cool:

Thanks.

P.S.: This is a duplicate post of [http://ubuntuforums.org/showthread.php?t=838440]("http://ubuntuforums.org/showthread.php?t=838440")

I apologize, but I do positively believe that whatever comes out of this will not only help me, but many others who have similar problems!

---

### Post by chandra on 2008-06-26
You could try these steps:

1. See if the printer has been stopped for any reason, and if so, restart it. Go to

System Settings -> Printers

select the printer and right click on it. If it has stopped, start it again and see if that works.

2. If the printer is set as default, deselect it, remove it, and reinstall the printer, again  using System Settings. Be sure you know which driver to use before you remove the printer, though. 

Caveat: If you are uncomfortable with this option, do not try it.

---

### Post by Cotopaxi on 2008-06-26
Chandra, I will defintelely give it a try, I will report back, as soon as I went through your instructions.

Thanks!

---

### Post by Cotopaxi on 2008-06-27
Chandra, Thanks for your effort to help.

Actually, after following through your steps, the situation was exactly the same: Printer is recognized, but NOTHING HAPPENS (No Printing)!

So what I did next was to re-install the drivers from the Brother Web-site, with an interesting result: In the CUPS page (localhost ) when I click on &#8220;Print Test Page&#8221; I get the following result:

&#8220; "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_16d_BROM5F423564_if0_printer_noserial": Permission denied" &#8220;.

I think, that I don't have the permission to print to the (USB) printer and I think this problem is related with the post: "Known Hardy Bugs" - "USB devices and permissions". 

The link: [http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

scroll down to the bottom, it is the second item from the bottom.

The problem is that I do not understand the instructions in the described Workaround.

Again, thanks for your help.

---

### Post by chrisccoulson on 2008-06-27
You could try temporarily disabling Apparmor for the cupsd process to see if your problem goes away. To do this, type the following in to a terminal:
```
sudo aa-complain cupsd
```

AFAIK, the 'Known Hardy bug' you refer to only affects people who have made manual changes to UDEV rules and then upgraded. It's unlikely that you're affected by it

---

### Post by plucky on 2008-06-27
> Under Gutsy, I was proposed an upgrade to Hardy, which I accepted, and everything went fine.


Have you installed the drivers for your printer again?


The **Brother** printer drivers are now in the Hardy repositories so you can open **Synaptic Package manager** and search for "brother" and you will find the drivers.

For your printer you need to install "brother-cups-wrapper-extra" and "brother-lpr-driver-extra".

After those are installed,then add the printer in Cups.


Good Luck

---

### Post by Cotopaxi on 2008-06-27
chrisccoulson:

I did "complain" and nothing happens, the result after printing a test page in CUPS: "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_16d_BROM5F423564_if0_printer_noserial": Permission denied"

Plucky:

When I was following Chandra's advice, I installed via synaptics,which actually caused the printer to become a "text only" printer, but without printing anything.

After that I tried with the drivers from the Brother webpage.

The Brother Link, should anyone want to have a look at:

[http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

Again, Thank you guys very much indeed for you help!

---

### Post by editrix on 2008-06-27
> **Cotopaxi said:**
> "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4f9_16d_BROM5F423564_if0_printer_noserial": Permission denied"

First off, have you checked that you're included in the printer group? Have a look at:
Control Centre/System Administration/User Management. 

While you're at it, add yourself to *all* the groups. You never know when you may need it, and it can't hurt.

---

### Post by Cotopaxi on 2008-06-27
Editrix, thanks for the tip!

I did already add myself to all the groups, allthough I do not know what most of the gropus mean! :lolflag:

Let's just recap 3 things:

1) The printer worked perfectly well under Gutsy,
2) After updating to Hardy it also worked perfectly well until...
3) ...until I made a few system updates with the update manager.

Thanks again, Editrix.

PS: Whatever the update manager proposes to update, I normally accept it, because I am not routined enough to know if something is worth updating or not.

---

### Post by Cotopaxi on 2008-06-27
This is eventually interesting:

When I open Open Office, it opens up perfectly, I can do everything whithin Open Office (EXEPT PRINTING) but, when I close Open Office, the KDE Crash Handler delivers the following message:

"The application unknown (soffice.bin) crashed and cuased the signal 11 (SIGSEGV).

In the "Backtrace window" I have the following:

"[Thread debugging using libthread_db enabled]
[New Thread 0x7f9a1cbfd780 (LWP 10187)]
[New Thread 0x42bd8950 (LWP 10210)]
[New Thread 0x40dfb950 (LWP 10188)]"

...."(No debugging simbols found)"

"[KCrash handler]
#5  0x00007f9a18e3096d in _XFreeExtData () from /usr/lib/libX11.so.6
#6  0x00007f9a18e3d570 in _XFreeDisplayStructure () from /usr/lib/libX11.so.6
#7  0x00007f9a18e2990f in XCloseDisplay () from /usr/lib/libX11.so.6
#8  0x00007f9a0f409c8a in qt_cleanup () from /usr/lib/libqt-mt.so.3
#9  0x00007f9a0f485e05 in QApplication::~QApplication ()
   from /usr/lib/libqt-mt.so.3
#10 0x00007f9a1077ac91 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#11 0x00007f9a1077a303 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#12 0x00007f9a0ee6d9da in X11SalData::DeleteDisplay ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#13 0x00007f9a0ee6dc44 in X11SalData::~X11SalData ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#14 0x00007f9a1077a293 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#15 0x00007f9a0ee7ca9e in X11SalInstance::~X11SalInstance ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#16 0x00007f9a10780683 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#17 0x00007f9a1c764676 in ?? ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#18 0x00007f9a1c5270be in DeInitVCL ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#19 0x00007f9a1c527895 in ?? ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#20 0x00007f9a1c5279d5 in SVMain ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#21 0x00000000004267dd in main () "

Is this any useful hint?

PS: The smilies are letter combinations, which are interpreted by the browser as smilies.

---

### Post by editrix on 2008-06-28
> **Cotopaxi said:**
> I did already add myself to all the groups, allthough I do not know what most of the gropus mean!

You have to think of your computer as both a server and a desktop computer. The reason you can do many amazing things in Linux (like multiple desktops) is that it thinks it's a server. That means you need a sysadmin, and that's **root**. It's **root** who decides who can do what--print, scan, etc--and that's what it means when you add yourself to a group.

> 1) The printer worked perfectly well 
3) ...until I made a few system updates with the update manager.

So it was an update. Actually, I suspect it was more than one update. Which kernel are you using?

> PS: Whatever the update manager proposes to update, I normally accept it, because I am not routined enough to know if something is worth updating or not.

I'm on dialup, so almost never update unless something's broken. Sometimes, that's a good thing.:)

> **Cotopaxi said:**
> 
When I open Open Office, it opens up perfectly, I can do everything whithin Open Office (EXEPT PRINTING) but, when I close Open Office, the KDE Crash Handler delivers the following message:

"The application unknown (soffice.bin) crashed and cuased the signal 11 (SIGSEGV).

soffice.bin I *think* has to do with their macros, and therefore *maybe* Java.


> In the "Backtrace window" I have the following:

"[Thread debugging using libthread_db enabled]
[New Thread 0x7f9a1cbfd780 (LWP 10187)] ... 

Oh boy. Way beyond me. But it looks like library problems. Maybe some conflict?

But let's try the easy things first:

If you still have an earlier kernel listed in Grub, try booting with that. Some things may have been overwritten so it may not help. But it won't hurt to try.

Second, I see this a.m. there are yet more updates and a new version of the -19 kernel. So you could try updating again.

In either case, it won't necessarily work automatically. You may have to reinstall the printer (but, I hope, not OpenOffice).

Best of luck, and keep in mind it's not usually this complicated. Hardy is not the best version of (K)Ubuntu ever issued. :(

---

### Post by Cotopaxi on 2008-07-01
Editrix,

I tried to list older kernels with 

```
dpkg --list 'linux-image*'
```

and this was the output:

||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-2. <none>         (no description available)
ii  linux-image-2. 2.6.22-14.52   Linux kernel image for version 2.6.22 on x86
ii  linux-image-2. 2.6.24-16.30   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-17.31   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-18.32   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-19.34   Linux kernel image for version 2.6.24 on x86
ii  linux-image-ge 2.6.24.19.21   Generic Linux kernel image
==============================================

The question is: how do I boot with an older Kernel? On this computer Kubuntu is the only OS and I don't know if any Grub is installed.

PS: thank you for your reply and sorry for my late reply, but I was on a trip.

---

### Post by editrix on 2008-07-01
> **Cotopaxi said:**
> Editrix,

I tried to list older kernels with 

```
dpkg --list 'linux-image*'
```

and this was the output:

||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-2. <none>         (no description available)
ii  linux-image-2. 2.6.22-14.52   Linux kernel image for version 2.6.22 on x86
ii  linux-image-2. 2.6.24-16.30   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-17.31   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-18.32   Linux kernel image for version 2.6.24 on x86
ii  linux-image-2. 2.6.24-19.34   Linux kernel image for version 2.6.24 on x86
ii  linux-image-ge 2.6.24.19.21   Generic Linux kernel image
==============================================

The question is: how do I boot with an older Kernel? On this computer Kubuntu is the only OS and I don't know if any Grub is installed.


Hmm. If you use Grub, it gives you a choice of kernels, so it's just a question of using the arrow key to choose the one you boot with. Sorry, I don't know how to get grub to give you a menu on boot--because for me, it always just shows up. You may have to research it.

I *think* you just listed the kernels available, not the ones you actually have installed. The dpkg man page says:
>  -l, --list [COLOR="Red"]package-name[/COLOR]-pattern...
         List packages matching given pattern.
     -L, --listfiles package-name...
             List files [COLOR="Red"]installed[/COLOR] to your system from package-name

I'm lazy and always use "locate" to find things. 

 ```
which grub
```
Should give you
```
/usr/sbin/grub
``` If Grub is installed.

This must be a nightmare for you.

Did you do the other things I suggested?

EDIT: You might want to install  startupmanager and see if that can give you a grub menu. It's in the repositories.

---

### Post by Cotopaxi on 2008-07-01
> **editrix said:**
> 
This must be a nightmare for you.

Did you do the other things I suggested?

EDIT: You might want to install  startupmanager and see if that can give you a grub menu. It's in the repositories.

About the nightmare, you see, I gave Windows the boot in order to free myself from the Microsoft slavery, but this problem is so tremendous, I actually never had it in the worst Windows system! ;)

Yes, I did all the other things you suggested.

I installed the starupmanager and I am actually able to reboot with an older kernel right now, but it still is not changing anything.

Hell, this is actually quite an interesting journey! :cool:

Again editrix, Thanks very much indeed for your help!

---

### Post by editrix on 2008-07-02
It's not that I'm abandoning you, but we've reached the limit of any knowledge I have.

At this stage, I'd start a fresh thread--maybe even in Absolute Beginners, since that's even more a melting pot for problems than General Help is.

Write a post that states your problem, then all the steps you've taken so far, as in 
Step 1
Step 2

Make sure to say you tried the workaround they talk about in the sticky.

You don't need to say things like you installed startupmanager, but you should say you've tried different kernels.

And, do remember, it's really not usually this bad/complicated. Good luck!

---

### Post by Cotopaxi on 2008-07-02
Editrix,

I will follow your advice on Monday, I am now on a trip.

Again, thank you very much indeed for your help and effort!

---

### Post by Cotopaxi on 2008-07-14
Ok, I finally managed to solve this one! (After 4 weeks!!:cool:

The link that brought me to the solution:

"http://kubuntuforums.net/forums/index.php?topic=3089184.0"


Essentially what I did was:
in the directory /etc/udev/rules.d/

the file "40-permissions.rules" I modified the text under "#Printers and Parallel diveces" to the text listed below:

# Printers and Parallel devices
SUBSYSTEM=="printer", OWNER="lp", GROUP="lp"
SUBSYSTEM=="ppdev",         GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*", MODE="0660", OWNER="lp", GROUP="lp"


Now, I would like to file a Bug Report on this one. Can anyone tell me how to do this?

To finish:

Editrix, thank you very much again for your help!

---

### Post by Cotopaxi on 2008-07-14
Sorry, How do I mark this post as solved? Thanks!:)

---

### Post by moore.bryan on 2008-07-15
this "fix" doesn't solve anything for me... it would seem hal/udev is still not even acknowledging my usb printer is connected!

---

### Post by Cotopaxi on 2008-07-17
Bryan,

I will give you intructions to perform one check, but my system is Kubuntu, so you will have to tranlate these instructions to your system.

In Main Menu>System Settings>Printers, click on "Add new Printer/Class".

Now click through, until you reach the window "Backend Selection", where you can choose the way the printer is connected. From the list of clickable items, there is one called "Local printer (parallel, serial, USB). Is this item CLICKABLE, or is it GRAYED OUT?

We will then start from there.

---

### Post by moore.bryan on 2008-07-17
@cotopaxi:
thanks, but i finally "solved" the issue. for whatever reason, the ehci-hcd and ohci-hcd modules weren't playing nicely together, but forcing the uhci-hcd module on-boot worked fine... thanks for your offer of assistance!

---

### Post by Cotopaxi on 2008-07-18
You are welcome, I am glad it got solved! :)

---

### Post by moore.bryan on 2008-07-18
as am i!!!
;-)

---

