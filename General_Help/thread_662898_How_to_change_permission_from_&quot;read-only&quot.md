---
title: "How to change permission from &quot;read-only&quot; to &quot;read and write&quot;
for CD-RW drive"
date: 2008-01-09
forum: General Help
---

### Post by slaabrockband on 2008-01-09
Situation:

places>computer>cd-RW Drive>permission>acces

Try to change from "read-only" to "read and write" and get the message:


 "permissions could not be changed"


I can only read - but I want to read and write from my CD-RW drive?

Is there a simple way?

---

### Post by p_quarles on 2008-01-09
Changing the permissions on a CD drive doesn't really make much sense. It should allow you to write to a blank or rewritable *disk*, but you'll only see the permissions when the disk is in the drive.

---

### Post by Craigus on 2008-01-09
> Is there a simple way?

Yes - it should just work. Try burning a CD.

---

### Post by slaabrockband on 2008-01-09
> **Craigus said:**
> Yes - it should just work. Try burning a CD.

I can asure you that I  have tried that a lot of times with bunch of different programs.

---

### Post by p_quarles on 2008-01-09
> **slaabrockband said:**
> I can asure you that I  have tried that a lot of times with bunch of different programs.
And I can assure you that the problem is not with the permissions on the drive itself. It's most likely because something got mixed up in your filesystem table. Can you post the contents of this file:
```
/etc/fstab
```

---

### Post by kdwillia on 2008-01-09
Another question is are you trying to burn to a disk that has already been burned to?

If so, was the disk "finalized"

---

### Post by slaabrockband on 2008-01-09
> **p_quarles said:**
> And I can assure you that the problem is not with the permissions on the drive itself. It's most likely because something got mixed up in your filesystem table. Can you post the contents of this file:
```
/etc/fstab
```


sure:

bash  /etc/fstab:  permission denied

---

### Post by p_quarles on 2008-01-09
> **slaabrockband said:**
> sure:

bash  /etc/fstab:  permission denied
That just tries to execute the file, and since it's not executable, permission is denied. 

To get the *contents *of the file, you'll need to either open it up with a text editor, or type:
```
cat /etc/fstab
```

---

### Post by slaabrockband on 2008-01-09
> **kdwillia said:**
> Another question is are you trying to burn to a disk that has already been burned to?

If so, was the disk "finalized"

First question Yes!


finalized ?Please explain

---

### Post by kdwillia on 2008-01-09
Finalized means that you turned a writable CD into a non writable CD.   Once a CD if finalized, you can no longer burn to that CD.

At that point, if you looked at its permissions, they would say Read Only.

Finalization is done when you burn a CD.  There is always an option to "Finalize" the disk.

Have you tried to a disk that has never been burned to?

---

### Post by slaabrockband on 2008-01-09
> **p_quarles said:**
> That just tries to execute the file, and since it's not executable, permission is denied. 

To get the *contents *of the file, you'll need to either open it up with a text editor, or type:





```
cat /etc/fstab
```      see screenshot

---

### Post by p_quarles on 2008-01-09
> **slaabrockband said:**
> see screenshot
Hmm. That looks okay. Let's make sure your account has the correct memberships. Type:
```
groups *your-user-name*
```
Basically, the output should include "cdrom" but you can cut and paste the output if you're not sure.

---

### Post by slaabrockband on 2008-01-09
> **kdwillia said:**
> Finalized means that you turned a writable CD into a non writable CD.   Once a CD if finalized, you can no longer burn to that CD.

At that point, if you looked at its permissions, they would say Read Only.

Finalization is done when you burn a CD.  There is always an option to "Finalize" the disk.

Have you tried to a disk that has never been burned to?

This is getting more and more spicy, I think I got you wrong ---- but the dics used -
are pure like virgins.... I dont get "read only"

---

### Post by slaabrockband on 2008-01-09
> **p_quarles said:**
> Hmm. That looks okay. Let's make sure your account has the correct memberships. Type:
```
groups *your-user-name*
```
Basically, the output should include "cdrom" but you can cut and paste the output if you're not sure.


The output include "cdrom"  (se Screenshot). What is your conclution? The problem 
has been bugging me for a week. It is time to go out datashopping ?

---

### Post by DoktorSeven on 2008-01-09
The question is, what do you try to burn a CD with, and what error message does it give back when it fails?

---

### Post by p_quarles on 2008-01-09
Hmm. That is strange. Are you getting any error messages when attempting to write to a CD? (other than just "disk is read only," since that's understood). This could be an issue with dbus or something.

But, it could also be a permissions issue, like you thought at first. But, not with the drive itself, rather with the mountpoint. Can you post the output of this?:
```
ls -l /media
```

---

### Post by slaabrockband on 2008-01-09
> **p_quarles said:**
>  Can you post the output of this?:
```
ls -l /media
```


Sure ( see screenshot)

I appreciate your help - right now it is midnight in my part of the world and Im going
to sleep. I'll  read and reply your posts tomorrow  Goodnight

---

### Post by slaabrockband on 2008-01-10
> **p_quarles said:**
>  Can you post the output of this?:
```
ls -l /media
```


Other try -  I think I got the code  right this time:


See Screenshot.

---

### Post by slaabrockband on 2008-01-12
'problem solved 



I bought a new burner

---

