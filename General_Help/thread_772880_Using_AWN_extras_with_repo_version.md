---
title: "Using AWN extras with repo version ?"
date: 2008-04-28
forum: General Help
---

### Post by abelthorne on 2008-04-28
Hello,
I've installed Avant Window Navigator in Hardy from the Universe repository. The awn-extras package is not available in it.

I know of the 3rd-party "testing" repositories that include the awn packages but I'd like to stick with the official repo version.

I've tried to compile awn-extras from source but get a compilation error. From what I've understood, I need to compile AWN itself first (some header files are missing).

Is there a way to compile/install only awn-extras so that it works with the 0.2.1 version that is in the Hardy Universe repository ?

---

### Post by azhtar on 2008-04-28
Check on awn site, they have repos on PPA for hardy

---

### Post by abelthorne on 2008-04-28
> **azhtar said:**
> Check on awn site, they have repos on PPA for hardy
I know, but as I said I'd like not to use them and stick with the official repository (Hardy Universe).
My goal is to build/install the extras and use them with this version, if possible.

---

### Post by moonbeam on 2008-04-28
> **abelthorne said:**
> Hello,
I've installed Avant Window Navigator in Hardy from the Universe repository. The awn-extras package is not available in it.

I know of the 3rd-party "testing" repositories that include the awn packages but I'd like to stick with the official repo version.

I've tried to compile awn-extras from source but get a compilation error. From what I've understood, I need to compile AWN itself first (some header files are missing).

Is there a way to compile/install only awn-extras so that it works with the 0.2.1 version that is in the Hardy Universe repository ?

If you install the various official awn dev packages in hardy and install all the additional deps needed for an awn extras build then you should be able to build from awn-extras v 0.2.1 source.  Do not try to build from later source as we broke compatibility after 0.2.1.

[https://code.launchpad.net/~awn-extras/awn-extras/0.2.1](https://code.launchpad.net/~awn-extras/awn-extras/0.2.1)

[http://wiki.awn-project.org/Awn_Extras:Installation#Building_From_Source](http://wiki.awn-project.org/Awn_Extras:Installation#Building_From_Source)

Not that 0.2.1 tends to have a lot more bugs than more current versions.

---

### Post by abelthorne on 2008-04-28
> **moonbeam said:**
> If you install the various official awn dev packages in hardy and install all the additional deps needed for an awn extras build then you should be able to build from awn-extras v 0.2.1 source.  Do not try to build from later source as we broke compatibility after 0.2.1.
I tried to compile awn-extras only and get an error with make:
```
aff-settings.h:29:38: error: libawn/awn-config-client.h: No such file or directory
```
It seems that libawn/awn-config-client.h is there only when compiling awn first (or I missed some point somewhere).

---

### Post by moonbeam on 2008-04-28
> **abelthorne said:**
> I tried to compile awn-extras only and get an error with make:
```
aff-settings.h:29:38: error: libawn/awn-config-client.h: No such file or directory
```
It seems that libawn/awn-config-client.h is there only when compiling awn first (or I missed some point somewhere).

That would indicate that you are attempting to build a post 0.2.1 version of awn-extras.  You need to download the 0.2.1 source if you want to go this route.

---

### Post by abelthorne on 2008-04-29
Whoops. You're right. I downloaded the latest version and didn't see the previous ones. I was blind on this case.

Thanks a lot. :)

---

