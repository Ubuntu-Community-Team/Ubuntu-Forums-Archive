---
title: "Unable to open terminal from &quot; Your system is running in low graphics mode&quot; screen."
date: 2016-08-18
forum: General Help
---

### Post by uxaar on 2016-08-18
Hi

I am running 14.10 ubuntu and i get this screen  "Your system is running in low graphics mode" .
I want to enter terminal from here but the usual key combination CTRL+ALT+F1 doesnt do anything.
I do not know what to do.
I find it impossible to go anywhere from here.

Can someone help me with some ideas please ?

Thank you.

---

### Post by mörgæs on 2016-08-18
Hi, welcome to the fora.

Soon we will recommend that you overwrite the installation with some version of 16.04.1, because 14.10 is out of support but we need to know more. 

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by uxaar on 2016-08-18
> **mörgæs said:**
> Hi, welcome to the fora.

Soon we will recommend that you overwrite the installation with some version of 16.04.1, because 14.10 is out of support but we need to know more. 

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.


Hi,

Well, that is the thing...
How can i run this code if i can't enter terminal ?

I cant get into my laptop at all because of this "Your system is running in low graphics mode" screen

So in order to run any code i would have to be able to access a terminal which i cant becasue no key combination works.

I  also tried to from failsafe mode to enter CTRL+ALT+F1, F2, T...etc but all i get is a blank screen.

So what to do ?

[COLOR=#DD4814]
[/COLOR]

---

### Post by mörgæs on 2016-08-18
Then I guess it's best just to install a light Buntu (X/Lubuntu) in version 16.04.1 (not 16.04.0), erasing the old system in the process, provided you don't have anything of value on the hard drive.

---

### Post by Impavidus on 2016-08-18
If you create a live usb of L/X/Ubuntu 16.04.1, which you'll have to do anyway to install that version, you can run a live session to run the abovementioned command and to make backups of the files you want to keep.

---

