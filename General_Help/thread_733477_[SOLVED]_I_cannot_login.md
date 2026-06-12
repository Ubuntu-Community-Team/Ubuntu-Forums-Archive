---
title: "[SOLVED] I cannot login"
date: 2008-03-23
forum: General Help
---

### Post by Garath531 on 2008-03-23
I somehow managed to mess up my ubuntu feisty fawn. When I try to login I get this message:

> 
(gnome-session:5445): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome certification directory '/home/*user*/.gnome2/': Permission denied


(Obviously I replaced my real username with *user*

I followed the directions in [this](http://ph.ubuntuforums.com/showthread.php?t=725520) thread and it didn't help. Does anyone know what is wrong?

Also, out of curiosity, is there anyway to enable the number lock by default?

---

### Post by jken146 on 2008-03-23
Press Ctrl+Alt+F1.  Log in.  Type ```
ls -l /home
``` and see what the permissions are for your user's directory.  Post the output please.

---

### Post by Garath531 on 2008-03-23
It says:
> 
total 4
drw-r--r-- 37 *username* *user* 4096 2008-03-23 18:30 *user*


---

### Post by Garath531 on 2008-03-25
I'm not sure what the rules on bumping are, but it has been 24 hours and I really do need this fixed, so 

*bump*

---

### Post by ibuclaw on 2008-03-25
Okay, first boot your PC into recovery mode.

enter these commands in order (might need to get a pen and paper.)

```

cd /home
chown yourname:yourname yourname -R
chmod 755 yourname -R
exit

```

First try that, as your user folder should look something like this:
>  drwxr-xr-x 117 user          user           4096 2008-03-26 01:31 user 

[EDIT]
And that's just what we know of your /home/name permissions in the hierarchy of the linux folder structure. Chances are that you don't have permissions to write to the lower folders. Or you may not be the own of the folders anymore (either way it's bad news). So the above commands should solve 99% all problems with permissions.

Consider yourself one of the very few exceptional if this doesn't work.

Regards
Iain

PS
Bumping is all down to general preference. As different people are on the forums everyday. I would say that once after 24 hours is ok. But if it drops back down again, you might as well start a new topic as you have a better chance of getting and answer the longer you are in the "unanswered" posts section.

---

### Post by Garath531 on 2008-03-25
Thank you very much tinivole and jken146! It worked.

---

### Post by ibuclaw on 2008-03-25
Your very welcome.

Sorry for the small delay in services, but I hope you come back with confidence.

Regards
Iain

---

