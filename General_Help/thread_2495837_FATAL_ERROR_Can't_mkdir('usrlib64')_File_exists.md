---
title: "FATAL ERROR: Can't mkdir('/usr/lib64'): File exists"
date: 2024-03-03
forum: General Help
---

### Post by darrinqatar on 2024-03-03
Hello All, newbie here. I just upgraded to 22.04 and now see the following come up:

FATAL ERROR:
Can't mkdir('/usr/lib64'): File exists at /usr/lib/usrmerge/convert-usrmerge line 41


You can try correcting the errors reported and running again
/usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
Do not install or update other Debian packages until the program
has been run successfully.


Would you please help me fix this? Thanks so much!

---

### Post by #&amp;thj^% on 2024-03-03
This is a know bug upgrading from 20.04 to 22.04 [https://bugs.launchpad.net/ubuntu/+source/usrmerge/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/usrmerge/+bugs?field.status:list=NEW)
EDIT: 
Try this first, it was reported to work by a Dev I'm familiar with it goes like this:
> This was a very obscure error during upgrade from one LTS release to another.

I finally (apparently) fixed it by running:

 ```
 sudo ln -s -f /usr/lib64/ld-linux-x86-64.so.2 ld-linux-x86-64.so.2
```

 ```
 sudo /usr/lib/usrmerge/convert-usrmerge
```
Now this is kind of a nuclear approach **_So I warn now have good back-up's in place first. _**
```
sudo apt remove --purge usrmerge
```

It might be best to just do a clean install>>>If you have good back-up's

---

### Post by darrinqatar on 2024-03-03
Thanks so much for your suggestions, I tried the first one and the error persists. I won't try the second one, probably best for me to restore from my image before the upgrade at this point as you said.
Hopefully Ubuntu can fix this in the future.

---

### Post by ActionParsnip on 2024-03-04
Be sure to comment on the bug to say it affects you.

---

