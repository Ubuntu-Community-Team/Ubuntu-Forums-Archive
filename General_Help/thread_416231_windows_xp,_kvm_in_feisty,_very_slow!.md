---
title: "windows xp, kvm in feisty, very slow!"
date: 2007-04-20
forum: General Help
---

### Post by justDIY on 2007-04-20
Machine:
Compaq nc6320 notebook
Core Duo T2500 processor (with VT support)
1gb ram
80gb 7200 rpm hdd

Host OS:
Fresh install of Feisty Desktop i386
All the kvm related tools installed with synaptic

Guest OS:
Windows XP Service Pack 2
6gb qcow image file created with qemu-img

I start the machine with the following command line:

kvm -no-acpi -m 384 -cdrom windowsxp.iso windows.img

The vm is very slow to boot, very slow.  I'd say about 30-45 seconds goes by after the virtual bios message clears the screen, and I get the "Windows XP" startup logo.  The screen is just black the entire time.  There is minimal hard drive activity, and both cpu cores are idle.  The logo comes up, one cpu core pegs at 100% and there is a small amount of hard drive activity.  Eventually the screen turns blue like it is about to present the welcome screen, I get a pointer that I can move around.  I'll spend another 30-45 seconds here, before I'm presented with the desktop.  Once on the desktop, the start menu opens ok, and small applications load up ok.  I haven't tried installing any larger apps or even setting up the network, since it's so darn slow.

Oh, I should mention the install took over an hour and a half.  It spent 45 min "detecting devices" before I'm even asked for the cd key.  Then another 20 min "installing networking", and another 30-45 min "installing start menu items".

I'd rather not go back to vmware server / player, since they don't like the 2.6.20 kernel, and I need this newer kernel for some other stubborn hardware.

any suggestions what I'm doing wrong?  This just seems unbelievably slow.

---

### Post by Ziox on 2007-04-20
you can try virtualbox ([www.virtualbox.org)](www.virtualbox.org)), just download and install the edgy version. It works fine on my clean feisty.

---

### Post by justDIY on 2007-04-21
thats the only suggestion, is try something other than kvm?  I'm upgrading from 6.06 and vmware server, and Windows ran very well under vmware.

I'm more interested in finding out why native hardware virtualization is running so poorly, opposed to installing another package that claims to do the same things.

---

### Post by justDIY on 2007-04-21
i do have to admit, virtbox is much faster, and I didn't have to struggle with manually patching source code to compile the kernel modules as I would have with vmware.

still curious to know what I did wrong with the native virt software, or maybe its just slow because its new?

---

### Post by finite9 on 2007-04-21
I have same issue with KVM.

Core2Duo 7200 2GB ram and nVidia 7600 512MB.

Installed kvm-16 in feisty repo and created image with qemu and it runs like a dog, but maybe not as slow as you describe.  seems mostly to be a graphics issue and hardware pointer issue.  the mouse drags along, but this is the same in VMware until you install vmware tools to support a hardware mouse pointer.  I wonder how you do the same thing in kvm?

I noticed that the gfx card in the virtual machine was cirrus logic and I could not increase resolution above 800x600.  I suspect that this cannot be changed by us mortal users, but that the devs need to add support for a gfx card that has better performance.

VMware on a much older laptop (AMD Turion64 ML-28 512MB ram) ran much much faster than kvm on core2Duo machine.

I have already enabled VT in BIOS and it *is* being used as the menu bar says QEMU/KVM, which according to someone on the kvm dev mailing list is how to determine if kvm is being used.

---

### Post by Tomy on 2007-04-22
I had the same experience installing Windows XP under kvm -- it took forever. And it is soo slow I don't think it is useable.

KVM is working:
```
tomy@feisty:~$ lsmod |grep kvm
kvm_amd                17032  0 
kvm                    61148  1 kvm_amd
tomy@feisty:~$ 
```When winXP starts up I get a white screen for about fifteen seconds -- I found a post on the kvm mailing list that said this is solved with kvm-19.

I was able to change the screen resolution to 1024x 768 but the mouse drags and everything is slow.

Running the system monitor while winXP was running showed that one of my two cpu's (dual core Athlon 64 X2) was at 100% load a lot of the time. 

Any ideas?

---

### Post by Tomy on 2007-04-22
I found this link in an old Feisty forum post and followed the instructions. Seemed to help a little but mostly everything is the same.

Edit: Actually, it runs much better. I set the display to 16bit color and that seemed to help. The mouse is jerky/sticky -- there must be some workaround for his -- I'll keep looking.
________________________________________________

[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)
**Working around a slow Windows virtual machine due to ACPI**

 If your Windows installation is set to use ACPI (this is the default), kvm can be quite slow. This is due to Windows heavily using a register that has a very large virtualization penalty. 
Fortunately, there is a simple workaround available: disable ACPI support in Windows.  The procedure for doing this is:[LIST=1]
[*]Select "My Computer" with the right mouse button.
[*]Select "Properties".
[*]Choose the "Hardware" tab.
[*]Click the "Device Manager" button.
[*]Select the entry under "Computer" with the right mouse button.  If it says "Standard PC", then there's no need to do anything.
[*]Select "Properties"
[*]Click the "Update Driver" button.
[*]Choose "Not at this time" and clock "Next".
[*]Choose "Install from a list" and click "Next".
[*]Choose "Don't search" and click "Next".
[*]Click "Next".
[*]Choose "Standard PC" and click "Next".
[*]Continue clicking "Next" and reboot the virtual machine.[/LIST]

---

### Post by berserker on 2007-04-22
> **Tomy said:**
> I found this link in an old Feisty forum post and followed the instructions. Seemed to help a little but mostly everything is the same.

Edit: Actually, it runs much better. I set the display to 16bit color and that seemed to help.

Setting colors to 16 bit and selecting Standard PC really helped.  Thank you!

---

### Post by Tomy on 2007-04-22
I solved the sticky/jerky mouse problem by using the virtual usbdevice. This also stops kvm from "grabbing" your mouse. Here is my current startup script. Full screen is toggled with <ctrl><alt>f. 

```
#!/bin/sh
kvm -no-acpi -full-screen -usb -usbdevice tablet \
-hda /home/tomy/kvm/winXP.img \
-cdrom /dev/cdrom \
-boot c \
-m 1024
```I only need winXP for a few apps and don't care what it looks like -- so I tuned it for performance: ControlPanel->System->Advanced(tab)->PerformanceSettings(button)->VisualEffects(tab)->AdjustForBestPerformance
This gives you the old classic look without visual effects and it feels more responsive.

---

### Post by Tomy on 2007-04-22
Success:)

I have Compiz working with winXP on one side of the cube.

---

### Post by smartbei on 2007-04-25
Hmmmm...Thanks fir all your help guys: Still have a problem with the mouse seeming to have a refresh rate of about 5-10 times a second. This is using the usbdevice hack by Tomy.

Also, I noticed that when I ran the VM in Qemu only (rather than Qemu/kvm) it booted up faster, though performance was the same.

Since I am trying to get this up for playing a game or two, the mouse is a serious problem. Anything else that would help? Should I try virtualbox?

Thanks!

---

