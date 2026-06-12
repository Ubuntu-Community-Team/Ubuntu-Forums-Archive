---
title: "Where is the..........."
date: 2007-08-19
forum: General Help
---

### Post by jaw175 on 2007-08-19
Having been able to get back in......after locking myself out in messing with my HOME file permissions, my login now says it can't find the Dmrc fie and that it is affecting the saving of the language setting.  Can anyone tell me where to find this file and how to edit it .....seemingly to re-instate its 644 status.
I am using Feisty 7.4 on AMD Athlon 64.  Thanks for any help you can give me to resolve this. :)

---

### Post by kevinlyfellow on 2007-08-19
It should be ~/.dmrc

If you don't have it, this is what mine reads
```
[Desktop]
Session=gnome

```

---

### Post by ruibernardo on 2007-08-19
Hi jaw175,

are you looking for this?
```
user@desktop:~$ ls -l ~/.dmrc 
-rw------- 1 user user 26 2007-06-14 01:29 /home/user/.dmrc
```It's a hidden file in your home directory.

EDIT: My .dmrc file says:

```
 [Desktop]
Session=default
```

---

### Post by jaw175 on 2007-08-19
Thank you for your replies. Really, I'm none the wiser. No doubt a manifestation of my noobility. The problem of this popping up as I hit enter for logging in does not affect me able to access my Home dir and its files in what I think is normal. This pop-up follows my having fixed getting back to my desktop after inadvertently locking myself out. Whilst it seems more of a nuisance, I thought it must relate to the setting of the correct number for the file permissions: If that is so, then I do not know how to fix those settings. My apologies if I was ( or still am being unclear) . :)

---

### Post by cwaldbieser on 2007-08-20
> **jaw175 said:**
> Thank you for your replies. Really, I'm none the wiser. No doubt a manifestation of my noobility. The problem of this popping up as I hit enter for logging in does not affect me able to access my Home dir and its files in what I think is normal. This pop-up follows my having fixed getting back to my desktop after inadvertently locking myself out. Whilst it seems more of a nuisance, I thought it must relate to the setting of the correct number for the file permissions: If that is so, then I do not know how to fix those settings. My apologies if I was ( or still am being unclear) . :)

Permission 644 is:
User: Read & Write
Group: Read
Other: Read

You should be able to right click and set the permissions, or you can use "chmod 644 ~/.dmrc" in the terminal.

---

### Post by dondad on 2007-08-20
Check the permissions of your home directory. If it has gotten changed, this can cause the problem you have. You can try to do a chmod -R on your home directory and make it 700 or 755 and this should fix the problem you are having. 

You can cause this problem by using sudo on a graphic app like nautilus rather than gksudo.

---

### Post by jaw175 on 2007-08-22
Problem solved.  Thanks cwaldbieser and dondad. Purely a matter of setting the permissions as cwaldbieser suggested. My apologies also for not being able to get back to the board sooner. Thanks again.  Small beer problem I know......but indicative of how much learning us noobs have to make in trying to understand how Linux works, but well worth it for obvious reasons!  :)

---

