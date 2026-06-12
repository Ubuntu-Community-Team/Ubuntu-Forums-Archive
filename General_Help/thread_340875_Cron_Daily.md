---
title: "Cron Daily"
date: 2007-01-17
forum: General Help
---

### Post by bananabob on 2007-01-17
I am getting the following message from Cron Daily:

> 
run-parts: /etc/cron.daily/beagle-crawl-system exited with return code 1

Can any one help me find the reason?

Thanks
James

---

### Post by dcstar on 2007-01-17
> **bananabob said:**
> I am getting the following message from Cron Daily:


Can any one help me find the reason?

Thanks
James

Run it in a terminal and look at the messages.

---

### Post by bananabob on 2007-01-17
David
I tried to run it from command line and got no messages. So I took a look at the code and found this

> 
# Mono requires a writable wapi directory
MONO_SHARED_DIR=`mktemp -d -p $TMPDIR .beagleindexwapi.XXXXXXXXXX`|| ( echo "Can't create wapi directory!" ; exit 1 )
chown $CRAWL_USER $MONO_SHARED_DIR


It would seem that a RC of 1 is due to inability to create the wapi directory - whatever that is?

Regards
James

---

### Post by dcstar on 2007-01-18
> **bananabob said:**
> David
I tried to run it from command line and got no messages. So I took a look at the code and found this



It would seem that a RC of 1 is due to inability to create the wapi directory - whatever that is?

Regards
James

If the "tmpdir" is set from a user login, then that could be a problem as cron runs it with root credentials.

You may be able to edit the script and set that variable to your own user directory and see if things work better.

---

### Post by bananabob on 2007-01-18
The TMPDIR is set thus:
> export TMPDIR=/tmp


On looking into  tmp I find that the directory has a 
> beagleindexwapi.dqTKxV5715 directory 
already in there.

Do you think that this directory needs to be deleted so that the script will work correctly?

I will try that tonight and see what happens tomorrow.

Cheers
James


ShhheeeZ I just realised that that is stupid because if it is in /tmp it will be deleted over a reboot anyway!
Oh well never mind I will take another look at the script.

---

### Post by bananabob on 2007-01-18
There is a bug open for this problem. It gives a resolution. The bug number is [63416]("https://launchpad.net/ubuntu/+source/beagle/+bug/63416")

---

