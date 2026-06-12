---
title: "Why is that everytime i do a update something messes up?"
date: 2008-07-06
forum: General Help
---

### Post by nickdbliss on 2008-07-06
Everytime my system runs an update, something gets broken. To start with, i was using open driver for my ATI RS485. I could use DRI and desktop effects with a charm. Now i cant. I had to enable crappy buggy prop. drivers. Anyways, it run fine with it for a while but then i couldnt watch movies or videos. Only black screen with sound. Sigh!
Sound was good until yesterday and today i can listen to music from both headphones and laptop speakers (Analog Device AD1981).Not good. Moreover i cant use Shift+Del to permanently delete files. That also happened with the recent update.
One more problem is that when i have mouse pointer to open applications menu, i couldnt use Mute,Unmute, Vol up or vol down keys on my laptop.

So anyone who can explain it to me, are updates done to replace bugs or bring more? Time to fix them again. Peace

---

### Post by kerry_s on 2008-07-06
ubuntu has many versions, you didn't say which you was using.

ubuntu is built on debian unstable, so any updates you do are coming from unstable, after the release only security updates are used.

the thing with using unstable is you get the latest, but you get everything that comes from being untested.

---

### Post by ibutho on 2008-07-06
Maybe you should look at Debian Stable or Debian testing. I have found them to be generally more stable than Ubuntu although if you use Stable you won't be running newer versions of most packages.

---

### Post by ChameleonDave on 2008-07-06
> **nickdbliss said:**
> Everytime my system runs an update, something gets broken. 

That's terrible (though probably an exaggeration).

Try using the Mint updater.  It classifies update according to their level of safety.

I have it, but to be honest I just install everything.  I like the cutting edge, even if I bleed frequently.  ;-)

---

### Post by danwood76 on 2008-07-06
On my desktop I install all the proposed updates (the ones that are really unstable) to help with testing but my PC never breaks upon update.
Make sure you dont have this repo enabled for updates as it could cause issues with less well known hardware setups.

---

### Post by ChameleonDave on 2008-07-06
> **danwood76 said:**
> On my desktop I install all the proposed updates (the ones that are really unstable) to help with testing but my PC never breaks upon update.
Make sure you dont have this repo enabled for updates as it could cause issues with less well known hardware setups.

Yeah, I have all sorts of experimental stuff in extra repos, but nothing major ever screws up after updates, except one time that there was a kernel update that didn't let me start X.  Reinstalling from a Hardy CD instead of dist-upgrading from Gutsy fixed that.

---

### Post by nickdbliss on 2008-07-06
> **kerry_s said:**
> ubuntu has many versions, you didn't say which you was using.

ubuntu is built on debian unstable, so any updates you do are coming from unstable, after the release only security updates are used.

the thing with using unstable is you get the latest, but you get everything that comes from being untested.

I am using Ubuntu Hardy. Thanks for the explaination. Now i know why it happens.

---

### Post by nickdbliss on 2008-07-06
> **danwood76 said:**
> On my desktop I install all the proposed updates (the ones that are really unstable) to help with testing but my PC never breaks upon update.
Make sure you dont have this repo enabled for updates as it could cause issues with less well known hardware setups.

Thanks for the advice, I am going to disable it for sure.

Edit: I am having it already disabled. Gonna disable other stuff.

---

### Post by nickdbliss on 2008-07-06
Can anyone tell me if i can revert back to previous system files , u know the way my system was before updates?

---

### Post by danwood76 on 2008-07-06
Even though Ubuntu is built on unstable debian it is only regarded as such due to the software not being tried and tested. Stable Debian runs the 2.4.xx kernel (the full stable kernel) and so will not support all the latest hardware, although will be far more stable.
I have to say the Ubuntu for me is 100% stable (at least for me on my machines) although the new GVFS with hardy has a lot to be desired of it.

The only way to get back a previous version of your OS is to do backups and restore them.
There is a project about that gives a sort of Mac OS timemachine type system (flyback I think [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)) allowing you to revert back to a previous days OS if you mess up.
Obviously this needs to be installed at a working state before you can revert.

Personally when I get my system to a good working point I tar the entire system allowing me to restore a working system if I ever need it, I then do an incremental backup every now and then.

It might be that a kernel update has broken a few things on your system, in which case you can boot the old kernel at the grub prompt by pressing escape and choosing an older kernel (version -19 is the latest I think, try going earlier than that).

---

### Post by nickdbliss on 2008-07-06
> **danwood76 said:**
> Even though Ubuntu is built on unstable debian it is only regarded as such due to the software not being tried and tested. Stable Debian runs the 2.4.xx kernel (the full stable kernel) and so will not support all the latest hardware, although will be far more stable.
I have to say the Ubuntu for me is 100% stable (at least for me on my machines) although the new GVFS with hardy has a lot to be desired of it.

The only way to get back a previous version of your OS is to do backups and restore them.
There is a project about that gives a sort of Mac OS timemachine type system (flyback I think [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)) allowing you to revert back to a previous days OS if you mess up.
Obviously this needs to be installed at a working state before you can revert.

Personally when I get my system to a good working point I tar the entire system allowing me to restore a working system if I ever need it, I then do an incremental backup every now and then.

It might be that a kernel update has broken a few things on your system, in which case you can boot the old kernel at the grub prompt by pressing escape and choosing an older kernel (version -19 is the latest I think, try going earlier than that).

I will try that and will let you know.thanks

---

### Post by nickdbliss on 2008-07-07
That didnt help. Still having the problems. I think i ll reinstall the system. Oh that reminds of that crappy MS.

---

### Post by nickdbliss on 2008-07-10
Great!! now DNS server is gone. Do i need to remember IP addresses now? Ok someone give me the link to the solution page. Damn!

---

### Post by carcdrcdr on 2008-07-10
Ok where to start... DNS:
What does:
```
cat /etc/resolv.conf
```
give you?

Next... What do you mean "do an update"?  Are you using apt-get? Synaptic?  Aptitude?

I recommend if you you think hosed your packages:
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get -f install
```

Other then that Im not really sure what your problem is unless you provide more details such as: how you update your computer, and what the updates were.

hope some of that helps ;)

---

### Post by nickdbliss on 2008-07-10
> **carcdrcdr said:**
> Ok where to start... DNS:
What does:
```
cat /etc/resolv.conf
```
give you?

Next... What do you mean "do an update"?  Are you using apt-get? Synaptic?  Aptitude?

I recommend if you you think hosed your packages:
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get -f install
```

Other then that Im not really sure what your problem is unless you provide more details such as: how you update your computer, and what the updates were.

hope some of that helps ;)

Ok buddy all those sudo commands gave me this (although i  have tried them earlier):
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Except sudo apt-get update which just read the package list.

I am using apt-get to update or upgrade.

and resolve.conf file shows this:
nameserver 218.248.240.24
nameserver 218.248.240.135
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5071
#
### END INFO

I forgot to mention i amusing ethernet connection right now. DNS problem happens with wireless connection.

---

### Post by nickdbliss on 2008-07-10
And yeah thanks for the reply buddy.

---

### Post by nickdbliss on 2008-07-10
Thanks to everyone for replying. I am just formatting the hard disk and removing ubuntu. SO much crap and orphan files are there that it is making me crazy. Oh reminds me of xp days. Any how, peace!!

---

### Post by jimv on 2008-07-10
Interesting.  The last time I had something break due to an update was when I was running Hardy Alpha 5.

---

### Post by nickdbliss on 2008-07-10
lucky you buddy. I have reinstalled my system n everything is working fine now. wheww!!

---

