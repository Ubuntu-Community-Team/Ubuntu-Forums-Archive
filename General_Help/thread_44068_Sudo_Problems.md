---
title: "Sudo: Problems"
date: 2005-06-24
forum: General Help
---

### Post by the_pc_dude on 2005-06-24
Hi, I'm having  an problem look at this [post ](http://ubuntuforums.org/showthread.php?t=43942)

---

### Post by Juergen on 2005-06-24
Did you create more than 1 user? Only the first is a sudoer by default.

If nothing works, boot into single-user. Look at /etc/group - your user should be in the admin group.

And maybe look at /etc/sudoers. You should *edit* this file only via 'visudo' because this does a syntax check 
(I hope you know a bit vi, or do 
```
export EDITOR=pico && visudo
```)
There should be an entry like this in it:
> # Members of the admin group may gain root privileges

%admin ALL=(ALL) ALL

> also unable to pick up public/pickup directoryWhat do you mean here?

---

### Post by the_pc_dude on 2005-06-24
Now I rememeber it was Warning: PostDrop: unable to pick up public/pickup directory.

---

### Post by Juergen on 2005-06-25
This seems to be related to postfix. If nothing helps try to re-install.

Look at the owner/group and permissions of /var/spool/postfix/*

Did you copy stuff from another linux-install? The user-ids might have changed then.

---

### Post by the_pc_dude on 2005-07-11
Ok Figured that error out did put in my full name in when installing after put in my full name it's not poping up.

---

### Post by RJARRRPCGP on 2005-07-12
[QUOTE=the_pc_dude]Ok Figured that error out did put in my full name in when installing after put in my full name it's not poping up.[/QUOTE]

What do you mean? I don't understand!

---

### Post by the_pc_dude on 2005-11-30
When It ask for your full name you have to put it,or the post drop error will happen.

---

### Post by RJARRRPCGP on 2006-07-10
> **the_pc_dude said:**
> Now I rememeber it was Warning: PostDrop: unable to pick up public/pickup directory.

I haven't gotten that message under Breezy Badger. I gotten that message repeatedly under Hoary. 

Thus this appears to be a Hoary issue. (possibly includes earlier versions) 

I don't appear to have this issue with Breezy Badger.

Haven't gotten Dapper yet, because I'm stuck with 56k. :(

---

