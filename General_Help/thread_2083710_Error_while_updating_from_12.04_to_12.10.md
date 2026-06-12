---
title: "Error while updating from 12.04 to 12.10"
date: 2012-11-13
forum: General Help
---

### Post by intelaravind on 2012-11-13
Hi,

I was trying to update my laptop from ubuntu 12.04 to 12.04 and unfortunately in between it ran out of power. Now there are lot of errors and gnome is not loading. I am able to access the terminal and lxde desktop. I have tried executing the following commands and most of them result in "Processing was halted because there were too many errors".

sudo dpkg --configure -a
sudo apt-get update
sudo dpkg --clear-avail
sudo apt-get clean
sudo apt-get upgrade

and the aptitude versions of the above.

Any help appreciated :)

---

### Post by philinux on 2012-11-13
> **intelaravind said:**
> Hi,

I was trying to update my laptop from ubuntu 12.04 to 12.04 and unfortunately in between it ran out of power. Now there are lot of errors and gnome is not loading. I am able to access the terminal and lxde desktop. I have tried executing the following commands and most of them result in "Processing was halted because there were too many errors".

sudo dpkg --configure -a
sudo apt-get update
sudo dpkg --clear-avail
sudo apt-get clean
sudo apt-get upgrade

and the aptitude versions of the above.

Any help appreciated :)

To be honest, in this situation I'd backup important stuf and do a clean install of 12.10

---

### Post by intelaravind on 2012-11-13
Hi,

Thank you for your reply. There will be a lot of problems if I do that. Is there no other way?

---

### Post by philinux on 2012-11-13
> **intelaravind said:**
> Hi,

Thank you for your reply. There will be a lot of problems if I do that. Is there no other way?

Try ```
sudo apt-get install -f
```

Then ```
sudo dpkg --configure -a
```

Post back the errors.

---

### Post by intelaravind on 2012-11-13
Tried this also. Same response :(

---

### Post by philinux on 2012-11-13
> **intelaravind said:**
> Tried this also. Same response :(

Maybe something here.
[http://serverfault.com/questions/8540/recover-from-shutdown-during-ubuntu-distribution-upgrade](http://serverfault.com/questions/8540/recover-from-shutdown-during-ubuntu-distribution-upgrade)

Interesting option there in the link  sudo dpkg --configure -a --abort-after=99999

[edit] from the man page. > --abort-after=number
              Change after how many errors dpkg will abort. The default is 50.


I'd still backup important stuff while you can get in.

---

### Post by intelaravind on 2012-11-13
That too did not work. Same error

---

### Post by philinux on 2012-11-13
> **intelaravind said:**
> That too did not work. Same error

What does this spit out.

```
sudo do-release-upgrade
```

There maybe an option to resume/resurrect the upgrade. Clutching at straws here.

---

### Post by intelaravind on 2012-11-13
The output is as below

Checking for a new Ubuntu release
No new release found



> **philinux said:**
> What does this spit out.

```
sudo do-release-upgrade
```

There maybe an option to resume/resurrect the upgrade. Clutching at straws here.

---

### Post by philinux on 2012-11-13
It sounds well and truly borked.

---

### Post by intelaravind on 2012-11-13
hmmm. is it possible to remove all the packages that causes the problem. Probably this will cause a chain of package removals..... I know. But as a last step may be I try that. How could I do the same?


> **philinux said:**
> It sounds well and truly borked.

---

### Post by philinux on 2012-11-13
> **intelaravind said:**
> hmmm. is it possible to remove all the packages that causes the problem. Probably this will cause a chain of package removals..... I know. But as a last step may be I try that. How could I do the same?

I know u said a reinstall would be problematic but it will be quicker.  Maybe someone else has an idea.

---

### Post by intelaravind on 2012-11-14
Any other way? Anyone

---

### Post by philinux on 2012-11-14
What gives if you try to reinstall ubuntu desktop.

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by intelaravind on 2012-11-14
From the logs I found that python 3 is causing the problem. Some EOF errors are thrown

> **philinux said:**
> What gives if you try to reinstall ubuntu desktop.

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

