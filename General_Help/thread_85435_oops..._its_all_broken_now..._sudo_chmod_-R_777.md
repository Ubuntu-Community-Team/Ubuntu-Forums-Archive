---
title: "oops... its all broken now... sudo chmod -R 777 /"
date: 2005-11-02
forum: General Help
---

### Post by snuffy on 2005-11-02
I think i made a newbie error.

i did the following to my system folder:

sudo chmod -R 777 / 

and now bad things happen...or to be precise, don't happen; like open office crashes, and i can't start synaptic or update manager.

is there any way to fix my mistake?

thanks for your time.
tim.

---

### Post by orbinick on 2005-11-02
try sudo chmod 755 -R

I'll check some info that pointed me into the right direction.

was it /usr folder?

---

### Post by matthew on 2005-11-02
Oh, no. Tim, I have bad news for you, bud. 

Unless you are able to find out the precise permissions that each and every folder and file on your computer SHOULD have it will be really hard to restore them and get your box running right again.

If it makes you feel any better I did the same thing my first week of using linux. 

The bummer is that the easiest way to fix it is to reinstall everything.

The advice the poster above me gave may help you to be able to use the system temporarily to recover your data. It will just be a temporary fix, though because there are folders and files that only root or only certain programs should have access to such as passwords. Unless you know what they all are and where they all are it just isn't possible.

---

### Post by btnheazy03 on 2006-05-02
[QUOTE=matthew]Unless you are able to find out the precise permissions that each and every folder and file on your computer[/QUOTE]You're .. . you're joking .. . :cry:
I have hundreds of thousands of files .. . :(

I guess now's the best time to switch to Dapper Drake

---

### Post by elamericano on 2006-05-02
You're files are all OK, but you system won't run properly if many system files don't have their correct permissions. For example, sudo will refuse to work if /etc/sudoers isn't 440. There are too many other cases to mention.

You shouldn't have any lost user files. Just back those up before reinstalling.

---

### Post by airtonix on 2006-06-05
arrrrrrgh for the love of linus, i did the same thing!

a'reinstalln we ago

---

