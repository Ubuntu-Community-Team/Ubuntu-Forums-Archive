---
title: "Can I restore files to a different Ubuntu version ?"
date: 2020-08-12
forum: General Help
---

### Post by nico16 on 2020-08-12
Hi, 

I was using Ubuntu 18.04 on my old laptop which basically died last week, just as the latest Ubuntu LTS 20.04.1 became available. 
I made a back up of my files with Deja Dup Backups on my old laptop (using 18.04). 
I now have a new laptop and installed Ubuntu 20.04 on it (didn't seem to make sense to install an old Ubuntu version). 

My question is can I restore my files with Backups on my new laptop, which runs with 20.04 even though the back up was made using 18.04 ? Will the different version of Ubuntu be a problem at all (e.g. with software data) ?? 

Thanks for your help.

---

### Post by CelticWarrior on 2020-08-12
It shouldn't be a problem.

The software is the same albeit a newer version but fundamentally nothing has changed. It should recognize the old backup.

---

### Post by HermanAB on 2020-08-13
Depends on which files you backed up.  

You can always restore data without a problem, but if you backed up the whole home directory then it may not be a good idea to restore it in total, since the DE may have changed and may not work with different version settings.

---

### Post by nico16 on 2020-08-13
Hi, 

Thanks a lot for your replies. Yes, it was pretty much all of the Home directory. So to be on the safe side, should I just restore my own personal data (Documents, Music, Pictures etc) and avoid any folder related to Desktop Environment and any specific software? 

I still would like to be able to restore data related to e.g. Firefox (bookmarks), Thunderbird (emails) and Keepass (passwords). Can I still do that ? 

Are there any folders (in Home) I should definitely avoid to restore ? 

Thanks a lot.

---

### Post by HermanAB on 2020-08-14
There is a hidden .info and a few other directories that you should not restore.  The troublesome ones are all hidden I think, but if you do a blanket restore, then they may get copied and screw up your newer/older DE.

---

### Post by nico16 on 2020-08-17
OK, many thanks for the advice. I figured the safest way would be to restore my files to a separate / specific folder on my new computer using Backups and then from there copy the files I really need in my Home folder. I know where my passwords / emails and bookmarks are located and the rest is just my personal files. Thanks.

---

