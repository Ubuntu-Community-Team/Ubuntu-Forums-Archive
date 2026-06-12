---
title: "How to back up files from a damaged linux system"
date: 2008-07-09
forum: General Help
---

### Post by DinoBoy on 2008-07-09
Now that i have given up finding a solution to repairing my HALD issues with my laptop ( [http://ubuntuforums.org/showthread.php?t=852775](http://ubuntuforums.org/showthread.php?t=852775) )
 i have decided to reinstall gutsy. 
The problem(s) are: 
1) i can not mount external HD since sudo does not work. 
2) same for the DVD burner.
3) i only have one partition and not enough room to create a new partition and back up to it.
4) If i boot from a liveCD, then all of the above will work, but then i can not access the existing files on the HD. 

I do know su password to the original system. 

Any HELLLP is appreciated!

---

### Post by HalPomeranz on 2008-07-09
> **DinoBoy said:**
> 
4) If i boot from a liveCD, then all of the above will work, but then i can not access the existing files on the HD. 


You should certainly be able to access your local files if you boot from a LiveCD.  "sudo fdisk -l" should show you the available partitions you can mount, and "sudo mount ..." should allow you to mount them (e.g., "sudo mount /dev/sda1 /mnt").

The LiveCD route is the mechanism I'd use to save my data in this situation...

---

### Post by DinoBoy on 2008-08-03
Thanks HalPomeranz!
Just came back from vacation. Helped me clear my head. 
Still, feel really stupid! 
LiveCD mounts all the local HDs but the files are locked because they are locked by the previous OS!
All i had to do was to log to the damaged system under recovery mode as admin. Go to the user acct. and run chmod 777 -R username.
Next time i reboot from liveCD i can access all files on the local HD and now i can back up on an external HD.

---

