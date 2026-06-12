---
title: "Education Please - Installing from Software Centre"
date: 2012-12-05
forum: General Help
---

### Post by Quarkrad on 2012-12-05
I current have everything installed under / (I mean my Home directory and all my apps) and have separate storage partitions that I can access via /media/.....   When I installed Virtualbox from the Software Centre it automatically installed everything in /Home - so in /Home I have a /Home/Virtualbox VMs directory where my various .vdi files are ultimately stored.   These take up a lot of space.   Is it possible, from my 12.04 Desktop, to install Virtualbox on one of my /media/.... partitions but stil run Virtualbox from my 12.04 Desktop?   In Windows speak it's like not installing in C:\Program Files but say, d:\Program Files.  The Software Centre seems to install everything in the same partition with no option to change.  Hope this makes sense.  (I would like my .vdi files located on another partition where I have GBs of free space - they are eating into my Ubuntu directory.  Note:  The partiton with lots of free space is another local HD).

---

### Post by Isamu715 on 2012-12-05
This is not an issue with installation. Go to Virtualbox preferences, in the *General* tab change *Default Machine Folder* to your desired location, like */media/whatever/*.

---

### Post by Quarkrad on 2012-12-06
Solved - thank you very much.

---

