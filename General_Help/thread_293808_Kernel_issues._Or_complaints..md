---
title: "Kernel issues. Or complaints."
date: 2006-11-05
forum: General Help
---

### Post by clockwork on 2006-11-05
So I am switching from gentoo to ubuntu, mostly cause I dont want to spend a ton of time dealing with "little" bugs and annoyances. I've been using linux for a long time so I know my way around fairly well. However I have never touched debian before and I have a few quick questions regarding the "ubuntu way"

First, is it possible to run a vanilla/home rolled/re-configured kernel and not have issues with packages ? I know some distributions setup their packages to look for their own kernels. I *HATE* having to use an initrd, and tons of modules. Its a pain in the arse, and makes trouble shooting a nightmare.

Second, what is the deal with fglrx ? I have right about 100 different howto's and they all conflict with each other. I need to have fglrx installed and working, of course the initrd loads 5 or 6 useless modules (framebuffers mostly) that cause problems with X. I tried using the blacklists, and the load lists (/etc/modules) but of course the wonderful initrd overrides those.

The only other thing I will be doing in the future is xen. Bearing that in mind, can I use a vanilla kernel ?

That covers what I need to know for now. Thank you in advance for your help.

---

### Post by bsussman on 2006-11-05
I too have been using linux a long time, though I have always preferred debian-based releases.

I predict you will have issues sooner or later, since ubuntu seems to be a very integrated distribution with certain goals in reliability and timeliness that may conflict with deep customization.

That being said, it would be interesting to read of your adventures along the way if you stick it out.

One warning - it does look like 6.10 is really a development release, not a production release.  They couldn't seem to bear to actually say that so they merely characterized it as "edgy" but many included packages are beta - by definition not production.  The traffic in the support forums seems to bear this out.

So you may want camp out in 6.06 until the next real production release.

---

### Post by clockwork on 2006-11-05
I have no problem running beta software. My problem is beta software running beta software. (eg portage breaking everything on the system, cause some *** of a developer thought it should be done "his way")

If ubuntu is that proprietary that you cant even roll your own kernel, I'll probably look elsewhere.

---

### Post by hexion on 2006-11-05
- You can compile your own kernel, from vanilla, and have no problems. Well, you'll need to patch it if you want wireless, sata, (...) support.
But I recommend not doing so.. Ubuntu devs patch current kernel with upstream code, so there's no really need in compiling your own kernel (except a few cases)

- For fglrx I recommend you Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Or better this, which is the howto I follow always with no problems at all:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)


You should have no problems with it ;)

---

### Post by bsussman on 2006-11-05
I may be overdoing the warning.

I am very conservative, coming from a Fortune100 System Reliability and Critical Support background.  I do not like innovation in production. I like thorough integration testing and total regression testing.

You might be fine here.

---

### Post by clockwork on 2006-11-05
Having worked at Sun and IBM, I think I got the production thing down. I wouldnt be using a distro that eliminates inittab and init scripts in production. No way, no how.

This however is just my laptop.

I dont care if its vanilla, I just dont want everything built has modules. Its messy and a pain in the *** when your trying to trouble shoot something.

Is there an official way to rebuild the ubuntu kernel ? (non-modules for everything)

---

### Post by bsussman on 2006-11-05
I do not believe there is an official way - the standard way of building a static-only kernel will work AFAIK.

I do not recall the parm since I do not bother building kernels much myself anymore :)

How ever you do it now should suffice.  Preserving the current working kernel and grub config is key to recovering from non-working builds, just as it always is.  kernel and header sources go in the standard locations and build is siilar to gentoo except you do not have emerge so the debian kernel build process is pretty much necessary.

Sorry to be so generic - debian is so good about these things...I am waiting for some other kernel-tinkerer to weigh in. :)

---

### Post by clockwork on 2006-11-05
So I got a kernel built, now I just need to figure out the ubuntu booting system. I get past all the module stuff and then it hangs at scripts/init-bottom

Which as best I can tell is the udev stuff.

---

