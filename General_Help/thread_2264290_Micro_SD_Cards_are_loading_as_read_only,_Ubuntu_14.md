---
title: "Micro SD Cards are loading as read only, Ubuntu 14"
date: 2015-02-06
forum: General Help
---

### Post by apple6 on 2015-02-06
I'm currently trying to format the SD so that I could install Deb Wheezy onto it, though I might use the NOOBs installer as it's meant to be really simple and I haven't tried it yet. It currently has RetroPie on it. 


I was trying to format and setup  the partitions using fdisk, and ran into the problems that follow. 


I've experienced similar[ish] problems earlier in the week from my phones SD card; I couldn't copy files onto it as it had been mounted as read only. This is what lead me to believe there was a fault on the computers side rather than the SD cards.


I've tried to format the SD card using [this guide]( [http://qdosmsq.dunbar-it.co.uk/blog/2013/06/noobs-for-raspberry-pi/](http://qdosmsq.dunbar-it.co.uk/blog/2013/06/noobs-for-raspberry-pi/) ) but mine seemed to bugger it at the last stage as I got the message : 


    Command (m for help): w
    fdisk: unable to write /dev/mmcblk0: Bad file descriptor
    
I think that this means the filesystem is read only, which is weird that it only popped up at the last stage, but then thats the write stage, so perhaps it makes perfect sense... 




If I grep in /dev I can see that the SD Card is there : 
    
    vco@geoHP:/dev$ a | grep mmc
    brw-rw----  1 root disk      179,   0 Feb  6 12:33 mmcblk0
    brw-rw----  1 root disk      179,   1 Feb  6 12:52 mmcblk0p1
    brw-rw----  1 root disk      179,   2 Feb  6 12:33 mmcblk0p2
    vco@geoHP:/dev$ 
    
    
And I can see that In GParted : [SD Location]([https://lh4.googleusercontent.com/gN6_xiVWjiC05WD1IAEBNt6UWSSI3rRgUA_1eJRssvfQ=w1188-h366-no](https://lh4.googleusercontent.com/gN6_xiVWjiC05WD1IAEBNt6UWSSI3rRgUA_1eJRssvfQ=w1188-h366-no)) as well as the error message GParted displays [about the file system being read only](  [https://lh4.googleusercontent.com/-vA2coIG4jO4/VNS7B5f5uqI/AAAAAAAAcOA/D3oxedU43pE/w1196-h450-no/a.png](https://lh4.googleusercontent.com/-vA2coIG4jO4/VNS7B5f5uqI/AAAAAAAAcOA/D3oxedU43pE/w1196-h450-no/a.png) ) that's the same [for both partitions]([https://lh3.googleusercontent.com/-yxYG6WE17Sw/VNS7B6M9jzI/AAAAAAAAcOE/nFqSnD1ksac/w1197-h452-no/b.png](https://lh3.googleusercontent.com/-yxYG6WE17Sw/VNS7B6M9jzI/AAAAAAAAcOE/nFqSnD1ksac/w1197-h452-no/b.png) )  


I had a similar problem with another SD Card, so I'm inclined to think that this is an issue with Linux rather than the card, that some setting has somehow been set to use SD Cards as read only... not sure how or why. (Note - the SD Card definitely isn't physically 'locked' on the Micro SD Card adaptor) 






Any advice much appreciated  ;) 


*******


edit 1 : turns out that the fat16 partition was mounted, I guess the ext4 was the only was that showed up as mounted in the finder window... not sure what difference that makes


*****


edit 2 - I repeated the fdisk steps after unmounting the other partition and got the same error message as previously. I might try just wiping in GParted. 


******
edit 3 - GParted didn't do anything differently, [similar error message]([https://lh6.googleusercontent.com/cLApz-1AV3EFpw_o2JFF3_UdC_ZUW5G-K65hjv7aC-Ut=w1158-h798-no](https://lh6.googleusercontent.com/cLApz-1AV3EFpw_o2JFF3_UdC_ZUW5G-K65hjv7aC-Ut=w1158-h798-no)). No reason why it would I guess. 


*******


edit 4 - [here's the full error message from gparted]([https://lh3.googleusercontent.com/-ZJSoxjCaGsI/VNS_IHl5QhI/AAAAAAAAcOs/0YvjGNI3fjw/w1197-h390-no/a.png](https://lh3.googleusercontent.com/-ZJSoxjCaGsI/VNS_IHl5QhI/AAAAAAAAcOs/0YvjGNI3fjw/w1197-h390-no/a.png))


*******


edit 5 - I've fount the following command [from this post]( [http://askubuntu.com/a/47547](http://askubuntu.com/a/47547) ) : 


    sudo mount -o remount,rw '/media/SGTL MSCN'


I don't really get what it's doing though, I thought that I'd be mounting something from `/dev` **to** `/media`....
    
******


edit 6 - I've just tried the following without any progress : 


    vco@geoHP:~$ sudo mount -w /dev/mmcblk0 /media/sdcard/
    [sudo] password for vco: 
    mount: block device /dev/mmcblk0 is write-protected but explicit `-w' flag given
    vco@geoHP:~$ 
    






*****


edit 8 - I tried to use `dd` on this after unmounting the SD card with the following (and similar) error : 




    vco@geoHP:/$ sudo umount /dev/mmcblk0p2 /dev/mmcblk0p1
    vco@geoHP:/$ sudo mount | grep mmc
    vco@geoHP:/$ sudo dd if=/dev/zero of=/dev/mmcblk0
    dd: failed to open ‘/dev/mmcblk0’: Read-only file system
    vco@geoHP:/$ 






*****


edit 9 - I've tried to mount the SD card from `/dev/mmcblk0` using `mount -w` but I get the following : 


    
    sudo mount -w /dev/mmcblk0 /media/sdcard/
    mount: block device /dev/mmcblk0 is write-protected but explicit `-w' flag given
    vco@geoHP:/$ 
    


********


edit 10 - [from this post here]([http://unix.stackexchange.com/questions/79309/filesystem-suddenly-read-only#comment116810_79309](http://unix.stackexchange.com/questions/79309/filesystem-suddenly-read-only#comment116810_79309)) I'm going to try and reboot the machine. 


******


edit 11 - after rebooting the SD card is still mounted as read only


*****


edit 12 - it does this for other SD cards as well, [here's GParted with a different card]([https://lh3.googleusercontent.com/-ay_Rs3BeItU/VNTskMykwmI/AAAAAAAAcPQ/ijvOIE4AJwU/w1197-h461-no/a.png](https://lh3.googleusercontent.com/-ay_Rs3BeItU/VNTskMykwmI/AAAAAAAAcPQ/ijvOIE4AJwU/w1197-h461-no/a.png))

---

### Post by sudodus on 2015-02-06
You have really tried a lot of methods to mount the SD cards.

See the last post (post #8) of this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

It looks like the cards are failing with the *gridlock* symptom, but there could be some bad hand-shaking between the UEFI/BIOS system or operating system and the card reader or some firmware, so that good cards cannot be read.

I suggest that you try to format the SD cards in another computer (with Windows or MacOS) and in a camera or mobile phone. That way you might separate a problem with the cards from a problem with the systems in the computer and/or the card reader.

---

### Post by apple6 on 2015-02-06
Thanks. Although I can't be 100 percent I think that lifetime is incredibly unlikely as I've tried this on 3 SD cards. One from the phone (which was kind of old) one from the Pi that had Retro Pie on it (not too old, not that used) and another one that had never been used. 


> **sudodus said:**
> 
It looks like the cards are failing with the *gridlock* symptom, but there could be some bad hand-shaking between the UEFI/BIOS system or operating system and the card reader or some firmware, so that good cards cannot be read


Never heard of this before. 

> **sudodus said:**
> 
I suggest that you try to format the SD cards in another computer (with Windows or MacOS) and in a camera or mobile phone. That way you might separate a problem with the cards from a problem with the systems in the computer and/or the card reader


I can try and format the card in Windows. I'll just go FAT32 unless there's anything else. I'm expecting this (formatting in another OS) to work, I'm not sure what the steps after that would be though. 

I'll post back when I've formatted as that's the acid test I guess. 

thanks.


EDIT - 

One scenario I hadn't considered (and don't know how to check as I'm out of SD's) is that putting the cards  into the Ubuntu machine is actually breaking them. If this was the case using them in another OS would give the impression that the fault lay with the cards. Maybe this is a bit paranoid I'm not sure whats really going on with all this ;)

---

### Post by sudodus on 2015-02-06
I have ***not*** had any problem with my Ubuntu 12.04 LTS and 14.04 LTS destroying SD cards. But before we know, it it one of the possibilities.

Good luck formatting to FAT32 in Windows :-)

---

### Post by efflandt on 2015-02-06
If you have one of the normal Raspbian images, you use dd to write the image directly to the SD or microSD device (after making sure that everything on the card is unmounted). But I have not tried that with an mmcblk device. You might try a USB card reader or computer that has internally USB connected memory card slots. That puts everything on the card including an mbr, FAT32 partition for config files, and Linux partition for everything else. Then you should either be able to expand the Linux partition with gparted, or the first time you boot it on a Pi, it will ask if you want to expand the partition to fill the SD/microSD (I have an older Pi with SD slot). The NOOBS thing is something that can be run from Windows to create the SD/microSD.

The typical Linux way: [http://www.raspberrypi.org/documentation/installation/installing-images/linux.md](http://www.raspberrypi.org/documentation/installation/installing-images/linux.md)

One thing that might be tripping you up is if the write protect tab moves when you insert the card or microSD to SD adapter. I know that I had that trouble with a microSD to SD adapter when the write protect tab was quite loose and the slot was tight.

---

### Post by apple6 on 2015-02-06
Hey - I used Windows and was able to format an SD Card.... 

Weirdly it didn't work with the Micro to regular SD adaptor that I was using, so I thought that it was that. 

But now I've booted into Ubuntu and I'm having the same problems again.... I'm really not sure what to do here, thanks

---

### Post by sudodus on 2015-02-06
I think there is some bad hand-shaking between the UEFI/BIOS system or  operating system and the card reader or some firmware, so that good  cards cannot be read (in Ubuntu).

Can the UEFI/BIOS system be updated to a newer version?

Does the card reader work with Ubuntu in another computer, another USB port, or via a USB hub?

Maybe another card reader works with Ubuntu.

---

### Post by apple6 on 2015-02-06
Thanks for your response Sudodus : 

> **sudodus said:**
> 
I think there is some bad hand-shaking between the UEFI/BIOS system or operating system and the card reader or some firmware, so that good cards cannot be read (in Ubuntu).


I'm not sure how to go about troubleshooting this to be honest. My current setup (on this laptop) is Windows 8 and Ubuntu 14 dual boot. I only use Ubuntu, windows is there because I paid for it and it's handy sometimes (this eve?!)

 > **sudodus said:**
> 
Can the UEFI/BIOS system be updated to a newer version?


Possibly - though I'm sure that I've read that isn't something that should really be done if one can help it? I would be concerned about pulling the rug from beneath the feet of both operating systems doing this. 

I've never done this before (I'm sure there are plenty of guides out there though, I'm not asking you of that). 

I'm not really understanding how this could be the problem either - as I've used SD cards with this Ubuntu version before and they have worked, the ones that I'm failing to use now are the very ones that I have used before. 


> **sudodus said:**
> 
Does the card reader work with Ubuntu in another computer, another USB port, or via a USB hub?

Maybe another card reader works with Ubuntu.

By card reader are you referring to the Micro Regular converter?  One of these : 

[IMG]http://www.digikingph.com/shop/images/tf_adaptor2.jpg[/IMG]



I think that (if this is what you mean) I've already answered this as I have used SD cards with this computer, using Ubuntu and the SD Card readers that I have. 

I didn't try the SD to USB adapter that I had previously though, I've just tried that and it doesn't work either. Exactly the same errors in GParted regarding read only file system. 


I can't convince myself that this is an Issue with anything other than Ubuntu, I'm sure it's an isolated case (as I have been using it before without issue) but still. I have no idea how to test this though, I don't know where the settings would be for such a thing and whether there's a file somewhere that has somehow had it's value to change to read only or something. 

Also regarding the catalyst for this, the only thing that I can think of is that earlier this week I took the SD from my phone without turning the phone off and put it into Ubuntu. It wouldn't let me do anything to the SD and said 'read only; etc etc... I was in a rush so didn't have time to try anything or test anything out. But that was the first time that this has happened, I'm not sure if something went wrong with me pulling the SD out of the phone which made Ubuntu lockdown SD card transfers or something mental ? I've not had any messages that imply this. 

Out of ideas, let me know what you thinks best, thank you!

---

### Post by sudodus on 2015-02-06
> **apple6 said:**
> ...
I didn't try the SD to USB adapter that I had previously though, I've just tried that and it doesn't work either. Exactly the same errors in GParted regarding read only file system. 


This is what I meant - and you have tried it now.
> 
...
Out of ideas, let me know what you thinks best, thank you!

I'm running out of ideas too, at least for your current Ubuntu system.

Obviously it works with Windows. Try another version of Ubuntu, for example Ubuntu 12.04 LTS (the original one) or 12.04.5 LTS (the final one with a newer kernel), supported until April 2017. Try it live (don't install until you know if it works).

---

### Post by apple6 on 2015-02-06
Im currently on a Lubuntu persistent stick (lubuntu 14) and I'm seeing the same error here, not sure what that say's to be honest. I'm second guessing the windows format now, but it definitely worked I took screenshots and everything. 

Very confused as to why this could happen and how. 

cheers


EDIT - Here's an image of the Lubuntu GParted error (just so we can actually see it) 

[IMG]https://lh5.googleusercontent.com/-b0F6tfY2eHk/VNU1elZ1IwI/AAAAAAAAcQA/bUdlW8SeIzA/w1597-h621-no/a.png[/IMG]

---

### Post by apple6 on 2015-02-06
Argh OK... Using a different adaptor has worked in Lubuntu (I'm pretty confused at this point...) and I have the following : 

[IMG]https://lh5.googleusercontent.com/-UA0bbyePSi8/VNU2ReOVh_I/AAAAAAAAcQM/veXsMHZl8do/w1506-h521-no/a.png[/IMG]

---

### Post by apple6 on 2015-02-06
I have both SD Cards working using this adaptor : 

[IMG]https://lh3.googleusercontent.com/XJ1WrLkwUq7lfPKJHQECXcYYCO3Knq8YRGVDz1GUEjov=w1412-h442-no[/IMG]

---

### Post by apple6 on 2015-02-06
Oh no! 

I formatted the SD Card in Lubuntu (from the USB) booted back into Ubuntu and now it's not working :/ 

[IMG]https://lh4.googleusercontent.com/-EdZ4HIOAGoc/VNU6DREtSJI/AAAAAAAAcQ8/lzoBRKmScEI/w864-h830-no/a.png[/IMG]

---

### Post by sudodus on 2015-02-07
> **apple6 said:**
> I have both SD Cards working using this adaptor : 



> **apple6 said:**
> Oh no! 

I formatted the SD Card in Lubuntu (from the USB) booted back into Ubuntu and now it's not working :/ 



Does it work if you format the SD Card in Lubuntu, and reboot into the same Lubuntu? (Can you mount it read-write?)

What are the versions of Lubuntu and Ubuntu?

---

### Post by apple6 on 2015-02-07
Hi Sudodus: 

> **sudodus said:**
> 
Does it work if you format the SD Card in Lubuntu, and reboot into the same Lubuntu? (Can you mount it read-write?)


I haven't tried this today but the fact that It loaded as read / write yesterday and enabled me to format it suggests that it will do so. I'll check again though, just to be clear on what I'm to check :
 

[LIST]
[*]Load Lubuntu up
[*]See what it mounts the SD card (read / write)
[*]Format the SD card
[*]Remove the SD card
[*]Reinsert the SD card and see if the system will allow me to write anything to it.
[/LIST]


> **sudodus said:**
> 
What are the versions of Lubuntu and Ubuntu?



Both 14, here's the Ubuntu info (I'm going to test the Lubuntu as above now so I'll post the spec from that then) : 

[IMG]https://lh5.googleusercontent.com/-XO7HunCfMLM/VNYFD_4oFpI/AAAAAAAAcRg/q3Pka0TGzFw/w1197-h666-no/a.png[/IMG]


thanks

---

### Post by apple6 on 2015-02-07
OK here's the Lubuntu version that I'm using : 

[IMG]https://lh5.googleusercontent.com/-0Iul8gVRE8U/VNYO3uH19jI/AAAAAAAAcR4/6r7O1J9sfV8/w879-h156-no/a.png[/IMG]

I have an sd card in the system and just tried to copy a test file onto it, here' the terminal output from that : 

```

lubuntu@lubuntu:~$ touch movethis.txt
lubuntu@lubuntu:~$ cp movethis.txt /media/lubuntu/8311-71FE/
cp: cannot create regular file ‘/media/lubuntu/8311-71FE/movethis.txt’: Read-only file system
lubuntu@lubuntu:~$ 
```


The SD Card is mounted as read only If i view it from GParted as well, I'm not sure if this is because I had left it in the system whilst booting out of Ubuntu and into Lubuntu.... seems like that should have been alright though. 

I'm now going to try and remove the card and reinsert it to see if that changes anything....

I have unmounted, removed and reinserted the SD card. Here is the output of mount, I'm guessing that hte `ro` at the start of the info in parens means that it's read only. 

```

/dev/mmcblk0p1 on /media/lubuntu/8311-71FE type vfat (ro,nodev,nosuid,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```

Going to open it in GParted anyway....

GParted still has it listed as being read only. 

I'm going to try unmounting it, and mounting it using the -w flag in the terminal (though I've tried this before, just for completeness) 

trying to unmount it I get this error (though theres nothing open thats using it)

```

lubuntu@lubuntu:~$ sudo umount /dev/mmcblk0p1 
umount: /media/lubuntu/8311-71FE: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
lubuntu@lubuntu:~$ 

```

So I'm going to unmount from the GUI... 

So I unmounted it, and now I have tried to mount it again using the -w flag, this is the message that I get from the terminal : 

```

lubuntu@lubuntu:~$ sudo mount -w /dev/mmcblk0p1 /media/lubuntu/
mount: /dev/mmcblk0p1 is write-protected but explicit `-w' flag given
lubuntu@lubuntu:~$ 

```

Now I'll print out the mount info : 

it's not in there, and it isn't listed as being mounted in the GUI either....



Not sure what else to do here. 


cheers

---

### Post by apple6 on 2015-02-07
I think that perhaps it's related to the way that the SD Card reader of the laptop is being handled by Linux or something, I've done the following tests : 

ro is read only rw read/write. 

USB Adaptor means that it's a USB Adaptor that takes an SD Card, which I'm putting the SD to Micro SD adaptor into. 

[IMG]https://lh3.googleusercontent.com/K70KKyB7cwbv7k9bQI2SoAsb_p9nXtVrWMfRlqtLaigS=w1197-h593-no[/IMG]

---

### Post by sudodus on 2015-02-07
Ubuntu version 14.04 LTS (released April 2014)
Lubuntu version 14.10 (released October 2014)

These are *different* versions. It seems to me that 14.04 will make the SD cards read-only.

It would still be interesting to see what happens if you make a FAT32 partition in Lubuntu 14.10 (and test that it is read-write). Then reboot into Lubuntu 14.10 (do not boot into Ubuntu). Will it still be read-write?

Or is the problem connected to booting with the SD card inserted? It should not be, but who knows?

-o-

I don't understand the list in post #23:

samsung
card 1
card 2

sandisk
card 1
card 2

but I guess this whole test was done in Ubuntu 14.04 LTS.

I suggest that you run Lubuntu 14.10, or if you don't like Lubuntu, try Ubuntu 14.10 or some other flavour. I think this is an issue of the kernel and kernel drivers, which are the same for all Ubuntu flavours (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu, Ubuntu Gnome ...) but different for different versions (14.04 LTS, 14.10 ...)

---

### Post by apple6 on 2015-02-07
> **sudodus said:**
> 
Ubuntu version 14.04 LTS (released April 2014)
Lubuntu version 14.10 (released October 2014)

These are *different* versions. It seems to me that 14.04 will make the SD cards read-only.



I didn't mean to say that they were the same, though I'm guessing you're highlighting that they can be different even though the 'main' number is the same. The thing is I have use 14.04 with sd cards previously, this is a new behaviour rather than one that has existed since I have used Ubuntu, so I'm not too sure about 14.04 making SD Cards read only. Unless you're referring to my version only (rather than a broad problem with 14.04). However, I've just Googled *ubuntu 14.04 sd card read only* and there are quite a lot of hits, so you could well be correct. Maybe I was just lucky before, hmm. 


> **sudodus said:**
> 
It would still be interesting to see what happens if you make a FAT32 partition in Lubuntu 14.10 (and test that it is read-write). Then reboot into Lubuntu 14.10 (do not boot into Ubuntu). Will it still be read-write?



Ah I didn't do this, sorry. I can do that soon. I'm sure it should work? 


> **sudodus said:**
> 
Or is the problem connected to booting with the SD card inserted? It should not be, but who knows?


I think the cards themselves are functioning alright. 

> **sudodus said:**
> 

I don't understand the list in post #23:


It's not well made sorry about that. Basically the samsung / sandisk are referring to different SD to Micro SD adaptors that I was using. 

> **sudodus said:**
> 
but I guess this whole test was done in Ubuntu 14.04 LTS.


Yeah this was all done in Ubuntu 


> **sudodus said:**
> 
I suggest that you run Lubuntu 14.10, or if you don't like Lubuntu, try Ubuntu 14.10 or some other flavour. I think this is an issue of the kernel and kernel drivers, which are the same for all Ubuntu flavours (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu, Ubuntu Gnome ...) but different for different versions (14.04 LTS, 14.10 ...)



Thanks, I guess after trying it out with Lubuntu 14.10 tomorrow I'll be able to say. I had some funky results with that in a prior post if I remember so I'm not too sure. I thought the point in LTS versions was that they supported them rather than making new versions? Perhaps I've misunderstood something, or maybe it's just security related. 

thanks!

---

### Post by sudodus on 2015-02-07
> **apple6 said:**
> [QUOTE=sudodus;13223990]
Ubuntu version 14.04 LTS (released April 2014)
Lubuntu version 14.10 (released October 2014)

These are *different* versions. It seems to me that 14.04 will make the SD cards read-only.



I didn't mean to say that they were the same, though I'm guessing you're  highlighting that they can be different even though the 'main' number  is the same. The thing is I have use 14.04 with sd cards previously,  this is a new behaviour rather than one that has existed since I have  used Ubuntu, so I'm not too sure about 14.04 making SD Cards read only.  Unless you're referring to my version only (rather than a broad problem  with 14.04). However, I've just Googled *ubuntu 14.04 sd card read only* and there are quite a lot of hits, so you could well be correct. Maybe I was just lucky before, hmm. 
[/QUOTE]
I was referring to your particular installed system, but the problem might be more general: 14.04 LTS does not work with those card-readers in combination with that kind of motherboard.

Did you see anything pointing to a bug report (when you googled *ubuntu 14.04 sd*)?
> 
> **sudodus said:**
> 
It would still be interesting to see what happens if you make a FAT32  partition in Lubuntu 14.10 (and test that it is read-write). Then reboot  into Lubuntu 14.10 (do not boot into Ubuntu). Will it still be  read-write?



Ah I didn't do this, sorry. I can do that soon. I'm sure it should work? 


> **sudodus said:**
> 
Or is the problem connected to booting with the SD card inserted? It should not be, but who knows?


I think the cards themselves are functioning alright. 

I think so too.
> 
> **sudodus said:**
> 

I don't understand the list in post #23:


It's not well made sorry about that. Basically the samsung / sandisk are  referring to different SD to Micro SD adaptors that I was using. 

> **sudodus said:**
> 
but I guess this whole test was done in Ubuntu 14.04 LTS.


Yeah this was all done in Ubuntu 


> **sudodus said:**
> 
I suggest that you run Lubuntu 14.10, or if you don't like Lubuntu, try  Ubuntu 14.10 or some other flavour. I think this is an issue of the  kernel and kernel drivers, which are the same for all Ubuntu flavours  (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu, Ubuntu Gnome ...) but  different for different versions (14.04 LTS, 14.10 ...)



Thanks, I guess after trying it out with Lubuntu 14.10 tomorrow I'll be  able to say. I had some funky results with that in a prior post if I  remember so I'm not too sure. I thought the point in LTS versions was  that they supported them rather than making new versions? Perhaps I've  misunderstood something, or maybe it's just security related. 

thanks!


In general the LTS versions are recommended. They are debugged and polished for several years, while the other versions are only supported for 9 months. But if you have problems with some hardware:

- new hardware - try a newer version: 14.10 or the version being developed, Vivid Vervet to become 15.04 in April.

- old hardware - try an older version (which means the previous LTS version, now 12.04 LTS: standard Ubuntu and Kubuntu are supported until April 2017, Lubuntu has passed end of life, Xubuntu will soon pass end of life).

It is strange that this card reader and these cards used to work in 14.04 LTS, but stopped working. Maybe it depends on the program packages that you installed via PPAs after all? Or maybe a bug appeared in 14.04 recently. You can get a user ID at [https://launchpad.net/](https://launchpad.net/) and write a bug report (unless you find a bug report, that decribes your problem. In that case, click on 'affects me too').

---

