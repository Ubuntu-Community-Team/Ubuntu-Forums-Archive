---
title: "Help save me from smashing my ipod w/ a sledgehammer!"
date: 2007-04-23
forum: General Help
---

### Post by zacinator on 2007-04-23
Over the last week ... i've read just about every post on ipods and have tried everything but to no avail.

First, let me tell you what i wanted to do.  I wanted to rip the files off my ipod so i could end all dependencies on MS and then erase windows on my laptop and have ubuntu on both my PC and laptop.  Sounds simple enough.
I first tried copying w/ gtkpod, yamipod, banshee, amarok.  The most any of them did was yamipod copyed one song.  
Then I tried copying in terminal.  Most I got was 1 songs.  I end up with...
[PHP]cp: cannot stat `Music/The Juliana Theory': Input/output error[/PHP] for every directory after the first 4 or 5.

So I tried Nautilas.  I copied my music onto my ipod thinking i'd use it as an external hd.  Then I hit copy and attempted to paste it in my home dir.  This resulted in the most succes.  60 files (still 1200 more to go).  Oh and typically i would have to restart my comp everytime i wanted to connect.  After a while it will finally say

[PHP]Error, "I/O error", while, copying...[/PHP]

On top of all of this my battery which charges great with other things (wall outlet, car charger, other computers), pretends to charge with ubuntu but seems to do the opposite.  It acts like its charging, but a fully charged ipod dies after about 3 hours of being plugged into my usb (which should be charging).

My fstab looks like this:
[PHP]/dev/sda2 /media/ipod vfat user,iocharset=utf8,umask=0000 0 0[/PHP]

Any ideas would be awesome!!!

---

### Post by tgalati4 on 2007-04-23
Post the output of:

lsusb -vv

Your USB port probably has a current limit and the IPod trips it then stops delivering power.  Thus your IPod doesn't get charged.  That might also explain the copying problems because the IPod quickly goes into play mode from USB/Mount mode and thus the file system can't see the files to copy.

Examine:

dmesg | tail

for any errors that might come up.

I routinely transfer 4 to 6 GB of music from my IPod Mini using GTKpod without problems.    It creates the database faithfully enough that I can see the music on my powerbook (using iTunes) as well.  You must format it and register it with iTunes first however.

If your iPod was formatted under Windows, then I can't speak for how it will react.

---

### Post by zacinator on 2007-04-23
This is from lsusb -vv
[PHP]Bus 003 Device 002: ID 05ac:1203 Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x1203 
  bcdDevice            0.01
  iManufacturer           1 Apple
  iProduct                2 iPod
  iSerial                 3 00000086B9B2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
[/PHP]

Last night I had a mini breakthrough...  I plugged it directly into the back of the computer instead of through the extension and it copied a new record of 369 files(of 2200)!  I also think it charged Then this:
[PHP]zac@zac-desktop:~$ dmesg | tail
[17227.304000] FAT: Directory bread(block 16063221) failed
[17227.304000] sd 0:0:0:0: rejecting I/O to offline device
[17227.304000] FAT: Directory bread(block 16063222) failed
[17227.304000] sd 0:0:0:0: rejecting I/O to offline device
[17227.304000] FAT: Directory bread(block 16063223) failed
[17227.308000] sd 0:0:0:0: rejecting I/O to offline device
[17227.308000] sd 0:0:0:0: rejecting I/O to offline device
[17290.608000] sd 0:0:0:0: rejecting I/O to offline device
[17290.608000] Buffer I/O error on device sda2, logical block 16458720
[17290.608000] lost page write due to I/O error on sda2
[/PHP]

This was formatted with windows...
Any new ideas?

Thanks

---

### Post by ashz on 2007-04-23
this could have something to do with it...who knows..

[http://www.linuxquestions.org/questions/showthread.php?postid=1197015#post1197015](http://www.linuxquestions.org/questions/showthread.php?postid=1197015#post1197015)

Disable CONFIG_EFI_PARTITION (File Systems -> Partition Types ->
Advanced Partition Selection -> EFI GUID Partition support) in your
kernel configuration, recompile.

cheers ash

---

### Post by BoneKracker on 2007-04-23
I've tried a bunch of different applications and have had the best luck with gtkpod.

---

### Post by tgalati4 on 2007-04-23
Well, here's what we know:

Your iPod is dutifully detected by the USB subsystem.  Your dmesg errors seem to indicate that the iPod is going off line.

In a terminal:

dmesg | more

Use the spacebar to scroll through the messages and q to quit.  We need to see the errors higher up in the file.  Tail only gives you the last few lines.

How is the battery life on this iPod?  Is it new, or do you only get an hour of play time before the battery quits?

If the battery is bad (high internal resistance, or shorted, or just old) then it will draw more current than normal.  This could trip up the USB hardware by limiting current and your iPod gets confused and goes to offline mode.  The iPod (most anyway) is an 80 MHz, dual-ARM9 processor--it's a computer that does its own thing.  It only communicates via USB or Firewire, and if it is not happy, it will behave the way it wants regardless of what it is connected to.

The fact that you can download different numbers of files seems to indicate that the transition to offline occurs at different times.  Although it could be the sector problem described in the link above, to me it sounds like a battery/power/USB problem.

Let us know what finally works.

Good luck.

---

### Post by Smuve on 2007-04-23
Not sure if you have done this already, but if you still have windows and iTunes somewhere, make sure the box is checked to -> manage songs manually.  It's easy to overlook and I read somewhere that this will solve many iPod + Linux annoyances.

---

### Post by zacinator on 2007-04-23
Thanks so much for all your suggestions... i will try them out when i get home!

@ ashz - That sounds very simular to my problem!  Hopefully that works for me!

@ tgalati4 - My ipod is a used 4th generation 20 gb i got on ebay around Christmas time.  The battery is certainly not the greatest and sometimes is fluky, but i can typically get 4 hours of continous play.  Last night i think i might have gotten it to charge by plugging it directly into my usb instead of through my extension cable (which perhaps doesn't carry current??).  It also goes offline randomly sometimes.  I'll post the dmesg results when i get home..

@ Smuve - I don't think i have that checked!  I hope it could be that simple!

---

### Post by zacinator on 2007-04-23
Success! Sort of haha.

Well I feel like an idiot for not seeing the checkbox that Smuve suggested about manually handling files.  I feel like more of an idiot for not seeing the use as hard drive check box!

After doing that it copied 1800 files before going offline...  This probably is where tgalati4 is probably right about my ipod being faulty.  Could also be the suggestion that ashz suggested.  But instead of starting over I just unmounted and mounted again then copied the other 400.  However, it froze about every 4 - 10 songs because it probably wasn't designed as a harddrive.  

Well hopefully I can now use ubuntu for all my ipod needs and finally put an end to windows at home.

Thank you all for all your help!

---

### Post by tgalati4 on 2007-04-23
IPods are normally pretty reliable.  Mac folks sometimes make a snapshot of their OS (Tiger) and use it as a backup boot device (through Firewire only).  

Since you bought this on ebay, it's history is unknown.  

On a Mac, you can use Disk Utilities and run Verify to see if there are disk errors.

You can also run sudo fsck /dev/whateveryourdeviceshowsupas  If it was formatted as FAT then it may detect errors.  If it was formatted as HFS (Mac system) then you will either need a Mac to check it or try finding fsck.hfs to check it.

You could have an internally shorted battery that doesn't allow pulling full current.  My iPod mini sometimes behaves strangely and it is due to the weak battery not being able to deliver stable current.  

Linux has a low tolerance for faulty hardware--especially harddisks and memory.

Due to wear-and-tear, you may need to reformat the iPod and start fresh, or you can simply delete all the files and use GTKPod to refill it.

iPods are normally pretty reliable, except for batteries, water intrusion, cracked screens when sitting on them, sand intrusion, dropping on concrete, going through the wash, anything else?

---

### Post by BoneKracker on 2007-04-24
I apologize if someone already addressed this.

If you're not already doing so, make sure you're plugging in as directly as possible to you USB subsystem and that you are using a powered USB port that is not also powering other devices.  If you computer has multiple USB hubs internally, use the one that has the least power load on it.

---

