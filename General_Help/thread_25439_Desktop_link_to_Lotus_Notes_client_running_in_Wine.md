---
title: "Desktop link to Lotus Notes client running in Wine?"
date: 2005-04-10
forum: General Help
---

### Post by Bob Owen on 2005-04-10
I use Lotus Notes at work and also at home.  I looked for a Notes client for Linux but was not able to find one, so I set up Wine first and then set up Notes in that which works fine.  Currently I can launch Notes by using the root terminal and typing wine /root/.wine/drive_c/lotus/notes/notes.exe, to which the splash screen comes up follwoed by the application.  However if I try setting up a disktop launcher with the same command all I get is the splash screen.  I think that this is a permissions problem since I can fire up Notes from the root terminal but not from a user's desktop link.  Any help much appreciated.  My experience with Linux starts with the release of Warty and reading Unix for Dummies.
cheers, bob

---

### Post by localzuk on 2005-04-10
Try running gtsu before the command, it will prompt for the root password when starting - so will run as root. (Or if in kde, kdesu).

---

### Post by flyinglizard on 2005-04-10
You don't have to run Notes as root,  try setting up wine under a non-root user and copy the Notes intall there.  Make sure you update the ownership and it should fire right up.

Also make sure you don't upgrade to wine 20050310 (Hoary),  Notes will not run correctly,  but it runs fine for me at 20041201 and earlier.

---

### Post by Bob Owen on 2005-04-10
[QUOTE=localzuk]Try running gtsu before the command, it will prompt for the root password when starting - so will run as root. (Or if in kde, kdesu).[/QUOTE]

Did you mean gksu instead of gtsu?  If I try gksu I see the prompt for the root password, but whatever I put in I get 'Failed to run wine as user root: Child terminated with 1 status'.  I have never set up a password for the root - do I need to do that first?
cheers, bob

---

### Post by Bob Owen on 2005-04-10
[QUOTE=flyinglizard]You don't have to run Notes as root,  try setting up wine under a non-root user and copy the Notes intall there.  Make sure you update the ownership and it should fire right up.

Also make sure you don't upgrade to wine 20050310 (Hoary),  Notes will not run correctly,  but it runs fine for me at 20041201 and earlier.[/QUOTE]

Apologies for newbie dumb question but how do I set up wine under a non-root user?  I ran winetools and it was set up in /root, where should I set it up to be non-root?  I don't mind uninstalling wine and reinstalling if necessary, it's all part of the fun of learning Linux.

---

