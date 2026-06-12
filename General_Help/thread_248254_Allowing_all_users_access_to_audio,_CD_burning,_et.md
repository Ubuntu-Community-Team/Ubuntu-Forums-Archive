---
title: "Allowing all users access to audio, CD burning, etc."
date: 2006-08-31
forum: General Help
---

### Post by majonesix on 2006-08-31
Hello,

I am currently managing a network of approx. 100 Ubuntu Breezy computers.  All have about 1000 users (and are set up to get all user info via LDAP).  I would like to allow people actually logged in via GDM access (and maybe even those on a virtual terminal) to a computer's audio, along with any other nifty resources that may be present, such as the CD burner or scanner.

If this were a single computer, with a small number of users, I would simply add them to the respective groups for those devices.  But I'm not really sure that adding each new account to each possible group that might be needed is the best way to do things.

Is there a simple way to allow this?  Or even a slightly complex way?

---

### Post by aysiu on 2006-09-01
There's probably some cool command-line/script way to do this, but adding 1000 users via GUI isn't that difficult, actually.

If you go to System > Administration > Users & Groups and then click on the group name (*lpadmin*, in this example), then you can go to **Properties**, select all the users you want (by pressing Control-A and then using Control-click to deselect the users you *don't* want to add) and then clicking **Add**.

You would have to repeat that only eight more times: *dialout cdrom floppy audio dip video plugdev lpadmin scanner*

---

