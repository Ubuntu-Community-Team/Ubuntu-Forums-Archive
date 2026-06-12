---
title: "error: can't find command 'hwmatch'"
date: 2021-01-19
forum: General Help
---

### Post by giobaxx on 2021-01-19
Hello to Every 


I need an help to understand how to properly solve an issue happened un an Ubuntu 18.04.

Basically once Ubuntu frezeed and the user was forced to run a Hard Reboot, ubuntu started wit the following error 


```
error: can't find command 'hwmatch' 
```

then clicking on the keyboard it asked for a ***username*** and ***password*** that i don't know.

Trying to understand the configuration i discovered that 

Ubuntu it was installed in ***efi mode*** and some *security enforcement* was done 

i found on the ***/etc/grub.d/40_custom*** the following line
```
#!/bin/sh
                    exec tail -n +3 $0
                    # This file provides an easy way to add custom menu entries.  Simply type the
                     # menu entries you want to add after this comment.  Be careful not to change
                    # the 'exec tail' line above.
                    set superusers="cmpadmn"
                     password_pbkdf2 cmpadmin grub.pbkdf2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
 
  That i suppose is the grub password. For the moment I have fixed the problems commenting out the two line on the ***40_custom*** file and running ***upgrade-grub*** but i would like to fix in a proper way re-enabling the security feature applied.
 
 Can someone tell me which is the relation between the ***hwmatch.mod*** and the grub password and how i can try to properly fix?

What i have notice is that in some ubuntu this module is


```
/usr/lib/grub/i386-pc/hwmatch.mod

```

and


```
/boot/grub/i386-pc/hwmatch.mod

```


in others it is just in 


```

/usr/lib/grub/i386-pc/hwmatch.mod  like the one that has problem

```


It is not clear for me, can someone has some experience about this issue?


Thanks in advance

---

