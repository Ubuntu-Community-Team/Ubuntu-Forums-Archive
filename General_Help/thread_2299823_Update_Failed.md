---
title: "Update Failed"
date: 2015-10-21
forum: General Help
---

### Post by daniell59 on 2015-10-21
After my last update failed, I tried to install them from the terminal. I would appreciate assistance with the following instructions.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
daniel@daniel-N68SA-M2S:~$

---

### Post by slickymaster on 2015-10-21
> **daniell59 said:**
> After my last update failed, I tried to install them from the terminal. I would appreciate assistance with the following instructions.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
daniel@daniel-N68SA-M2S:~$

Did you tried the solution the terminal itself gave you?```
sudo dpkg --configure -a
```

---

### Post by daniell59 on 2015-10-21
> **slickymaster said:**
> Did you tried the solution the terminal itself gave you?```
sudo dpkg --configure -a
```

Did so and go the following.

Errors were encountered while processing:
 liboxideqt-qmlplugin:i386
 liboxideqtquick0:i386

---

### Post by Bashing-om on 2015-10-21
daniell59; Well,well ....

Package manager has encountered a situation and does not know how to deal with it. Wants a helping hand, huh .
Let's get a broad overview of what is going on.
Post the outputs - between code tags - of terminal commands:
```

uname ## so we know the platform architecture ##
apt-cache policy liboxideqt-qmlplugin:i386 ## what is installed ans where it came from ##
apt-cache policy liboxideqtquick0:i386
sudo apt update ##check the sources##
sudo apt upgrade ##check the package manager condition ##

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep a package manager
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by daniell59 on 2015-10-21
I don't know whether or not the problem has been solved.

---

### Post by sandyd on 2015-10-21
> **daniell59 said:**
> Did so and go the following.

Errors were encountered while processing:
 liboxideqt-qmlplugin:i386
 liboxideqtquick0:i386

Can you post the full output starting from when you ran dpkg please?

---

### Post by daniell59 on 2015-10-21
> **sandyd said:**
> Can you post the full output starting from when you ran dpkg please?

Are you saying that I should update it again?

---

### Post by daniell59 on 2015-10-21
Please see image.

---

### Post by slickymaster on 2015-10-22
> **daniell59 said:**
> Please see image.

Can you please post back here in the thread the full output you get from```
sudo dpkg --configure -a
```

---

### Post by daniell59 on 2015-10-22
I was able to solve the problem. I am ashamed to say that I forgot the command that I used in the terminal. All I remember was that it did not work until I put sudo in front of it.

I think that it was apt-get install -f

---

