---
title: "Sony Ericsson W810i mp3 issues."
date: 2007-05-08
forum: General Help
---

### Post by guitarmaniac on 2007-05-08
I recently bought a Sony Ericsson W810i and its a great phone. 
It's one of the most feature filled phones I've used. However its not perfect.
My only drama is that when I copy music over to the MP3 folder so I can listen to it on the phone it sometimes freezes, won't unmount properly and when I play the music all the tags must be read incorrecly, eg Killswitch Engage becomes Killswitch E.
If I have muliple songs by the same band the bands name may be read differently for different songs, so not only is there Killswitch E but theres Killswitch En and Killswitch Eng.

Anyone know of a fix for this problem?

---

### Post by tcdrewiv on 2007-05-08
I'm having the same problem under feisty.  The phone is perfect... the problem is feisty.  With dapper and edgy I could right click the desktop icons, select eject and the file transfer would finish perfectly.  With feisty file transfer to the w810i phone card is incomplete. There is no eject option, only unmount.  When you use the unmount option you will get ify file transfer.  I have this same problem on 3 other installations of feisty. one clean and two upgrades.

I can sudo eject /media/PHONE and files transfer to the phones internal memory works fine.
When I sudo eject /media/PHONE CARD it will not eject.

There a numerous threads to problems with ejecting usb devices and others.(The workaround relating to moving the fdi file in hal does not solve this problem.)

Hopefully there will be a fix where you can properly eject the device as in edgy and dapper.

---

### Post by guitarmaniac on 2007-05-09
I don't think its Feisty specific as it did the same thing in Edgy for me.

---

### Post by SuperAndy on 2007-08-31
is there any chance of this being fixed in gutsy? because bluetooth is slow as hell, and doesn't really have the functionality that USB does

---

### Post by cub on 2007-10-01
I have the same trouble with my W880i. If someone find a way to make this work I sure would like to know.

---

### Post by guitarmaniac on 2007-10-01
I've found that the mounting system in KDE is a bit better.
Still not 100% though.
Once you've copied the songs to your phone, try playing them in a media player before unmounting.
Seems to work for me.

---

### Post by cub on 2007-10-02
I'm starting to suspect it's the phone itself fault. I've tried to move songs to it from Ubuntu as well as Windows. In Windows either with file drag'n'drop (as suggested on the Sony Ericsson page) and the Disc2Phone app. The same result. However if check the files or play them from my computer everything looks fine, but playing or looking for an artist using the phone I get the naming problem.
So I called Sony Ericsson support. Of course they had never heard of ANYONE else ever having this problem. And it couldn't be the phone since it "impossible for the phone to change the ID3-tag". I try to explain the ID3-tag is untouched but the phone doesn't seem to be able to read it correctly.
So. They tell me to update the firmware in my phone (standard reply anybody?). I'm surprised they didn't ask me to reboot. ;)
Anyway it turns out my firmware is very old. Strange since I updated this summer, but the firmware is from January. I try to update and is told by the phone that I already have the latest version. Another call to support who answer "try again".

Not buying a Sony Ericsson next time.........

---

### Post by phoochka on 2007-10-02
I have a W810i for more than a year now and have no problems in Windows. But in ubuntu (7.04) a lot of my usb powered removable drives just dont un-mount, they keep saying files need to be written even if I have _just_ plugged them in. 
I bought a 2gig Mem Stick Pro Duo of ebay which can get in my laptops MS/SD slot (with the help of an adapter) and thats how I do most of my mp3 transfers now. 

Tags in the phone do bug sometimes but its usually fixed after a restart. I would guess that newer phones with better software would fix this.

---

### Post by OliverN on 2007-10-02
> **tcdrewiv said:**
> I'm having the same problem under feisty.  The phone is perfect... the problem is feisty.  With dapper and edgy I could right click the desktop icons, select eject and the file transfer would finish perfectly.  With feisty file transfer to the w810i phone card is incomplete. There is no eject option, only unmount.  When you use the unmount option you will get ify file transfer.  I have this same problem on 3 other installations of feisty. one clean and two upgrades.

I can sudo eject /media/PHONE and files transfer to the phones internal memory works fine.
When I sudo eject /media/PHONE CARD it will not eject.

There a numerous threads to problems with ejecting usb devices and others.(The workaround relating to moving the fdi file in hal does not solve this problem.)

Hopefully there will be a fix where you can properly eject the device as in edgy and dapper.

Instead of

```
$ sudo eject /media/PHONE CARD
```

do

```
$ sudo eject /media/PHONE*CARD
```

This worked fine for me :)

---

### Post by tgalati4 on 2007-10-02
I've had a w810i since Dec 06 and I've experienced a few problems as well.  I'm using a SanDisk 4GB card.  I get strange pops between tracks.  This seems to be consistent with others' experience and it's a firmware issue that will not be fixed.

The unmounting issue:  

>sudo umount '/media/PHONE CARD'

Apple issued a fix that works in Tiger OS X so that ejecting either PHONE or 'PHONE CARD' will eject both.

I don't think Linux can handle an external USB device that has multiple mounts--it treats each USB connection as a single device.  So always remember to umount PHONE and just pull the cord--but wait to make sure all of your data is written.  This can take longer than Nautilus will indicate.

I have not had ID3 tag problems but realize that their are 3 or 4 flavors of ID3 (ID3V1, ID3V2.2, ID3V2.3, ID3V2.4 with Unicode Charset).  Depending on what ID3 tag editor that you are using, you will get a different result.  Banshee uses something different than Easytag and GTKPod.  Tags edited in one do not show up properly in the other.  Avoid using XMMS to edit tags, it tends to screw them up.

So:

When describing the ID3 issue, it's helpful to mention the complete music file path before being dumped to the phone.  How the file is processed with affect its ID3 tag and thus the phone may have issues reading it.

Overall it's a good phone, but Sony's support is lacking.

---

### Post by Inigo Montoya on 2007-10-02
i had/have exactly the same two problems as described above:
[LIST=1]
[*]unmounting the phone after copying stuff on it broke sometimes causing the transfered files to only be partially copied
[*]ID3 tags were not consistently shown in the mp3 playing app of the phone
[/LIST]
i really like the phone so i searched for some workarounds:
[LIST=1]
[*]i bought a cheap usb card reader to transfer the files. it works way faster than transfering the files by connecting the phone with the usb cable.  mounting/unmounting works quite reliablly too.
[*] there is a small thread that discusses the id tag issue [here]("http://www.se-world.info/thread.php?threadid=165020&highlight=titeln.unvollst%E4ndig") (sorry german...). they suggest [jtagger]("http://dronten.googlepages.com/jtagger") for editing the mp3's id tags. i used KDE's file property dialog for editing so i switched to jtagger which solved the problem (i "updated" all ID tags - see jtagger).
[/LIST]
greetings

---

### Post by linux phreak on 2007-10-16
Hi i have a se w810i as well.I did not find any problems during file copying but an irritating(to me) thing is that there is no progress window showing the actual transfer of files and i am often left guessing the time taken to complete the task.Is there any way to enable it or is fiesty lacking such a feature

---

