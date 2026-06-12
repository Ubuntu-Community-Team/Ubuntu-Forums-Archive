---
title: "Samba Sharing Setup"
date: 2013-11-05
forum: General Help
---

### Post by NM5TF on 2013-11-05
hi Ubu gurus....here I go again ;)

I have 3 distros.....Ubu 12.04.3, Ubu 14.04, Linux Mint14

I have a dedicated Home partition....

I am trying to set up Samba file sharing between the 3,
but am getting "permission denied, you are not the owner"
errors...root is defined as owner....

is it possible to change ownership to my user account ??
I am the only user on this pc, so it doesn't present a
security risk I believe....

TIA,

Tommy

---

### Post by TheFu on 2013-11-05
Are you triple booting or are all 3 OSes running concurrently?
Is there HOME directory encryption involved?

---

### Post by NM5TF on 2013-11-05
> **TheFu said:**
> Are you triple booting or are all 3 OSes running concurrently?
Is there HOME directory encryption involved?

triple booting...each OS in dedicated partition....

did not encrypt Home partition when setting it up

---

### Post by TheFu on 2013-11-05
I am confused.
/home is shared regardless of which OS you boot.
Samba is a network protocol to allow a different system/OS to connect to a running machine with a file system.  With triple-boot, only 1 OS will run at a time ... how will samba work for you?  Is there another machine on the network?  If so, we just want to get Samba working from 1 of the Linux versions first, then ... move on to the others.

Sorry for the questions.  I could completely misunderstand what you need.

---

### Post by jamesisin on 2013-11-05
What is the path to the folder you are attempting to share?

---

### Post by jamesisin on 2013-11-05
If you are triple-booting, you can't use a Samba share to share between the instances since only one of those instances will be running at any given time.

---

### Post by ksraju007 on 2013-11-05
> I am trying to set up Samba file sharing between the 3,
but am getting "permission denied, you are not the owner"
errors...root is defined as owner....

is it possible to change ownership to my user account ??

Chaging ownership should be easy. Just run the below command in a terminal...

[COLOR="#0000FF"]sudo chown -R <username>:<username> /path/to/folder[/COLOR]

Hope this solves your issue.

---

### Post by NM5TF on 2013-11-05
well it looks like I'm the person who is confused...

I guess I didn't realize what Samba does or is used for...

I was trying to access some files from Linux Mint without having to
resort to using root access....

I will have to regroup & do some more reading....I
will repost when I have a better understanding of
what is needed

sorry for the confusion, but thanks for the replies

Tommy

---

### Post by jamesisin on 2013-11-06
If you are running a triple boot system, create a separate partition for sharing files and give it more open access.  Another alternative is to join a domain and use a domain account for access (so that each machine is actually using the same user instead of a unique user per machine).  There are likely many other options.

---

### Post by TheFu on 2013-11-06
Actually, if the uid (the number, not the name) match across all three OSes, then nothing special is needed to access the files besides mounting the place where the files you want to access are stored.  Most of the time, the userid that gets created during installation is (1000) - the "name" doesn't matter or even need to match, just the number. Look in the /etc/passwd to see the number on each OS. 

Of course, if encryption is involved, things are more complex.

Howerver, based on your description, you have 
* 1 /home partition
* 1 swap partition
* 3 Linux partitions ... 1 per OS.

If the files you want to access are in /home, nothing more needs to be done.

To get more help, post the output from **sudo parted -l**.

---

