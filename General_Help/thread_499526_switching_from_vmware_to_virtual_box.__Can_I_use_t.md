---
title: "switching from vmware to virtual box.  Can I use the same windows install?"
date: 2007-07-12
forum: General Help
---

### Post by xl_cheese on 2007-07-12
I currently have vista ultimate installed using vmware.  Can I use the same install while running virtualbox?

I've been attempting it, but everytime vista boots using vbox I loose my mouse pointer and have to hit the powerbutton to shutdown and restart.  Virtual box at least gets to the screen where I can choose to start windows normally, etc...  I select booting normal and then the vbox window goes black and stays that way.

I'd like to not have to reinstall vista as I only can use 10 installs via msdn product key.

/var/lib/vmware-server/Virtual Machines/Windows Vista Ultimate/Windows Vista Ultimate.vmx

---

### Post by UK-Wobbie on 2007-07-12
> **xl_cheese said:**
> I currently have vista ultimate installed using vmware.  Can I use the same install while running virtualbox?

I've been attempting it, but everytime vista boots using vbox I loose my mouse pointer and have to hit the powerbutton to shutdown and restart.  Virtual box at least gets to the screen where I can choose to start windows normally, etc...  I select booting normal and then the vbox window goes black and stays that way.

I'd like to not have to reinstall vista as I only can use 10 installs via msdn product key.

/var/lib/vmware-server/Virtual Machines/Windows Vista Ultimate/Windows Vista Ultimate.vmx

What do you mean on this sorry? Do you mean that you wanna run vista on virtualbox and vmware at the same time? From the same H Drive?

Or do you mean that you like to run vista on vmware and put virtualbox in vista?

:confused:

---

### Post by xl_cheese on 2007-07-12
> **UK-Wobbie said:**
> What do you mean on this sorry? Do you mean that you wanna run vista on virtualbox and vmware at the same time? From the same H Drive?

Or do you mean that you like to run vista on vmware and put virtualbox in vista?

:confused:

No,  I've been using vmware, but want to try virtual box instead.  I've read that virtual box is less blurry and I want to give it a try to see for myself.

thx.

---

### Post by UK-Wobbie on 2007-07-12
> **xl_cheese said:**
> I currently have vista ultimate installed using vmware.  Can I use the same install while running virtualbox?

I've been attempting it, but everytime vista boots using vbox I loose my mouse pointer and have to hit the powerbutton to shutdown and restart.  Virtual box at least gets to the screen where I can choose to start windows normally, etc...  I select booting normal and then the vbox window goes black and stays that way.

I'd like to not have to reinstall vista as I only can use 10 installs via msdn product key.

/var/lib/vmware-server/Virtual Machines/Windows Vista Ultimate/Windows Vista Ultimate.vmx

I see what you saying now sorry :lolflag:

I have not use vmware be for! What is it like? Is it sh*t lol 
I use more of vbox that works ok with me on linux and windows.

You are saying that when you start vista from vbox it gets a black screen and the mouse pointer stops showing? Have you got it on vista in the vbox setup menu? I have not use vista in vbox be for sorry but i have use Xp and that works, I used it in ubuntu and Windows 2000

What ram have you got in your computer? Vista needs 2GB to run ok and not slowly.

In the vbox setup menu on makeing the hdrive you may need more then 4GB and 2GB of ram in your computer! Put the ram to a 1Gb if you can! Vbox may not yet you but play with it :) 

If your computer runs slow then put the ram down a bit! 

Sorry about the bad spelling

---

### Post by UK-Wobbie on 2007-07-12
> **xl_cheese said:**
> No,  I've been using vmware, but want to try virtual box instead.  I've read that virtual box is less blurry and I want to give it a try to see for myself.

thx.

I say virtual box is ok :lolflag: I like it!
You can use the same h drive if that what you like to no! In the vbox setup you can upload your backed up h drive image.

Give it the same ram and put it on vista, Then click on the backed up h drive and your away :)

---

### Post by xl_cheese on 2007-07-12
I get this how far I get when trying to start vbox with the image originally created by vmware:

[[IMG]http://img373.imageshack.us/img373/1276/screenshotli1.th.png[/IMG]](http://img373.imageshack.us/my.php?image=screenshotli1.png)

Once it times out and tries to boot normally It just goes to a black screen.  IF I click my mouse in there I loose the mouse pointer forever.

Maybe I will try to do a windows repair.

---

### Post by qpieus on 2007-07-12
It sounds like you're asking if virtualbox can use an OS image that was created using vmware. I found plenty of references in a google search saying that virtualbox can't use vmware images, however, this post on the virtualbox forums seems to say you can convert an vmware image so that virtualbox can use the converted image. This would mean you would not have to reinstall the guest OS, which is what you are asking about, I think. Here's the link:
[http://www.virtualbox.org/discussion/1/747](http://www.virtualbox.org/discussion/1/747)

---

### Post by UK-Wobbie on 2007-07-12
> **xl_cheese said:**
> I get this how far I get when trying to start vbox with the image originally created by vmware:

[[IMG]http://img373.imageshack.us/img373/1276/screenshotli1.th.png[/IMG]](http://img373.imageshack.us/my.php?image=screenshotli1.png)

Once it times out and tries to boot normally It just goes to a black screen.  IF I click my mouse in there I loose the mouse pointer forever.

Maybe I will try to do a windows repair.

Have a go on windows repair Or it may be that when you instell vista on a computer and then put the hdrive out from that computer in to a 2st computer it will not work 100% by settings!

It may be like that! If you install vista on vmware it will make the settings for that! If you move the hdrive image to vbox it cannot read the settings to work! 
:confused: I do not no sorry! 

But saying that on black screen thing i use to get that on ubuntu on my xp computer! If you make the ram low it use to make the screen black and then go slow! 

Hope you get it going :)

---

### Post by UK-Wobbie on 2007-07-12
> **qpieus said:**
> It sounds like you're asking if virtualbox can use an OS image that was created using vmware. I found plenty of references in a google search saying that virtualbox can't use vmware images, however, this post on the virtualbox forums seems to say you can convert an vmware image so that virtualbox can use the converted image. This would mean you would not have to reinstall the guest OS, which is what you are asking about, I think. Here's the link:
[http://www.virtualbox.org/discussion/1/747](http://www.virtualbox.org/discussion/1/747)

Hey i have not use vmware be for and do not no alot about it! 
But i did not no that vmware and vbox hdrive image is not the same!

I no windows 2007 virtua pc can run vbox images!

---

### Post by xl_cheese on 2007-07-13
> **UK-Wobbie said:**
> Have a go on windows repair Or it may be that when you instell vista on a computer and then put the hdrive out from that computer in to a 2st computer it will not work 100% by settings!

It may be like that! If you install vista on vmware it will make the settings for that! If you move the hdrive image to vbox it cannot read the settings to work! 
:confused: I do not no sorry! 

But saying that on black screen thing i use to get that on ubuntu on my xp computer! If you make the ram low it use to make the screen black and then go slow! 

Hope you get it going :)

Thanks for digging that up.  I couldn't get it to work tho after spending last night and this morning messing with it.  

I just removed the old image.

Now I'm running into problems just trying to install via vbox....

---

