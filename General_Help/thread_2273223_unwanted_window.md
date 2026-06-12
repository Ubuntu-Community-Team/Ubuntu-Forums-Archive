---
title: "unwanted window"
date: 2015-04-11
forum: General Help
---

### Post by Ronald_Williams on 2015-04-11
Last year I had a professional (?) geek install Ubuntu on an older HP laptop. (Ubuntu only, no other system on hard drive)

It took forever for him to figure out how to make it connect to my wireless router.

It now works, (more or less) with Firtefox. HOWEVER: a window keeps popping up in the upper right hand portion of the screen that says: "Wired connection not connected." He couldn't get rid of this, and neither can I.

I bought: "The Official Ubuntu Book" and read through as much of it as I could understand with no help.

I tried to reinstall Ubuntu from the CD in the book with no luck!

I forgot the password and don't know how to change it.

It works, more or less, logging in as "guest."

Any help would be greatly appreciated.

---

### Post by pmi2 on 2015-04-11
You will need a valid password sooner or later, so you may as well recover that first.  Basically, almost any changes you will have to make, or any new software you want to install will require a password.

You could try following the directions for what to do if the password is lost, here:

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

It is also helpful to know what is actually installed, if for no other reason then b/c people here will ask what version you have.  
If you can open a terminal window in your guest login, then try:

```
lsb_release -r
```
or, for more information:

```
lsb_release -a
```
this is what mine looks like:

```
peter@Flattop:~$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
peter@Flattop:~$ lsb_release -r
Release:    14.04
```

---

### Post by grahammechanical on 2015-04-11
By the way, the original problem is fixed by clicking on the Network Manager icon and selecting Edit Connections. Then select the Wired connection and click Edit. In the General tab untick the box labelled Automatically Connect to this Network when it is Available. And then click save.

Regards.

---

### Post by Ronald_Williams on 2015-04-11
I'm running 12.04 LTS
Can't get to the menus on the procedure recmmended I get GRUB and can't get past thast.

Is there any way to erase and reload perhaps???

BTW, thank you.

---

### Post by pmi2 on 2015-04-11
Erase and reload the Ubuntu OS?  Sure, but I would not be too quick to do that.

If someone else with more expertise had trouble to connect to your router, then you may have difficulty doing that also.  Setting up wireless connections seems to fall into two categories... either everything works out of the box, or it can become a major PITA. (been there, done that)

At the very least, I would try to find out what took extra effort to set up, perhaps the model of your installed wireless adapter, etc...

The standard way to reinstall from scratch is to download the latest LTS version in .iso format, then burn it to a DVD (or USB stick), make sure you can boot and run the os in trial mode from that media _before you erase your working os_, backup any personal files you may have created, and then reinstall.

Frankly, someone here can probably help you recover a working password once they know the Ubuntu version you have now.

edit:

Are you sure you can't get to the recovery menu?  I think the process is a little different in 14.04 (not sure about 12.04), so someone may be able to give you more exact directions.

---

### Post by Ronald_Williams on 2015-04-11
Had a store wipe the hard drive and reloaded from the CD in the book.

Starting to set it up now.

Thank you for your responses.

---

