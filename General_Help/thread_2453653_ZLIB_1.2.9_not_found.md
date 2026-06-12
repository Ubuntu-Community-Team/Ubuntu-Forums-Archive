---
title: "ZLIB_1.2.9 not found"
date: 2020-11-14
forum: General Help
---

### Post by col48 on 2020-11-14
I've just downloaded and installed the purebasic program language (from [www.purebasic.com](www.purebasic.com) - the paid-for version) into my 16.04 system.

But on trying to launch purebasic in Terminal, I get this error:

```
purebasic: /lib/x86_64-linux-gnu/libz.so.1: version `ZLIB_1.2.9' not found (required by purebasic)
```

In that folder, owned by root, there is libz.so.1 and libz.1.2.8 and the first is just a link to the second. There is no libz.1.2.9

**How should I fix this?**

In two or three places (incl a thread on this forum) there is a suggestion along the lines of
move (surely this should be copy?) libz.so.1 to the program folder - in this case, .../purebasic/compilers  (which is in the $PATH) - and then
ln -sf libz.so.1
but there must be more to it than this, since libz.1.2.9 does not exist anywhere on my system.  I think messing with the libz on root might mess up my system, and I am not expert enough to deal with that.

---

### Post by dinkidonk on 2020-11-14
This is a common issue when downloading pre-build software. The software is most likely build on Ubuntu 18.04, on 20.04 the version of zlib is 1.2.11 - so you will need to run the download on 18.04.

---

### Post by col48 on 2020-11-14
Thanks dinkidonk.

Unfortunately I do not have access to 18.04.

I do have access to a separate 20.04 machine.  If I copy libz_1.2.11 from there on to my 16.04 box, would it be backwards compatible?  If so, can I ring-fence it to the purebasic environment so that it does not trip anything else up?

If so, how?

Would putting it into the purebasic/compilers folder with an accompanying lib.so.1 link do the trick?

---

### Post by dinkidonk on 2020-11-14
Most likely libz_1.2.[9|11] links to some other shared object which does not exist on 16.04. And even if you get the zlib sorted, the downloaded software is probably linked to other SO's not available anywhere else than 18.04. I'm not familiar with purebasic, but if you've bought a license to the software, you should contact the vendor and ask their support what to do.

---

### Post by col48 on 2020-11-14
Thanks - I'll do that.

EDIT:
I've raised it with purebasic support but I don't expect a reply for a few days (it is currently the weekend, and in any case the Covid pandemic may have affected working hours in France/Germany)

There is a thread on the purebasic forum which raised this issue quite a while ago, but it looks as if this was a "we are working on this" matter which has not yet been resolved.  I can't see it being a high priority because later versions of Ubuntu have a later version of libz (1.2.11 is currently the latest and is the one recommended on the software website) so for most new users the problem will not be present. I imagine that purebasic 5.72 requesting 1.2.9 does *not* mean it won't work with 1.2.11!

My workaround pending advice from purebasic is to download purebasic 5.70, which does fire up its IDE - although (being well past bedtime) I haven't tried writing even "Hello World" yet!

Not marked as SOLVED because this is a workaround, not really a solution.

---

### Post by dinkidonk on 2020-11-15
If you do not want to update your system, you could run 18.04 or 20.04 as a virtual machine and use the software in the VM. That is probably the best and fastest sollution to the problem.

---

### Post by col48 on 2020-11-15
That's true, dinkidonk.

Purebasic is not just available for Ubuntu but Linux in general as well as Mac and Windows, so it will be a measure of the small team at purebasic to see if they come up with the same idea.  I doubt if the issue is more than an unplanned side effect of building the software at a particular moment.

---

