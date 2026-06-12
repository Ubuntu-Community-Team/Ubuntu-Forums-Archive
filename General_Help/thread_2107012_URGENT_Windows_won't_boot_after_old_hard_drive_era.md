---
title: "URGENT: Windows won't boot after old hard drive erase"
date: 2013-01-20
forum: General Help
---

### Post by LilLZ on 2013-01-20
Hello. I have a dell dimension 9100. I have two drives on it, a ~160gb drive that came with it with xp, and a 500gb drive with win7. I put the win7 in myself and had been using that. Finally, I decided to erase the old drive with xp on to install linux on it. After erasing the old drive, my computer won't start up. It says it cant find sata 1 or 3. I've tried switching the cables hooking up to it but that doesn't help. If I push continue after it tells me how it can't find them, it says 'loading pbr for descriptor 2...done' and stays there. I did not erase windows 7, I checked. Whats wrong? I erased the old drive so I could install ubuntu on it... I'm guessing since thats the drive the computer came with, I deleted the mbr... I have an external drive with ubuntu I can use to fix this. Before you say to use the windows install disk to fix it, I've already tried that. The repair utility doesn't scan and thus doesn't see my install.

---

### Post by Wolfgange on 2013-01-20
Hello, I'm not sure if you've done this, but try burning and putting in a live version of ubuntu (assuming you have access to another computer...) and updating/reinstalling grub.

---

### Post by LilLZ on 2013-01-20
I've already tried do boot-repair recommended, tried sudo apt-get install lilo

3. Fix the MBR using lilo using the command:

sudo lilo -M /dev/sda mbr

and still nothing.

Update: The more I think about it, the more that it seems like its NOT an mbr thing. I think this because of the fact that the windows repair disk doesn't see any installation of windows.

---

