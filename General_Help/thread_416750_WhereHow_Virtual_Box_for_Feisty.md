---
title: "Where/How Virtual Box for Feisty"
date: 2007-04-21
forum: General Help
---

### Post by Kalixa on 2007-04-21
Today I decided I would like to try out Virtual Box, but I don't know how to install it. I tried visiting Virtual Box' homepage, but their are only install files for dapper and edgy. I couldn't find it in the repository either. So where and how do I install Virtual Box?

---

### Post by raja on 2007-04-21
Installing Virtualbox on Ubuntu is fairly easy and it is a great piece of software. I have a [post on my blog ]("http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html")with instructions to install it. You can use the terminal and just copy and past the instructions.

---

### Post by Kalixa on 2007-04-21
> **raja said:**
> Installing Virtualbox on Ubuntu is fairly easy and it is a great piece of software. I have a [post on my blog ]("http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html")with instructions to install it. You can use the terminal and just copy and past the instructions.

I am following your guide, and everything is going fine until I have to type this command:

sudo echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" >> /etc/fstab

I get a message saying:


bash: /etc/fstab: Permission denied

Is this ok? I don't understand why permission is denied. I did include sudo.

---

### Post by ebash on 2007-04-21
Do instead:
```
echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" | sudo tee -a /etc/fstab
```

---

### Post by Kalixa on 2007-04-21
> **ebash said:**
> Do instead:
```
echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" | sudo tee -a /etc/fstab
```

Ok. Thank you.

Now can someone link to a guide or something on how to use Virtual Box. I tried to create a virtual drive. But I couldn't figure it out.

---

### Post by raja on 2007-04-21
> **ebash said:**
> Do instead:
```
echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" | sudo tee -a /etc/fstab
```

Thanks for that ! I will include the correction in my instructions.

---

### Post by raja on 2007-04-21
> **Kalixa said:**
> Ok. Thank you.

Now can someone link to a guide or something on how to use Virtual Box. I tried to create a virtual drive. But I couldn't figure it out.

You can read the manual at VirtualBox's site. What OS do you want to run as the guest? I can guide you through the steps.

---

### Post by rabideau on 2007-04-21
I posted instructions here:

[http://ubuntuforums.org/showthread.php?t=415525](http://ubuntuforums.org/showthread.php?t=415525)

Anyone got the shared drives working yet??? How about USB???

---

### Post by raja on 2007-04-21
I have a shared folder working very well (more reliably than using samba shares with vmware) and can access USB devices too. I have mentioned the steps in my tutorial (see my signature).

---

### Post by Kalixa on 2007-04-22
> **raja said:**
> You can read the manual at VirtualBox's site. What OS do you want to run as the guest? I can guide you through the steps.

I am trying to install the >40mb version of Debian.

---

### Post by raja on 2007-04-22
So which step did you get stuck at when creating a new machine? Choose the location where you want to have the virtual machine and use a dynamically sized disk of about 4 GB. If you have the installation disk as an iso, you can mount it as a cd. If you have already burnt it, you can mount it from the physical cd drive. Then you just have to start the machine and allow it to boot from the cd.

---

### Post by Kalixa on 2007-04-22
> **raja said:**
> So which step did you get stuck at when creating a new machine? Choose the location where you want to have the virtual machine and use a dynamically sized disk of about 4 GB. If you have the installation disk as an iso, you can mount it as a cd. If you have already burnt it, you can mount it from the physical cd drive. Then you just have to start the machine and allow it to boot from the cd.

Ok. I will give it a try. Thank you.

---

### Post by jocheem67 on 2007-04-23
I'm on virtualbox for the first time, ans got it running fairly well..
Got usb going, got my virtual drive up and running. Got sound and so forth. It's working pretty swiftly...

Hmmmm, I think a good tutorial would be the thing to do, as there are several threads regarding virtualbox...

Though I'm not a linux guru, I could add some nice tricks which I collected from all over google....

Well we'll see...

---

### Post by raja on 2007-04-23
> **jocheem67 said:**
> 

Hmmmm, I think a good tutorial would be the thing to do, as there are several threads regarding virtualbox...



Yes, I have found it to be a great piece of software. I have put up a howto on my blog (see my signature) - will be glad if you have a look and suggest some tricks. You can also use it as a starting point if you write one in the forums here.

---

### Post by happybill on 2007-04-24
Hello,

Earlier this year, I struggled, and failed, to install VirtualBox in Dapper Drake.  When it was announced that Feisty Fawn would include VirtualBox, I ceased struggling and waited, then downloaded and installed Feisty at the first opportunity.  Virtualbox was not there.  I found this thread and Raja's very helpful howto.  
I'd like to ask Raja a couple of questions, please.

1.  Raja's advice about necessary files to load differs from VirtualBox advice on their download site.
2.  There is now a Feisty package on the VirtualBox download site.  

Is it best to stick to the Edgy package or use the Feisty package, Should I follow Raja's advice, or the advice on the VirtualBox site?

Happybill.

---

### Post by raja on 2007-04-24
Yes, I noticed that they now have a package for Feisty. I think you should use the Feisty package in that case. I havent tested it though.

---

### Post by jocheem67 on 2007-04-25
I installed the edgy one. 

Only two dependencies which installed easily. 

Nonetheless it's better to install the feisty one.

I struggle getting usb to work properly, will report back later...

---

### Post by raja on 2007-04-25
I would be interested in knowing about your problems with USB and how you solved them.

---

### Post by Kalixa on 2007-04-26
I am still struggeling on how to get an OS to work inside Virtual Box. I try to follow the guide for creating a new virtual machine. I chose what to call the machine, which kind of OS it is, and choose which hard drive to use. But nowhere in the guide through creating a new virtual machine do I get to choose the actual image which it should be based on. I am totally lost!

---

### Post by raja on 2007-04-26
Once you have created a virtual machine it is like a pc without an OS installed. You have to install an OS as you would do on such a PC. What guest OS do you want and how are you trying to install it?

---

### Post by Kalixa on 2007-04-27
> **raja said:**
> Once you have created a virtual machine it is like a pc without an OS installed. You have to install an OS as you would do on such a PC. What guest OS do you want and how are you trying to install it?

I am trying to install debian. I have made the virtual machine. But when I boot up the machine. (I have not choosed an ISO image to use yet) the program just gives me a message saying:

FATAL: No bootable medium found! System halted.

---

### Post by raja on 2007-04-27
> **Kalixa said:**
> I am trying to install debian. I have made the virtual machine. But when I boot up the machine. (I have not choosed an ISO image to use yet) the program just gives me a message saying:

FATAL: No bootable medium found! System halted.

Again, making a virtual machine just gives you a hard disk with a bios. You have to get a bootable medium from which you can install the OS. Download the install cd and mount it in the virtual machine as an iso or from the physical cd drive. Then you have to install the OS just as you would on a normal PC.

---

### Post by Kalixa on 2007-04-27
> **raja said:**
> Again, making a virtual machine just gives you a hard disk with a bios. You have to get a bootable medium from which you can install the OS. Download the install cd and mount it in the virtual machine as an iso or from the physical cd drive. Then you have to install the OS just as you would on a normal PC.

I am indeed trying to load the Debian ISO from the virtual machine. I start the virtual machine. Go to Devices>Mount CD/DVD-ROM>CD/DVD-ROM Image... and load up my Debian ISO image. But this does not help in any way. Nothing really happens. The screen just keeps giving me the fatal error message.

---

### Post by raja on 2007-04-27
Do you have the cdrom pointing to the iso **before** you start the device?

---

### Post by Kalixa on 2007-04-28
> **raja said:**
> Do you have the cdrom pointing to the iso **before** you start the device?

I can't belive I did not know that. Well Debian just booted up on my virtual machine. I will give it a try. Thank you!

---

### Post by dagrump on 2007-04-28
Wow, it took me awhile to get this working, but I've got 1 of my usb keys working. This works great on my laptop, I'm very impressed.

---

### Post by robtotheb on 2007-04-29
Just a warning to people.  Don't do any important work in photoshop from inside virtual box it has a very NASTY habit of corrupting the .psd file on save. Happened twice to me now and todays corruption has lost me some v important work. Guess its back to windows for photoshop work.  I'm holding back and not trying to flame!!!  sob sob

---

