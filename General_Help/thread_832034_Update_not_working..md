---
title: "Update not working."
date: 2008-06-17
forum: General Help
---

### Post by roclin on 2008-06-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I correct this? It comes up on my update s and will not update.:confused::(

---

### Post by VMC on 2008-06-17
> **roclin said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I correct this? It comes up on my update s and will not update.:confused::(

Did yo open a Terminal and run the command given: 'dpkg --configure -a'

---

### Post by avtolle on 2008-06-17
At the terminal```
sudo dpkg --configure -a
```

---

### Post by roclin on 2008-06-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Cannot update. This pops up.

---

### Post by LaRoza on 2008-06-17
Run this in terminal:
```

sudo dpkg --configure -a

```

To run updates again:
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean

```

---

### Post by roclin on 2008-06-22
When I try to load my updates this pops up:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I'm new to all this so keep this in mind when helping me.

Thanks, 
Charles Gray

---

### Post by PmDematagoda on 2008-06-22
> **roclin said:**
> When I try to load my updates this pops up:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I'm new to all this so keep this in mind when helping me.

Thanks, 
Charles Gray

Open a terminal through Applications>Accessories>Terminal and then execute:-
```
sudo dpkg --configure -a
```
you will be asked for your password but you will not see if as you type it. After the command is executed try and see if the problem is now solved.

Also, the Resolution Center is not the right place to post these types of questions since that particular section is to settle problems in forum conduct etc. and not for support requests, we have special sections for that like the section I moved your thread to:).

---

### Post by PmDematagoda on 2008-06-22
roclin, I don't know if you actually knew this, but you made two threads on this same topic previously and all of them got the same one, including the new one so please look at your old threads without creating new ones. Also understand that creating duplicate threads is not allowed here and that one thread will be more than enough.

---

### Post by roclin on 2008-06-27
When I try to install my now 96 updates I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Chuck Gray
[email]sunlightpro@att.net[/email]

---

### Post by schwascore on 2008-06-27
have you tried running the code it suggests?
```
sudo dpkg --configure -a
```
if so and it did not work, please post the error so we can help.  The more information you provide, the more we can do to help.

---

