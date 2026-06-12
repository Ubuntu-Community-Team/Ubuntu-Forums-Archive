---
title: "Problem with Read only system"
date: 2012-11-19
forum: General Help
---

### Post by holatu on 2012-11-19
Hi!

I recently install Ubuntu x64 12.10 on my laptop.
Its a Sony VAIO VPCEG (4gb Ram, Intel HD graphics, 500gb HD)

The problem is that apparently my hard drive is damaged, so, after a few seconds of starting the system automatically switches to "Read Only System"

Already tried to repair the file system with "fsck-As"

Already also modified the file
/ etc / fstab
so that the partition / dev/sda1 is:
............ (rw, errors = continue)

There is a way to disable the option in ubuntu to mount the file system as "read only" when it encounters errors?

I know that there is the possibility of loss of information, but I can not buy another hard drive at this time ....

(sorry for my bad english, it's not my native language)

---

### Post by finny388 on 2012-11-19
Are you dual booting with Windows?

If so, does Windows have the same problem?

Is the hard drive an SSD or mechanical? (or what size is it?)

If it is mechanical you can try spinrite.

But if the hard drive is going to die your only choice ultimately is to get a new one. If possible, you might want to leave it alone until you can save up enough money.

As far as assessing that, hopefully someone else can offer you some good diagnostic techniques.

You are right to use fstab to tell ubuntu how to mount it. please post your fstab file.

---

### Post by rnerwein on 2012-11-20
> **holatu said:**
> Hi!

I recently install Ubuntu x64 12.10 on my laptop.
Its a Sony VAIO VPCEG (4gb Ram, Intel HD graphics, 500gb HD)

The problem is that apparently my hard drive is damaged, so, after a few seconds of starting the system automatically switches to "Read Only System"

Already tried to repair the file system with "fsck-As"

Already also modified the file
/ etc / fstab
so that the partition / dev/sda1 is:
............ (rw, errors = continue)

There is a way to disable the option in ubuntu to mount the file system as "read only" when it encounters errors?

I know that there is the possibility of loss of information, but I can not buy another hard drive at this time ....

(sorry for my bad english, it's not my native language)

hello
run fsck by single partitions e.g. --> fsck -r /dev/sda1 .... fsck -r /dev/sdax
this will cause fsck to ask you for confirmations and you can see whats going on.
if you type "y" have a look later in /lost+found if there are some files ( it's mostly possible to recover the files wich are in there).
good luck

---

### Post by holatu on 2012-11-20
Hi :)

thank you for your answers...

I already have done all of the fsck stuff.. When ubuntu starts, it went well... and after a minutes later it become again as "read-only system" so i can't run the terminal even as root, because this..

Here is my fstab log:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e0a0ef64-a216-482d-aded-64e91ae99fd7 /               ext4    errors=continue 0       1
# swap was on /dev/sda5 during installation
UUID=a16906bc-b98f-48f0-a11d-e7f8aa13c82c none            swap    sw              0       0



Again, i have done lots of stuff including repairing the file system... The main problem is with the s.m.a.r.t. i have many sectors damaged... i want to ignore them so my system doesn't became "read-only"

suggestions???

---

### Post by holatu on 2012-11-20
> **finny388 said:**
> Are you dual booting with Windows?

If so, does Windows have the same problem?

Is the hard drive an SSD or mechanical? (or what size is it?)

If it is mechanical you can try spinrite.

But if the hard drive is going to die your only choice ultimately is to get a new one. If possible, you might want to leave it alone until you can save up enough money.

As far as assessing that, hopefully someone else can offer you some good diagnostic techniques.

You are right to use fstab to tell ubuntu how to mount it. please post your fstab file.


I don't have windows, just formated..
When i try to install windows it stuck, so ubuntu is my only available option..

my hard drive is an small one..

---

### Post by dannyboy79 on 2012-11-20
does this work?
```
sudo mount -n -o remount /
```

---

### Post by holatu on 2012-11-20
> **dannyboy79 said:**
> does this work?
```
sudo mount -n -o remount /
```

Yes, but after a while, the system became "read-only" again.. and it won't work because of this... i have to reboot and start on live cd...

i have try everything... I just want a way to stop the "read-only system"  procedure..
is there a way to change that???

I know my hard drive has errors, as i see in the s.m.a.r.t. analysis...

i want to disable the option that turns my  system in "read-only" :roll:
suggestions??

---

### Post by itzsujoy on 2012-11-20
Hi,
I already have installed Java and JRE.
The "java -version" command showing the following output:
"java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode)"
But when I test in Firefox for Java in [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)  its showing :
Something is wrong. Java is not working. 
I also typed "about:plugins" in Firefox url bar. But I did not find any Java plugin there.
Please help me.

---

### Post by dannyboy79 on 2012-11-20
> **itzsujoy said:**
> Hi,
I already have installed Java and JRE.
The "java -version" command showing the following output:
"java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode)"
But when I test in Firefox for Java in [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)  its showing :
Something is wrong. Java is not working. 
I also typed "about:plugins" in Firefox url bar. But I did not find any Java plugin there.
Please help me. This is a thread about something totally different then what you're asking about. Please go start your own thread in either Absolute Beginner or General Help.

---

### Post by dannyboy79 on 2012-11-20
> **holatu said:**
> Yes, but after a while, the system became "read-only" again.. and it won't work because of this... i have to reboot and start on live cd...

i have try everything... I just want a way to stop the "read-only system"  procedure..
is there a way to change that???

I know my hard drive has errors, as i see in the s.m.a.r.t. analysis...

i want to disable the option that turns my  system in "read-only" :roll:
suggestions??can you try added the following option to your / fstab line?
errors=continue,barrier=0
I know you already have errors=continue but add the barrier one as well. 

I don't know what to change to get it so that linux stops making your drive read only, it's doing it on purpose to prevent data loss. It's doing this for a reason and I would just give up on the drive and get a new one. 

PS I have a 1TB drive with 329 bad sectors and I am currrently using grsync to get everything off it before I throw it out.

---

### Post by holatu on 2012-11-20
> **dannyboy79 said:**
> can you try added the following option to your / fstab line?
errors=continue,barrier=0
I know you already have errors=continue but add the barrier one as well. 

I don't know what to change to get it so that linux stops making your drive read only, it's doing it on purpose to prevent data loss. It's doing this for a reason and I would just give up on the drive and get a new one. 

PS I have a 1TB drive with 329 bad sectors and I am currrently using grsync to get everything off it before I throw it out.

I did that already just few minutes ago...
But the system became "read-only" again after a while :(

---

### Post by holatu on 2012-11-21
Is there any options that could be disabled in order to stop ubuntu doning that to my system??

There has to be at least one app, any file that i could modified..

Please.. I have not money at all xD
And i need to do some homework and research... 
I don't care about the loss of information (i constantly back up in my external drive...) i need my system working and stop doing that "read-only" thing.

Please, save me :cry:

---

### Post by dannyboy79 on 2012-11-21
Sorry, I don't know how to prevent it from happening. It has to be a setting but I don't know what to change.

As a side note, you could always run a live cd or usb stick and do your work and just save it to your external hard drive.

---

### Post by Wlsie on 2012-11-21
Hi I have similar problem. I have 32-bit 12.10. Recently completed the updates from update manager and the filesystem is going into read only. When i do fsck-As i get EOFError: EOF read where object expected. What is the problem?

---

### Post by mayagrafix on 2012-11-21
try booting from a live Ubuntu CD. See if you can avoid read only that way.

---

### Post by dannyboy79 on 2012-11-21
most likely your hard drive is dieing. check /var/log/syslog, /var/log/kern.log, and dmesg output for drive write errors. Boot to a live cd or live usb stick and check the drives health.

---

