---
title: "14LTS+16LTS how to access other account"
date: 2016-11-18
forum: General Help
---

### Post by FerryGnu on 2016-11-18
Hi, I have 14LTS and 16LTS side by side. When I boot 14 I would also like to be able to see some data on 16 but when I navigate to the Home then my account on 14, it shows "Acess-Your-Private-data.desktop"

I did a search and found some things to try but nothing lets me see in the 16 folders. I have that home folder encrypted on both 16 and 14, is that why I can't get access or is there some way to do this? 

Both 16 and 14 have the same login details and password if that helps. 

Currently I am using NAS-drive on the home network to pass files between them when I boot into each one, but that NAS-drive is not secure and I do not want to transfer emails and passwords etc via the NAS. 

Is there any way I can gain access to 16 from 14 or to 14 from 16. I don't care which way, as long as I can pass data when needed.

Thanks

---

### Post by oldfred on 2016-11-18
I have seen similar issues, but rarely need to directly access another install.
I use a shared ext4 data partition for all my normal data in /home.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home. (now have obsoleted Picassa and /home is even smaller).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by FerryGnu on 2016-11-18
Thanks OldFred,

I should have thought about it a bit more. Using Veracrypt I created a container on the NAS and can use that as the swap between the two. Just tested it and there are no ownership problems with the container on the NAS. It's a little more work shuffling stuff in and out, but not something I have to do daily. Mostly I am back to using 14 but had been using 16 until it started messing with the wine applications so went back to 14 and all is good. It's EOL is 2019 so it will be fine. By then 16 will be more stable. :)

I am using clonezilla for backups and imaging the entire SSD. Love the brute force approach.

---

