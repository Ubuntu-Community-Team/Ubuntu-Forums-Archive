---
title: "Xubuntu, sources.list, and 12.04 Security Updates Until 2017?"
date: 2014-02-19
forum: General Help
---

### Post by BuntuSeriously on 2014-02-19
Just had a quick question for the community; as I seem to be getting mixed information concerning Xubuntu's security updates timeline.

As I have been given to understand, "updates" will be available for 12.04 until April 2015.  Frustratingly, I've not found a resource which mentions just *which* updates are being referred to here (recommended? backports?? unsupported???).

Digging deeper to add a bit more confusion, sources.list indicates that the distro is regularly taking its security updates from security.ubuntu.com as undifferentiated from Precise; and, ergo, should be receiving all the same updates until Precise is no longer covered (April 201_7_).  From sources.list:
```

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

```
Now, unless I'm missing something crucial, it would seem as though sources.list infers we'll be getting full _*security*_ updates for Xubuntu 12.04 until Precise is cut off (April 2017).

If not, why? We all seem to be taking these updates through the main Ubuntu pipe without any particular qualification...


Thanks again --

---

### Post by deadflowr on 2014-02-19
The base of Ubuntu(things like the kernel and xorg packages) will be getting updates until 2017.

But the stuff for the xubuntu-desktop, will only be getting updates until 2015.

So security would be a mixed bag if you kept running it beyond 2015.

Make sense?

---

### Post by BuntuSeriously on 2014-02-19
Makes sense.

I guess the Xubuntu team simply closes off their contribution to the Precise collection April next.

Want to stick with 12.04 as long as I can; but this might just cement an upgrade to the next LTS again at that point...

{sigh}

Thanks, and have a great day ;)

---

### Post by grahammechanical on 2014-02-19
Just to muddy the waters a little bit. Ubuntu 12.04 itself will not be getting much more than security updates after 14.04 LTS is released. Ubuntu 12.04 has received 4 of what are called point releases over the last two years, at six monthly intervals. This has brought the hardware enablement stack up to date. So, the latest 12.04 is 12.04.4. Attention is switched to bringing out point releases of 14.04 LTS.

---

### Post by deadflowr on 2014-02-19
Yes.
A small difference, but a difference none the less.
(A few security updates versus no security updates for the desktop packages)

On a different note, I did notice the LTS hardware stack enablement wiki page was updated recently
to reflect how the point release hardware stack will be handled.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

So come August 12.04 will drop from having to support 4 hardware stacks to just 2.
(The original stack, which comes with 12.04, 12.04.1, and the new stack built from 14.04, thus dropping the quantal,raring,and saucy stacks)

Interesting stuff.

---

