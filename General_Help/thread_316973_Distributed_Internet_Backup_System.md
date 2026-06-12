---
title: "Distributed Internet Backup System?"
date: 2006-12-11
forum: General Help
---

### Post by Olav on 2006-12-11
I'm putting this in the general section because I think it could be important for everyone. We all make backups of our important data, right? :cool:

In search of a convenient solution I stumbled up on this: [http://en.wikipedia.org/wiki/Distributed_internet_backup_system](http://en.wikipedia.org/wiki/Distributed_internet_backup_system)

It looks like a very good idea. It is basically a P2P system where you send your data to other users (encrypted, so they can't do anything with it) to keep for you, and where you also provide storage for those other users' files.

Unfortunately, the project looks almost dead. Perhaps this is why there are also no packages for Ubuntu.

So, are there any Ubuntu users actually using this? Are there better solutions? Short of paid-for services, of course.

---

### Post by adaptr on 2006-12-11
> **Olav said:**
> It looks like a very good idea.
I beg to differ.

>  It is basically a P2P system where you send your data to other users (encrypted, so they can't do anything with it)
Actually, they can... erm... **DELETE** it.
Which is what a backup system is usually designed to avoid.

---

### Post by Olav on 2006-12-11
> **adaptr said:**
> I beg to differ.

Actually, they can... erm... **DELETE** it.
Which is what a backup system is usually designed to avoid.
Yes, they could delete it. But I believe the system takes care of that by storing every backup in such a way as to guarantee redundancy. But then, it would depend on enough users actually participating. Which is one of the reasons why I am asking: are there any users here.

I do have my doubts as well, but I still think something like this could work. Perhaps the project needs extra developers, so more progress can be made?

---

### Post by adaptr on 2006-12-12
I think you're underestimating my point.

It is analogous to finding files on P2P sites, or torrents - anything that distributes software.

While you know that there are potentially dozens of machines holding the data you are after, can you ever be absolutely **certain** that you will find all of the pieces?

Statistically, you can never be certain of that - and you do want to be certain when you back up your data.

And it's not just dependability - it is plain security as well.

No matter what kind of uber-encryption will be used to transmit and store that data - and it is **very** expensive to perform 1024 or 2048 bit public key encryption on the *data* - you are, essentially, giving away your data to potential hackers.
It would be trivial for any participant to copy all data that is stored on his machine, even if only for a second, and perform ever-more efficient brute force attacks on it - which may take months, who cares, he has **copied all the data**.
Not only that, his collection of encrypted files just keeps growing as long as he participates in this scheme.

This last makes it only provably secure when there are a lower bound of people participating - and guess what, you cannot force that as a requirement, as it will always be voluntary.

---

### Post by technodigifreak on 2006-12-12
adaptr is right, the other users can delete it.  I have used it and was not impressed, besides it's still only in Alpha stage.  

The best option is to purchase space on someone else's servers in a different data center.  Get a business contract with them that states they will not delete your data.  Then rsync the data over ssh to the remote location.

However there are a few, cheap (or free) alternatives.  Setting up an rsync P2P setup with your friends.  This works best with 3 people or more.  A sync's their backup to a directory at both B and C, B sync's their backup to a directory on A and C, and thus, C sync's to a directory on A and B.  That way everyone has at least 2 "online" backups.  Of course the size of the backup and the physical locations should be taken into account, but this system works very well.

---

