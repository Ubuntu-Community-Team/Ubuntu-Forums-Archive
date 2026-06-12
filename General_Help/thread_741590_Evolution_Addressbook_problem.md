---
title: "Evolution Addressbook problem"
date: 2008-03-31
forum: General Help
---

### Post by schase02 on 2008-03-31
Hi folks,

When I try to look at the addressbook - or add a contact I get the error message "unable to load addressbook"

Googling some, I copied the addressbook to a diff name, recreated it, and copied the addressbook back - chmod'd 744 to all, my username is the owner on the files.  No luck.

I cannot seem to import the db file format either.  and I tried completely removing evolution, re-adding it - and copying the files back onto itself.  No luck.

I'm thinking now that the addressbook must be corrupted in some fashion.  Is there another way to get the contacts back into it?

---

### Post by schase02 on 2008-04-01
I tried another complete uninstall (removed .evolution directory also) and reinstall.

still no joy.

---

### Post by tribeaffeldt on 2008-06-22
I have a similar problem.  I imported my Evolution profile from an earlier version on Fedora 6 or 7.  The mail came in fine, but not the contacts.  Worse yet, I cannot create any new contacts.

/home/tribeaffeldt/.evolution/addressbook/local/system has two files in it

1) addressbook.db
2) addressbook.db.summary

I tried changing the permissions on these from Read Only to Read/Write.  That didn't work.

I'm not sure what else to try.:confused:

---

