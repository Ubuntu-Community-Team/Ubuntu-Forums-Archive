---
title: "resize2fs taking longer than normal"
date: 2014-05-16
forum: General Help
---

### Post by M_D on 2014-05-16
I am having an issue with resize2fs taking a lot longer than normal, and was looking for advice.  Before I delve into the details a little history on my experiences.  I have a file server that ran 10.04 then 12.04 and then 13.10 I ran a raid 5 array with 2TB volumes.  When I ran out of space, I would get another 2TB drive add it to the array.  Growing the array generally took about 100 hours then the resize of the filesystem only took a few minutes.  When I hit the 16TB limit, I then split the 2TB drives into 1TB partitions and put them into separate arrays.  When I first started out, I had to shrink the filesystem down and move drive over.  I let the resize run for about 3 weeks, before I killed it upgraded to 13.10, then it only took a few hours to shrink.  With 14.04 I put a new server together and got 7 4TB drives.  I put 6 4TB drives in raid 5 giving me a 20TB volume.  I added the 7th drive to it, took my usual time of about 100 hours to grow the array and just a few minutes to resize the filesystem.  I always did online array growth and offline resize.  I have all of the drives using gpt with ext4.  I then took my 2TB drives and put them into 4TB raid 0.  I added 1 of the volumes to my existing 20TB array and reshaped it from a raid5 to raid6, this took about a week.  I then took the rest of the my 4TB raid 0 volumes and added it to the array, it then took about 100 hours for the array to grow.  My raid array is now sitting at 14 4TB volumes, 7 of which are 2TB drives raided together all using mdadm.  I then did an offline resize, and it has been running for about a week now.  My concern is that this is incredibly longer than my usual experience, even though I am adding a considerable amount more at one time.  I don't want to kill it at the risk of losing data.  I can't see the progress.  When I ran into shrinking taking forever and not completing, I ran it with the -p to watch the progress and it got stuck on step 2.  It would take about 8-12 hours to tick to complete then just start over on step 2.  I was able to fix my problem by upgrading to 13.10.  I am going to continue to wait and hope that it finishes.  But if it doesn't finish at what point should I kill it and then where do I go from there?  Down grading to 13.10?  Oh, and my OS is not on the raid.  Any help or recommendations would be appreciated.

---

### Post by Brian_K on 2014-05-16
Perhaps I can help break my friend's post into some more discernible points.

1a) MD has a file server running a ton of 2tb drives in software raid 5.  Every time he runs out of space, he simply added another 2tb drive or 2 and grew volume.  Growing the volume took about 100 hours each time.  Resizing the filesystem was only a couple minutes.
1b) MD created a new raid 5 array with 6x 4tb drives recently (due to space in his drive chassis).  He grew it to 7 drives and it still took about 100 hours.  Again, resizing the filesystem was only a couple minutes.

2a) After MD had his new 4tb raid 5 array running, he started to turn his 2tb drives into 4tb raid 0 arrays with the intent of adding the 4tb pairs as single 4tb drives in the new array - essentially creating a hybrid raid array.
2b) MD added one of the pairs to the 4tb array and reshaped it from raid 5 to raid 6.  Essentially, the drive space did not increase but he added another layer of redundancy with this additional "drive."  Reshaping the 7x 4tb drive raid 5 array to a 7x 4tb + 2x 2tb hybrid raid 60 array took about a week.  Since the drive size didn't grow, there was no need to resize the filesystem.
2c) Adding the rest of the 4tb pairs to the hybrid raid 60 array took about 100 hours... the same as growing did before.  HOWEVER, it has taken over a week to grow the filesystem, and it is still going.

MD does not want to cancel his filesystem growth and lose his existing data.  Ideas?

---

### Post by joerg_ac on 2014-05-21
It maybe a little off topic, but you can speed up the reshaping by switching on the use of a bitmap using 

          mdadm --grow --bitmap=internal /dev/md1

This only switches on the bitmap. Then you give the command to grow and after the re-shaping has finshed you can swith it off again with for example

          mdadm --grow --bitmap=none /dev/md1

you only need the bitmap for actions like re-shaping and not for usual operation

Another performance boost might come from changing the max and min speeds. You can check your current setting with 

         cat /proc/sys/dev/raid/speed_limit_min 

and 
    
         cat /proc/sys/dev/raid/speed_limit_max

I did set set the values using

echo 50000 > /proc/sys/dev/raid/speed_limit_min 
echo 200000 > /proc/sys/dev/raid/speed_limit_max

Of course this means higher load from the re-shaping that you might notice in the performance of usual access.
But you can always reduce the speed_limit_min if you are working with the array and increase the value if you do not need the array for work.

of course "cat /proc/mdstat" tells you about the current speed and finishing prediction.

With these settings the re-shaping of an 7 disk 20TB RAID 6 array into a 9 disk 28TB array took only about 20 hours.

I hope this helps in the future.

---

