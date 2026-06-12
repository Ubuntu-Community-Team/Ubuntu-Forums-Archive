---
title: "Migrating from ubuntu one – can it be this simple?"
date: 2014-04-15
forum: General Help
---

### Post by BigJules on 2014-04-15
I’ve been using U1 as backup thru deja-dup for years, with full satisfaction. With U1 on its way out, now what?

Could it be as easy as leaving everything in place as is, just going to deja and changing the Backup Location in Storage to point to Local folder > my Dropbox folder? 

Five seconds work! :P

As far as I can see, I get it all: 
proper encryption, fine grain select of folders to back up, incrementals, control over auto/not, frequency, visual prompt of progress, accessible to new build computer etc

As far as I can see, there’s these unknowns:
Restore: will it? will nautilus integration still work? Will Dropbox handle incrementals into the full backup?

Would think so to all, but one of you out there is probably going to spoil my day...

---

### Post by buzzingrobot on 2014-04-15
DejaDup would create a new backup in your local Dropbox folder and the Dropbox daemon that runs on your system would sync that folder with Dropbox. To DejaDup, it's just another local folder.

Remember to exclude that folder from the backup, and I don't think I'd go for a restore without pausing Dropbox syncing first.

---

### Post by sffvba[e0rt on 2014-04-15
My biggest concern would be if something happens to the back-up on the local drive (accidentally deleting it / corruption), this will again sync to Dropbox and might compromise the back-up...

---

### Post by twinkel1961 on 2014-04-15
I migrated to copy.com which started off with a free 15Gb storage space. Clients exist for Android, Apple, Windows and Linux.

If you start with this link you and I will both get an additional bonus of 5Gb, so you will end up with 20Gb to start with: [https://copy.com/?r=VZlg7v]("https://copy.com/?r=VZlg7v")

Data is downloaded to all clients (except smartphones). I use it to share common scipts and data with different machines.
The only draw-back I found was with Android, where it does auto-upload photos but not the photos from bluetooth, whatsapp etc. programs.

---

### Post by BigJules on 2014-04-15
Wouldn't this be the same as if you'd wrecked your original data anyway?
(This for not found above)

---

### Post by sffvba[e0rt on 2014-04-16
> **BigJules said:**
> Wouldn't this be the same as if you'd wrecked your original data anyway?
(This for not found above)

Thing is, if you wreck your data on your system you restore it from your "backup".  If your backup also got trashed where are you going to restore from then?  Dropbox continuously syncs to the cloud, so if the backup on the local system which is in the Dropbox folder gets corrupted the changes will upload to the cloud too.

---

