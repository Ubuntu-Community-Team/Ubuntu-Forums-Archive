---
title: "Ubuntu MD5"
date: 2007-02-17
forum: General Help
---

### Post by sooqing on 2007-02-17
Hi everyone!

I just received 10 Ubuntu 6.06 LTS CDROMS from Canonical. I booted them live onto machines with no HDD and performed a md5 hash on them.

#md5sum /dev/cdrom

The official sum is ""E2E ... 58E" but I got "F44 ... D6E". All 10 CDs have the same sum.

I would like to ask if anyone can perform the same thing and check if it was the same. I am using GNU/Linux for an opposition party in a country with oppression and I hope the CDs are not fake, ie. with trojans.

---

### Post by sooqing on 2007-02-17
bumpz...

---

### Post by sooqing on 2007-02-21
bumpz...

---

### Post by Ramses de Norre on 2007-02-21
> **sooqing said:**
> Hi everyone!

I just received 10 Ubuntu 6.06 LTS CDROMS from Canonical. I booted them live onto machines with no HDD and performed a md5 hash on them.

#md5sum /dev/cdrom

The official sum is ""E2E ... 58E" but I got "F44 ... D6E". All 10 CDs have the same sum.

I would like to ask if anyone can perform the same thing and check if it was the same. I am using GNU/Linux for an opposition party in a country with oppression and I hope the CDs are not fake, ie. with trojans.

There is a difference between 6.06.1 and 6.06, have you got the right official key? (Just a thought, I don't have a dapper cd here to check)

---

### Post by jimbob on 2007-02-21
I just ran md5sum on my CDROM copy of 6.06 LTS and this is what I got:

7590336a8cda13d7aada8333ae4a6958 

Sorry about that.

I read somewhere that running md5sum on the cdrom itself will not match because of extra things like sector labels and inodes that are added to the original .iso file on hard disk.  Please correct me if I'm wrong.

Try copying the data back to an .iso file on your hard drive and running the md5sum on that.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

