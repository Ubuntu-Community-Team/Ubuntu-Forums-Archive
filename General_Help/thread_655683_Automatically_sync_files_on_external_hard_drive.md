---
title: "Automatically sync files on external hard drive?"
date: 2008-01-01
forum: General Help
---

### Post by FRuMMaGe on 2008-01-01
I bought an external hard drive for backup purposes. I have different folders allocated to different file types (pictures, movies, 3d models, etc) and I would like to have Ubuntu automatically synchronize them with the corresponding folders on the external drive.

This is because I do not want my drive to break and leave me no way to keep the files I currently have.

---

### Post by tcpip4lyfe on 2008-01-02
Not sure if I'm understanding the question correctly but you might look into DRBD. 

[http://www.drbd.org/](http://www.drbd.org/)
[http://www.calivia.com/blog/mike/drbd-on-ubuntu-dapper-drake-and-gentoo](http://www.calivia.com/blog/mike/drbd-on-ubuntu-dapper-drake-and-gentoo)

We use it at work to sync files in real time on a redundant server. It's pretty straight forward on 2 nodes but Im not sure if you can do it with just one so you'll have to check it out.

Make sure you understand what you're doing first though.  There are some nasty commands in there.


Other then that a simple copy script on that runs everyday. Something like:

cp /home/data /mnt/external/data

That's probably easiest.

---

### Post by FRuMMaGe on 2008-01-02
> **tcpip4lyfe said:**
> Not sure if I'm understanding the question correctly but you might look into DRBD. 

[http://www.drbd.org/](http://www.drbd.org/)
[http://www.calivia.com/blog/mike/drbd-on-ubuntu-dapper-drake-and-gentoo](http://www.calivia.com/blog/mike/drbd-on-ubuntu-dapper-drake-and-gentoo)

We use it at work to sync files in real time on a redundant server. It's pretty straight forward on 2 nodes but Im not sure if you can do it with just one so you'll have to check it out.

Make sure you understand what you're doing first though.  There are some nasty commands in there.


Other then that a simple copy script on that runs everyday. Something like:

cp /home/data /mnt/external/data

That's probably easiest.

Thanks for this, I never thought of using a bash script.

Is there a way to make it automatically ignore duplicates (not ask for prompt) so I can run it in the background while only rewriting the necessary data

---

### Post by mdurham on 2008-01-02
take a look at 'rsync', I think that's the right tool for you.

---

### Post by capink on 2008-01-02
> **mdurham said:**
> take a look at 'rsync', I think that's the right tool for you.

I second that. If you want it done automatically, just make a script and place in either /etc/cron.daily or /etc/cron.weekly

---

### Post by berthiggins on 2008-01-02
Or if you want do do it through a GUI then Grsync could be what you need it is in the repo:)

---

### Post by FRuMMaGe on 2008-01-02
> **capink said:**
> I second that. If you want it done automatically, just make a script and place in either /etc/cron.daily or /etc/cron.weekly

Can you give me an example of a simple bash script that will copy all the files in my home directory (while maintaining the directory structure) to the external hard drive and not to overwrite any previously existing files?

---

### Post by capink on 2008-01-02
```
#!/bin/bash
rsync -a /path/to/your/home/* /mount/point/of/your/extenal/drive
```

Edit: Don't forget to make the script excutable.

---

### Post by rubicon on 2008-01-02
By the way, I too am wondering how to back up my files _at the very moment when new drive being connected_. Cron will do it from time to time, but I need it to be done at once. Where should I look for some tips?

I know that drives is mounted automatically by HAL, so I just need to write some script and put it in /etc/hal.d/mount (rough guess). Am I on the right way?

---

### Post by tcpip4lyfe on 2008-01-02
Taken from the rsync site:


#backup to a spare disk


#I do local backups on several of my machines using rsync. I have an
#extra disk installed that can hold all the contents of the main
#disk. I then have a nightly cron job that backs up the main disk to
#the backup. This is the script I use on one of those machines.
```

    #!/bin/sh

    export PATH=/usr/local/bin:/usr/bin:/bin

    LIST="rootfs usr data data2"

    for d in $LIST; do
	mount /backup/$d
	rsync -ax --exclude fstab --delete /$d/ /backup/$d/
	umount /backup/$d
    done

    DAY=`date "+%A"`
    
    rsync -a --delete /usr/local/apache /data2/backups/$DAY
    rsync -a --delete /data/solid /data2/backups/$DAY

   

```
The first part does the backup on the spare disk. The second part
backs up the critical parts to daily directories.  I also backup the
critical parts using a rsync over ssh to a remote machine

---

