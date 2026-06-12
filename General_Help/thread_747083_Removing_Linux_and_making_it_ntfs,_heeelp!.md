---
title: "Removing Linux and making it ntfs, heeelp!"
date: 2008-04-06
forum: General Help
---

### Post by Dmarcisz on 2008-04-06
I have linux mint and i dont really like it so i want to remove it completely and put vista back onto it. When i put the vista boot disk in my laptop i cannot install vista because the hard drive is not ntfs, so i am stuck on linux :( Please help but i am a noob so try to explain plz

---

### Post by Tomatz on 2008-04-06
Don't put vista back on?

---

### Post by LaRoza on 2008-04-06
Format the disk as NTFS.

---

### Post by Dmarcisz on 2008-04-06
Eh but vista is better, and also im asking how do i format this to ntfs, because i dont know

---

### Post by oligray on 2008-04-06
eh but you must be like a spastic or suthin... xp is better than vista.... and linux is better than xp...

i cba to find the article but bill gates said linux is better than any other operating system especially windows.

---

### Post by Tomatz on 2008-04-06
> **oligray said:**
> eh but you must be like a spastic or suthin... xp is better than vista.... and linux is better than xp...

i cba to find the article but bill gates said linux is better than any other operating system especially windows.

Chill mate ;)

If he likes vista so much let him have it.

As its not an ubuntu issue he will have to go to the "vista" forums anyway. Oh but they don't have a worldwide community ready to help anyone with any problem for free :(

---

### Post by jakupl on 2008-04-06
Hahaha funny stuff :)

can you format in gparted? in that case, boot using the ubuntu live cd, run gparted and format :)

---

### Post by Tomatz on 2008-04-06
> **jakupl said:**
> Hahaha funny stuff :)

can you format in gparted? in that case, boot using the ubuntu live cd, run gparted and format :)

Not ntfs you can't ;)

Oh wonderful vista  :lolflag:

---

### Post by oligray on 2008-04-06
i am doing my all to rid my life of windows.. but until ive finished school i still need it..

however i am working on getting it on my external drive.. but i might buy a cheap desktop pc.. because my laptop uses VIA graphics card and they are a bitch to get working.. if you like vista its your choice.. but i would rather have my pc running faster on a better looking desktop for free... sept i dont pay for windows software anyways..

---

### Post by jakupl on 2008-04-06
> **Tomatz said:**
> Not ntfs you can't ;)

bugger ;)

---

### Post by mick8985 on 2008-04-06
Run the livecd
```
sudo apt-get install ntfsprogs
```
Now you can format it to ntfs in gparted, enjoy your bloated OS.

---

### Post by ghost_ryder35 on 2008-04-06
boot the vista CD and then click install.... some windows come up etc... then select the custom install, then delete the partioton and hit refresh, then create a partiton and format it then finish the install
 
[http://www.winsupersite.com/reviews/winvista_03.asp](http://www.winsupersite.com/reviews/winvista_03.asp)

---

### Post by ginjabunny on 2008-04-06
boot a cd with GParted or Parted Magic on it and it should let you delete all the partitions, then when you boot from the install CD setup should just see an empty disk and you can create a partition.
Alternatively boot MSDOS disk with fdisk on it and use that to delete all the non-dos partitions.
I haven't done this with Vista but with XP you need to reset the master boot record after install because grub/lilo data is still in it, boot from the cd into repair console and run fixmbr. 

Alternatively keep Mint (which I use) and install Virtualbox then you can install Vista, XP and anything else you like in a virtual machine.

---

### Post by Joeb454 on 2008-04-06
You could just boot an Ubuntu Live CD, and delete the partition with Linux Mint on, and then reboot with the Vista disk in, because it will be unformatted space, Vista will install fine :)

---

### Post by SunnyRabbiera on 2008-04-06
> **Dmarcisz said:**
> Eh but vista is better, and also im asking how do i format this to ntfs, because i dont know

Bah, enjoy your bloated DRM loving, Virus attracting, memory hogging, privacy hating, blue screen of death love piece of crap OS...

What was so bad about Mint? what issues did you have?
what is this about games or something??

Bah forget it, enjoy having a crappy OS

---

### Post by Pap3r on 2008-04-06
You could just not reinstall Vista.  If you really want Winblows, I seriously recommend XP over Vista 10:1, I'd be more willing to try gaming on Damn Small Linux than switch to Vista :lolflag:

---

### Post by Laser Dude on 2008-04-06
The Vista CD *should* have a copy of fdisk on it.  You should run Windows off the CD, and then type "fdisk".  I'm not sure how to get any further, because it's been years since I last did this.  You should really ask this in a Windows support place, because once you've run fdisk, it has nothing to do with Linux any more.

Why, exactly, do you need Windows Vista?  You say you need it for school, but what programs do you need?  Most of them have alternatives, and even so, many Windows programs actually run *better* in Wine than in Vista.

Also, you *could* try running Windows inside a VM, or you could do a dual boot...

And come on people, what's up with the bashing?  It's not our choice what operating system he runs.  Although in our opinion Windows sucks, that's not our choice to make...

---

### Post by SunnyRabbiera on 2008-04-06
Yeh but he is asking for it.

---

### Post by Pap3r on 2008-04-06
> **Laser Dude said:**
> Although in our opinion Windows sucks, that's not our choice to make...

It's not our opinion though-- Winblows just sucks.

---

### Post by oligray on 2008-04-07
i need windows for school.. because i could manage without it however it makes life easier because i am working on computers within school and my computer id rather have my set up as it is now. :)

i am gonna buy another pc solely for ubuntu..

---

