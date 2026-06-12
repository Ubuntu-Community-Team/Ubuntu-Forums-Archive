---
title: "Dual boot killing windows?"
date: 2006-07-12
forum: General Help
---

### Post by sponge008 on 2006-07-12
So, the last time I tried to install Ubuntu, almost a year ago, it worked. However, my freshly installed Windows immediately broke. When I booted into it via GRUB, it would show the loading screen, then restart. Now, I decided to try Ubuntu again, as a new Linux user. Surprisingly enough, it worked. However, after getting 3 kernels and hence 8 total entries in GRUB, I decided to delete the oldest of the three. Big mistake. The same thing happened to Windows. So, does anyone know what causes this? I'm actually about to install Fedora Core, but may switch back to Ubuntu. (another reason for switching is that Wine doesn't like me in Ubunutu for some reason)

---

### Post by Najand on 2006-07-12
> **sponge008 said:**
> So, the last time I tried to install Ubuntu, almost a year ago, it worked. However, my freshly installed Windows immediately broke. When I booted into it via GRUB, it would show the loading screen, then restart. Now, I decided to try Ubuntu again, as a new Linux user. Surprisingly enough, it worked. However, after getting 3 kernels and hence 8 total entries in GRUB, I decided to delete the oldest of the three. Big mistake. The same thing happened to Windows. So, does anyone know what causes this? I'm actually about to install Fedora Core, but may switch back to Ubuntu. (another reason for switching is that Wine doesn't like me in Ubunutu for some reason)

Do you know the windows partition or can you mount the winodws partition inside ubuntu?

---

### Post by sponge008 on 2006-07-12
> **Najand said:**
> Do you know the windows partition or can you mount the winodws partition inside ubuntu?

Ah crap. I just reformatted. Basically, last time I tried to "repair installation" through install CD, Windows STILL didn't work after repair. Other than this, I really don't have much information to add.
 :(

---

### Post by sponge008 on 2006-08-20
OMFG it hapenned again! This time, I didn't do anything specific in Fedora Core 5, merely, when I tried to boot back into Windows, the blue bar moved, then, where normally the user names would show, just a black screen! AHHHHHHHHHHHH!! Please, does anyone have any idea of what's wrong?

---

### Post by kerry_s on 2006-08-20
How are you setting up for duel boot? For instance do you got 2 partions already made? Are you resizing windows after install(you have to defrag before resize)? No one can help you if you don't give no information about your setup, all we can say with the info so far is it's screwed up, try it again.

---

### Post by sponge008 on 2006-08-20
installation:
1)clean format
2)partition: windows, linux, shared FAT32
3) install windows, then linux

---

### Post by The Noble on 2006-08-21
I don't know if this will help, but when I did a dual boot a while ago (windows on one hd, Ubuntu on another), The grub would show 2 entries for windows: One that said Windows XP, and the other that said Win 98/2000/XP. If I selected the Win 98/2000/XP, It would start some weird mode and freeze. Otherwise, XP worked. Just something to try.

---

### Post by ProjectGod on 2006-08-21
i've had this similar problem. nothing drastic. the computer boots to the login dialog box then restarts whenever i try to use xp and win2k. usually you'd see the BSOD (blue screen of death) but windows auto turns on "reboot on error". I'm 100% sure its because of ubuntu dual boot. but its nothing severe (like i mentioned previously). 

i thought it was my physical disk that was stuffing up. this was negative. furthermore the event logs have this queer thing i cannot remember. its still there. but if you get a chance to boot windows, check the event logs and post the error found there. i bet its exactly the same as the error on mine.

---

### Post by sponge008 on 2006-08-21
Noble: my Windows is "other".

God: How is that not drastic? Your OS died...or do you not use it much? Anyways, in my system event log, I have a bunch of warnings about "ftdisk", and 2 warnings about "disk". COuld this mean anything? I'm going to defrag today.
 
Update: When I woke up this morning, I turned on my computer (it boots default into Windows) and let it alone for an hour or so. When I came back, Windows was alive! So far, the only fishy things I've noticed are that Firefox absolutely DIED. Like, even when I reinstalled it, the only thing I could use was my bookmarks file. (a backup, the latest one was empty) I'm going to try to defrag today.

Also, if I have to reinstall Windows, I believe it will overwrite GRUB. How will I get GRUB back in that case, to be able to boot into Linux as well?

Thanks for the help.

---

### Post by sponge008 on 2006-08-22
Does anyone have any ideas? I'm in Windows right now, and am not turning off the computer.

---

### Post by fakie_flip on 2007-04-22
Try installing Windows on its own hard drive and Linux on another hard drive instead of both of them on the same drive and see if that works.

---

