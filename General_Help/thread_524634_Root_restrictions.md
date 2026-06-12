---
title: "Root restrictions"
date: 2007-08-13
forum: General Help
---

### Post by M.a.d on 2007-08-13
Hi

I need to apply two security measures but am not able to figure out how. You smart people on the forum will know how to do it for sure :) :

1) Restrict a user to view other user home folder, and restrict the user to even view the systemfiles in / (root).

2) I don't know how to script, so perhaps one of you can tell me how to: set up so Ubuntu automatically restore certain files and folders (perhaps from a restore set) everytime a user (except admin) logs on.

Thanks in advance :)

---

### Post by kidders on 2007-08-14
Hi there,

> **M.a.d said:**
> Restrict a user to view other user home folderIf you mean you want to prevent users from viewing the contents of each others' home directories, then it's up to each individual user to decide what he wants others to be allowed to see.

> **M.a.d said:**
> restrict the user to even view the systemfiles in /There is not normally a valid reason for wanting to do this.

> **M.a.d said:**
> set up so Ubuntu automatically restore certain files and foldersAre you referring to things the user logging in has write access to?

---

### Post by M.a.d on 2007-08-14
> **kidders said:**
> Hi there,

If you mean you want to prevent users from viewing the contents of each others' home directories, then it's up to each individual user to decide what he wants others to be allowed to see.

In this particular case it's an administrator who would want the user only to be allowed to view it's own home folder. But I guess right-clicking the Home folder and choose None under Others in Permissions will do the trick...

> **kidders said:**
> There is not normally a valid reason for wanting to do this.

Ordinary users does not have the rights to modify system files, but it could be nice to also be able to hide them. I don't know, it would just be nice to be able to on a public available computer.

> **kidders said:**
> Are you referring to things the user logging in has write access to?

Yes. If I want to restore any modifications a user has made to e.g Firefox, screen resolution, wallpaper etc, so _everything_ is restored to status quo when the user logs on the next time. This is particular relevant on a public computer, when people use the same account.

I know this probably is quite complicated but that is why I ask :)

---

### Post by kidders on 2007-08-14
Hey again,

> **M.a.d said:**
> Ordinary users does not have the rights to modify system files, but it could be nice to also be able to hide them.I doubt that! If your users were unable to access any applications & system libraries, they wouldn't even be able to log in ... let alone do anything productive. Besides, most Linux systems are *very* standardised ... without ever having used your computer before, most users will still know exactly where everything is, so attempting to hide things wouldn't achieve much.

> **M.a.d said:**
> If I want to restore any modifications a user has made to e.g Firefox, screen resolution, wallpaper etc, so _everything_ is restored to status quo when the user logs on the next time.Don't worry ... you'll hopefully find this one quite straightforward. :-) If you wanted to, you could modify (and lock) one of the login scripts, for each of your user accounts. There are so many ways of triggering automated startup tasks, that users are very unlikely to miss just *one* of them.

In many cases, simply deleting application settings ought to be enough.

---

