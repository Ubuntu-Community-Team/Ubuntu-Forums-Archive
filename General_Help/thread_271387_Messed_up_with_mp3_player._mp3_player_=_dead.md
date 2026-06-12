---
title: "Messed up with mp3 player. mp3 player = dead"
date: 2006-10-04
forum: General Help
---

### Post by Anonii on 2006-10-04
Hello,

I bought that mp3 I was thinking of buying (I even made a thread about it) today. The detection worked great (It uses USB for transfering songs.) It worked great. Until 3hours ago... I removed all the songs to add others, and suddenly I had only 90MB free, and the total space is 1GB. So I went to IRC, and started figuring out what to do.  Some guys told me to remove the hidden files, that turned the free space to 630MB. That was great. But I wanted the other 370MB back, too!
So someone said "Format it" and told me to check the partition out with gparted. I downloaded gparted, and checked out the seperate /dev/sda partition, which had 370MB free(evil eh?), But there were no options on gparted on how to delete this etc. So someone proposed me:
```
sudo umount /dev/sda1 && sudo mkfs.msdos /dev/sda1
```
Hooray it worked!
***_BUT_***
I had just opened the Pandora Box... When I unplugged the device. Only the starting splash screen would load, and nothing more. An endless boring splash screen. No menus, no songs, nothing. Viva Emptiness!

In this really sensitive situation (my new mp3 ****** up) I went into a rage. Started chatting furiously on irc to find a solution, searching on google etc.

I firstly tried:
> 
 sudo mkdir /mnt/usb
 sudo mount /dev/sda1 /mnt/usb

*Bad superblock error...*


Then I tried to unmount it. It said that /dev/sda1 was not mounted. I could not mount it too, because of the superblock error.

Then a lad in IRC proposed me this:

```
mkfs.vfat /dev/sda1
```

Succesfull, but nothing more than the endless splash screen in my tiny mp3 player monitor :/

Then this:

```
mkfs.msdos -F 32 /dev/sda1
```

nothing.

Everything was screwed up!
He told me then, to open /dev/sda (sda1 dissapeared after the reboot) and create sda1, and then "mkfs.vfat" it. I did it. It didnt work. /dev/sda is just a partition with 1000MB of empty space, the exact space of the mp3 player... :(
I guess that I deleted the menus and other essential files for the mp3 when I formatted it for the first time, and thats why I get this eternal splash screen...

Do you have any ideas? I'd really appreciate any kind of help!!
Tomorrow I'll go to the shop and try to make them fix it, but i doubt it, since I used such brute methods... Of course I'll admit nothing and say that "my uncle wanted to add some music, and he unplugged the device before rejecting it, and he gave me the mp3 player with this problem". If that doesnt work. I dont really know what I will do.
*But dammit! Help me, please!*


Thanks!

(The mp3 is a version of "Sigmatel MSCN Music Player". I cant find any more info, because its a version of the local store I bought it. I also have their firmware upgrade, but its only for windows.)

---

### Post by whizbaby on 2006-10-04
Firmware - I think that's exactly what is gone. Perhaps the store will flash it on the drive for free or maybe a download is available somewhere over the net. If not there's a little chance to put a kind of linux on it (have seen this at a friend's, will ask him about it).

---

### Post by Anonii on 2006-10-04
Great, if its a firmware problem ,its solved. I have the link for the upgrade. I'll go and download it.

I'm actually uninstalling Ubuntu and installing Window just for this. Then installing Ubuntu again....
brb :D

---

### Post by Anonii on 2006-10-04
Ta~ta! Windows installed, mp3 fixed! Windows seem great! I think I'll keep them!
*Just joking >:3*

Anyway..
How tough is this on Linux:
[IMG]http://img.photobucket.com/albums/v148/Assa-san/fixed.jpg[/IMG]Right click on the device, format and an "Enter" fixed, what an IRC channel couldnt fix. <:

(Internet Explorer fails so hard!)

---

### Post by 3rdalbum on 2006-10-05
Usually when my father's MP3 player bricks itself, a quick format in Gparted fixes it.

---

### Post by yopnono on 2006-10-05
> **Anonii said:**
> Ta~ta! Windows installed, mp3 fixed! Windows seem great! I think I'll keep them!
*Just joking >:3*

Anyway..
How tough is this on Linux:
Right click on the device, format and an "Enter" fixed, what an IRC channel couldnt fix. <:

(Internet Explorer fails so hard!)

Sorry to break your heart but... I'm sure you can use linux and fix your issue. Have had stuff like yours and Gparte work fine for this or the terminal. Anyhow it's fixed now so :)

---

