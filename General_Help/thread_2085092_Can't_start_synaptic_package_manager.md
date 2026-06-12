---
title: "Can't start synaptic package manager"
date: 2012-11-17
forum: General Help
---

### Post by ubto66 on 2012-11-17
ubuntu 12.04 
running on a usb memory stick
lxde

Several times I have used synaptic package manager in order to remove older
kernels, and it has worked every time.
I use a procedure I found on the internet.

This time synaptic package manager would not open and I got an error message.
Info:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I do not understand the message, and I do not know how to resolve it.

Thanks, if you could tell me what to do.

Remark: The error occurred after updating to the latest kernel, and I have restarted.

---

### Post by QIII on 2012-11-17
An update was interrupted and things are in an odd state.

In the terminal, do

```
sudo dpkg --configure -a
```

and press enter.  Enter your password carefully when prompted.  It will appear as though nothing is happening when you type.  This is a normal safety feature.

The update process should continue and finish and things should be normal thereafter.

---

### Post by kc1di on 2012-11-17
hi ubto66,

The error message conatains the answer:
go to a terminal and run the following command
```
sudo dpkg --configure -a
```

Then run the following also:
```
sudo apt-get autoclean 
sudo apt-get clean
```

try to start synaptic from the same terminal with
```
sudo synaptic
```
if it opens fine if not post any error messages you receive here

---

### Post by ranger1021994 on 2012-11-17
You might have broken packages or you might have interrupted some installation process.

Try :
```
sudo dpkg --configure -a
```

---

### Post by ubto66 on 2012-11-17
Thank you for all the answers.
You were right. It was an error regarding the last updating.
I tried to update again, and though it said something about update errors
in the terminal, during the update procedure, it finished updating and know
synaptic package manager runs.

---

### Post by kc1di on 2012-11-17
Glad you got it going :)
when you have a moment please mare thread as Solved - thanks

---

### Post by dkolars on 2013-09-19
> **kc1di said:**
> hi ubto66,

The error message conatains the answer:
go to a terminal and run the following command
```
sudo dpkg --configure -a
```

Then run the following also:
```
sudo apt-get autoclean 
sudo apt-get clean
```

try to start synaptic from the same terminal with
```
sudo synaptic
```
if it opens fine if not post any error messages you receive here

Just ran into this problem, and wanted to say that this fix WORKED...  autoclean hung the first time, but I ran clean, then autoclean and I'm back in business...  I would attempt to open Synaptic PM or Ubuntu Software Center, it would flash on the screen, then disappear...  NOW it works.  Thanks, Gracias, Merci, Danke, Mahalo!!

---

