---
title: "Keeping remote folder synchronized"
date: 2015-09-07
forum: General Help
---

### Post by XBNCPRk on 2015-09-07
This may seem a bit confusing so I'll try to sketch it out as best as possible... 

There are several machines that use a shared ftp folder that is attached to the wifi router. The machine that uses it most often is a media server that writes copies of its performance logs, smart data logs, file lists, etc so that these are all accessible from other machines without waking the media server (and thus waiting for a 16 hd raid array to spin up and mount). On that server, it is mounted locally using curlftp from from fstab using
 ```
curlftpfs#[ftpusername]:[ftppassword]@[xxx.xxx.xxx.xxx]          /local/mount/point   fuse    auto,user,uid=1000,allow_other,_netdev          0       0
```

My issue is that when writing things to this folder, not everything gets created on the remote ftp drive. Some simple text files can get copied to the remote drive correctly (using a seperate script in /etc/network/if-up.d) but other folders/files are created in the same mount point but only stored locally. IE - if i make a folder  /local/mount/point/newstuff it will not show up on the shared ftp drive in its correct directory tree location, only on the local machine. 

Further, this causes a flag when mounting the remote folder about the mountpoint not being empty, and suggests using the nonempty mount option, which I assume is because there are the local-only folders in that same path. 

What I would like is for everything in that local mount point to be mirrored on the remote ftp drive in real time (not via rsync from a cron job, rc.local, if-up.d, etc). I had assumed the bind option when loading it from fstab would handle this but it is incompatible with curlftp (as well as also possibly being the wrong answer all together). 

Any help would be greatly appreciated.

---

### Post by XBNCPRk on 2015-09-08
*shameless bump*

Anyone have any ideas?

---

### Post by papibe on 2015-09-08
Hi XBNCPRk.

Have you look into syncing tools? For instance: [Seafile]("https://www.seafile.com/en/home/"), or [Syncthing]("https://syncthing.net/")?

Just a thought,
Regards.

---

### Post by XBNCPRk on 2015-09-09
Thanks and I have thought about a few of them... while there are a large number of cloud services that can be used for free, this is information that I wish to store locally for a couple different reasons.

---

### Post by papibe on 2015-09-09
Both of those options are softwares, not cloud services. You could run them in your LAN for local syncing.

Regards.

---

### Post by XBNCPRk on 2015-09-09
Sorry, I just glanced at the tops of the pages for each of them, saw diagrams of clouds and dismissed them without reading further. The ftp share though is on a large usb flash drive mounted directly to the router, not a standalone machine. 

The purpose of that is to allow all the machines in the house to hibernate/sleep when not in use - with the exception of the pi's. Those Id rather not use for hosting an ftp share since every power flicker (of which there are many down here in sunny FL) is likely to cause a freeze and/or corrupt the sd card.

---

### Post by XBNCPRk on 2015-09-10
Found the issue finally -- the ftp share was never mounting correctly from the fstab file. 
Deja dup and a couple of the other scripts/apps that were writing to it were mounting it independently, which is why they were able to access it and write but the simpler scripts not. Now if only I could find a simple way to keep logging scripts from creating two time-stamped files if the script takes longer than a minute to run...

---

