---
title: "Black Screen after login"
date: 2008-02-05
forum: General Help
---

### Post by Parind on 2008-02-05
I was playing around with my screen saver settings for the first time and after I selected a screesaver, I clicked preview. Suddenly the screen went black. All it shows now is my mouse pointer. I can hit ctrl+alt+arrow keys to go to different desktops but its completely BLACK every where.

I pressed Ctrl+Alt+F1, it shows that the system fails at two screen resolutions and then finally settles on 1028x768
then, 
kinit: name_to_dev_t(xxxxxx) = sda5(8,5)
kinit: No resume image, doing normal boot

and then it goes to my login and password, which by the way, works just fine. I just can not log into the GUI.

System: Recently purchased Vostro 1400 with Windows XP, which got replaced with UBUNTU 7.10 (Gusty Gibbon).

Can somebody guide me to resolution ? Elaborate explanation would be appreciated since its just been 2 days that I'm using a Linux system.

---

### Post by zvacet on 2008-02-05
After you login type 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Parind on 2008-02-05
Thanks sir. It worked. I greatly appreciate your quick response.
The only question I have now is, Why did that happen ? 

I noticed something though, after I login, the desktop goes black and then it takes a little for it to return and show me my desktop. So in short, it takes a little longer to completely login. Any idea why ?

---

