---
title: "unable to write cd media in dvd drive"
date: 2006-10-24
forum: General Help
---

### Post by glenndavy on 2006-10-24
Hi all
I've got 3 ubuntu systems at home at moment 
- all with dvd burners in 
- all burn dvds without an issue. -
- 1 can burn cd images to cd media, 2 cant. 
- The 2 that can't could before they were ubuntu machines 
- The 2 that cant are kubuntu machines,(though not originally i.e. installed as ubuntu and 'converted' via aptitude)
- The 1 that can was installed from a 'server' install disk, and had the gnome desktop added with apt-get.

The error is get from cdrecord, inspite of using -dev=ATAPI:/dev/hdx is that it "Cdrecord: cannot Load Media". Trying from the gui, Im simply asked to Load media, and when  I do it insists I havent.

dmesg has this line at the end of it 'cdrom: This disc doesn't have any tracks I recognize!'
 
anyone have __any__ idea how I can persuade these machines that "yes, infact there is a blank cd in the tray"

thanks
Glenn

---

