---
title: "compiz stopped working after i tried to install GIT"
date: 2008-07-09
forum: General Help
---

### Post by evoviiigsr on 2008-07-09
I attempted to install the GIT version of compiz and it never worked, so I uninstalled GIT and compiz stopped working...i've uninstalled and reinstalled a few times..i'm a ubuntu noob by the way. Here's my output:

Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1360x76 to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

---

### Post by sayakb on 2008-07-10
Add the repository as indicated here:
[http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)
And then do:
```
sudo apt-get install compiz compizconfig-settings-manager
```

---

### Post by evoviiigsr on 2008-07-10
ok so it installed and I'm able to use the settings manager, BUT the effects aren't working...also, when i go to appearance and then visual effects it says that desktop effects could not be enabled

now my output says:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

---

### Post by evoviiigsr on 2008-07-11
bump

---

### Post by evoviiigsr on 2008-07-18
anyone?

---

### Post by sandeepy on 2008-07-18
you can try doing :

sudo aptitude remove compiz

this will remove the dependencies which might be causing problems. then do 

sudo apt-get install compiz

---

### Post by evoviiigsr on 2008-07-18
Thanks, but that didn't work...i get teh same output

---

### Post by sandeepy on 2008-07-18
i am not sure of this but you may reboot and then on the terminal (before ur X session begins), you can remove the .X* (infact all the unnecessary config) files in ~. 

you might want to search a little

---

