---
title: "Alternatives to the cp command?"
date: 2008-02-07
forum: General Help
---

### Post by krelverehan on 2008-02-07
I am just curious if there is a command line alternative to the CP command? I mainly use that command to back-up all my media to my external hdd. So quite often I am transferring upwards of 120gbs. I am comfortable on the command line, but is there a command that will show the status of the transfer (a little more advanced than cp -v)?

Thanks!

---

### Post by banewman on 2008-02-07
you can try - rsync - it works well for backups - man rsync in a terminal for usage.
:)

---

### Post by nukie77 on 2008-02-07
if you are using it for backup purposes, have you looked at rsync?

---

### Post by macogw on 2008-02-07
Since they didn't describe rsync, it's nice because it only copies the first time. Then it has an index and each subsequent backup is just updating the old backup based on what has changed in the index.

---

### Post by krelverehan on 2008-02-07
No, I haven't, I'll give it a shot, though!

---

### Post by bodhi.zazen on 2008-02-07
Or you can dd or you can tar (tar allows compression).

---

### Post by krelverehan on 2008-02-07
Is there a way to us rsync to automatically back-up my home folder to my external hdd at, lets say, 5am every morning?

---

### Post by geo909 on 2008-02-07
That won't answer your last question.
Just wanted to mention that if you want to copy the contents of folder 
/path/to/folder to /path/to/destination/folder
you have to type:
```
rsync -a /path/to/folder[COLOR="Red"]/ [/COLOR]/path/to/destination/folder
```

or if you don't add that backslash, it will create a sub-directory in the destination folder, containing all the stuff.

ANyway, here is a very good article/howto about rsync, it helped me a lot:
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

---

### Post by krelverehan on 2008-02-07
This may sound like a stupid question (I reckon this is the place for them), but on the site you linked me, geo, I found a useful script that goes like this: 
> 
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

Now how do I use this script? Do I save it to a blank text file and ./ it? Sorry, I am not sure.

---

### Post by bodhi.zazen on 2008-02-07
I advise you save it , as a text file, in ~/bin

Then 

chmod u+x ~/bin/file_name

then it should be in your path. If not, execute it with 

~/bin/file_name

(Or add ~/bin to your path in .bashrc)

---

### Post by geo909 on 2008-02-07
> **krelverehan said:**
> Now how do I use this script? Do I save it to a blank text file and ./ it? Sorry, I am not sure.

 Well, you can run it as you said, it's not mandatory to save it to your bin folder or add it to your path.
Just set the right permissions.

---

