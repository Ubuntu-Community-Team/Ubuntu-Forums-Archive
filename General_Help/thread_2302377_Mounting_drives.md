---
title: "Mounting drives"
date: 2015-11-09
forum: General Help
---

### Post by Spency on 2015-11-09
I have apt-mirror running on my home server; with my configuration the total download is estimated to be around 300Gb. Following this  guide: [http://www.tecmint.com/setup-local-repositories-in-ubuntu/](http://www.tecmint.com/setup-local-repositories-in-ubuntu/) I linked /opt/apt-mirror/mirror/ to /srv/ftp/ (STEP 6). An 800Gb partition is mounted @ /opt; a 50Gb partition is mounted @ /srv. Since I don't understand exactly how this link works, I'm worried I may have problems when my /opt/apt-mirror/mirror/ directory exceeds the size of the partition that is mounted @ /srv. In other words, will my apt-mirror directory link to my ftp break when it exceeds 50Gb? Is this a symbolic link that has no impact on the 50gb partition mount @ /srv?

Thanks again.

---

### Post by ajgreeny on 2015-11-10
If I understand what you are saying properly there is no need to worry.

A couple of years ago I used to run 5 separate OSs (all Linux distros) on my machine and I always made symbolic links to the main data folders of /home in my main OS into the /home/user folder of the other OSs, ie, they did not have separate /home partitions.

I had about 100GB of data linked to the usual data folders within /home which was itself in the 12GB root partition of those OSs.  It looked as if all the data files were in /home of each OS but in fact all the data remained in the /home partition of my main OS.  The volume of data is never of any consequence as far as I am aware.

---

