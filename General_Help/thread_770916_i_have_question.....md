---
title: "i have question...."
date: 2008-04-27
forum: General Help
---

### Post by elonlon on 2008-04-27
i have question.
i saw on YouTube people whit Linux that can see all the 4 desktop in like square and when they close windows is dispersed like fire or something like this and when they open windows is open not in normal ways how can i do it too?
if it help when i look on YouTube the name i saw was like "Gnome + beryl"
all the time i saw this word Beryl
and here like to YouTube whit the clip i saw:

[http://www.youtube.com/watch?v=684OLRsTrrs&feature=related](http://www.youtube.com/watch?v=684OLRsTrrs&feature=related)

thank you very much for the help:)

---

### Post by MaindotC on 2008-04-27
Hi, elonlon.  What you saw was a project called Beryl, but it is now named Compiz-Fusion.  You can view the homepage for the project at [http://www.compiz-fusion.org](http://www.compiz-fusion.org).  You can enable this in Ubuntu depending on several factors, but mainly your video card.  You can follow this tutorial [http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200) or if you do a site search of ubuntuforums in google like this:
```

compiz-fusion how to site:ubuntuforums.org

```

Please let us know how it works out for you.

---

### Post by elonlon on 2008-04-27
OK i let you know if it work or not
if i will successes work it ON on the right way

---

### Post by elonlon on 2008-04-27
where exactly I download it i don't find it

---

### Post by elonlon on 2008-04-27
:(:(:(:(:(
I saw that people that use Ubuntu 8.04 can't get this 3D windows

---

### Post by MaindotC on 2008-04-27
There may be an issue with Compiz-Fusion, but as of right now the method for installing it can be found at this thread:  [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

If there are any issues, it will depend on the type and quality of hardware you use.  I hope this helps!

---

### Post by elonlon on 2008-04-27
i follow what he sayed and it don't work

---

### Post by MaindotC on 2008-04-27
> **elonlon said:**
> i follow what he sayed and it don't work

What did it say when it didn't work?  Can you post the exact output?

---

### Post by elonlon on 2008-04-27
elon@elon-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by elonlon on 2008-04-27
where the smili is it spost to be therehoe you do it ok?

---

### Post by MaindotC on 2008-04-28
Xgl isn't present.  Try doing this first:

```

sudo apt-get install xserver-xgl

```

the follow the thread I posted above.  I hope this helps!

---

