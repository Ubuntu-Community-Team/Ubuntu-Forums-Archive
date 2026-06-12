---
title: "/home is nearly full"
date: 2013-12-27
forum: General Help
---

### Post by elim-qiu on 2013-12-27
Today I got warning when login to my ubuntu 13.10 saying that /home has only 54.4MB remaining. But I think it has at least 8GB.

What's the possible problem any one can think?

I tried to check desk but I only know how to force check partition /, not the partition /home.

What should I try?

Thanks a lot

---

### Post by deadflowr on 2013-12-27
Home's a separate partition, then run
```
df -h
```
in a terminal
/home should be listed with the total, used, and free marked.
the -h means human-readable, so it'll be easier to understand.

---

### Post by andrew.46 on 2013-12-27
One of the benefits of having a really, really simple partition scheme :

```

andrew@skamandros~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       290G   12G  264G   5% /
tmpfs           1.6G     0  1.6G   0% /dev/shm

```

:)

---

### Post by Bucky Ball on 2013-12-27
Hmm. That is odd, then.

---

### Post by deadflowr on 2013-12-28
baobab(disk-usage analyzer) is another thing to look at.
It'll list the space usage from biggest to smallest.

---

### Post by elim-qiu on 2013-12-28
I've found the problem!

My /home partition was kept from 12.04. Even I did a fresh installation of 13.10, I did not format /home. That way I saved all the personal data from previous usage.

Thought of my /home volume problem, I used the installation usb, runing trial ubuntu and try to copy everything in /home to /bk so that I can re-format /home. It turns out the volume was really full while file browser's property didn't count any hidden folder and .thunderbird directory took many GB's of HDD space!

After remove the app thunderbird mail and delete ~/.thunderbird directory, I got most of space I thought remained. It's just that simple!

But why it downloads all mails from my gmail account? I used IMAP mail server, it says using remote mail folders. Am I wrong that it suppose just fetch the mail list and download the mail only when I open it?

What should I do to prevent download everything from my gmail account? Thanks

---

### Post by VinDSL on 2013-12-28
> **elim-qiu said:**
> What should I do to prevent download everything from my gmail account? Thanks
All I use is IMAP.  Different mail clients handle this different ways.

The 'trick' is to tell your email proggie to download the message headers only -- not the messages themselves.

In Thunderbird, there is a 'check box' setting on each individual account (in "Synchronization & Storage")  that says "Keep messages for this account on this computer".  

Make sure that box is un-checked.  ;)

---

### Post by elim-qiu on 2014-01-03
Thanks a lot VinDSL and others. The .thunderbird size problem was solved. I think there some other hidden folders related to uninstalled software that took nearly 1Gb. It's ok for now but would be nice to have something like registry clean in windows, can clean up my account.

---

### Post by cmcanulty on 2014-01-03
It is tricky at install to keep home, you not only have to not format it but select /home partition and then click change and select /Home otherwise the default is do not use this partition. Caught me once. Wish they would change that or a least put a warning up.

---

