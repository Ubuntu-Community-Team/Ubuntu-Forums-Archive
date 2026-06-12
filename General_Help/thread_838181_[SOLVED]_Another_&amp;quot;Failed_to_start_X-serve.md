---
title: "[SOLVED] Another &amp;quot;Failed to start X-server&amp;quot; problem"
date: 2008-06-23
forum: General Help
---

### Post by Nathan_M on 2008-06-23
Hi,
I'm running Hardy with all the latest updates (including proposed) as of two days ago.
I started up my computer last night, and got the "Failed to start X-server (your graphical interface)" error. I'm then presented with a login terminal, so I log in, and try sudo dpkg-reconfigure xserver-xorg. I get the first grey box with the blue background asking me about frame buffering or something, then my computer just won't respond. I can't choose anything. I've tried looking at dpkg-reconfigure --help to see if there's an option to automatically select the defaults and there isn't. So I'm not sure what to do. At the moment I'm running from a Gutsy CD I had lying around. Any ideas?

---

### Post by Tomatz on 2008-06-23
Hi sorry to hear that.

What graphics card/drivers are you using?

---

### Post by Nathan_M on 2008-06-23
I'm running a Dell Inspiron 640m laptop. So it's an inbuilt graphics card. Using the default driver that comes with Hardy.

---

### Post by Lr5 on 2008-06-23
Try if the x server fix option in the recovery mode helps.

---

### Post by Nathan_M on 2008-06-23
That didn't work... I did get a possibly helpful error message though... it only flashed up quickly, so I didn't get to write it down properly:

"Unable to [???] /etc/x11/[then some filename with lots of numbers on the end]: Read only filesystem"

(The [???] is "create" or "write to" or something like that.) How do I fix that??

---

### Post by danwood76 on 2008-06-23
That error message is probably because your main partition is being loaded read only.

Reboot into normal mode and when you login to the terminal check the X logs for errors with the following command:
```

cat /var/log/Xorg.0.log | grep '(EE)'

```
(remember its case sensitive)

Post the errors ;)

---

### Post by Nathan_M on 2008-06-23
Nothing comes up... just the line at the beginning explaining what (EE) and (WW) and stuff means.

---

### Post by danwood76 on 2008-06-23
Thats odd, are you logging in and letting it crash out back to a terminal?
Errors should come up, if not then its something else possibly one of your startup programs.

When you get dropped back to a terminal run 'dmesg' and see if there are any kernel errors.

---

### Post by Nathan_M on 2008-06-23
I've managed to fix it! There was a couple of settings added to my fstab... the line which mounts my ubuntu partion. Forgotten what they were now! Should've written them down but I thought I'd remember. I've never heard of them before, so I just removed them, rebooted, and it worked!

---

