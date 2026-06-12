---
title: "Shell script to check folder size"
date: 2007-10-04
forum: General Help
---

### Post by MikePS on 2007-10-04
Hi all,

I am at work right now, and my superiors asked me to write/find a shell script for the Ubuntu 6.06 Server edition that checks a folder size, and if it's above a certain limit, it will send an email.

I found [this](http://www.cyberciti.biz/tips/shell-script-to-watch-the-disk-space.html) and it works perfect, but this script checks your harddisk/filesystem, and not the folders.
Can anyone here help me find or help me create a script like that??

I thank you in advance,

Mike

---

### Post by McNils on 2007-10-04
Use "du -sk dir" to finds out folder size.

---

### Post by MikePS on 2007-10-04
I know how to check the folder size, my request was slightly different.
Maybe I didn't put it the right way, either way, example:

Folder reachers 500 MB which is the folder's limit.
When the folder reaches 500MB an email is send to me.

That's practically what we want to have in a script which we wil put in /etc/cron.daily

---

### Post by SeanTater on 2007-10-04
This should do the whole kit and kaboodle

```
folder='/path/to/folder' ; (( `du -sm $folder | cut -f 1` > 500 )) && ( echo "$folder too big" | mail username@server)
```

Mind you, you will need to have exim4 or postfix installed to email from the command line

---

### Post by MikePS on 2007-10-10
Thanks a lot!
I believe I am on the right way now!
Could you explain how this script works so I can edit it if I need to? I am assuming the 500 means 500 MB right?

I tried running this script though, but nothing happens.
I have a folder that is 61 MB, I changed the limit to 50, and ran the script, but it seems like nothing happens, and no email is send.

What could be wrong?
Thanks again for all your help!
And yes, postfix is installed : )


[EDIT]

My colleage fixed it for me, and it works now.

He changed it to:

```
 #!/bin/sh

FOLDER='/path/to/folder';
MAXSIZE='50';
MAILADRES='username@server.com';

if [ "du -sm $FOLDER | cut -f 1" > "50" ] ; then
        echo "$FOLDER too big" | /usr/sbin/sendmail $MAILADRES
        echo "test";
fi

```

I hope this helps other people who are looking for the same script.
Thanks everyone for all your help.
Thread can be closed!

[/EDIT]

[EDIT2]

Ok, I need your help one more time, seems like this script sends an email saying I am over the size, even when I am not.
The folder it checks is 61 MB, and the limit is set on 500MB now.

Script:
```

#!/bin/sh

FOLDER='/path/to/folder';
MAXSIZE='500';
MAILADRES='username@server.com';

if [ "du -sm $FOLDER | cut -f 1" > "$MAXSIZE" ] ; then
        echo "$FOLDER passed maxsize of $MAXSIZE MB please delete some files." | /usr/sbin/sendmail $MAILADRES
        echo "test";
fi

```

I am assuming the > sign doesnt quite work.
If I put an = sign there, nothing happens. (no emails get send).

Thanks in advance again!

[/EDIT2]

[EDIT3]

Is it also possible to check multiple folders in one script, and send the emails seperate?

[/EDIT3]

---

