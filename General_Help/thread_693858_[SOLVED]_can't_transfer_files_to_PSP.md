---
title: "[SOLVED] can't transfer files to PSP"
date: 2008-02-11
forum: General Help
---

### Post by HappyFeet on 2008-02-11
my PSP mounts OK, and a window opens with my folders on it. however, it does not let me transfer files to it. this worked OK in feisty and gutsy when it first came out. what happened? changing permissions and doing sudo nautilus does nothing to allow me to transfer files. i have a small xp partition for gaming, and can transfer files to xp then the PSP, but would like to do it in ubuntu. help?

---

### Post by HappyFeet on 2008-02-11
bump

---

### Post by linuxisfree on 2008-02-11
> **HappyFeet said:**
> my PSP mounts OK, and a window opens with my folders on it. however, it does not let me transfer files to it. this worked OK in feisty and gutsy when it first came out. what happened? changing permissions and doing sudo nautilus does nothing to allow me to transfer files. i have a small xp partition for gaming, and can transfer files to xp then the PSP, but would like to do it in ubuntu. help?
 
Changing permissions (chmod) does nothing? Ok, i don't know if i'd go THIS far but, what about changing ownership (chown)?

---

### Post by HappyFeet on 2008-02-11
did that, no go.

i tried to change permission via right click as root. can you tell me how to chmod via command line?

---

### Post by linuxisfree on 2008-02-11
> **HappyFeet said:**
> did that, no go.
 
i tried to change permission via right click as root. can you tell me how to chmod via command line?
 
try this... In Terminal Type:
 
```
sudo chmod 777 /media/<name of PSP>
```
 
"/media/<name of PSP>" is your PSP mount point (whatever your mountpoint is... change it to whatever is appropriate)

---

### Post by HappyFeet on 2008-02-11
thanks alot for the info. as it turns out, my psp or ubuntu has decided to play nice and let me transfer stuff. i guess it might just be a hit or miss thing depending on if the gods are smiling down on me. i had a little trouble getting it to connect to xp also, so it's probably a  sony issue. thanks again.

---

### Post by linuxisfree on 2008-02-12
Anytime:)
 
So, i'm guessing you didn't have to change your permissions?

---

