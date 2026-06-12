---
title: "Free up space - Delete install files?"
date: 2006-07-05
forum: General Help
---

### Post by ahaslam on 2006-07-05
Hi,

Ive noticed that if I download & install something with apt-get or Synaptic, then remove the application(s), it doesn't require downloading again if I choose to reinstall it. 

I would like to know where these install files are stored and whether it's safe to remove them? I would also like to know if it's possible to automatically remove such files once an installation is complete?

I have a decent internet connection and don't mind re-downloading, if it means freeing up a significant amount of disk space.

Thank you,

Tony.

---

### Post by 23meg on 2006-07-05
They're kept in the apt cache, in /var/cache/apt. It's safe to remove them. You can adjust cache preferences in Synaptic's preferences under the "Files" tab.

---

### Post by thunderduck3141 on 2006-07-05
well that all depends
i think they are stored in var, not sure
but if you have a big harddrive, lets say more than 80gigs, then dont bother, i keep everything (and i install A LOT) and it only takes up about 7 gigs

---

### Post by ahaslam on 2006-07-05
[QUOTE=23meg]They're kept in the apt cache, in /var/cache/apt. It's safe to remove them. You can adjust cache preferences in Synaptic's preferences under the "Files" tab.[/QUOTE]
Thank you very much :D

---

### Post by ahaslam on 2006-07-05
[QUOTE=thunderduck3141]well that all depends
i think they are stored in var, not sure
but if you have a big harddrive, lets say more than 80gigs, then dont bother, i keep everything (and i install A LOT) and it only takes up about 7 gigs[/QUOTE]
I've used 20Gigs of a total 40, so don't really want to keep these files, as I'm constantly adding to the disk.

Thanks for your view though,

Tony.

---

### Post by zhoux on 2006-07-05
the manual code to clean is "sudo apt-get autoclean" and "sudo apt-get clean"...also i think that once the installed files take up a certain percentage of your harddrive space, apt-get automatically cleans it...

---

### Post by ahaslam on 2006-07-05
[QUOTE=zhoux]the manual code to clean is "sudo apt-get autoclean" and "sudo apt-get clean"...also i think that once the installed files take up a certain percentage of your harddrive space, apt-get automatically cleans it...[/QUOTE]
Thank you,

What's the difference between them? Does the 'autoclean' set it automatically delete the installation files after an install? 

Thanks again,

Tony.

---

### Post by zhoux on 2006-07-05
i'm not too clear on the differences between autoclean and clean....but i know 'clean' command clean more stuff....

and...no...autoclean doesn't mean automatic cleaning....

though that would be nice :)

Edit: according to this [thread]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=sudo+apt-get+autoclean")
sudo autoclean cleans partial packages....
so sudo clean would clean everything....

23meg's explanation is much better...

thanx

---

### Post by 23meg on 2006-07-05
[QUOTE=Anthony Haslam]What's the difference between them? Does the 'autoclean' set it automatically delete the installation files after an install? 
[/QUOTE]

The following is from the manpage for apt-get, which you can access with ```
man apt-get
```
> 
**clean ** 
clean clears out  the  local  repository  of  retrieved  package
              files.   It   removes   everything   but   the  lock  file  from
              /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/.
              When  APT is used as a dselect(8) method, clean is run automati&#8208;
              cally. Those who do not use dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.

**autoclean**
              Like  clean,  autoclean  clears  out the local repository of re&#8208;
              trieved package files. The difference is that  it  only  removes
              package  files that can no longer be downloaded, and are largely
              useless. This allows a cache to be maintained over a long period
              without  it  growing  out  of  control. The configuration option
              APT::Clean-Installed will prevent installed packages from  being
              erased if it is set to off.



---

### Post by ahaslam on 2006-07-05
Thank you both for clearing thing up. I will run 'sudo apt-get clean' later.

Thanks again,

Tony.

---

### Post by ahaslam on 2006-07-05
I looked in /var/cache/apt/ - there was 387MB worth of stuff.
I ran "sudo apt-get clean" - it's all gone!
I have set Synaptic to delete the files after installation.

My sincere thanks,

Tony.

---

