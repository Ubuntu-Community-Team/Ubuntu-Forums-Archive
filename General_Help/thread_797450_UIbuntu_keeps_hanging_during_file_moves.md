---
title: "UIbuntu keeps hanging during file moves"
date: 2008-05-17
forum: General Help
---

### Post by infocom on 2008-05-17
Hi

I have Ubuntu 8 and everything is fine with it except sometimes during a backup script I have. 

I am using rsync for server backups. I recently added in a folder rotation script, so basically moves all the files from one folder to another before making another copy. I have thousands of files, it can take say 5 minutes to move them all.

During the copy it sometimes just hangs. Completely hangs, not just the program I am using, the whole OS. I have to switch off the computer and restart every time. 

This is obviously quite bad as its a backup script that needs to run every night. I cant have it hang all the time.

Is there a way, a log or something, to find out what is causing it to hang? 

Thanks

---

### Post by infocom on 2008-05-19
does anyone have any idea about this? the specific script which is hanging ubuntu is:-

```

mv /home/myuser/files/5/* /home/myuser/files/tmp/
mv /home/myuser/files/4/* /home/myuser/files/5/
mv /home/myuser/files/3/* /home/myuser/files/4/
mv /home/myuser/files/2/* /home/myuser/files/3/
mv /home/myuser/files/1/* /home/myuser/files/2/
mv /home/myuser/files/tmp/* /home/myuser/files/1/
cp -al /home/myuser/files/2/* /home/myuser/files/1/

```

thanks

---

### Post by infocom on 2008-06-25
Hi. I am still having this issue. Is there anything I can do to investigate why it hangs? 

P.S. I changed the above script to the following because I think the above will move all files, whereas the new one will just rename folders:-
mv /home/myuser/files/5 /home/myuser/files/tmp
mv /home/myuser/files/4 /home/myuser/files/5
mv /home/myuser/files/3 /home/myuser/files/4
mv /home/myuser/files/2 /home/myuser/files/3
mv /home/myuser/files/1 /home/myuser/files/2
mv /home/myuser/files/tmp /home/myuser/files/1
cp -al /home/myuser/files/2 /home/myuser/files/1

---

### Post by phildacey on 2008-07-18
I'm having a similar issue when I run a simple rsync backup command:

```
sudo cp -ivrT /mnt/video/ /mnt/videobackup/
```

It gets 15/20 minutes through then the whole system hangs and needs restarting. I've had a look through /var/log syslog and dmesg but can't see anything that looks amiss (although I can't really say I know what I'm looking for). If anyone thinks they can prod me in the right direction I'll post any system info necessary.

---

