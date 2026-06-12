---
title: "Accidently RM -RF * in /"
date: 2007-08-29
forum: General Help
---

### Post by swarm on 2007-08-29
Argh, I was installing the folding @ home stuff, and went to delete the dir, and typed one too many .'s before the folder. I stopped it as soon as i could, but SSH stopped working right afterwards... can i undo this? or... do i need to reinstall? I can still type commands on the box

---

### Post by Wolki on 2007-08-29
Does apt still work? If so, you might have a chance to fix it be reinstalling the packages. Get a list of installed packagers, then do "sudo apt-get reinstall <packages>". 

If I didn't make a mistake, the following should output a list of all installed packages:

```
dpkg --get-selections | grep -e "[[:space:]]install$" | sed -e "s/install$//" | sed 's/[[:blank:]]//g' | tr -s "\n" " "
```


Good luck.

---

### Post by swarm on 2007-08-29
Thanks, but I ended up just reinstalling. After a reboot it wouldn't start up.

---

