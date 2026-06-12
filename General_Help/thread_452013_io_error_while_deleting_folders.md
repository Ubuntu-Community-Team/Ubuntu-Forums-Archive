---
title: "i/o error while deleting folders?"
date: 2007-05-22
forum: General Help
---

### Post by atozitsthateasy on 2007-05-22
Hello Ubuntu forums! How are you all? I just registered to get a little (or big, I really don't know) help on this error while I was trying to delete folders. Let me post the screenshot of the incident.

---

### Post by bobplano on 2007-05-22
well it sounds like some kind of external device. does a little icon appear on the desktop when its plugged in? or in more jargony terms is it mounted? there is a difference between these two but most likely if its on your desktop its mounted. what kind of device is it anyway?

---

### Post by atozitsthateasy on 2007-05-22
It's a external hard drive, that I have my collection of stuff.

The hard drive icon appears when I turn it on.

---

### Post by FuturePilot on 2007-05-22
That happened to me once. It was only one folder though. My external HD came disconnected before everything was copied onto it. The folder became corrupted I think. I had to boot Windows to delete it.:(

---

### Post by atozitsthateasy on 2007-05-22
This pretty much sounds like a solution.

I have one more question though, is there a solution to deleting it off by means of Linux?

Oh, and thank you all for helping me on this problem. :)

---

### Post by FuturePilot on 2007-05-22
I was wondering the same thing. Hopefully someone knows a way to be able to do this without Windows.

---

### Post by bobplano on 2007-05-22
you could try
```
sudo rm -rf /media/...
``` 
that should delete almost any folder you want, just replace /media/... with wherever the folder is

---

### Post by atozitsthateasy on 2007-05-22
that didn't work. :(

oh, well. I think I have to use *shudders* Windows...

Well, thanks for your help. :)

---

