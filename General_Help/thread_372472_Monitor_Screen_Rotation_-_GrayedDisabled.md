---
title: "Monitor Screen Rotation - Grayed/Disabled"
date: 2007-02-28
forum: General Help
---

### Post by v8YKxgHe on 2007-02-28
Hey,

I've just got a new Dell 2007FP Monitor and I would like to rotate it on it's side for when I am coding. However, when I go to System->Prefs->Screen Resolution the option to rotate the screen is grayed/disabled. Why is this? I have ran "sudo dpkg-reconfigure xserver-xorg" to see if that would do anything but it hasn't. 

Is there another way to rotate it?

Regards

---

### Post by veloce on 2007-02-28
You could try xrandr.  I think the command would be:

sudo xrandr --screen 0 -r left

but check the man page.

---

### Post by v8YKxgHe on 2007-03-01
Thanks veloce, but I was trying this before and got no where:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I have an ATI X800XT with the fglrx drivers installed. Could it be that these drivers don't support rotation?

---

### Post by radinator on 2007-03-05
I've been using xrandr for quite some time with my Dell 2405FPW monitor - until I just updated to kernel 2.6.15-28-amd64 and fixed the subsequent nvidia driver headaches.

Now, trying to do 'xrandr -o 1' gives the following:
```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

