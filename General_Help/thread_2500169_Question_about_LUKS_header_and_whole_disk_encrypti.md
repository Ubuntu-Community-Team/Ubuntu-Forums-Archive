---
title: "Question about LUKS header and whole disk encryption"
date: 2024-08-24
forum: General Help
---

### Post by wjbmd48 on 2024-08-24
I use LUKS whole disk encryption on my Lubuntu systems. I have occasional initramfs startup problems, and I finally figured out that it's very useful to know the system's LUKS header to insert into the fsck utility string for getting the system back.

My question is, how securely should I store my header string?

I.e., is it possible to figure out the encryption code from the header string, or is it simply a hash that can't be worked backwards?

Thanks!

---

### Post by TheFu on 2024-08-25
It is a judgement call, as with most things security related.

Do you post your password manager's DB on the internet?  Sure, it is encrypted, but why risk it, right?  Bring that same skepicism to how secure you should treat the LUKS header dump information.  Why tempt the bad guys?

OTOH, I've never needed any LUKS header since I started encrypting my laptops around 2015.  I do have excellent backups, so if something terrible should happen, I'd wipe the system or replace the SSDs and follow my system restore process to get everything back.  Sure, it would be a bad day, but no data would be lost.  I've had 2 SSDs fail since then and one in my main VM server is starting to complain with SMART data issues now.  

Daily, automatic, versioned, backups are the solution to so many issues.  I get they are boring.  They do actually work for many data issues and security problems.  For people thinking their RAID solves issues.  There are times when RAID failures require flushing everything and starting over .... using backups.

---

### Post by wjbmd48 on 2024-08-25
Thanks! Very helpful.

But my question is, can the encryption code be cracked from the LUKS header?

Thanks for taking the time,

Bill

---

### Post by currentshaft on 2024-08-25
> **wjbmd48 said:**
> Thanks! Very helpful.

But my question is, can the encryption code be cracked from the LUKS header?

Thanks for taking the time,

Bill

Yes. The LUKS header is the only thing which differentiates random data from your encrypted volume, which cannot otherwise be "cracked".

---

### Post by TheFu on 2024-08-25
Can someone, somewhere, crack LUKS with the additional information provided in the LUKS header?  

Who can say?  It is impossible to know.  

Who are you worried about attacking your encryption?  That's the real question.  Can the NSO, NSA, Cozy Bear, SVR, or APT31 crack it?  Impossible to know.

Can't a 12 yr old with limited computer skills or his mother crack it?  99.99% no.  Can I?  99% no, probably higher, but if you have a terrible passphrase or token security, the likelihood of being cracked goes up astronomically.

The data is strongly encrypted.  Access to the data keys is controlled by access to the header information.  This is why adding or changing a passphrase for LUKS doesn't require any changes to the data storage. Just the header information "slots" are modified. If any of the 8 slots can be accessed by "good guessing", then all the encrypted data is unlocked.  At least that's how I think it works.

The manpage for cryptsetup has more details and the design of LUKS1 and LUKS2 can be found online, if you search.  LUKS2 closes some big gaps that were in LUKS1, so people who care greatly about security AND have a valid reason for being worried should migrate to LUKS2 sooner than later.  Normally, that would mean a fresh install is needed.

If you look at the data contained in the header, it should be obvious that some of this would be helpful to anyone attempting to crack the encryption.  If you like, store the header dumped information inside your password manager.  I keep lots of things inside mine (but not the LUKS header).

---

### Post by wjbmd48 on 2024-08-25
OK, all very helpful, thanks to all of you for answering my question!

Bill

---

