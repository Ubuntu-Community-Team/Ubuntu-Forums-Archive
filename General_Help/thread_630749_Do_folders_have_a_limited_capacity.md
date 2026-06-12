---
title: "Do folders have a limited capacity??"
date: 2007-12-03
forum: General Help
---

### Post by nikolas68 on 2007-12-03
I'm trying to move my mp3 music to the music folder....but i can only fit 4 Gb in the folder and then  Gnomad2 closes itself. Since i have no idea why it does that...i was wondering if there's a preset maximum capacity for a folder!

---

### Post by -grubby on 2007-12-03
I suppose it depends on the filesystem you use, maybe EXT3 (default ubuntu filesystem) has a max of 4GB per folder

---

### Post by bingoUV on 2007-12-03
Could be a limit of Gnomad2. There is no limit of folder size for ext3 (filesystem used in ubuntu by default)

---

### Post by nikolas68 on 2007-12-03
> **nathangrubb said:**
> I suppose it depends on the filesystem you use, maybe EXT3 (default ubuntu filesystem) has a max of 4GB per folder

I did use EXT3 for my installation: is there a way to change the max capacity??

---

### Post by mellowd on 2007-12-03
ext3 has a max volume size of 2 - 32TB so I doubt it's because of that.

---

### Post by nikolas68 on 2007-12-03
> **bingoUV said:**
> Could be a limit of Gnomad2. There is no limit of folder size for ext3 (filesystem used in ubuntu by default)

I've already looked into Gnomad settings: there's nothing....

---

### Post by nikolas68 on 2007-12-03
> **mellowd said:**
> ext3 has a max volume size of 2 - 32TB so I doubt it's because of that.

....is it changeble? i need at least 20 Gb for my music folder

---

### Post by mellowd on 2007-12-03
2TB is far higher that 20GB. 

This is odd though. What happens if you copy the files over from a terminal and then open the folder?

---

### Post by nikolas68 on 2007-12-03
....i think something is wrong: I renamed my first 4Gb music folder Music A-D, then created another one Music D-H and try to continue the transfer of the files.....but as soon as i press the transfer button, the Gnomad2 window closes itself....

---

### Post by nikolas68 on 2007-12-03
> **mellowd said:**
> 2TB is far higher that 20GB. 

This is odd though. What happens if you copy the files over from a terminal and then open the folder?

The files are in my Mp3 player and i'm trying to copy them on the PC.....i don't think i can copy them form a terminal....

---

### Post by mellowd on 2007-12-03
You should be able to. Depends on how its mounted. Have a look in /mnt to see if you can see your mp3 player there.

---

### Post by nikolas68 on 2007-12-03
> **mellowd said:**
> You should be able to. Depends on how its mounted. Have a look in /mnt to see if you can see your mp3 player there.

sorry....i have to go to work: but i've looked in the /mnt and there's no mp3 there....

---

### Post by LaRoza on 2007-12-03
The FAT32 filesystem has a limit of 4 GB - 1 Byte. If you are using EXT3, it is not a filesystem problem, perhaps the application's.

---

### Post by mellowd on 2007-12-03
> **nikolas68 said:**
> sorry....i have to go to work: but i've looked in the /mnt and there's no mp3 there....

What do you see in /mnt?

And work at 3am? You sound like me...



p.s. How's Cape Town? I'm missing it :(

---

### Post by nikolas68 on 2007-12-03
> **mellowd said:**
> What do you see in /mnt?

And work at 3am? You sound like me...



p.s. How's Cape Town? I'm missing it :(


sorry bokkie...really on my way out....in the /mnt there's nothing :confused:

CT is good....surf is UP!!! :)

---

### Post by mellowd on 2007-12-03
I really seem to think there is an application issue. 


You could try copying the mp3's to another folder, and then copying it from the terminal from that folder to where you actually wanted it to go. At least that will show you where the problem lies.

---

