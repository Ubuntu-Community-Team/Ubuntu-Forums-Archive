---
title: "XP Won't load, only Ubuntu"
date: 2007-12-22
forum: General Help
---

### Post by tehsage on 2007-12-22
So, here's the story:

I was using XP a couple hours ago to play Half Life 2. It crashed mid-game, so, I just turned off my computer. XP hates it when you turn it off incorrectly and gives that error message in the beginning. But, anyway. I load up ubuntu and I noticed that my XP partition wasn't showing on my desktop. I found that the partition wasn't mounted and I couldn't do it. It said I could force mount it so I did. Now, I can access my XP Partition and I can see the files are intact. But, I used GRUB in order to dualboot XP and Ubuntu, and now, my menu.lst was changed and the windows stuff I had in it was deleted. I readded the stuff and I had an erro r along the lines of "unsupported or corrupt executable". I read a couple of posts and tried something else. I currently have this for my menu.lst:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Now, I'm just, clueless. It says my OS is missing and when I  try to load up the XP installation CD, I get the Blue Screen of Death. Anybody have any idea?

---

### Post by Craigus on 2007-12-22
> when I try to load up the XP installation CD, I get the Blue Screen of Death

What happens if you run memtest86+ from your ubuntu CD ?

---

### Post by tehsage on 2007-12-22
Hold on, I need to make a Live Cd. I'm at a LAN. The worse place to have a problem with Windows. >_>

---

### Post by Sef on 2007-12-23
Get Super [GRUB Boot Boot Disk]("http://supergrub.forjamari.linex.org/").  Use that to reinstall your GRUB.

---

