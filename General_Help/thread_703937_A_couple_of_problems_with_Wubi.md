---
title: "A couple of problems with Wubi"
date: 2008-02-21
forum: General Help
---

### Post by 5nak3 on 2008-02-21
Hello, just finished getting Wubi installed and had a little play around but now i have a couple of questions which i tried finding answers to but to no avail so i was hoping someone would help me.

1) Almost immediately after logging in i get a message saying there are new updates available, i read about the upgrade from 7.04-7.10 is dangerous via wubi and as a newbie i do not want to experiemnet with that. However when i checked the update manager i noticed many of the updates were actually for various bits of software e.g. open office, firefox etc... I just want to know can i use this update manager to update those programs safely of will i corrupt the wubi install if i do update?

2) I downloaded and installed opera as i cannot get used to firefox web browser (lack of mouse gestures), i just wanted to make sure that it is actually safe to install programs within ubuntu via wubi.

3) Finally for now i guess, is there any type of antivirus / firewall software i can use with wubi just for that extra peace of mind.

Hopefully, someone will be willing to help. Many thanks in advance

---

### Post by ago on 2008-02-22
> **5nak3 said:**
> 
1) Almost immediately after logging in i get a message saying there are new updates available, i read about the upgrade from 7.04-7.10 is dangerous via wubi and as a newbie i do not want to experiemnet with that. However when i checked the update manager i noticed many of the updates were actually for various bits of software e.g. open office, firefox etc... I just want to know can i use this update manager to update those programs safely of will i corrupt the wubi install if i do update?
Yes all updates are fines, just do not click on upgrading to 7.10.

> 2) I downloaded and installed opera as i cannot get used to firefox web browser (lack of mouse gestures), i just wanted to make sure that it is actually safe to install programs within ubuntu via wubi.
Yes you can install what you want. Of course if you use binary blobs, nobody can guarantee what is in there.

> 3) Finally for now i guess, is there any type of antivirus / firewall software i can use with wubi just for that extra peace of mind.
There are no known virus in the wild for Linux, the available antiviruses are mostly to protect windows machines by stopping files that have win32 viruses. The firewall is built into the kernel and by default all ports are closed. If you need to open ports you may use a graphical firewall configurator. For anything see in add/remove programs

---

### Post by 5nak3 on 2008-02-22
Thank you for replying, I just have a few questions more to clarify things if you would not mind.

Firstly, i had a look at all the files in the update manager but i couldn't find the check option relating to the 7.10 upgrade. Could you just confirm where the upgrade from 7.04 to 7.10 option is, so i can avoid it?

And also when you said "if you use binary blobs, nobody can guarantee what is in there" i take it you mean the use of open source binaries?

Ok i believe that should sort out all my initial questions. On a completely unrelated note  I have a a 10 or so year old pc somewhere with a 8gb hard drive do you think that it would be able to run a full linux (more specifically ubuntu) setup? If it could i could always learn the ropes via that.

Many thanks

---

### Post by ago on 2008-02-22
> **5nak3 said:**
> Firstly, i had a look at all the files in the update manager but i couldn't find the check option relating to the 7.10 upgrade. Could you just confirm where the upgrade from 7.04 to 7.10 option is, so i can avoid it?
It will appear as a separate button on the top of the update manager. It's not a checkbox.

> And also when you said "if you use binary blobs, nobody can guarantee what is in there" i take it you mean the use of open source binaries?
Packages (even binaries) within ubuntu repositories are fine because they are signed and everyone can check what's in there, hence it is extremely difficult for someone to tamper with them. For other binaries (in whatever OS) you have to trust whoever wrote the package, and the website hosting it, and that nobody spoofed such website, and that nobody changed the packages on the way when you were downloading them... 

> Ok i believe that should sort out all my initial questions. On a completely unrelated note  I have a a 10 or so year old pc somewhere with a 8gb hard drive do you think that it would be able to run a full linux (more specifically ubuntu) setup? If it could i could always learn the ropes via that.

Yes but I would not put Gnome or KDE there. You can try Xubuntu, but even that might be to heavy. I found IceWM to be ideal on low spec machines, that requires installing from the alternate ISO without installing any desktop package, then manually installing icewm. Note that the Ubuntu graphical installer requires 256MB of memory, otherwise you have to use the ALTERNATE ISO. If you have less than 128MB you should consider PuppyLinux or DSL. See also [http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by 5nak3 on 2008-02-22
Hmm, yeah i figured that my old system would probably not run ubuntu but i might look into some lighter distrobution.

Thank you so much for the help in getting me on my feet so to speak.
So far i am very impressed with what i have seen, i look forward to future releases.

---

### Post by 5nak3 on 2008-02-22
ok big problem for me, mycomputer seemed to just crash and i had to do a hard reset now i get the hal.dll corrupt or missing error. currently i am booting from my windows cd running the recovery console with chkdsk /r.

could someone give advice on what to do if this doesn't work or what happens after the chkdsk finishes?

please i'm in need of some serious help.

currently seems to be stuck on 51 percent. help me.

----edit----
well i managed to fix the problem with the chkdsk /r windows booted again :) 
so this throws a new problem that i need an answer to, will wubi still work? and more importantly, if the pc crashes or if things go wrong and there is a power cut. is this type of behaviour the norm?

---

### Post by ago on 2008-02-22
When you have power outages you can always risk a filesystem corruption whether you use wubi or not.

---

### Post by 5nak3 on 2008-02-22
well things seem to be back to the way they should be :D i'm a happy bunny again lol, the only thing i am not too keen on to be fair is being a newbie.
The ubuntu environment is user friendly but just learning how to do some basic things is a pain, but then again i guess we all have to start from somewhere.

---

