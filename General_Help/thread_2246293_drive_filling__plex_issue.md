---
title: "drive filling / plex issue?"
date: 2014-09-29
forum: General Help
---

### Post by Forbees on 2014-09-29
hey been about two years since i've had to ask for help but i guess i'm a little stuck >,<


got an HTPC server at my old house (about 40min drive) that i use to stream my plex content, terraria server, and mumble server


been noticing plex was acting up a little bit, lagging about ever 8 minutes so i VNC's to my HTPC and got warnings that the hard drive was almost full (80SSD for filesystem, seperate raid 5 for media content)

i don't have that many programs installed on the SSD, and i cleared out the trash, downloads folder, and removed a couple programs i don't use anymore.... but i'm still only showing about 1.5 gigs of free space on my main drive.


where else should i look to start deleting garbage? is there a program that'll map out the usage of my drive so i can look easier? i know if i were to reformat and install the programs that i absolutely need i'd only be using about 30-40 gigs, so i need to figure out where this 30 gigs of junk is on my main drive lol


running Ubuntu 12.04LTS - probably going to do a clean install of 14.10 in the near future but i'd have to physically be there to do it. i know that the main drive filling up might not have anything to do with plex acting up but i figure this is where i should start

---

### Post by Forbees on 2014-09-29
guess i might have jumped the gun.. removed wine and PlayOnLinux - both which last i checked didn't have any games installed, and a few other small programs now i'm down to a reasonable drive capacity. but would still like some input on easier ways to figure out what's eating up drive space other than mindlessly removing things lol

---

### Post by Habitual on 2014-09-29
I use this often and it works for me.
```
#!/bin/bash
/usr/bin/du -sk ./* | /usr/bin/sort -n | /usr/bin/awk 'BEGIN{ pref[1]="K"; pref[2]="M"; pref[3]="G";}  \
{ total = total + $1; x = $1; y = 1; while( x > 1024 ) { x = (x + 1023)/1024; y++; } printf("%g%s\t%s\n" \
,int(x*10)/10,pref[y],$2); } END { y = 1; while( total > 1024 ) { total = (total + 1023)/1024; y++; }  \
printf("Total: %g%s\n",int(total*10)/10,pref[y]); }'
``` save it. ( I can it bdu.sh for better disk usage)

chmod it to 700 and stick in in your "$PATH" and cd into any directory and run it.
or you can run it as root or with sudo privileges, otherwise, you'll see "Permission denied" errors

Sample output from the first directory I check when space is an issue (/var/)
```
cd /var/
sudo /path/to/bdu.sh
0K    ./lock
0K    ./run
4K    ./local
4K    ./mail
4K    ./opt
4K    ./tmp
13.4M    ./backups
14.1M    ./log
185.9M    ./spool
427M    ./lib
762.4M    ./cache
Total: 2.3G
```

/var/log/cache is huge, so 
```
cd /var/cache
```
and run 
```
/path/to/bdu.sh
```

You'll get it in no time. :)

I hope that helps.

---

### Post by Forbees on 2014-09-29
nice script! looks like i got 6.7 gigs in /lib/ and about 4.7 gigs in /modules/ 

surprisingly with the 6 years i've been using ubuntu i've still never learned my way around the file system like i have with windows...

---

### Post by Forbees on 2014-09-29
it also says i have over 8 gigs in my home folder, but when i run it inside my home folder i only have 27 megs?

---

### Post by Habitual on 2014-10-01
/home is likely mounted under the root partition, show us the output of terminal > ```
df -hT
``` please.

---

### Post by Forbees on 2014-10-01
```

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       66G   37G   26G  60% /
udev           devtmpfs  3.8G  4.0K  3.8G   1% /dev
tmpfs          tmpfs     772M  1.1M  771M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.8G  324K  3.8G   1% /run/shm
/dev/md0       ext4      3.6T  2.2T  1.3T  64% /mnt/Server-Data

```

---

### Post by Forbees on 2014-10-06
update

i've been out of town the past 4 days, have not done anything to the computer, came home and df -hT is saying that /dev/sdb1 is used at 100%

wtf?

---

### Post by Forbees on 2014-10-06
looks like the computer just froze... locked up and i can't vnc into it anymore..... guess i have to make a drive to be there physically and figure something out :(

---

### Post by Forbees on 2014-10-06
~update update~

letting it sit overnight helped, able to get in via vnc this morning. when ubuntu said my drive was full it pulled up the disk analyzer

according to the disk analyzer, my /mnt/ is taking up 2.4TB and that's why i have no room....  i have my 4TB RAID5 mounted in /mnt/ and even transmission which writes directly to the RAID is giving me drive full errors even though i still have about 1.3TB of unused space. i remember the first time i set this up on... i think it was 10.04... the RAID would try to auto-mount in /media/ which caused problems like this and it was fixed by going to /mnt/

so what do i need to do to remind ubuntu that my raid5 and filesystem ssd both are only about 60% full and are not the same drive?

---

### Post by Forbees on 2014-10-06
updateX3

unmounted the RAID and it still thinks its full... now both df -hT and ubuntu's disky analyzer say /home is using about 48gigs, but the contents inside them (disk analyzer and the script you provided) are only a few hundred megs

still unable to figure out where this mysterious data is coming from that doesn't seem to exist lol. did do some cleaning in the hidden home folders, found folders with files for programs i uninstalled (steam POL etc)

---

### Post by Forbees on 2014-10-23
well i guess this just means i'll have to do a clean upgrade to 14.04 or 14.10 then :-p been putting that off for awhile

---

### Post by Forbees on 2014-10-27
final update

found a 48gig file ~/.xsession-errors.old

and removed it :D that takes care of the why the home folder was saying its full with no signs of why it's full

had to ```
ls -lah
``` to find it

---

### Post by Habitual on 2014-10-28
So, you didn't run [bdu.sh]("http://ubuntuforums.org/showthread.php?t=2246293&p=13132179#post13132179") in your /home/<x> directory?

---

### Post by Forbees on 2014-10-28
i did, but it didn't show that file in the list. bdu.sh was only showing 8 gigs in the home folder

---

### Post by Habitual on 2014-10-28
> **Forbees said:**
> i did, but it didn't show that file in the list. bdu.sh was only showing 8 gigs in the home folder

I just noticed this myself. It only reports on Directories!
Well. I didn't write it so feel free to make it better. :)

I guess the idea is get a size for a directory and then cd into it and```
ls -hal *
```?

---

### Post by Forbees on 2014-10-28
apparently ```
ls -hal
``` and ```
ls -lah
``` are the same thing

but that was how i found it... still not sure why i'd have a  ~/.xsession-errors.old taking up 48 gigs

---

### Post by Habitual on 2014-10-29
> **Forbees said:**
> apparently ```
ls -hal
``` and ```
ls -lah
``` are the same thing

Yes, they are. I use "-hal" as a reference to HAL9000

> **Forbees said:**
>  but that was how i found it... still not sure why i'd have a  ~/.xsession-errors.old taking up 48 gigs
It may have been collecting xsession "errors" since the day you installed the OS.

Doesn't hurt anything to nuke it.
Reading some of it may be an issue since it is such a large file.
Maybe 
```
tail -n 100 ~/.xsession-errors | less
``` can help determine if it is an issue that needs to be addressed.
Or just nuke it and check it periodically after doing so.

Glad it worked out in any event.

---

### Post by Forbees on 2014-10-29
i nuked it since it had .old on the end. the "new" one is only like 256kB

---

