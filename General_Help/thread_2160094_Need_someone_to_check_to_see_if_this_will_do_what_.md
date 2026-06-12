---
title: "Need someone to check to see if this will do what I think it will..."
date: 2013-07-05
forum: General Help
---

### Post by Despotism on 2013-07-05
Background - I have 6TB Raid 5 Array, recently about 6 years of my family photos disappeared, I have no idea when, or how, and I am pretty sure files have been moved around, copied and deleted, as well as reboots have happened since the files where gone.

My family and I are sad of cause, there is no real apparent reason why just this one folder on the array is missing all it's files (I've searched and can't find anything in any other folder) I've done a lot, but I'm using the foremost command to recover pictures.

The problem is it's command doesn't have any real structure enabling functions :/ It just dumps found files on another Array I have :/.. If I could just right click on the folder and say "Undelete" it would be so much simpler but I can't find anywhere that option is available.

So I'm running foremost, however it's taking a really long time and it's throwing up every freaking picture (even ones not deleted/missing) into the recovery folder.
I've tried using other undelete programs but they don't appear to work the same or give some BS error about unknown file system.

I've created some CRON jobs and I want to make sure they do exactly what I think they will do.

45 * * * * find /home/mediacenter/recover/jpg -size -500k -type f -delete
55 * * * * find /home/mediacenter/recover/jpg -size +5500K -type f -delete
01 * * * * mkdir /home/mediacenter/recovery/$(date +%Y%m%d_%H)
02 * * * * find /home/mediacenter/recovery/jpg -type f -exec mv {} /home/mediacenter/$(date +%Y%m%d_%H) \;

Here is what I want it to do.
At 45 minutes every hour, it searched the folder and deletes any files less than 500K - Because none of my pictures are smaller than 500K, they are all between 750K and 4.9mb.
At 55 minutes every hour, it searched the folder and deletes any files greater than 5.5mb.
At 01 minutes every hour, it creates a time stamped folder in the parent recovery folder. Time stamp is date and hour.
At 02 minutes every hour, it moves the entire contents of the recovery folder into the time stamped parent subfolder.

Is this what these commands will do?

---

### Post by Cheesehead on 2013-07-06
Is there some particular reason you want these operations run independently?
Is there some particular reason you want them to run hourly instead of, say, weekly?

For example, if the :45 job is delayed or takes longer than 10 minutes, the :55 will run before it is complete.
Is there a scenario where you really want this to happen? 

You might get better results creating a single script, and triggering that script from cron (or Upstart, or dbus, etc).
A script will also give you much more flexibility in feedback or logging the results.

To answer your specific question: No, I think you have made syntax errors in the 'find' command. It will look for a specific file named 'jpg' instead of filenames that include *.jpg

---

