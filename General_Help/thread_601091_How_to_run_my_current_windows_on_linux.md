---
title: "How to run my current windows on linux"
date: 2007-11-02
forum: General Help
---

### Post by eXeCuTeR+ on 2007-11-02
How can I run Windows on Linux?

Thanks.

BTW,
How can I use/run compiz? I installed compiz-settings manager and the whole compiz package.

Thanks again.

:)

---

### Post by Maestro23 on 2007-11-02
Vmware: [http://www.vmware.com/](http://www.vmware.com/)

Virtual Box: [http://www.virtualbox.org/](http://www.virtualbox.org/)

If you just want to run Windows based programs, look into Wine: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by eXeCuTeR+ on 2007-11-02
> **Maestro23 said:**
> Vmware: [http://www.vmware.com/](http://www.vmware.com/)

Virtual Box: [http://www.virtualbox.org/](http://www.virtualbox.org/)

If you just want to run Windows based programs, look into Wine: [http://www.winehq.org/](http://www.winehq.org/)

Download both programs?
BTW,
I'm gonna run my current windows and not a new one, right?

BTW 2,
I entered into vmware.com and didn't find a download for it.
Could you send me a download?

---

### Post by Therion on 2007-11-02
As for Compiz-Fusion, some starting points are [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"), [here]("http://wiki.opencompositing.org/Plugins/Animation") and [here]("http://wiki.opencompositing.org/PluginsMain").

---

### Post by lyndaj70 on 2007-11-02
I use VirtualBox personally. It works pretty good. Have it running Win2k on my laptop for the couple of programs I haven't found successful replacements for yet, and am planning to put Vista on this desktop that way and eliminate the dual boot sometime in the future...

Good luck!\\:D/

---

### Post by eXeCuTeR+ on 2007-11-02
Ok thanks guys.

---

### Post by eXeCuTeR+ on 2007-11-02
How do I run compiz?
I reinstalled it and installed compizconfig-settingsmanager but how do I run it now? how do I get to the windows thingy?

---

### Post by Maestro23 on 2007-11-02
> **eXeCuTeR+ said:**
> How do I run compiz?
I reinstalled it and installed compizconfig-settingsmanager but how do I run it now? how do I get to the windows thingy?

Here's a nice tutorial that should help: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by eXeCuTeR+ on 2007-11-02
> **Maestro23 said:**
> Here's a nice tutorial that should help: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Thanks mate.

---

### Post by eXeCuTeR+ on 2007-11-02
How can I run windows on linux?
I wanna run my current windows system (that already exists in my computer) on linux and not make a new one.
is that possible?
if so, please tell me how.

i downloaded virtualbox btw,
how do i do it now?

thanks :)

---

### Post by arkara on 2007-11-02
i think it is possible by making an image of your windows partition and then run it on a virtual machine.
or you can create a new virtual system. the problem is that you won't be able to achieve a 3d acceleration, and also there could be problems with the virtual hardware, cause windows is installed on your physical hardware and virtual hardware is not the same with you physical one.
you can get a virtualization software by typing
sudo aptitude install virtualbox on your terminal

---

### Post by eXeCuTeR+ on 2007-11-02
> **arkara said:**
> i think it is possible by making an image of your windows partition and then run it on a virtual machine.
or you can create a new virtual system. the problem is that you won't be able to achieve a 3d acceleration, and also there could be problems with the virtual hardware, cause windows is installed on your physical hardware and virtual hardware is not the same with you physical one.
you can get a virtualization software by typing
sudo aptitude install virtualbox on your terminal

but it says that i need to make a new harddisk or something =o
what do i do then?
there is a New button and Existing.. button.
There's nothing in the Existing button I guess, gotta check next time im on linux.

---

### Post by arkara on 2007-11-03
virtual machines are working on virtual hard drives.
these hard drives are stored on your physical hard drive as a file.
this add button is to add a virtual hard drive that you already have.
i think that you don't have one so go ahead and create one it's very simple.
the next thing you have to do is to choose the new hard drive for the virtual machine you have created.

---

