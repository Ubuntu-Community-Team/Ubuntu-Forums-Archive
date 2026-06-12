---
title: "Automating backup of USB drive key??"
date: 2007-07-31
forum: General Help
---

### Post by jboehm on 2007-07-31
Hi,

I keep my thunderbird profile and mail folders on a usb drive key so that it is portable and cross platform.  This data is very important to me.  How can I set thing up, so that I can execute a backup script when the drive key is mounted.

I am familiar with rsync but what I don't know is how to kick off a script every time the drive key mounts.

Thanks for the help,
Jon

---

### Post by jnorthr on 2007-07-31
Think i saw a feature like this yesterday in ubuntu 7.0.4, but can't remember which way to find it. try under 'computer' then right-click on usb drive. Something in that areas offers the ability to run a program each time the device is mounted and/or unmounted. Sounds like that is what you want, otherwise you may just need a chron job to do it every so often.

---

### Post by jboehm on 2007-08-01
I did some looking last night.  There is a control panel called something like Removable media.  In there, there is an option, somthing like Auto Launch application upon mount.  Basically I created a scripted titles "autorun.sh" on the top level of the removable drive.  Every time the dive mounts it runs the autorun.sh script.  Pretty easy and pretty neat.

Thanks for the leed,
Jon

---

### Post by Incense on 2007-08-01
I have never used it, but I heard them talking very highly about it on the Linux Action Show a couple weeks ago, and I think it may do what you want. It's called conduit. Let us know if it works. 

Fiesty Build on GetDeb

[http://www.getdeb.net/app.php?name=Conduit]("http://www.getdeb.net/app.php?name=Conduit")

---

