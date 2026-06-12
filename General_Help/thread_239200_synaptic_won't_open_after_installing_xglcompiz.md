---
title: "synaptic won't open after installing xgl/compiz"
date: 2006-08-18
forum: General Help
---

### Post by TheRingmaster on 2006-08-18
I recently installed xgl/compiz from this post [http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl%2Fcompiz](http://www.ubuntuforums.org/showthread.php?t=222034&highlight=xgl%2Fcompiz)
and now I can't open synaptic package manager.

also the number pad on my microsoft wireless keyboard stopped working. The UP, Down, Left, Right function of the number pad works. It just can't get it to detect the numbers.

(everything worked great before installing xgl/compiz)

---

### Post by canadianwriterman on 2006-08-18
Open a terminal and do this:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

That should do the trick.

---

### Post by TheRingmaster on 2006-08-18
> **canadianwriterman said:**
> Open a terminal and do this:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

That should do the trick.
which one of my problems will this fix?

---

### Post by yatt on 2006-08-18
> **jpazindustries said:**
> which one of my problems will this fix?

Synaptic.

To fix the other one:
System->Preferences->Keyboard->Layouts

click the ... button, select any keyboard layout (just not the one you are using), click OK. Click ... again, and click the first layout again. I have to do this each time I log in.

---

### Post by shanepardue on 2006-08-18
> **canadianwriterman said:**
> Open a terminal and do this:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

That should do the trick.

what does that do? that fixed my synaptic, but how did it?

---

### Post by TheRingmaster on 2006-08-18
I don't have any other layouts or models available for me to use. Is there any other way to fix my numeric pad?

---

### Post by yatt on 2006-08-18
> **shanepardue said:**
> what does that do? that fixed my synaptic, but how did it?

The file libvte.so.4 was apparantly missing, so that command made a symbolic link to libvte.so.9, which is the same enough to get synaptic running.

---

### Post by TheRingmaster on 2006-08-19
still no fix for my numlock problem?

---

### Post by TheRingmaster on 2006-08-19
hello out there. Still no fix for my numlock problem?

---

### Post by TheRingmaster on 2006-08-19
Admins, Please delete or lock this thread. 

Thank you

---

