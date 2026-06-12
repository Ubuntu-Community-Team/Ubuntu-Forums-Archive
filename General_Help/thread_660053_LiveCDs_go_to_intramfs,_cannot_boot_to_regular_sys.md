---
title: "LiveCDs go to intramfs, cannot boot to regular system."
date: 2008-01-06
forum: General Help
---

### Post by stzasnail on 2008-01-06
Well, I just installed Windows next to Ubuntu. While going through the Windows install, it said it needed some space on my drive that has Ubuntu on it. (I was installing it on my secondary drive) I thought it just needed it for the MBR, so, I whipped out Gparted and shrank my ext3 partiton by 1.5 gigabytes. When I went through the install, I had found that Windows had installed on that 1.5 gigs of FAT32. Well, I didn't think it was a problem and just went on ahead and booted Windows. It worked fine (except for a reoccuring low memory error). I also booted up my Linux install 3 times last night with no trouble. This morning, I came to find that when I tried to boot my Ubuntu install, things that would normally take less than a second to do normally in startup were taking whole minutes. I let it sit trying to boot for about half an hour before giving up. I decided that if worse came to worse, I would have to re-install. I tried to boot into a LiveCD to store away my importanat information in a small packet of Windows-readable ext2, I was greeted by a plain intramfs terminal. I have tried booting from several CD's with the same result. Does anyone have any idea what's going on? Could my partition of FAT 32 seperating the ext3 and the swap be causing it? If so, how could I fix it? I really need help right now!!

---

### Post by stzasnail on 2008-01-06
Sorry for the bump, I just really need to get this fixed. I need to at least be able to back things up. Any help would be appreciated!

---

### Post by stzasnail on 2008-01-06
Well, after about a 45 minute boot I was finally able to get into my system. After some time with Conky and the System Monitor, it seems that my CPU is constantly full, I have no clue why, not many processes are running, and my system being idle usually results in only about a 7% cpu usage. The second most likely cause is bad disk sectors, although this would not account for the sudden CPU usage. I reformatted over the Windows install mentioned in my first post and restarted the computer with no luck, Still a 45 minute boot. I checked my BIOS for the CPU speed and it was set to its normal speed. i have been trying to check for CPU overheating, although this is very unlikely as I clean my heat sink monthly, have 5 case fans, and my processor fan is up and running. I don't know what could have suddenly cut my CPU power down to a tenth of its normal power, I have not touched anything inside, and any settings from Windows would not carry over to Ubuntu, right? 


*sigh* Oh, and sorry for the triple post.(It's just the fact that nobody's replied.  : P)

---

