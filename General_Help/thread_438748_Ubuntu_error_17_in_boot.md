---
title: "Ubuntu error 17 in boot"
date: 2007-05-10
forum: General Help
---

### Post by bear^ on 2007-05-10
Howdy folks, new user and new Linux user.

I have searched around for several hours after help for this problem but nothing seems to work.

Straight forward, i get Error 17 when i try to boot linux.

I have 1 HDD with 3 partitions on it. 1 for Windows (NTFS) and 2 for Linux (ext3 formated). 1 Linux partition is on 15 gb and have the main innstallation, the other at 5 gb containes the swap files.

Now i have innstalled without any errors, the error comes when i try to start withouth the liveCD in. 

What i have tried is many documents found on google, like some i found here. Nothing seems to work. I have tried working around the bootloader, mounting, maped. Everything i could find of information that could help from this problem, and nothing works.

Anyone having a solution here?

---

### Post by ikonia on 2007-05-10
The most likley cause for this is grub getting its knickers in a twist due to the PC bios's boot order.

What I suggest you do is boot off the livecd, mount your Linux partition and read the /boot/grub/device.map dile on the mounted partition. That will tall you what grub is using for hd --> device mapping.

Once you see that you can see which disk grub expects "hd0" to be, if thats not your actual boot device, reinstall the grub boot loader with ~
[quote]
sudo grub
[quote]

then use the correct rood(hdX,X) and setup (hdX) options and you should be fine.

---

### Post by bear^ on 2007-05-10
I cant seem to get it to work. 

What am i suppose to wirte instead of the Xs? Remember that im a total noob on this and even the most simple thing for you guys are atomical fysic for for me. Break it to me gentle and like im a kindergarden kid (at this stage i realy am).

So i tried to read the map thingy file. Made no sense at all but i played along, trying to understand it.

But i do see that HD0 aint sett to my ext3 partitino but my NTFS partition. 

So i tried the root (hdx,x) thingy, replace the x,x with 0,2, wich i do belive is my ext3 partition but honestly, im just pressing buttons here.

And then i tried setup (hd0) but that didnt work, just got error 17, couldnt mount something something. Tried some more numbers, didnt work. Hey, i feel like a 1 celled animal. Stumping my head at a wall when i could just go around it.

So here i am, still using my LiveCD, banging my head (bloody at this stage) on a brick wall and just cant understand how the howydodlydey i should make this work.

Just some more information. The NTFS partition is sett with a /boot flag. Do you think i have to change that boot flag so it boots first from the ext3 linux partition? 

I dont know, pleas help me :)

---

### Post by bear^ on 2007-05-10
Anyone?

---

### Post by Josey on 2007-05-10
Follow reinstall grub instructions here
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

I'll quote that page in less detail...
Boot the live cd and open terminal
```
sudo grub
```

then you'll have this prompt...
```
grub>_
```

input this
```
grub> find /boot/grub/stage1
```

you'll have something that looks like this
grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Then use the output you see for the next command... in the example we use (hd0,1) but yours might be different depending upon the output of the first command.

```
grub> root (hd0,1)
```

and last

```
grub> setup (hd0)
```

Hopefully this is what you see from that command...
> grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.


This fixed my error 17... basically this finds your old grub list and reinstalls it.

---

### Post by bear^ on 2007-05-10
Thanks, but it seems like theres a deamon in my computer, becaus when i start grub (sudo grub) and enters there "find /boot/grub/stage1" i get "error 15: file not found".

Honestly, i dont know what the freakingdelly is up with my computer now.

---

### Post by Josey on 2007-05-10
heres what I found on error 15

[http://ubuntuforums.org/showthread.php?t=307867&highlight=error15](http://ubuntuforums.org/showthread.php?t=307867&highlight=error15)

They had luck fixing it in this thread...
[http://ubuntuforums.org/showthread.php?t=135348&highlight=error15](http://ubuntuforums.org/showthread.php?t=135348&highlight=error15)

good luck :)

---

### Post by bear^ on 2007-05-10
> **Josey said:**
> Follow reinstall grub instructions here
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

I'll quote that page in less detail...
Boot the live cd and open terminal
```
sudo grub
```

then you'll have this prompt...
```
grub>_
```

input this
```
grub> find /boot/grub/stage1
```

you'll have something that looks like this
grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Then use the output you see for the next command... in the example we use (hd0,1) but yours might be different depending upon the output of the first command.

```
grub> root (hd0,1)
```

and last

```
grub> setup (hd0)
```

Hopefully this is what you see from that command...


This fixed my error 17... basically this finds your old grub list and reinstalls it.

Well, i tried that one. And i got no error this time. It seemed to innstall withouth problems. But i still got the error 17.

Im starting to get anoyed here. I thouth i should be easy with Linux, seems like its a tad worse then Windows at this point.

---

### Post by bear^ on 2007-05-11
Anyone that can help? Cmon.

---

