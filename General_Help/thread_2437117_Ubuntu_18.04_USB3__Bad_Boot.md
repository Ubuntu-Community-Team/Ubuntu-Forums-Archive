---
title: "Ubuntu 18.04 USB3  Bad Boot"
date: 2020-02-18
forum: General Help
---

### Post by box02-0 on 2020-02-18
Hi.                                                                                                                                                       Feb.18.2020

I want to make a bootable USB stick containing a copy of my Live Ubuntu 18.04 which resides on an internal SSD in my desktop.

I booted an older USB2 stick containing Ubuntu 14.04, and:
    Gparted formatted a 256gb USB3 stick with a 160gb ext4 partition.
    Copied my Live Ubuntu 18.04 to the 160gb partition on the USB3 stick.
    Changed the UUID of the USB3 stick to match the UUID of my Live Ubuntu 18.04 (tune2fs).
    Copied (dd) the first 446 bytes of the USB2 stick to the USB3 stick.

I BIOS disabled the SSD, and tried booting the USB3 stick– nothing.

I booted the older USB2 stick, ran boot-repair and ‘reinstalled GRUB’ and then ‘Restored MBR’ on the USB3 stick.

Again, I tried booting the USB3 stick. This time I got into Grub Rescue:
    I did a Set Prefix=(hd0,msdo1)/boot/grub, set root=(hd0,msdos1), insmod normal,  & normal.
    And it booted!!

I selected Ubuntu and up comes the Ubuntu screen with the flashing red dots. After several seconds I heard my speakers click, and all looked aok. The problem is it kept looping – the Ubuntu red dots cycled and the LED on the USB3 stick was flashing. I waited 10 minutes and then the Ubuntu red dots stayed ON (no longer cycling), but the LED on the USB3 stick continued to flash.

Figuring that perhaps there was a bad copy of the Ubuntu 18.04 on the USB3 stick, I once again copied my live Ubuntu 18.04 onto the USB3 stick -  with the same results.

I think that I created the Ubuntu 14.04 USB2 stick with an ISO file. I don’t want to do this for the USB3 stick as I want it to be a Live copy of my Ubuntu 18.04. I can’t make an ISO of my live Ubuntu as it would way exceed 4gb.

I’ve run out ideas and steam. Any help would be greatly appreciated.

Thanks,
M...

---

### Post by dragonfly41 on 2020-02-18
My intuitive approach would be to just boot into original LiveUSB and then use mkusb in LiveUSB session to create a new (second) LiveUSB on the second device.
But perhaps I'm missing something here?

---

### Post by box02-0 on 2020-02-18
Hi.
I will investigate mkusb and see if it will allow me to make a bootable usb installing my live ubuntu 18.04 and let you know.

Thanks for the prompt reply,
M...

---

### Post by DuckHook on 2020-02-18
I've read your post twice now and still don't understand what you are trying to do. Perhaps it would help if you tell us what your end goal is—what you are trying to achieve. I don't understand why you are going through the trouble of copying, dd-ing, fiddling with partitions, etc. Nor do I understand what role the obsolete and EoL 14.04 stick is playing in your efforts.

The usual methodology to create a "Live" USB is to choose this option from the ISO during the installation process. This installs a read-only system partition on your USB stick for the OS itself, then a separate R/W partition that allows the installation of additional apps, data, etc.

If, on the other hand, what you are really looking for is ***not*** a "Live" USB but rather a fully functioning install on your USB stick, then simply choose the full system install option and your USB stick will behave like a SSD/HDD with a full standard system on it. Note that performance will suffer because USB sticks combined with the USB interface is not optimal for speed, but lots of people do, indeed, successfully run such portable installations. With a fast USB stick on a USB 3.0 port, it's not that bad.

In both cases, you can copy data back and forth from your desktop to your USB stick easily.

---

### Post by box02-0 on 2020-02-18
Hi.

I'm simply trying to make my live Ubuntu work on a bootable USD.

The reason I'm using Ubuntu 14 is because it is the only bootable ubuntu I have on a USB. (I know I can make a new one from 18.04 - I just haven't bothered yet.) Since I will be playing with UUID,s I prefer to boot with an Ubuntu on a USB and not worry about duplicate UUIDS.

So once again, I have a live Ubuntu 18.04 loaded with 70+ apps that I would like to copy onto a bootable usb. Then I can use this usb to work on other systems and have all my apps. I don't know if this is even doable.

I remember that an Ubuntu ISO file is limited to 4gb. I hope I'm wrong here. If I could, I would build an iso from my live system and install it on a usb.

I've made several ssd's from my live ubuntu as backups - and I've done so using DD. However, I can't dd a 512gb ssd to a 256gb USB - or can I?

Sorry for any confusion.

M...

---

### Post by DuckHook on 2020-02-18
Okay, I think I see what your end goal is. You are not looking for a Live USB at all, but rather, you want to clone your SSD/HDD onto your USB stick.

I've never tried that, but in theory, I don't see why it wouldn't work. However, do note the following:

[LIST]
[*]It is not possible to achieve your end goal by creating a LiveUSB. A LiveUSB is a technically specific type of installation described in my previous post.
[*]Based on your comments, you also wish to avoid a full **virgin** install on a USB stick. While such an install would give you the full benefits of a typical installation without the limitations of a LiveUSB, you don't want to duplicate the effort of installing 70-odd apps and associated data.
[*]Therefore, what you are describing is a USB stick that you want to clone with the full installation already resident on your computer.
[/LIST]
Cloning is not that difficult, but you must keep the following in mind:

[LIST]
[*]The target USB stick needs to be as large as the sum of all your Linux partitions. You cannot clone a larger partition into a smaller one.
[*]You will need two USB sticks—one for your target and another on which to install a LiveUSB session so that it can act as the operating system on which to run the cloning process. It is not possible to clone a disk that is in use, which means that you cannot perform this procedure from the OS you normally boot with. It must be kept off-line.
[*]What you want to do has nothing to do with ISOs or their limitations so you need not worry about 4GB limits.
[*]It is easy to change partition UUIDs. It can be done after the cloning is complete by simply using *tune2fs* on the newly cloned USB stick.
[*]Cloning carries risks. *dd* is one method, but it isn't nicknamed "Disk Destroyer" for nothing. You may wish to consider [Clonezilla]("https://www.clonezilla.org/").
[*]Do not even think of using the 14.04 stick. It is out of support, is full of security holes and no knowledgeable user can help you with it because we have all nuked it from our system years ago.
[/LIST]
I'm afraid that any further help or advice from me will be quite limited. This is a process that I've never tried before. Perhaps someone else who has actually done this will jump in with further observations/guidance.

---

### Post by box02-0 on 2020-02-19
Hi DuckHook.

Absolutely Yes:  "You are not looking for a Live USB at all, but rather, you want to clone your SSD/HDD onto your USB stick."

I should have phrased it that way myself. My bad.

Interestingly enough I have cloned my Live Ubuntu SSD several times in the past using DD, but from SSD to SSD - never to USB. 

IMHO there seems to be some subtle differences in the boot process between a hard disk/ssd and a USB. This may be causing my looping problem.

Yes I will nuke the Ubuntu 14.04 USB - It was the only bootable Ubuntu I had on a USB and I've been too lazy to make a new one. That one was built from a 14.04 ISO a few years back. I will make a new one from an 18.04 ISO.

I will follow your procedure and report back.

Thanks for all your advice.

M...

---

### Post by box02-0 on 2020-02-22
[SIZE=2]Hi.                                                                                                                                 Feb.22.2020[/SIZE]

 [SIZE=2]I finally figured out what my problem is. The Patriot 256gB USB3 stick is BAD. When I say bad I mean extremely sloooooow. That&#8217;s why I said it was looping when I booted it as I mentioned in my opening post. [/SIZE] 

 [SIZE=2]I tried booting it again and watched it loop &#8211; then decided to go for dinner. When I got back it had actually booted. It took more than 30 minutes to boot. It wasn&#8217;t looping, just slow.[/SIZE]
 [SIZE=2]
A simple test on the Patriot USB3 (Disks &#8211; benchmark Partition) clearly showed that it was bad. Fortunately Amazon will be refunding me.[/SIZE]
 [SIZE=2]
So here is what I did on another USB3 stick:[/SIZE]
 [SIZE=2]1. Booted with an Ubuntu USB (built from an 18.04 ISO after nuking the 14.04).[/SIZE]

 [SIZE=2]2. Gparted formatted (ext4) the USB3 stick with the Partition size of my Active Ubuntu.[/SIZE]
 
 [SIZE=2]3. DD 1[SUP]st[/SUP] 446 bytes (MBR) of my Active Ubuntu to the USB3:[/SIZE]
 [SIZE=2]    sudo dd if=/dev/sda of=/dev/sdc bs=446 count=1 [/SIZE] 
 
 [SIZE=2]5. Gparted copy my Active Ubuntu onto the USB3 ext4 partition. (Note the UUID remains the same as the      Active Ubuntu.)[/SIZE]
 
 [SIZE=2]I BIOS disabled the SSD where my Active Ubuntu resides, and booted the new USB3. Slow, but it&#8217;s all there. Mission accomplished![/SIZE]
 
 [SIZE=2]A learning process for me. Thanks for all your input. [/SIZE] 
 
 
 [SIZE=2]M&#8230;.[/SIZE]

---

### Post by DuckHook on 2020-02-22
Glad you finally found a way. Your solution is interesting. I would probably not have done things the way you did, but it works for you and that's what's important.

Cheers and Happy Ubuntu-ing!

---

