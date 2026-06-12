---
title: "Backup/restore dual boot laptop question"
date: 2021-02-26
forum: General Help
---

### Post by harry5552 on 2021-02-26
My Dell 7506 Laptop needs to go in for repair but I'm worried if they replace it, I'll lose everything on the SSD.


It's setup as dual boot Win 10/Ubuntu 20.10 and the backup device is a Synology NAS - could anyone recommend any software that could backup/restore  (preferably over WIFI) both OS's in a single operation please?


TIA

---

### Post by blackbird34 on 2021-02-26
If they're replacing the SSD, yes, it's a very good idea to back up first. 

What about Clonezilla?  See [https://clonezilla.org/](https://clonezilla.org/)
"Clonezilla Live enables a user to clone a single computer's storage media,[SUP][[9]]("https://en.wikipedia.org/wiki/Clonezilla#cite_note-9")[/SUP] or a single partition on the media, to a separate medium device." (from [https://en.wikipedia.org/wiki/Clonezilla](https://en.wikipedia.org/wiki/Clonezilla) ) 

There are other alternatives here: [https://alternativeto.net/software/clonezilla/?platform=linux](https://alternativeto.net/software/clonezilla/?platform=linux)

---

### Post by harry5552 on 2021-02-26
Thanks BB, Clonezilla sounds exactly what I'm looking for - it's the keyboard and screen that are dodgy not the SSD so my concern is if they decide its more cost efficient to replace that repair

---

### Post by TheFu on 2021-02-26
Pull the SSD out.
Put in a tiny SSD ($20) with a minimal Linux on it before sending it in.  Plus they won't attempt to install Windows on a 20G SSD.
No worries.

K.I.S.S.

Tools that make clones are many, but those aren't really good backups.  
Backups can be taken while a system is running. Clones cannot.
Backups take just a few minutes every day to accomplish. Clones take hours.
Backups allow many versions, so if crypto-ware happens, you can restore from last week or 37 days ago or 83 days ago, but don't need 83 full copies.

No *backup* tools that I know understand both Linux and Windows in a single command.  Some have different binaries for each OS, but basically work the same on all of them.

---

### Post by harry5552 on 2021-02-27
good idea TheFu but wouldn't that invalidate the warranty? - it's only 3 months old

---

### Post by rbmorse on 2021-02-27
While I agree completely with TheFu about cloning as backup in general, in this particular instance it may be the best solution. 

Clonezilla will do the job, but some people find its ncurses-based interface a little opaque.  It will certainly teach you that a computer is a literal beast that will do exactly what you tell it even when that's not what you really wanted.  If you read screen options carefully, understand how the application defines terms, and take your time, Clonezilla will serve you faithfully.  In my experience most problems arise because the user doesn't understand where and how Cloneazilla differentiates between disks and partitions and ends up telling it to do something other than expected/desired.  The documentation is critical to achieving a successful backup/restore cycle, especially if restoring an image to a device that is a different size from the original source.  

There is a new entrant in the field called Rescuezilla. It appears to be a Clonezilla clone with a GUI front end.  I've played with it a little and had no problems either creating images or writing them back to system devices.  It does a good job of automatically handling situations where the restore target is large enough to hold the source data, but smaller in total capacity than the source drive...a situation that can be problematic with Clonezilla.  

I want to be clear that I don't have extensive experience with Rescuezilla.  My system is dual-boot with Windows 10 but the Linux side does not use filesystems other than the basic FATxx and EXT4 or logical volumes or encrypted filesystems.  

Rescuezilla has a Sourceforge page that has more information.  

[https://sourceforge.net/projects/rescuezilla/](https://sourceforge.net/projects/rescuezilla/)

There's a download link there for the Github page that holds the package.  

Rescuezilla is tons easier to use than Clonezilla, but Clonezilla has been around for years and comes from a know entity.  All I know about Rescuezilla is that the developer appears to be earnest.

---

### Post by TheFu on 2021-02-27
> **harry5552 said:**
> good idea TheFu but wouldn't that invalidate the warranty? - it's only 3 months old

Depends on your location/jurisdiction. Are you really sending it in to the factory? If not, swapping the storage shouldn't matter. There was a ruling in the US a few years ago about this. I've been buying "refurbished" laptops the last few years for 50% off, so the warranties aren't too long.

The way I deal with warranties is whenever I get a new laptop, before I even boot it, I pull the storage out, put it on a shelf and install the storage I want, then load my OS. That way the unmolested storage can be put back when needed for service while the warranty applies.  

After the warranty is up (I put a calendar entry for that), I have a spare HDD/SSD which can be used for backups or sneaker*net or put into a used system that I sell or whatever.

---

### Post by harry5552 on 2021-02-27
> **rbmorse said:**
> While I agree completely with TheFu about cloning as backup in general, in this particular instance it may be the best solution. 

Clonezilla will do the job, but some people find its ncurses-based interface a little opaque.  It will certainly teach you that a computer is a literal beast that will do exactly what you tell it even when that's not what you really wanted.  If you read screen options carefully, understand how the application defines terms, and take your time, Clonezilla will serve you faithfully.  In my experience most problems arise because the user doesn't understand where and how Cloneazilla differentiates between disks and partitions and ends up telling it to do something other than expected/desired.  The documentation is critical to achieving a successful backup/restore cycle, especially if restoring an image to a device that is a different size from the original source.  

There is a new entrant in the field called Rescuezilla. It appears to be a Clonezilla clone with a GUI front end.  I've played with it a little and had no problems either creating images or writing them back to system devices.  It does a good job of automatically handling situations where the restore target is large enough to hold the source data, but smaller in total capacity than the source drive...a situation that can be problematic with Clonezilla.  

I want to be clear that I don't have extensive experience with Rescuezilla.  My system is dual-boot with Windows 10 but the Linux side does not use filesystems other than the basic FATxx and EXT4 or logical volumes or encrypted filesystems.  

Rescuezilla has a Sourceforge page that has more information.  

[https://sourceforge.net/projects/rescuezilla/](https://sourceforge.net/projects/rescuezilla/)

There's a download link there for the Github page that holds the package.  

Rescuezilla is tons easier to use than Clonezilla, but Clonezilla has been around for years and comes from a know entity.  All I know about Rescuezilla is that the developer appears to be earnest.

thanks, never heard of it but will have a play

---

