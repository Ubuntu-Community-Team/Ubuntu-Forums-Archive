---
title: "Media Server Partitioning"
date: 2014-10-03
forum: General Help
---

### Post by kieran5 on 2014-10-03
Hi
I am relatively new to Ubuntu/Linux with about 10 months experience.
I am building a media server and need some advice re partitioning (advice not tech support!)
I would like to know if any other media builders could offer up some wisdom as to what partitions I may need?
The server will host all my music, films, tv shows and pictures. It will also handle a CUPS server and a small file server.
I am building it with 14.04 LTS desktop, it will be headless and kept in a cupboard. It has 2GB of ram and won't be used for anything other than streaming media. I have 2.5TB of disk to play with (500GB + 2TB).

I was thinking along the lines of partitioning for
1) The OS and system files partition (may include the file server here)
2) Music partition
3) Film partition
4) Pictures partition
5) TV shows partiton
6) Swap (Will I need this on a server that will only be used to stream media?)

Is there anything else that I am should be thinking about? Also how much space will the OS partition require? And do I need a swap for a system that wont be doing an awful lot?
Many thanks

---

### Post by yancek on 2014-10-03
15-25GB for the operating system should do unless you plan to install a lot of additional software.
I would do 4GB swap for multimedia and since you have enough drive space.


Create mount points for each of the partitions you want under the /mnt directory to simplify things and also because that is the standard place for them.  You can put them anywhere but...?  You then need to have an entry for each in the /etc/fstab file if you want them mounted on boot.

---

