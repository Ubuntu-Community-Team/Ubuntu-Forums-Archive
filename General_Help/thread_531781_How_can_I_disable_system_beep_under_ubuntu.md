---
title: "How can I disable system beep under ubuntu?"
date: 2007-08-22
forum: General Help
---

### Post by yinglcs2 on 2007-08-22
How can I disable system beep under ubuntu?
I already go to Sound Preferences and uncheck 'Enable system beep'.

What else do I need to do?

---

### Post by Ek0nomik on 2007-08-22
What else is there to do?  When are you hearing the system beep?

---

### Post by ebash on 2007-08-22
Disabling the system beep from the "Sound Preferences" settings doesn't guaranty that the system beep will be disabled. It's up to each application to check the global settings and to honor them. As you can see not every application does it.

The best way that I found to disable the system beep is to remove the kernel module that creates it. This has the advantage to turn off the PC speaker completely thats the speaker creating the beeps. It will work for all applications.

Execute the follow command in a terminal and try to see if you hear a beep:
```
sudo rmmod pcspkr
```

In order to always disable the speaker after each system boot add the following lines to the file /etc/modprobe.d/blacklist:
```

# No more beeps
blacklist pcspkr

```

---

### Post by steinarhugi on 2007-10-21
Thanks ebash, this solved the problem for me. I had disabled it successfully before (in 7.04) but when I upgraded to 7.10 it started beeping like crazy again, even though it was disabled in Sound preferences,

---

