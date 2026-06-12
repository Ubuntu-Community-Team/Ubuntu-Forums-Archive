---
title: "NVIDIA trouble"
date: 2006-11-11
forum: General Help
---

### Post by Slothman on 2006-11-11
Hi,
I updated Edgy yesterday, and when I turned on my computer this morning X wouldn't start! I got this error message in the log:

FATAL COULD NOT OPEN /lib/modules/2.6.17-10-generic/volatile/nvidia.ko
NO SUCH FILE OR DIRECTORY

FAILED TO LOAD THE NVIDIA KERNEL MODULE

I installed the new nVidia driver (9629) and restarted X. I got the 'lovely' gray nVidia splash screen and everything seemed to work! 

Just a minute ago new updates became available and I updated, but after a reboot I got the same old problem!!! So I've gone back to using the 'nv' driver for the mo. 

Does anyone know how to resolve this problem??

Thanks

---

### Post by bollix47 on 2006-11-11
Try uninstalling nvidia-glx via synaptic, then switch back to the nvidia driver.

You may have to re-install the nvidia driver again.

---

### Post by Slothman on 2006-11-11
Sorry for the noob question, but how do I completely uninstall the nvidia driver?

Thanks

---

### Post by bollix47 on 2006-11-11
That would usually depend on how you installed it in the first place.  

If you're asking cause you want to re-install it after removing nvidia-glx from synaptic I don't think you have to.  Just re-install the nvidia driver using the same steps you used earlier.

I had a similar problem when updates came thru and I merely re-installed nvidia driver without uninstalling it.

---

### Post by igknighted on 2006-11-11
You should not need to reinstall the driver.  What happened was when you upgraded to edgy, the kernel was updated.  You just need to update the new kernel, and how you do that in Ubuntu I have no idea.  On my suse partition I downloaded the binaries from nvidia directly, and if you did that you can try this:
```
cd <*insert directory of driver binary installer here*>
sh <*insert file name here*> -K
```

If you installed through apt (or synaptic), or if that doesn't work I'm not sure where you'd go next.

---

### Post by bollix47 on 2006-11-11
All I did when an upgrade messed up my nvidia installation was to run the following from where I downloaded the new drivers:

sudo sh NVIDIA*.run

---

### Post by OffHand on 2006-11-11
Do this:

Install the driver again.

--open your terminal--

```
uname -r
```

```
sudo apt-get install linux-headers-2.6.17-10-generic
```
(If you are running the 386 kernel or another one replace generic with yours)

Now to 'fixate' the driver:

Logout, press ctrl+alt+F1, login and use the link below to make the changes you need.

[http://www.ubuntuforums.org/showpost.php?p=1700610&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1700610&postcount=2)

---

### Post by Slothman on 2006-11-11
I may have confused people in my first message, I did upgrade to edgy, I already had edgy working, I had a software update and after that I got the nVidia driver problem, i tried re-installing it with apt-get but that hasn't solved it. I'm gunna try re-installing it using sh NVIDIA*.run see if that fixes it :-k

---

### Post by bollix47 on 2006-11-11
Just to clarify, I ran sudo sh NVIDIA*.run when X failed to start on reboot.

If you already have X running due to one of your tries you have to follow these instructions:

Open a terminal and run this:

```
sudo apt-get install linux-kernel-headers build-essential

```

Above is probably not required as you should already have them but it won't hurt to check.

When finished logout and hit alt-ctrl-f1 .
Enter login and passw on the terminal screen.

Now run

```
sudo /etc/rc2.d/S13gdm stop

```
.
If you use kdm it's S13kdm, if you are on dapper I think the number is S99.
In any case you can write up to /etc/rc2.d/S and then hit tab.
This will list possible suggestions.

Next, cd to the directory where you have the driver.Run:

```
sudo sh NVIDIA*.run
```

( again writing sudo sh NV and hitting tab will autocomplete for you or list any possible combinations).

And now you are running the installer. If it asks to compile the module
(very likely) and then says it didn't find the headers, do the following:

```
sudo ln -s /usr/src/linux-headers(press TAB here) /usr/src/linux
```

(most probably it's linux-headers-2.6.17-10)

Now rerun the installer and everything should go fine.

Before going back to graphical mode you should disable nv by doing the following:

```
sudo nano -w /etc/default/linux-restricted-modules-common
```

find the line DISABLED_MODULES=""

change it to DISABLED_MODULES="nv"

rewrite the file


To go back to graphical mode run


```
sudo /etc/rc2.d/S13gdm start

```

That should return you to graphical mode.

---

### Post by Slothman on 2006-11-11
I installed the nvidia driver (9629) using sh NVIDIA*.run and everything is working now :D 

Thanks for the help guys ;)

---

