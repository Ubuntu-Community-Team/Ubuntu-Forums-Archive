---
title: "Script backup/check network share mounted"
date: 2013-02-22
forum: General Help
---

### Post by il pepe on 2013-02-22
Hi,

I'm setting up an automated backup system for my laptop.
I backup to my network share.

Currently is scripted some simple rsync lines, which work. I would like to do this automated, so I would be using CRON.

The only thing is I work in differnent setups: Home and at work...
And I only have the share at home.

The share is mounted as a folder, so i guess if the share isn't mounted, let say at work, then i suppose the cron job will start backing up into this empty mount folder...

How can i solve this?
I need to check first if the share is mounted, but i have now clue how to do this...

best regards,
Pieter

---

### Post by albandy on 2013-02-22
You can use mount to show your mounted devices and grep to filter a text so if you type
mount | grep "text"
it will display the lines containing "text"
if no line is displayed means that there is no line containing "text"

So for example, if my backup mountpoint is /backup if I type

```

RESULT=$(mount | grep "/backup")

if [ "$RESULT" == "" ]
then
echo Disk not mounted 
#add your actions here
else
echo Disk mounted 
#add your actions here
fi

```

---

### Post by il pepe on 2013-02-22
Blazing fast reply!
Thanks, I'll give it a try this afternoon (not connected to the share right now, so can't test it :-) )

---

### Post by il pepe on 2013-02-22
mm

---

### Post by dcstar on 2013-02-22
> **il pepe said:**
> mm

If it is solved then MARK the thread.

---

### Post by schragge on 2013-02-22
I'd rather simplify it a bit further
```

if findmnt -no fstype /backup >/dev/null; then
   echo Disk mounted
else
  echo Disk not mounted
fi

```

---

