---
title: "Unetbootin"
date: 2012-12-27
forum: General Help
---

### Post by anon_private on 2012-12-27
I have downloaded Unetbootin for Linux but I cannot get it to execute.

How can I change the  permissions. I tried chmod, but that did not work. I tried changing the attributes in Properties, but that also failed. I tried sudo chmod, and that did not work either.

---

### Post by slickymaster on 2012-12-27
Did you try to install it using the package manager:
```
sudo apt-get install unetbootin
``` and simply run ```
unetbootin
``` from the shell?

In any case the easy way for installing unetbootin is through the software center.

---

### Post by Dennis N on 2012-12-27
Install unetbootin using a package manager. When it's done, the program is good to go, in Lubuntu under System Tools.

Using apt in the terminal:

```
sudo apt-get install unetbootin
```

---

### Post by anon_private on 2012-12-27
Hi,

No, it did not occur to me that I needed to install.

I downloaded the Linux version from Souceforge and tried to run it on the desktop - why does this not work?

Thank you

---

### Post by Dennis N on 2012-12-27
> **anon_private said:**
> Hi,

No, it did not occur to me that I needed to install.

I downloaded the Linux version from Souceforge and tried to run it on the desktop - why does this not work?

Thank you

I see a binary file offered for Linux, **unetbootin-linux-581**. However, for best *buntu integration and to avoid security issues always use a Ubuntu package manager (or Lubuntu Software Center) which uses the Ubuntu repos, or trusted PPAs, as software sources whenever possible. 

That said, as to your question:

The downloaded file won't run unless it is executable, AND you as the user have the necessary permission, AND the system can find it and related resources. Just double-clicking on it will not necessarily work.

---

### Post by mrjava on 2012-12-27
> **anon_private said:**
> Hi,

No, it did not occur to me that I needed to install.

I downloaded the Linux version from Souceforge and tried to run it on the desktop - why does this not work?

Thank you


The file you downloaded was most likely not executable.

---

### Post by anon_private on 2012-12-27
Right.

I had a look at Synaptic Package Manager and saw two files:
unetbootin
unetbootin-translations.

I had a look at Lubuntu Software Centre and saw, in the Basket
unetbootin
+ many files (requested by unetbootin).

I was confused as to what I should install, so I decided to use the command prompt:

sudo apt-get install unetbootin

The first atempt prompted a lubuntu panic.

The second attempt was sucessful.
The last line read: ldconfig deferred processing now taking place. I then saw the command prompt.

On typing unetbootin in Terminal I got the message 'QGtkStyle was unable to detect the current GTK+ theme'.

But unetbootin started.

Is everything alright?

If so, I will try and make the bootable USB.

I can't find unetbootin in the dropdown menus.

Where is it on the USB stick?

I have not rebooted as yet

If I decided later to remove unetbootin. How would I do this?

Thanks.

A

---

### Post by anon_private on 2012-12-27
Bad news.

I have rebooted and tried typing unetbootin in Terminal.

I got the following response:


'lubuntu@lubuntu:~$ unetbootin
The program 'unetbootin' is currently not installed.  You can install it by typing:
sudo apt-get install unetbootin
lubuntu@lubuntu:~$'

It looks like I can't install to a USB

I suppose I will have to use sudo apt-get install unetbootin then make my other USB stick bootable before any restarts, reboots, etc.

I am a little disappointed

---

