---
title: "quick ssd trim question"
date: 2016-10-21
forum: General Help
---

### Post by jaarvidsen on 2016-10-21
ive got one 1tb ssd, which is split into a / and a data partition mounted in /media/data
ive enabled trim on the / partition, but im unsure of the syntax for the data partition

my fstab looks like this
-------------
# / was on /dev/sda1 during installation
UUID=e8d62866-10fc-44ae-84f3-46bff4ecf1a3 /               ext4    discard,errors=remount-ro 0       1
# /media/data was on /dev/sda2 during installation
UUID=cbb74593-7bd5-43a2-bf16-16bfd01a7553 /media/data     ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=6f47555c-bd67-4a9a-8047-f94d63a2b928 none            swap    sw              0       0
-------------
so i guess i wanna add the discard option to the data partitoon as well, do i just make it discard,defaults?

thanks

---

### Post by QIII on 2016-10-21
Hello!

The discard option has come under heavy fire for some time and many recommend strongly against its use -- that includes Theodore Ts'o, the developer of ext4.

I use a daily cron job to trim.  

fstrim-all will trim all mounted filesystems that support trim.

---

### Post by jaarvidsen on 2016-10-21
so remove the discard bit from fstab and simply create a cron job that runs the command 'fstrim-all' ? thats it?

also this [http://manpages.ubuntu.com/manpages/trusty/man8/fstrim-all.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/fstrim-all.8.html) it only runs on samsung and intel ssd's by default
mines a Corsair Force Series LE 960GB - you think its safe?

---

### Post by QIII on 2016-10-21
If you are concerned, you can just have your cron job trim each of your supported partitions individually in sequence.  I actually have mine doing that and reporting to a very minimal log.

---

### Post by jaarvidsen on 2016-10-21
thanks for help! ill do that then. i always thought discard was needed, at least thats the info i found like 4 years ago when i got my first ssd, and thats what still is in my howto_trim_ssd text file which ive kept since then

---

### Post by oldfred on 2016-10-21
I believe this still has some of the best info on SSD.
I do add noatime in fstab.
        [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 
    
I add my own daily trim as a cron job. It shows a second mount /home, you can just use your mount of /media/data. I like that it also adds a log file.
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

I do not have /home so commented out with #.
 sudo nano /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD 
   #!/bin/sh
# trimSSD
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

---

### Post by jaarvidsen on 2016-10-21
so ill add noatime like this
# / was on /dev/sda1 during installation
UUID=e8d62866-10fc-44ae-84f3-46bff4ecf1a3 /               ext4    noatime,errors=remount-ro 0       1
# /media/data was on /dev/sda2 during installation
UUID=cbb74593-7bd5-43a2-bf16-16bfd01a7553 /media/data     ext4    noatime,defaults        0       2


and then add jobs to root's crontab ( i prefer crontab to using /etc/cron.daily) looking like:
50 18 * * * sudo fstrim -v /  
55 18 * * * sudo fstrim -v /media/data

?

thanks for all help

---

