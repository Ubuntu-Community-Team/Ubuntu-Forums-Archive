---
title: "Ubuntu Studio: what works with low latency and generic?"
date: 2007-05-23
forum: General Help
---

### Post by mjitkop on 2007-05-23
Just wondering with Ubuntu Studio: I understand the use of the low latency for audio editing but...

1/ if I use the low latency kernel, what will not work and would work with the generic kernel?

2/ if I use the generic kernel, is there anything that will not work and would only work with the low latency kernel?

---

### Post by blazercist on 2007-05-23
no no no you have it all wrong, the low latency kernel just means that cpu polling is more frequent.
You CPU sleeps between cycles, with a higher polling rate it just sleeps less often, this is better for apps that are time sensitive for instance, a Game Server or multimedia stuff live audio/video because it keeps it from flickering/stuttering thats all.  There is no negative affect save perhaps slightly higher cpu usage, not really noticable though.

---

### Post by mjitkop on 2007-05-24
Thank you very much for this explanation, blazercist! :D 

I haven't noticed any problems with my system with the low latency kernel so until I experience some issues, I will keep using it. This is good because this is the kernel by default.

I feel better knowing this now. :D

---

### Post by blazercist on 2007-05-24
I was contemplating compiling a low latency kernel on my regular feisty system, but I don't want to use a vanilla kernel I want the ubuntu one and I don't know how to recompile only to compile a fresh one so I hold off on it.

---

### Post by shen-an-doah on 2007-05-24
> **blazercist said:**
> I was contemplating compiling a low latency kernel on my regular feisty system, but I don't want to use a vanilla kernel I want the ubuntu one and I don't know how to recompile only to compile a fresh one so I hold off on it.

If you want the low latency kernel, you can just install it from the Ubuntu Studio repositories. My blog has info on how to "upgrade" from Feisty to Studio (basically adding the Studio repos and installing the studio components). Link's in my sig.

---

### Post by blazercist on 2007-05-24
shen chek your pms/

---

### Post by shen-an-doah on 2007-05-24
> **blazercist said:**
> shen chek your pms/

I did and then my internet died :D

---

### Post by cino on 2007-07-17
I have a similar problem if anyone still reads this thread.
I have installed Studio and can only run with generic kernel, not the low latency...
If I disable my restricted graphics driver (I think this is where all my problems are coming from) and try restarting in low lat., are my problems solved?

I will try this myself post for my own enjoyment but anyone, is this prob why low latency kernel is not working?

Also, one of the errors I was getting was that under the low latency kernel I was being told that timidity was not installed, ergh.

The generic kernel allows ardour to work ok with Jack, and I just rediscovered PD!

But I have so much more reading to do... 
 why doesnt my low latency kernel work?

---

### Post by cino on 2007-07-17
Disabled Restricted Driver and now when running restricted driver manager;

You need to install the package
linux-restricted-modules-2.6.20-16-lowlatency
for this program to work.

This is after I have restarted with the low latency kernel...

---

### Post by bomanizer on 2007-12-02
Hello all (if anybody is still reading this thread)! I installed the lowlatency kernel on my 7.10 and I saw a BIG performance boost on gui-stuff, like: video playback with compiz, etc. Anyway, all is well but suspend and hibernate are broken. I have the generic kernel, of course, but running low latency is nicer... any ideas on what might be the trick here?

-Cheers

---

### Post by logos34 on 2007-12-02
> **bomanizer said:**
> Hello all (if anybody is still reading this thread)! I installed the lowlatency kernel on my 7.10 and I saw a BIG performance boost on gui-stuff, like: video playback with compiz, etc. Anyway, all is well but suspend and hibernate are broken. I have the generic kernel, of course, but running low latency is nicer... any ideas on what might be the trick here?

-Cheers

Same problem here.  No suspend or hibernate.  I'd be satisfied if either worked.

As a result I'm running 64-bit generic with basically the ubuntustudio-desktop (full audio suite minus the graphics and video pkgs).  I like to call it my 'Ubuntu Pseudio' setup.  At least it resumes from hibernate.  

The -rt kernel gives a definite speed boost...apps open a lot quicker and overall things are snappier.  But I gotta have some power mgmt features working...and it seems there was also a bug related to the desktop panel running on the -rt (but who knows)...So after three install attempts to get things working properly I finally decided to go with ubuntu 7.10 x64 and tack on all the studio pkgs and themes.  So basically I have a nominal studio setup minus the low-latency kernel.

If some of the studio folks could direct me and others with pwr mgmt issues to a workaround I'd appreciate it. Cause I've tried uswusp, hibernate pkgs to no avail, and I've tried seemingly every possible configuration of /etc/default/acpi-support...also fiddled with suspend in Bios (S1, S3, S1+S3 etc etc).

---

