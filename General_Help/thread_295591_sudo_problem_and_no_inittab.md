---
title: "sudo problem and no inittab"
date: 2006-11-08
forum: General Help
---

### Post by edrappin on 2006-11-08
Hi everyone,

Newbie here so please be gentle. I was going to change my nameserver address using sudo vi resolv.conf but it would not let me modify the file. I am guessing it is some kind of user permission problem. I am a bit befuddled. 

In addition, in the process of installing matlab, I discoverd I have no inittab file. Since this discovery I have rebooted several times without problem. Why do not have this file? Does somebody have one that I should use?

Thanks for all the help

---

### Post by K.Mandla on 2006-11-08
Hi. I can't speak to the resolv.conf problem; you might try switching to root access with *sudo su* and edit it that way. Or maybe try it with nano or gedit or mousepad or kate ... ?

If you're using Edgy, inittab has been split off into several files, most of which are inside /etc/event.d, if I recall correctly. Inittab and the new configuration files are somewhat similar, but you might have to get creative.

---

### Post by edrappin on 2006-11-08
Thanks K.Mandla

I have tried all of your suggestions for editing my resolv.conf file. Still no write permission. I am really baffled by this one.

Thanks for the update on inittab. Do you happen to know the default run level for Edgy?

---

### Post by boban on 2006-11-08
try:
```

ls -l /etc | grep -i resolv.conf

```

and post it's output...

---

### Post by edrappin on 2006-11-08
Thanks for the help

edrappin@edrappin-desktop:~$ ls -l /etc | grep -i resolv.conf
-rw-r--r--  1 root   root        54 2006-11-07 18:46 resolv.conf
-rw-r--r--  1 root   root        54 2006-11-08 11:50 resolv.conf.dhclient-new

---

### Post by edrappin on 2006-11-08
let me add that I can modify all other files in /etc or /usr or any other root directory. The problems seems to be solely with resolv.conf

---

### Post by edrappin on 2006-11-08
I must have been sleep computing last night :-D . The reslolv.conf file was locked. chattr -i /etc/resolv.conf did the trick. 

Consider this thread closed.

---

### Post by boban on 2006-11-08
Not only you were sleeping ;-)

I sterted today's programming 13h ago... And I don't see the end of it...

---

