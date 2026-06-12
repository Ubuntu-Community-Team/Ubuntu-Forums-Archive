---
title: "software updater suddenly will not work"
date: 2014-05-17
forum: General Help
---

### Post by Richard_Brickley on 2014-05-17
I tried to update my Ubuntu 14.04 today.  I get the message 
You are not allowed to perform this action
you do not have the required privileges to perform this action
I had updated this os several times before without any problems and I do not know what changed in the last few days.

---

### Post by deadflowr on 2014-05-17
Seems weird. 
Perhaps, first try this.
Right-click on the Software Updater icon, in the launcher.
Then see if it has an option for "quit".
If it does, click on the quit option, and then wait a few seconds, then try relaunching it.

If that doesn't work, on to phase two...

---

### Post by Richard_Brickley on 2014-05-19
Clicking on quit did not work.  If I click on ok when it tells me I do not have the privilege, the program will look like it is starting to download the update but will just disappear in a couple of seconds.

---

### Post by sammiev on 2014-05-19
What happens if you try to update in Terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

Please post any errors.

---

### Post by deadflowr on 2014-05-19
> **sammiev said:**
> What happens if you try to update in Terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

Please post any errors.

^^^^Phase two

If posting the output , use code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

