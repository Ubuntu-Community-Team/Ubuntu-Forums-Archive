---
title: "gaim 1.3.0"
date: 2005-05-16
forum: General Help
---

### Post by SpEcIeS on 2005-05-16
Just a a question. Ubuntu comes with gaim 1.1.4, so why not 1.3.0? I am currently building 1.3.0, but I am curious as to why they chose 1.1.4. Will 1.3.0 be with the next version?


Thanks  :smile:

---

### Post by bored2k on 2005-05-16
Gaim 1.3 was released 6 days ago. Ubuntu has a "couple" more days than that. It can't have what hasn't been done ;).

Next version will include the latest version at the moment, wether its 1.3.1 or 7.5 :D

---

### Post by SpEcIeS on 2005-05-16
[QUOTE=bored2k]Gaim 1.3 was released 6 days ago. Ubuntu has a "couple" more days than that. It can't have what hasn't been done ;).

Next version will include the latest version at the moment, wether its 1.3.1 or 7.5 :D[/QUOTE]
Hehe...  :smile: I guess it pays to read everything.  :) I thought it had been out for a while; how silly of me.  Thanks for the quick reply, and hopefully the next release will be 7.5.  ;-)

---

### Post by bored2k on 2005-05-16
[QUOTE=SpEcIeS]Hehe...  :smile: I guess it pays to read everything.  :) I thought it had been out for a while; how silly of me.  Thanks for the quick reply, and hopefully the next release will be 7.5.  ;-)[/QUOTE]
 LoL . I didn't even know it had been released btw so thanks for the info, just installed the .autopackage ;).

---

### Post by SpEcIeS on 2005-05-16
[QUOTE=bored2k]LoL . I didn't even know it had been released btw so thanks for the info, just installed the .autopackage ;).[/QUOTE]
Autopackage, does that work? I have been compiling gaim 1.3.0 and it ends up being 18MB <???> Kind of big.  ](*,) I wonder why? This is the configure line that I am using:

**./configure --prefix=/usr --enable-debug=no --target=i686**

Perhaps I will download the autopackage instead and give it a try. :) Thanks :)

---

### Post by bored2k on 2005-05-16
[QUOTE=SpEcIeS]Autopackage, does that work? I have been compiling gaim 1.3.0 and it ends up being 18MB <???> Kind of big.  ](*,) I wonder why? This is the configure line that I am using:

**./configure --prefix=/usr --enable-debug=no --target=i686**

Perhaps I will download the autopackage instead and give it a try. :) Thanks :)[/QUOTE]
 Yes it works. I dislike ./configure, I'm a spoiled debian boy :D. You don't even need to install as root, you just ./file.autopackage and when asked for root password tell it "no password" :D. It's painless !
[center][[IMG]http://img233.echo.cx/img233/3021/screenshot19lj.th.png[/IMG]](http://img233.echo.cx/my.php?image=screenshot19lj.png)[/center]
edited image]

---

### Post by SpEcIeS on 2005-05-17
Looks good, but I do not like installing software in my home directory. Is there a way to use the root password in Ubuntu, besides sudo, which did not work? Well, maybe I did not do something right. :)

Regarding my compiled version, is it possible that all of the features of gaim are built into the application? Maybe that is why it is so darn big.  :roll: Hopefully someone has some insight on this one; I am stuck.  :confused:

---

### Post by bored2k on 2005-05-17
[QUOTE=SpEcIeS]Looks good, but I do not like installing software in my home directory. Is there a way to use the root password in Ubuntu, besides sudo, which did not work? Well, maybe I did not do something right. :)

Regarding my compiled version, is it possible that all of the features of gaim are built into the application? Maybe that is why it is so darn big.  :roll: Hopefully someone has some insight on this one; I am stuck.  :confused:[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

Why do you still want to compile it ? that's what autopackage is there for.
Yes you can set a passwd, read above.

---

### Post by SpEcIeS on 2005-05-17
[QUOTE=bored2k][http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

Why do you still want to compile it ? that's what autopackage is there for.
Yes you can set a passwd, read above.[/QUOTE]
Probably because I am stubborn. :D Thanks for the link to the Root I have wondered, off and on, how this was done. You are a big help and it is greatly appreciated. :)

---

### Post by bored2k on 2005-05-17
[QUOTE=SpEcIeS]Probably because I am stubborn. :D Thanks for the link to the Root I have wondered, off and on, how this was done. You are a big help and it is greatly appreciated. :)[/QUOTE]
I am a hermit.
This entertains me. I don't know who's getting more out of this ;)

---

### Post by moon2js on 2005-05-17
Anything in the newer gaims worth the trouble of installing them before Breezy comes along? My only issues with gaim right now really are file transfers and crashing due to some kind of glitch/bugginess with SCIM/UTF support.

File transfers don't work although I find that is often a network problem as often I can't even do file transfer with MSN Messenger on Windows. Is it possibly an issue of port forwarding? I've had endless problems with file transfer and p2p and I'm beginning to suspect it might have something to do with my ISP.

Also, I tend to have weird glitches using SCIM. Gaim will suddenly quit without warning if I go to change my "friendly" name and I press any arrow button to try to deselect what my current "friendly" name is (so I can just edit and not retype it complete). I also find it suddenly shuts down the program sometimes if I switch to a different input method while chatting to a friend, which is quite annoying.

---

### Post by mhearn on 2005-05-20
[QUOTE=SpEcIeS]Looks good, but I do not like installing software in my home directory. Is there a way to use the root password in Ubuntu, besides sudo, which did not work? Well, maybe I did not do something right. :)

Regarding my compiled version, is it possible that all of the features of gaim are built into the application? Maybe that is why it is so darn big.  :roll: Hopefully someone has some insight on this one; I am stuck.  :confused:[/QUOTE]
 sudo support is going to be added to autopackage in the next week or so, most likely, when we release 1.0.2 - we just have a few random problems to figure out with Slackware deadlocks ....

---

### Post by SpEcIeS on 2005-05-20
[QUOTE=mhearn]sudo support is going to be added to autopackage in the next week or so, most likely, when we release 1.0.2 - we just have a few random problems to figure out with Slackware deadlocks ....[/QUOTE]
That sounds great. :) Another wonderful improvement for the linux world. :D

---

### Post by rykel on 2005-05-31
Hi there,

You CAN enable a root account in Ubuntu:

sudo passwd root

To disable it:

sudo passwd -l root

Hope tat helps!

btw, if you are keen to join the autopackage user community, let me know. just message me using ur newly installed Gaim 1.3.0.     :grin: 


Regards,

Rykel
ICQ: 22768140
MSN: lifestylediamond

I love autopackage!

---

### Post by SpEcIeS on 2005-05-31
[QUOTE=rykel]Hi there,

You CAN enable a root account in Ubuntu:

sudo passwd root

To disable it:

sudo passwd -l root

Hope tat helps!

btw, if you are keen to join the autopackage user community, let me know. just message me using ur newly installed Gaim 1.3.0.     :grin: 


Regards,

Rykel
ICQ: 22768140
MSN: lifestylediamond

I love autopackage![/QUOTE]
Thanks for the tip. :) This messageboard is very helpful, I found that one a while ago, and have yet to implement it. As far as gaim 1.3.0 is concerned, I downloaded it via synaptic, apt, using the Backports repositoriy. It works really well.  :grin:

Thanks again. :)

---

