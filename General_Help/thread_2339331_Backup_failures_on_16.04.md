---
title: "Backup failures on 16.04"
date: 2016-10-07
forum: General Help
---

### Post by trash1464 on 2016-10-07
I am also getting Backup failures after a clean install of 16.04 LTS. Can anyone help? [ATTACH=CONFIG]271533[/ATTACH]

---

### Post by deadflowr on 2016-10-07
Odd error.
Somehow it thinks duplicity is missing, which is the actual part of the backup that does the heavy lifting for Ubuntu's backup program deja-dup.
First see if duplicity is installed,
easy enough, try this in a terminal:
```
dpkg -l duplicity
```
if the results return anything other than* ii  duplicity * try reinstalling the package:
```
sudo apt install --reinstall duplicity
```

---

### Post by trash1464 on 2016-10-07
Interesting, Looking around in the Backup configuration options, I discovered an "Install" button. Clicking on that initiated an installation after which backups now run as before on 14.04LTS. It seems duplicity is no longer installed by default. I'm sure your terminal commands would have accomplished the same. Thanks for the help. Now to figure out how to mark this thing solved...

---

### Post by deadflowr on 2016-10-07
Yeah, weird, huh?
To mark as solved go to the top area above the first post where it says *Thread Tools*, drop down to the Mark thread as solved and click.

---

