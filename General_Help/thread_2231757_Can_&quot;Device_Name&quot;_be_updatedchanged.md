---
title: "Can &quot;Device Name&quot; be updated/changed?"
date: 2014-06-27
forum: General Help
---

### Post by David D. on 2014-06-27
I got an HP Envy 17t-J100 to replace the HP dv7 I had been using for a number of years.  I moved the SSD from the dv7 to the Envy 17, and was successful in booting with everything working.  

It is a small thing, but I notice the the device name listed in "About This Computer" and the initial line in terminal still state "HP Pavilion dv7 Notebook PC".  Is there a file that can be edited or a CLI to update the device name to "HP Envy 17 Notebook PC"?

---

### Post by uRock on 2014-06-27
Hello, I think I found your answer here [http://askubuntu.com/questions/9540/how-do-i-change-the-computer-name](http://askubuntu.com/questions/9540/how-do-i-change-the-computer-name)

> You need to edit the computer name in two files:

```
/etc/hostname 
```
and

```
/etc/hosts
```
These will both need administrative access, so run

```
gksu gedit /path/to/file
```
Simply replace any instances of the existing computer name with your new one. When complete, restart your computer, and the name will have been changed.

See also:

[How do I change the hostname without a restart?]("http://askubuntu.com/questions/87665/how-do-i-change-the-hostname-without-a-restart")

---

### Post by David D. on 2014-06-27
Thank you uRock, that made the changes.

---

### Post by uRock on 2014-06-27
Awesome! You're welcome.

---

