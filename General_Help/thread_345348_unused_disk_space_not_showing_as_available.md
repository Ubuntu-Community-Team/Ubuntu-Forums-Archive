---
title: "unused disk space not showing as available"
date: 2007-01-24
forum: General Help
---

### Post by phiphedog on 2007-01-24
Hi,

I am running edgy and my disk is not showing all the unused disk space as available space to me and I am missing 2 gigs of space?

I was just converting video files and it used up all of my disk space on /

I then restarted the PC to find out that I could not get past the login screen due to the disk being full.

I restarted the PC in recover mode and deleted these files from my /home/username directory using command rm -rf /home/username/filename.* and then an ls -ali to confirm that they had been deleted

I restarted but was still unable to login due to no disk space. I had deleted over 2 gigs of files in the  last command.

I then restarted the PC in normal mode and at the login prompt hit Ctrl+Alt+F1 and from there logged into a shell as a normal user and ran a df -h which showed 

Size  Used  Avail  Use%  Mounted on
31G      29G           0       100%      /

I then deleted more files as a normal user and after a restart was able to login and open up Gnome

Running a df -h now gives

Size  Used  Avail  Use%  Mounted on
31G     28G     690M    98%     /

What has happened to the other 2 gigs of space an why is it not available?
I have tried doing a disk check but with no joy, I'm still missing the 2gigs of space that I deleted as root (#) in recovery mode. 

Does anyone know how I can get this back?

Thanks
Phiphedog

---

### Post by SyvanX on 2007-01-24
Here's my df -h

> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G   31G   38G  45% /

My values don't add up either, it's probably some sort of estimation problem.  Even without the -h option the values don't add up.  They don't even have the correct %Use.

There's a little info here
[http://www.netadmintools.com/art122.html](http://www.netadmintools.com/art122.html)

It basically says, you might have a lot of tiny files eating up your i-nodes.  run df -i to see if your inodes are full.

---

### Post by dannyboy79 on 2007-01-24
use sudo aptitude clean:
which according to man does this;

clean  Removes  all  previously  downloaded .deb files from the package
              cache directory (usually /var/cache/apt/archives).


or use sudo aptitude auto-clean;

autoclean
              Removes any cached packages which can no longer  be  downloaded.
              This  allows  you to prevent a cache from growing out of control
              over time without completely emptying it.

or the other thing, if you delete stuff from nautilus, it'll put it in your trash folders. check those for garbage you don't need! also, your tmp folder may contain stuff you don't need! good luck.

the best thing would be to spend $149.99 and get a 500GB hdd by Western Digital from ([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=TSD-500AAKS](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=TSD-500AAKS)) it's sata 300gb, then get this case from vantec ([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=V13-3252)](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=V13-3252)), it's awesome. you can convert an internal sata port into an external port or the external hdd case can also be used with usb as well. it's pretty sweet!

---

### Post by JamieC on 2007-01-24
Ensure the files are completely removed:
```

rm -rf /home/<username>/.Trash

```

---

### Post by phiphedog on 2007-01-31
Thanks for the replies guys, I found the missing space in the /root/.Trash folder on another computer.

I was using a terminal as root on computer A and I'd deleted the files on computer B over NFS.

Thanks for the speedy replies even though it took me a week to try try em out.

---

