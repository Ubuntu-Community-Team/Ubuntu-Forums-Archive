---
title: "synaptic package manager"
date: 2008-07-07
forum: General Help
---

### Post by wfp on 2008-07-07
Hi was trying to install java 5 from the terminal,and shut the terminal down before the install was complete, now when i try to open a terminal window i get this message> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor help to a newbie please

---

### Post by mcduck on 2008-07-07
You should do what the error messgae tells you to do. Open a terminal and run this command:

```
sudo dpkg --configure -a
```

---

### Post by dexter.deepak on 2008-07-07
go to the terminal and type :
```
sudo rm /var/lib/dpkg/lock
```

OR 
simply reboot !!

---

### Post by iaculallad on 2008-07-07
> **dexter.deepak said:**
> go to the terminal and type :
```
sudo rm /var/lib/dpkg/lock
```

OR 
simply reboot !!

DON'T. Since you're not getting any errors such as:

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Go with what mcduck had posted. The Error Message displayed had clearly stated the solution to your problem, only without displaying the complete command:
[B]
sudo dpkg --configure -a[/B]

---

### Post by wfp on 2008-07-07
Thanks you all for your help, error messages are gone and java installed. just installed hardy last night with a dual boot of xp still trying to learn my way around. Thanks:)

---

