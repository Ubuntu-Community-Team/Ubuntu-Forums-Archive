---
title: "HPLIP-3.16.2 doesn't install?"
date: 2016-02-12
forum: General Help
---

### Post by Butthead on 2016-02-12
Hi,

Quick question for the forum here.  For the last three days or so, I have a box pop up saying that there is a new version of HPLIP (3.16.2) available for upgrade, but when I click on the "install" button in the box nothing happens.  I'm just wondering if it's because of the printer (a cheap Hewlett Packard Desk Jet D1660) I have installed, or something else?  It's really not that pressing of a problem, because the HP device manager I currently have installed (3.15.11) seems to be printing fine.  Anyone know if this model of printer (Desk Jet D1660) is still being supported in the newer versions of HPLIP?  Thanks for any info!

---

### Post by mountainman70 on 2016-02-12
I am having the same problem. Running Ubuntu 14.04. Printer is a HP 2510. Printer is still printing good. Haven't had time to check for a solution. Hope you find the answer. Will try and check later.

---

### Post by mountainman70 on 2016-02-12
> **Butthead said:**
> Hi,

Quick question for the forum here.  For the last three days or so, I have a box pop up saying that there is a new version of HPLIP (3.16.2) available for upgrade, but when I click on the "install" button in the box nothing happens.  I'm just wondering if it's because of the printer (a cheap Hewlett Packard Desk Jet D1660) I have installed, or something else?  It's really not that pressing of a problem, because the HP device manager I currently have installed (3.15.11) seems to be printing fine.  Anyone know if this model of printer (Desk Jet D1660) is still being supported in the newer versions of HPLIP?  Thanks for any info!

Butthead Here is an update to my previous post. 
I have a test HD running 15.10 to see if there are any problems with it on this computer and to see what I need to fix to get it like I want. I prefer running LTS as I do not need latest bells & whistles. I could not remember which HD I was using so I checked and found the printer was not installed. 
I went here: 

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

and downloaded the printer file to my desktop and then followed the prompts to install and everything works.

I then hooked up my 14.04 and found that I had the 3.15.11 file. So I D/Led the file from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) to my desktop and followed the prompts to remove 3.15.11 and install 3.16.2 and everything works fine now. I thought that I had already updated the printer but I had not. 
I think all you need to do is install the new update and you should be good to go. If you can you should make a Backup of your HD first.

---

### Post by Butthead on 2016-02-13
Hi Mountainman70,

Thanks, that did the trick! \\:D/

I forgot about the automatic install option that makes things super simple.  The last time I attempted the HPLIP upgrade, I did it the manual way, and that wasn't all too fun (I was thinking I would have to do it  like that again). 8-[

Anyway, HPLIP-3.16.2 is running fine now.  I wonder if a new version of HPLIP were to come out if it would install automatically (by just clicking the upgrade prompt box) this time? :confused:

---

### Post by mountainman70 on 2016-02-13
I really don't know. I always use the D/L site and do it that way. Glad I could help.

---

### Post by Butthead on 2016-02-14
Hmm, the last two (or so?) times that there's been a HPLIP upgrade, I've had a box pop up on the screen at login time informing me of it, and then offering to install it for me. :confused:

Your way is just as easy though. ;)

---

