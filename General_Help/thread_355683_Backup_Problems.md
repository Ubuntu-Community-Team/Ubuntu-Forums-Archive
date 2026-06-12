---
title: "Backup Problems"
date: 2007-02-07
forum: General Help
---

### Post by hotpurple on 2007-02-07
Hi all,

I've been attempting to use simple backup config for a few days now but have been having a few problems.

The problems seem to revolve around mounting the external usb hard disk I'm using. This works most of the time but occassionally fails to mount, which causes the backup to go into /media/usbdisk instead (which is obviously in my root partition). This causes my system to fall over becuase the hard disk fills up and the system can't write to any files on the root partition.

This appears to happen at random, which is becoming really annoying. I have tried setting a cron job to run just before the backup starts that will mount the external hard disk, but this seem to work at random also.

Please see the following crontab I have setup:

```

# m h  dom mon dow   command
45 2 * * * /etc/init.d/vmware stop
0 5 * * * /etc/init.d/vmware start
40 2 * * * /bin/mount -t xfs /dev/sdd1 /media/usbdisk/

```

My backup runs at 3.00 am

Can anyone see what I'm doing wrong, or suggest a way to stop my hard disk filling up?

Cheers

Chris

---

### Post by DagMan on 2007-02-07
I suppose you could put a file on the usbdisk with an odd name and then test for it being there or not before the backup starts and either abort or reattempt the mount if it is not.

---

### Post by hotpurple on 2007-02-12
Sorry to be a complete newb, but how would I do that?

Cheers

Chris

---

### Post by DagMan on 2007-02-15
I don't really understand what you posted about crontab, but if you can instead have the job schedular launch a script that will look to see if the usbmedia is actually mounted before it starts, and if not then try to remount x amount of times and if it is mounted then run whatever it is that does the backup or else just quit...

For example,  if your cron job is called 'Job-1' and you remove it from running but instead have a script called 'Job-1-handler' running at the sceduled time, and this is not a working script but someone else can surely clean it up and tailor it more to your needs.

```
#!/bin/bash
y=0

function numberone()
{

if [ $y -ge 10 ] ; then
  exit
fi

x=`mount | grep /dev/that-should-be-mounted`

if [ "$x" != "" ] ; then
  Job-1
  exit
else
  mount /dev/that-should-be-mounted
  let y=y+1
  sleep 10
  numbertwo
fi
}

function numbertwo()
{

if [ $y -ge 10 ] ; then
  exit
fi

x=`mount | grep /dev/that-should-be-mounted`

if [ "$x" != "" ] ; then
  Job-1
  exit
else
  mount /dev/that-should-be-mounted
  let y=y+1
  sleep 10
  numberone
fi
}

numberone

```

For example... to test if the device is mounted and if not, try to mount it and test again, wait 10 seconds... test again... and do it 10 times before giving up.
That's a rough and dirty script that won't work until you insert the relevant parts anyway.  you'de have to provide a lot more info for example what the device is that is mounted, like /dev/sdb1 at /media/usb or something.  Also you need to state what the actual job is that cron is set up to run.  

Good luck, I'll try to come back to this but I'm pretty busy recently.

---

### Post by hotpurple on 2007-02-15
Dagman,

Thank you for that script. I'm not at the PC at the moment but I will try to see if that works later.

Again, many thanks

Chris

---

### Post by DagMan on 2007-02-15
Your welcome, I hope you undertood that the script needs editing and will not work as it is right now though.

---

