---
title: "WINE or VMWare"
date: 2007-02-24
forum: General Help
---

### Post by dyrer on 2007-02-24
Hello
I wonder what is better to run Windows Programs and hardware as well WINE or VMWare?

---

### Post by altaaa on 2007-02-24
That totally depends on what you want to do...

---

### Post by TheKid965 on 2007-02-24
I would agree with that assessment.  It all depends on what you want to do:

If you only run the occassional Windows program, Wine is a viable solution.  If the "occassional Windows program" is something ilke MS Office or Photoshop, it's better to get Crossover (a commercial version of Wine optimized for these programs).  Wine will probably run them as-is, but Crossover provides extra speed and stability in my experience, particularly with later versions.  (The frontend is also a boon to newer users who need some hand-holding getting things set up.)

If gaming is what you want to do, Wine may not be enough; try Cedega instead, which is optimized for DirectX 9.  Unfortunately, it's pay-to-play (and a subscription fee at that).

VMWare lets you run Windows as a virtual machine.  If you can afford the complete version (the free-as-in-beer VMWare Player is *very* limited in what you can do with it), it's generally worth the money if you need to use Windows programs or hardware extensively and dual-booting isn't an elegant solution.

Again, it's all up to you and what you think your needs are.

---

### Post by ffxr on 2007-02-24
to be honest i cant stand WINE, it hasnt worked well for me at all for dreamweaver 8 & photoshop 7.. if you have a decent pc with plenty of RAM, i would go with a virtualisation solution...

ve been using virtualbox & its less painful to set up that vmware..

(this is only my opinion)

---

### Post by joegiampaoli on 2007-02-25
Use wine for small windows executables where you know they will run only if you copy the proper dll's into the wine directory, but when you really need to do more intensive things, then run VMware.

---

### Post by veloce on 2007-02-25
> **TheKid965 said:**
> 
VMWare lets you run Windows as a virtual machine.  If you can afford the complete version (the free-as-in-beer VMWare Player is *very* limited in what you can do with it), it's generally worth the money if you need to use Windows programs or hardware extensively and dual-booting isn't an elegant solution.


Also "free as in beer" is VMWare Server.  This is much more useful. About the only thing it doesn't have is the experimental 3d graphics support that the (not free) VMWare Workstation has.

---

### Post by bhartsock on 2007-02-25
Depends on what you do.

I am a web developer, so I have to test IE 6,7, Firefox 1.5, 2.0 (Windows and Linux).  VMWare is perfect for this, because I can create multiple virtual machines to handle different cases and different versions of the same software.

I also don't like Wine because it is a pain to setup, VMWare is super easy and quick (except for the actual VM machine install, but after that you can copy the virtual hard drives to speed to process up).

---

