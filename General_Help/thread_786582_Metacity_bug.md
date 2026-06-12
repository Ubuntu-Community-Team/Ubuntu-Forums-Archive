---
title: "Metacity bug"
date: 2008-05-08
forum: General Help
---

### Post by castironpants on 2008-05-08
This is a bug that seems to have followed me from Gutsy to Hardy. Randomly, my window borders will look weird, as shown in the screenshot. I've tried multiple themes, and it does it to all of them at one point or another. What's wrong?

[IMG]http://img140.imageshack.us/img140/4633/screenshot1resizedbr0.png[/IMG]

---

### Post by joselin on 2008-05-08
Are you using emerald and compiz?

---

### Post by castironpants on 2008-05-08
Compiz yes, emerald no. That's why it's a Metacity bug. As I recall, though, it did the same thing with emerald on Gutsy.

---

### Post by joselin on 2008-05-08
> **castironpants said:**
> Compiz yes, emerald no. That's why it's a Metacity bug. As I recall, though, it did the same thing with emerald on Gutsy.

In this case, try to launch compiz from a terminal and then post here the output.

```
compiz --replace
```

---

### Post by castironpants on 2008-05-08
Hmm, this might be something:

jeremy@box:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d7 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by imperius1 on 2008-06-27
I'm having the exact same problem. I've tried numerous solution posted in the forums and no joy. The only thing I could do was install emerald and try to find a theme similar to the stock human theme. I'm not entirely happy with this solution and find the problem only presents itself with the human theme. Please let me know if anyone has a good solution to this issue. Thank you.

---

### Post by castironpants on 2008-06-27
I seem to have made one big discovery about the bug, at least on my computer, and that is that it only occurs when OpenOffice is open. It usually happens TO openoffice, but it seems the closer another window is to it, the more likely it is to affect it.

---

