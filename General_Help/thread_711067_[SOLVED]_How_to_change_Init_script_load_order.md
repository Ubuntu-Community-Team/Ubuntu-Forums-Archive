---
title: "[SOLVED] How to change Init script load order"
date: 2008-02-29
forum: General Help
---

### Post by BigBadOwl on 2008-02-29
Hi there

I'm running LCDd which uses the start script /etc/init.d/LCDd which was installed as part of the LCDproc Ubuntu package. I'm also running mythlcdserver which is installed with the MythTV Ubuntu package and is started indirectly by the /etc/init.d/mythtv-backend startup script.

The problem is that the LCD does not display the output from MythTV unless I exit Mythfrontend, kill mythlcdserver and then restart mythfrontend (which automatically restarts mythlcdserver). I have to kill mythlcdserver, just restarting mythfrontend is not enough.

It seems to me that the mythlcdserver is starting before LCDd startup script has run.

/etc/init.d/LCDd
/etc/rc0.d/K60LCDd
/etc/rc1.d/K60LCDd
/etc/rc2.d/S60LCDd
/etc/rc3.d/S60LCDd
/etc/rc4.d/S60LCDd
/etc/rc5.d/S60LCDd
/etc/rc6.d/K60LCDd

/etc/init.d/mythtv-backend
/etc/rc0.d/K24mythtv-backend
/etc/rc1.d/K24mythtv-backend
/etc/rc2.d/S24mythtv-backend
/etc/rc3.d/S24mythtv-backend
/etc/rc4.d/S24mythtv-backend
/etc/rc5.d/S24mythtv-backend
/etc/rc6.d/K24mythtv-backend


How do I go about changing the load order of the mythtv-backend script and the LCDd script to test this theory?

Many thanks.

---

### Post by banewman on 2008-02-29
These files are in /etc/init.d with a link to the appropriate runlevel - the default in ubuntu is runlevel 2.
The links start with K (for kill) and S (for start), then a number, then the prog name.
If you type in a terminal -
sudo nautilus /etc/rc2.d
you can rename the relevant progs - the higher the number the later it will start.
:)

---

### Post by MrCaptainC on 2008-02-29
> **BigBadOwl said:**
> Hi there

I'm running LCDd which uses the start script /etc/init.d/LCDd which was installed as part of the LCDproc Ubuntu package. I'm also running mythlcdserver which is installed with the MythTV Ubuntu package and is started indirectly by the /etc/init.d/mythtv-backend startup script.

The problem is that the LCD does not display the output from MythTV unless I exit Mythfrontend, kill mythlcdserver and then restart mythfrontend (which automatically restarts mythlcdserver). I have to kill mythlcdserver, just restarting mythfrontend is not enough.

It seems to me that the mythlcdserver is starting before LCDd startup script has run.

How do I go about changing the load order of the mythtv-backend script and the LCDd script to test this theory?

Many thanks.
I think that the load order is determined by the S## or K## values in the rc.d directory for your run level.  So if a link was S10script1 it would run before S20script2

So if you want to get myth running after LCD then ensure that the symbolic link has a number less than the link for myth

I could of course be completly wrong but it may be worth a try.

Hope this helps,
Chris

Edit: banewman beat me to it :)

---

### Post by Yellow Pasque on 2008-02-29
Look in the appropriate run-level directory. In this case:
```
cd /etc/rc5.d
ls -l
```

Wow, that's what happens when I start a post, take the trash out, then come back and finish the post :)

---

### Post by BigBadOwl on 2008-02-29
I'm not sure if this is the correct way to fix this, but I solved it by doing the following

mv /etc/rc2.d/S60LCDd /etc/rc2.d/S23LCDd
mv /etc/rc3.d/S60LCDd /etc/rc3.d/S23LCDd
mv /etc/rc4.d/S60LCDd /etc/rc4.d/S23LCDd
mv /etc/rc5.d/S60LCDd /etc/rc5.d/S23LCDd

which moves the startup symlink to load before the mythtv symlink.

I can't imagine how a complete novice would solve this problem... it really does raise the entry level for Ubuntu adopters trying to move away from Windows or Mac

---

### Post by banewman on 2008-02-29
So happy we could help get it working for you :)
Can you mark the post as solved pls so others can find solutions :)

---

