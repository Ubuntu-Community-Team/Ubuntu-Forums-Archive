---
title: "silverlight/moonlight problem"
date: 2013-08-08
forum: General Help
---

### Post by george-saulnier on 2013-08-08
So my company has begun using a program called Dayforce to manage payroll and scheduling at work. the idea is that it is cloud based and employees can access their schedule and request time off and such from home. the program is built on Silverlight and does not want to run on my Ubuntu 13.04 chromium or firefox browsers or so ti tells me every time I try to open it. I have installed Splashtop because that said it would run silverlight program but that has failed. I installed the mono-complete package from the Ubuntu depository to run moonlight; that too has no effect. I cannot down load the silverbrite plug-in or program because I get a 403 Forbidden message because the server won't/can't access it. Anyone got any ideas? can one use WINE somehow?

---

### Post by Habitual on 2013-08-08
Virtualbox+Windows = tried and true.

---

### Post by george-saulnier on 2013-08-08
habitual what does that mean?

---

### Post by wildmanne39 on 2013-08-08
He is saying to install virtualbox, then install windows in it and use windows in a virtual machine.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

You will be able to run ubuntu and have windows running at the same time in virtualbox it is great to have this option.

---

### Post by george-saulnier on 2013-08-08
okay i installed virtualbox now how do i get windows on there?

---

### Post by wildmanne39 on 2013-08-08
The link I gave you has all the information you need to install an operating system in virtualbox, start with documentation on there site. 

Of course you will need a windows disk.

---

### Post by howefield on 2013-08-08
Do you have a Windows installation disk ?

There are a few videos that you can watch over at the Virtualbox youtube channel which will give you an idea of what is involved, eg...

[http://www.youtube.com/watch?v=mMP41VoDu-E](http://www.youtube.com/watch?v=mMP41VoDu-E)

---

### Post by george-saulnier on 2013-08-08
i don't have a windows disk.

---

### Post by Mark Phelps on 2013-08-08
> **george-saulnier said:**
> i don't have a windows disk.

Then ... you can't use Virtual Box -- as that requires a fresh installation of Windows to work.

---

### Post by KivalliqKid on 2013-08-08
Microsoft created some free Windows PC VHD's for testing internet explorer. Since IE cannot exist without Windows you need to install VirtualBox and it will install Windows and whatever version of IE you choose to 'test'. This is large and takes quite a bit of time. You can follow the steps from Webupd8: [http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html](http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html)

---

### Post by timgood on 2013-08-09
I'm using VirtualBox and still having problems with the Silverlight plugin. I can't access BT Sport channels, and using Windows 7 the Silverlight example page won't run. Works with XP, but still not able to access BT Sport.

---

