---
title: "$HOME/.dmrc file ignored at log in"
date: 2006-09-21
forum: General Help
---

### Post by schaefscha on 2006-09-21
Eveytime I log in after entering the password the following message pops-up.

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I've tried already to change the permissions (both as regular user and root) but with no success. I've thought the upgrade to 6.06 would fix it, but it didn't... Now I'm clueless on what to do!

Any ideas would be welcome. Thnx

---

### Post by Ramses de Norre on 2006-09-21
This should fix it:
```
sudo chown `whoami`:`whoami` .dmrc && chmod 644 .dmrc
```

---

### Post by ayoli on 2006-09-21
and maybe also:
```
sudo chmod 755 /home/your_username
```
if it is not already set like that.

---

### Post by schaefscha on 2006-09-22
Thnx! Seems like it's fixed!

---

### Post by PriceChild on 2006-09-22
> **ayoli said:**
> and maybe also:
```
sudo chmod 755 /home/your_username
```if it is not already set like that.

EDIT

whoops what i pasted was stupid... and you'll want to use a "-R" just after the 775.

---

### Post by ayoli on 2006-09-22
> **PriceChild said:**
> The warning message said 644... not 755

warning message says:
> File should be owned by user and have 644 permissions. 
that's for ~/.dmrc file, and:
> User's $HOME directory must be owned by user and not writable by other users.
is the reason for: sudo chmod 755 /home/your_username

---

### Post by srafx on 2006-09-29
I'm having the same error at login but none of this helps.  I know that the .dmrc file is at 664, but I still get that error at login.

Let me know if anyone has any other ideas.

thanks.

---

### Post by srafx on 2006-09-29
Okay, its fixed.  I created a new user to compair what was different and found that my user somehow had the file group set to 'admin' and not what the user name is.  Infact, the group of what my username didnt even exsist.  

Anyone know how this happened?  And why does there have to be a group named after each user and why wouldnt that user be in that group?

for example if i created a user test, it would create a group test.  The home folder would have the following:

file owner: test
file group: test

but the user test wouldnt be in the group test?  Let me know if you know.

---

### Post by wensveen on 2007-03-01
After trying everything in this thread, it's still not working for me.
Here is a part of ls -al from my home dir:
```

matthijs@twins:~$ pwd
/local/home/matthijs
matthijs@twins:~$ ls -al
total 712
drwxr-xr-x 63 matthijs Domain Users   4096 2007-03-01 07:58 .
drwxr-xr-x  4 root     root           4096 2007-02-09 15:12 ..
drw-r--r--  2 matthijs matthijs       4096 2007-02-19 08:03 .dmrc

```
My home dir is set to /local/home/matthijs. This is because /home is a NFS mount (for roaming profile purposes), but I never use that because it slows down some programs.

I've tried creating a .dmrc directory in /home/matthijs but that does not work either.
Any ideas?

Is there some way to check if GNOME has $HOME set correctly?

---

