---
title: "Swap in old firefox profile, change ownership or permissions ?"
date: 2018-07-26
forum: General Help
---

### Post by verenard on 2018-07-26
I made a new ubuntu 18.04 install on a new disk.
I want my old firefox profile from my old disk.
I usually just copy/paste it over, which seems to work fine.
But should I really be changing permissions and ownership etc to match the new OS installation ?

---

### Post by deadflowr on 2018-07-26
You would only need to change ownership if the new user is different.
And permissions only need to be writable by the owner.
Which should be what they are, right?

---

### Post by #&amp;thj^% on 2018-07-26
> **deadflowr said:**
> You would only need to change ownership if the new user is different.
And permissions only need to be writable by the owner.
Which should be what they are, right?
+1
Been doing  it this way for a very long time now with no problems.

---

### Post by verenard on 2018-07-26
Is owner "me" a generic name ?

---

### Post by deadflowr on 2018-07-26
Is me what it says in properties, by chance?
If so, me equals your current username.

---

### Post by verenard on 2018-07-26
But it's different to the one for my new install.

---

### Post by deadflowr on 2018-07-26
What's different?

---

### Post by #&amp;thj^% on 2018-07-26
> **deadflowr said:**
> What's different?

+1 Kind of confused here myself. :)
Also is the OP restoring the whole the whole ".mozilla" folder or just the "profiles.ini" file.

---

### Post by &amp;KyT$0P# on 2018-07-26
> **verenard said:**
> I usually just copy/paste it over, which seems to work fine.
But should I really be changing permissions and ownership etc to match the new OS installation ?
If it 'seems to work fine', why mess with it?

---

### Post by verenard on 2018-07-27
My user name is different. One for the old install, one for the new. So does that mean a new owner of files ?
I'm restoring the whole .mozilla folder - for the passwords and bookmarks etc.

---

### Post by #&amp;thj^% on 2018-07-27
As long as you _did not_ copy the folder using elevated or root privileges>>>all should work as expected.
So my question to you is>>>is it working?

---

### Post by verenard on 2018-07-27
I didn't do that and it's working.

OK, what about all the other stuff I want to move from one disk to another - pictures etc. I moved a load and, in the permissions tab, they have the old owner but the new computer as a group with read/write permission.
Would it be better to change owner before moving stuff to a new installation - so that both owner and group are the same ?

---

### Post by #&amp;thj^% on 2018-07-27
> **verenard said:**
> I didn't do that and it's working.

OK, what about all the other stuff I want to move from one disk to another - pictures etc. I moved a load and, in the permissions tab, they have the old owner but the new computer as a group with read/write permission.
Would it be better to change owner before moving stuff to a new installation - so that both owner and group are the same ?
There is no need to do anything but move the files and folders you wanted>> they will just take care of themselves because you the user regardless of a different user name is the one moving them. (Hope that makes sense)

---

### Post by verenard on 2018-07-27
Ah. 
See, what I thought was that owner is set as a security measure. So only if you are the original root owner can you set permissions.
So that if you don't want other people tinkering with your files then you as owner can deny permission. Then as nobody else is owner then they can't change it for themselves, no matter if they are super user on their own machine.
But I was just assuming.
I could just try it all out and see.

Some files won't copy over to the new disk, there is a permissions error and all their permissions are for original root.

So, if I have a load of files I just copied over from an old disk then, as I am not the original root owner, I don't have full control over the permissions do I ?

---

### Post by verenard on 2018-07-27
It's OK I'm figuring this out. 
Using 
ls -l 
I can see that ownership has changed on files I've moved to my new drive.

---

### Post by #&amp;thj^% on 2018-07-27
> **verenard said:**
> 
Some files won't copy over to the new disk, there is a permissions error and all their permissions are for original root.

So, if I have a load of files I just copied over from an old disk then, as I am not the original root owner, I don't have full control over the permissions do I ?
Please read this for a better understanding [https://wiki.archlinux.org/index.php/File_permissions_and_attributes](https://wiki.archlinux.org/index.php/File_permissions_and_attributes)

---

### Post by verenard on 2018-07-27
cool, thanks.

---

### Post by oldfred on 2018-07-28
Internally system is not actually using your name.
It is using user 1000 for first user, 1001 for second user etc.
Only time it may be an issue is if you change from first to second user when you reinstall.

should show files as user 1000 unless you save something as root.
ls -n /home/$USER

User fred is 1000
fred@bionic-z97:~$ getent passwd $USER
fred:x:1000:1000:fred,,,:/home/fred:/bin/bash

---

