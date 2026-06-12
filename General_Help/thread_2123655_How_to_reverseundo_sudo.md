---
title: "How to reverse/undo sudo?"
date: 2013-03-08
forum: General Help
---

### Post by KingNeil on 2013-03-08
I have an SH file

sudo -i
run command here

Once I have run the command, I want to remove the root privileges...

So... how do I "undo" the sudo command, so speak?

---

### Post by cortman on 2013-03-08
```
su user_name
```

So for me, it would be

```
su cortman
```

---

### Post by steeldriver on 2013-03-08
```
sudo -k
```

revokes the user's cached credentials - see the man page for details

```
man sudo
```

---

### Post by lisati on 2013-03-08
> **KingNeil said:**
> I have an SH file

sudo -i
run command here

Once I have run the command, I want to remove the root priveleges...

So... how do I "undo" the sudo command, so speak?

If you have used "sudo -i", you can return to "normal" privileges with:
```
exit
```

---

### Post by KingNeil on 2013-03-08
lisati.... that is exactly what I was looking for

> exit

**Thank you. However, I do have another issue... (see next post)**

---

### Post by KingNeil on 2013-03-08
The issue is... I'm trying to do the following, in an SH file...

```
sudo -i
command that requires sudo
exit
command that doesn't require sudo
```

And, it doesnt seem to work...

How would I go in and out of a sudo privileges within an SH file??

---

### Post by prodigy_ on 2013-03-08
> **KingNeil said:**
> ```
sudo -i
command that requires sudo
```
Why not just **sudo command**?
**-i** is short for 'interactive' and you generally don't use interactive things in scripts.

---

### Post by mikewhatever on 2013-03-08
> **prodigy_ said:**
> Why not just **sudo command**?
**-i** is short for 'interactive' and you generally don't use interactive things in scripts.

+1. There shouldn't be any need for sudo -i in a script.

---

