---
title: "Questions about disk usage and mounting volumes"
date: 2007-09-08
forum: General Help
---

### Post by mahasmb on 2007-09-08
122 GB HDD
~ 35 to 40 GB Windows XP
~ 80 to 85 GB Ubuntu Ultimate Edition 1.4 (Feisty Fawn)


1.) I swear I'm missing like 20 GB ... and I don't know why.

Here's how it is. In Disk Usage Analyser it says I have a partition of 78 GB (My Ubuntu install). _**Please see my "Diskusage_unmounted.png" file.**_

Out of **78 GB**, it says I'm **using 43.9 GB** with **34.1 GB free**. But my root directory is only using **22.6 GB**. 

**43.9 - 22.6 = 21.3 GB that I really can't account for.**

a.) What's using up all this space? Is it just the Ubuntu OS? 
b.) Shouldn't a reasonable operating system use no more than 5-10 GB? 20+ GB seems like way too much.

I'd guess that since Disk Usage Analyser says that I have a partition of 78 GB when I know my partition is a little more 85 000 MB ( around 83 GB?) that it would mean that the 83-78= 5 GB would be what Ubuntu would be using for just the OS. So it definitely wouldn't need those 21.3 GB I can't find.


2.) a.) Does mounting a Windows partition in Ubuntu take up space away from the Ubuntu partition? 
      b.) If so, about how much?

When my Windows partition is mounted, 19.9 GB under /media/ get filled up. Like as if in order for Ubuntu to read 19.9 GB on a virtually partitioned Windows hard drive it needs to use about that much space in Ubuntu. (I know this isn't the case in Windows)

Can someone please clarify all this for me? I hope I was very clear and precise about my assumptions and with the questions I want answered.

20 GB is a lot for me. I'd really like to retrieve that space if I could :( .

---

### Post by forestpixie on 2007-09-08
Linux keeps 5% of the disk space for when you run out of space I think  - I found it somewhere here - sorry - can't remember where :( 

Good news is that you can change it, although I didn't for all my partitions - just my data  storage ones

Don't think mounting win would take up space 

If I can find the information I'll post it here

Edit - pretty sure it's tune2fs, but can't remember how I used it to reclaim the space. Have a search around in the forum's.

---

### Post by mahasmb on 2007-09-08
Thanks, but that still doesn't seem to add up. 5% of my whole hard drive is no more 6.1 GB. Although, I'd guess Ubuntu would only use the 5% from its own partition.

---

### Post by vanadium on 2007-09-08
use

df -h

for a comprehensive overview of what is available on your partitions and what is used. One reason why less space might be available than the nominal space of your disk is the file system overhead. For example, more data will fit on the same disk is it is formatted in fat32 than when it is formatted in ext2. ext3 will result in even fewer space available for use because of the extra space needed for the journalling.

Mounting does not cost you any disk space.

---

### Post by mahasmb on 2007-09-08
Alright, so would that really make up for the 20+ GB? That really seems like a lot to me. It's a quarter of the partition...

With the df -h command, it says I'm using about 44 out of 79 GB.

EDIT: I have a 60 GB laptop that's half Windows and half Feisty Fawn. I can account for all of the space it uses.

---

### Post by Vadi on 2007-09-08
Just a tip, I installed Gutsy in VirtualBox, and a clean install, no programs added besides what Gutsy game with, was 2.6GB.

For comparison, XP right from the start was 4.6GB...

---

### Post by vanadium on 2007-09-08
Running "sudo du /home / -hcs I find

36G     /home
39G     /
74G     total

Thus, / - /home = 39 - 36 = merely 3G for mostly system files.

"df -h"

reveals a total space of 71G, of which 39G is used as seen above.

My disk is 80GB. My swap is 506 M. If I am interpreting this all correctly, then there is 80 GB(total) - 0.5G(swap) - 71G(useable) = 8.5G not accounted for, which I think is file system overhead.

---

### Post by mahasmb on 2007-09-08
> **Vadi said:**
> Just a tip, I installed Gutsy in VirtualBox, and a clean install, no programs added besides what Gutsy game with, was 2.6GB.

For comparison, XP right from the start was 4.6GB...

Exactly. I've always been told that Linux uses way less space than Windows. Especially with Windows Vista which alone needs 15 GB. Which is beyond ridiculous.


> **vanadium said:**
> Running "sudo du /home / -hcs I find

36G     /home
39G     /
74G     total

Thus, / - /home = 39 - 36 = merely 3G for mostly system files.

"df -h"

reveals a total space of 71G, of which 39G is used as seen above.

My disk is 80GB. My swap is 506 M. If I am interpreting this all correctly, then there is 80 GB(total) - 0.5G(swap) - 71G(useable) = 8.5G not accounted for, which I think is file system overhead.

Again, I see your point. Your 80 GB is only "missing" 8.5 GB, but mine... is "missing" 21.5 GB. That's a big difference.

---

### Post by mahasmb on 2007-09-13
Any ideas whatsoever out there?

---

### Post by Vadi on 2007-09-13
Did you try checking gparted?

The disk usage analyzer shows the *combined* of all patritions it finds, I think.

---

### Post by mahasmb on 2007-09-14
Well, no. It depends on which partitions are mounted. And it shows -- well if you look at the pictures, you can see that it'll even show me how much my biggest folders take up.

---

### Post by mahasmb on 2007-09-25
This just doesn't add up to me.

> 
maha@maha-dlu:~$ sudo du -h --max-depth=1
Password:
12K     ./.gtkpod
488K    ./.spumux
65M     ./google-earth
20K     ./.gnome
4.0K    ./Music
448K    ./.kvirc
35M     ./.googleearth
28K     ./.gnucash
8.0K    ./.serpentine
2.2M    ./.openoffice.org2
4.0K    ./.icons
4.0K    ./.lyrics
16K     ./.themes
16K     ./.audacity-data
74M     ./.picasa
4.6M    ./.gdesklets
72K     ./.fontconfig
12K     ./.easytag
28K     ./.tomboy
24K     ./.anjuta
200K    ./.dvdrip
16K     ./.hydrogen
36K     ./.qalculate
108K    ./.blender
[COLOR="SeaGreen"]16G     ./MyDocuments[/COLOR]
168K    ./.BitTornado
116K    ./.bluefish
8.0M    ./.kde
4.0K    ./.gnome2_private
12K     ./.gobby
8.0K    ./.wireshark
324K    ./.metacity
716K    ./.gimp-2.2
19M     ./.thumbnails
8.0K    ./.compiz
524K    ./.config
68K     ./.gconfd
51M     ./.wine
28K     ./.xmms
12K     ./.avidemux
9.6M    ./.opera
16K     ./.mcop
8.0K    ./.update-manager-core
300K    ./.nautilus
1.7M    ./workspace
4.0K    ./.hardinfo
31M     ./.gnome2
20K     ./.mplayer
88K     ./.adobe
8.0K    ./.gourmet
36K     ./.evolution
13M     ./azureus
4.0K    ./.kino-history
48K     ./.gkrellm2
28K     ./.xine
4.0K    ./.update-notifier
1.3M    ./.wapi
1.4M    ./.gconf
145M    ./Desktop
8.0K    ./.nedit
64K     ./.listen
22M     ./.mozilla
104K    ./.amsn
40K     ./.qdvdauthor
8.0K    ./.compizconfig
116K    ./.macromedia
8.0K    ./.3ddesktop
656M    ./.beagle
20K     ./.gramps
59M     ./.ies4linux
604K    ./.local
4.0K    ./.denemo
20K     ./.AbiSuite
404K    ./.gaim
356K    ./.vlc
112K    ./.amaya
4.0K    ./bin
56K     ./logs
4.0K    ./amsn_received
484K    ./.loki
16K     ./PicasaDocuments
24K     ./.xchat2
460K    ./.gimp-2.3
8.0K    ./.banking
12K     ./.qt
8.0K    ./.gpixpod
16K     ./.endeavour2
2.1M    ./ies4linux-2.0.5
8.0K    ./.glchess
568K    ./.gstreamer-0.10
80K     ./.aria
37M     ./.azureus
4.0K    ./.Trash
20K     ./.automatix
8.0K    ./.elinks
48K     ./.jpilot
40K     ./.subversion
4.0K    ./.giFT
[COLOR="Red"]17G     .[/COLOR]



> 
maha@maha-dlu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/hdc2              79G   55G   21G  73% /[/COLOR]
varrun                221M  224K  220M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb            221M   96K  221M   1% /proc/bus/usb
udev                  221M   96K  221M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   33M  188M  15% /lib/modules/2.6.20-16-generic/volatile




> maha@maha-dlu:~$ sudo du -hx --summarize /
Password:
[COLOR="#ff0000"]53G     /[/COLOR]



Now I'm missing about 30 Gigs of space. Before I was only missing about 20 GB. Disk Usage Analyser tells me that "/" is using less than 23 GB. I haven't downloaded anything besides regular Ubuntu upgrades. Please tell me what's going on here. I'm afraid I'll be left with nothing soon and since I can't see where it's going to, I won't be able to get rid of the space.

---

### Post by Vadi on 2007-09-25
Maybe the downloaded packages are being kept... in synaptic, in preferences, there's an option to delete the downloaded files after you've installed them. I'm not sure if that's the case for *all* of the files though.

---

### Post by mahasmb on 2007-09-25
Neither of the following have helped in any way. I've tried them out numerous times.

> 
sudo aptitude clean
sudo apt-get autoclean


---

### Post by Vadi on 2007-09-26
Try asking a question on launchpad.net then, that's usually the last place I go to get a question answered and it gets answered the.

---

### Post by mahasmb on 2007-09-26
It turns out that Simple Backup Config had saved to a folder that nothing else could detect. The only way I could even access the folder (or even tell how big it was )was if I used "gksudo nautilus".  And even then, I had to clear the trash can under "/root". Which didn't work with the simple "sudo rm" commands. I had do delete the files while I was in Windows XP.

So, problem finally solved.

I have another question though.

What folders should I backup if I want to restore my computer to the exact same settings, with the exact same programs, with the exact same drivers etc?

I've had to do fresh installs way too many times and I am sick and tired of not only doing the fresh installs but also having to reconfigure both of my computers to exactly as they were before.

---

### Post by Vadi on 2007-09-26
I'd love that question answered also.

I know that stuff about your gnome panels, gnome terminal, and metacity stuff is stored somewhere in one of these:

gnome .gnome2 .gconf .gconfd .metacity

Because doing "rm -rf .gnome .gnome2 .gconf .gconfd .metacity" promply reset those settings to default. (Don't ask me why I did that. I don't know. I do know that the terminal is one powerful thing now though).

---

### Post by pavlos340 on 2007-09-27
Hello, first time i use ubuntu and i am really impressed!! Wow No crash, no Ctrl+Alt+Del no Microsoft Service pack whatever etc. The only reason that i keep Xp is the use of some specific programs i can not find in ubuntu yet!!!

But though i have a small problem. Maybe one of you experienced users can give me a tip. When i installed ubuntu 7.04 i left Xp with a partition of 9GB  and ubuntu with 40GB, now in Xp i have only 920MB free left. As you can imagine this amount of space is good enough for nothing. I need more space for Xp. Is there any way i can do that? And if not if i use my Xp restore cds, is the partition of ubuntu formated and showed as one whole partition for xp??

Thank you in advace!!!:)

---

