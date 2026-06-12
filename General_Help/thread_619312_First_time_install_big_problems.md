---
title: "First time install big problems"
date: 2007-11-21
forum: General Help
---

### Post by fiddilydee on 2007-11-21
okay here is the whole story. I have a computer that was preloaded with vista. I am now fed up with it's infinite amount of verification and comfirmation and stupid seemingly unfixable errors. I decided to install ubuntu, I am completely new to linux.

I booted off of the cd and messed around with it to make sure I could still do everything I wanted (media and photo editing) of course it is even better than windows for this stuff. So I want to get rid of windows completlely and put Ubuntu on. I boot into it again make a seperate partition for my media and format the windows partition. After a couple of installation attempts (it did stall a few times) it finally completed but it will not accept the username/passowrd i typed in even though I know they are right.

So I try a couple of things I read on here to change the password in recovery mode, it is telling me my user does not exist even though it automatically named my computer the same thing and this is printed in the bottom left corner the whole time. I try installing it again it is still booting from the old computer name and not accepting any of the things I put for username/password.

So I load up my friends external hard drive to put my media on so I can do a full format and it cannot mount it even though it was working fine before. I am starting to get rustrated with this.

Any tips or ways I can format everything besides my media partition because the first install created 3 or 4 locked partitions which I figure is causing my reinstallation issues (not recognizing new user profile)

I know that was long but any help would be appeciatied

---

### Post by oneadvent on 2007-11-21
Seems easy enough..try the cap lock.

I know that is stupid, but it has happened to me before. 

Also, did you name your computer the same as your username?

---

### Post by murataht on 2007-11-21
I don't know if I understand your problems correctly. Anyway I will try to answer:
1)if you want to format the hard disk, have you tried to boot up with Gutsy CD, and use fdisk? or even GParted? I think fdisk is quite straight forward, give it a shot, if you haven't yet. 

2) or why don't you create a new user under recovery mode, if it says your username does not exist? and give it a new password. if you succeed you don't have to reinstall all.

hope this helps.

---

### Post by fiddilydee on 2007-11-21
thanks but how do you create a new user?

---

### Post by oneadvent on 2007-11-21
```
useradd --help    
```

that should give you the syntax for what you want.

---

