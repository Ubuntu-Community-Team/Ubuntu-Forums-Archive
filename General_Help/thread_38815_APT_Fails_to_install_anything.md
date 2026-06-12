---
title: "APT Fails to install anything"
date: 2005-06-02
forum: General Help
---

### Post by Witchhammer on 2005-06-02
Hello people,

I am having a prouble with apt-get, everytime I try to install something it says this:

Reading Package Lists... Done
Building Dependency Tree... Done
E: The package jre needs to be reinstalled, but I can't find an archive for it.

I have installed Java manually because if I try to do apt-get isntall jre I get the same error, any thoughts?

---

### Post by xristos on 2005-06-03
First of all uninstall tha package of java that you manuallu installed .
Then read this [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) 
If you have any questions feel free to ask .

---

### Post by SAPnet on 2005-06-03
[QUOTE=xristos]First of all uninstall tha package of java that you manuallu installed .
Then read this [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) 
If you have any questions feel free to ask .[/QUOTE]
 That only shows how to install using apt-get.

And the package that says to use cannot be found... any ideas?

Brad.

---

### Post by xristos on 2005-06-03
Check this out [http://www.ubuntuforums.org/showthread.php?t=39025](http://www.ubuntuforums.org/showthread.php?t=39025) .

---

### Post by Witchhammer on 2005-06-07
Yeah well I googled and couldn't find this so I guess I'll ask here.

How would I go about removing Java which I installed manually?

---

### Post by Witchhammer on 2005-06-15
Ok I deleted java then I installed it the way it says in the Ubuntu guide.

Though apt still gives the same error as before:

Reading Package Lists... Done
Building Dependency Tree... Done
E: The package jre needs to be reinstalled, but I can't find an archive for it.

Any idea's?

---

### Post by machetti on 2005-06-15
[QUOTE=Witchhammer]Hello people,

I am having a prouble with apt-get, everytime I try to install something it says this:

Reading Package Lists... Done
Building Dependency Tree... Done
E: The package jre needs to be reinstalled, but I can't find an archive for it.

I have installed Java manually because if I try to do apt-get isntall jre I get the same error, any thoughts?[/QUOTE]
 hi, what i think happened is that you ran "apt-get update" now any time you want to install something it looks for the software on the internet. what you should try to do is find out how to disable this .

---

### Post by jaranguren on 2005-07-10
witchhammer,  i had this same problem but for a different package and here's what I did to get rid of the error

ERROR FROM APT
Reading package lists... Done
Building dependency tree... Done
E: The package kernel-image-2.6.112470-020-08-ba needs to be reinstalled, but I can't find an archive for it.

WHAT  I DID TO REMOVE ERROR
sudo dpkg -r --force-remove-reinstreq kernel-image-2.6.112470-020-08-ba

hope this helps.

---

### Post by Juggernaut on 2005-07-21
Hello,

I've got the same problem.

I have a Brother HL 5130 laser printer.

Gnome was able to detect it, but didn't have the according driver. I thought I wouldn't get the best results when using a driver for a similar model (5040 I think).  

Brother provides drivers for Linux on their homepage, even in deb-format. The name is something like hl5130blabla.deb

I tried to install that wih dpkg, but it wouldn't work because some dirs were missing.

I tried to create those missing directories manually and sort of messed everything up.

It's still not working, but now whenever I start synaptics, I get the same error message the OP ran into:
E: The package hl5130blabla needs to be reinstalled, but I can't find an archive for it.

I tried to de-install the driver with dpkg -r --force-remove-reinstreq hl5130blabla but it always tells me that it can't find anything to remove. 

Tried sudo apt-get autoclean, update, upgrade and the like, but to no avail.

It'd be great if someone could help me with this!

---

### Post by Dave In Sidney on 2005-08-05
Yet another in the same boat. My problem came while trying to install drivers for a Brother MFC-6800. Has anyone found a solution yet?

---

### Post by mbeach on 2005-08-11
i've got the same error after trying the deb package for the Brother MFC-8840.  Well done brother.  Now the Synaptic manager won't start - keeps giving the same error you guys got "the package mfc8840dlpr needs to be reinstalled, but I can't find an archive for it."

I've tried the --force-remove-reinstreq suggestion, but still no luck.

mb.

---

### Post by mbeach on 2005-08-12
I managed to clear my error by editing the 
/var/lib/dpkg/status
and
/var/lib/dpkg/available

files.  I remove the sections having to do with the Brother printer.

---

