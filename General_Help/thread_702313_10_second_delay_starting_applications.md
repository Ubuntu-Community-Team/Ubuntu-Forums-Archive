---
title: "10 second delay starting applications"
date: 2008-02-20
forum: General Help
---

### Post by goskier on 2008-02-20
When I start windowed applications using the Ubuntu 7.10 desktop I get a 10 second delay before the window for the new app appears. It is not a problem forking new processes. e.g. in a terminal window, a command will run immediately. It is when a new windowed app is started. It doesn't matter whether I start from the shortcut launcher, or whether another application creates the new app (e.g. if I get RapidSVN to launch gedit to edit a file, then I get the delay).

Sometimes (rarely) the problem goes away and everything starts quickly, but that is quite rare. Usually the delay is there. It is always exactly 10 seconds, so it feels like some sort of timeout in some component somewhere.

The CPU usage and disk usage are tiny, so it's not some memory/CPU/disk hog.

I notice there was a post last year on the beginner forum about this very problem:
[http://ubuntuforums.org/showthread.php?t=422366](http://ubuntuforums.org/showthread.php?t=422366)
I didn't see any resolution to this and can find no other reference. But the problem is real.

Other developers in our group are running on the same hardware using Ubuntu 7.04 and earlier and they see no problem. I'm the only one who sees it and I run Ubuntu 7.10. 

Any ideas?
Thanks.

---

### Post by GuDoN on 2008-02-20
> running on the same hardware using Ubuntu 7.04 and earlier and they see no problem. I'm the only one who sees it and I run Ubuntu 7.10


Ubuntu 7.10 comes with Compiz out of the box.

Please could you check that you do not have any Window decorations on, go and check it out at the Administration Menu > Appearance. (Last Tab)  Make sure it is none.

Compiz is known to give problems sometimes. I highly doubt it might be that, but at the moment, thats the best advice I can give you mate.

Kind Regards.
GuDoN

---

### Post by goskier on 2008-02-20
Started Preferences+Appearance (with usual 10 second delay!). Visual Effects are set to none. So that's not it.

Thanks.

---

### Post by matigol on 2008-02-20
Which graphic card are you use ?

---

### Post by erginemr on 2008-02-20
Is there any peculiar text message output when you run a graphical application from the terminal, say gedit, totem, rhythmbox, etc?

---

### Post by goskier on 2008-02-20
It's an ATI Radeon running the fglrx driver in dual-screen mode.
There are no messages, just a delay, then the app starts normally.

Thanks.

---

### Post by spmckenney on 2008-03-03
goskier -

Check out:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/128521](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/128521)

I just added my hostname to the localhost line and the annoying delay was gone.

Hope this helps -
spmckenney

---

### Post by PreviousN on 2008-03-03
Just to rule out graphics drivers causing the problem, I suggest you try envy. 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And the deb:
[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu4_all.deb)

Envy will scan your hard ware and download the newest driver for your card, compile it, then rewrite your xorg. Then, if you want you can even enable desktop effects or not. After that, you'll be sure that its not a graphics issue. 

Also, you might try a memory test. 

And finally, the guy who suggested running a gui application from the terminal is right. It could give you infos. Try this:

open a terminal
type in "firefox" and then hit enter. Watch what happens.

---

### Post by erginemr on 2008-03-03
to **spmckenney **-> This is very promising. And is actually a trick used to speed up Ubuntu.

to **PreviousN **-> He already reported that he tried running apps from terminal with no feedback whatsoever.

He has posted his last message a week before. Personally, I don't think he will ever come back. I am afraid we have lost another Ubuntu user wannabe. :(

---

