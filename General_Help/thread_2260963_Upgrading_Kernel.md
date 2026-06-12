---
title: "Upgrading Kernel"
date: 2015-01-15
forum: General Help
---

### Post by rakesh343 on 2015-01-15
Hi.

How do we upgrade kernel? My Ubuntu 14.04 is currently using the kernel 3.13.0.40. I'm having serious problems with wireless connection. In one of the forum's discussion, someone has suggested that upgrading kernel may soleve this problem. It was suggested that if we move to kernel 3.16.0.28 or something like that, the problem may be resolved. Please help me out.

---

### Post by Doug S on 2015-01-15
One suggestion is to try the most recent kernel for your system, which is 3.13.0-44, which should get installed as part of your regular update process.
There are many ways to do the regular update stuff, such that it includes kernel updates. Myself I do this:```
sudo apt-get update
sudo apt-get dist-upgrade
```If running with kernel 3.13.0-44 still doesn't work for you, then report back, and we'll go from there.

---

### Post by rakesh343 on 2015-01-16
I precisely did that and currently on the kernel you mentioned. The problem persists. Please guide me further.

thanks.

---

### Post by UsrBinSomething on 2015-01-16
I just recently built a kernel in Gentoo, here are the main steps.
1. Download the kernel source for the version you want.
2. Unpack the source code, into a folder like /usr/src/linux.
3. Figure out the details of which hardware you have. Use the 'lspci' command and note down the wi-fi, networking, graphics and sound chips.
4. Run 'make menuconfig' - there will be a massive ncurses menu for selecting various kernel options and drivers.
5. Drivers are located in device drivers. There are different sections for networking, multimedia, and graphics etc.
6. Locate the various hardware drivers in this list. Press space to select it as either 'M' for module or '*' for a built in part of the kernel.
7. Save the kernel configuration.

Other details are [here: https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Kernel]("https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Kernel") . In the Gentoo handbook there are also instructions for configuring Grub so you can choose between the new kernel and the old one. It's quite a lengthly job and command line based - it took me 3 hours on the first attempt.

---

### Post by rakesh343 on 2015-01-16
Dear UsrBinSomething,

> I just recently built a kernel in Gentoo, here are the main steps.
1. Download the kernel source for the version you want.
2. Unpack the source code, into a folder like /usr/src/linux.
3. Figure out the details of which hardware you have. Use the 'lspci' command and note down the wi-fi, networking, graphics and sound chips.
4. Run 'make menuconfig' - there will be a massive ncurses menu for selecting various kernel options and drivers.
5. Drivers are located in device drivers. There are different sections for networking, multimedia, and graphics etc.
6. Locate the various hardware drivers in this list. Press space to select it as either 'M' for module or '*' for a built in part of the kernel.
7. Save the kernel configuration.


I don't really understand the method. Can you please elaborate?

---

### Post by craig10x on 2015-01-16
14.04 will be getting the 3.16 kernel after february 5th (if you can wait it out) and that time 14.04.2 incremental release will be available and though your 14.04 will be up to date at that time, it won't automatically get the 3.16 kernel but is easy to add by installing the Hardware Enablement Stack which can be done by entering just one terminal command...i plan on doing that myself because i really need the 3.16 kernel because 3.13 causes multimedia instability problems for me and i know that 3.16 does not because i ran 14.10 for a while (which has 3.16 of course)...

You can read more about it here (a previous post i had in this section of the forum):
[http://ubuntuforums.org/showthread.php?t=2260141](http://ubuntuforums.org/showthread.php?t=2260141)

There are actually much easier ways to get 3.16 kernel right now (other then actually compiling it as was previously suggested) but the drawback is you won't get automatic updates on it in the software updater but if you install the Hardware Enablement Stack (when it's available after Feb 5th or so) you WILL...So, if you can hold out, that's a major advantage...

---

### Post by Doug S on 2015-01-16
You can also get kernels to test from the [kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") .

Just recently, [I did a pos]("http://ubuntuforums.org/showthread.php?t=2259883&page=2&p=13204922#post13204922")t on installing, and later removing, kernel PPA kernels.

Edit: also see post 15 in the above referenced thread for a link to the very kernel you mentioned in your first post.

---

### Post by rakesh343 on 2015-01-16
Dear Doug, Craig10x,

What if I install 14.10, which you guys say runs on 3.16.0-28? I need to figure out fast if my problem is taken care of. As I had mentioned in the first thread that the problem is wth the wireless connection which is dropping some time after I start my computer. Since no help was coming for my thread [http://ubuntuforums.org/showthread.php?t=2260958]("http://ubuntuforums.org/showthread.php?t=2260958") and [http://ubuntuforums.org/showthread.php?t=2260466&p=13205852&mode=linear#post13205852]("http://ubuntuforums.org/showthread.php?t=2260466&p=13205852&mode=linear#post13205852"), I thought of upgrading the kernel as suggested by someone in one discussion thread.

Do you think it is OK to test wireless connection on the new kernel? Since I don't really understand everything, I thought of this as a way of testing. Is it ok?

---

### Post by Doug S on 2015-01-16
> **rakesh343 said:**
> Dear Doug, Craig10x,

What if I install 14.10, which you guys say runs on 3.16.0-28?If you are uncomfortable with changing kernels and such, then that might be the easiest for you.

---

### Post by Cliff_Simonds on 2015-01-16
You can also get step by steps for different new kernel versions at [Your Own Linux]("http://www.yourownlinux.com/")!

---

### Post by monkeybrain20122 on 2015-01-16
+1 to kernel ppa. Create a folder called ker, say, in your home. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), choose your kernel  version, then download the following 3 files into ker:
Linux-headers generic, linux-headers-all and linux -image, choose i386 for 32 bit OS, amd64 for 64 bit.

Then open a terminal
```
cd ker
sudo dpkg -i *.deb
```

Then reboot, that's it. If something doesn't work, reboot,  log into the previous kernel (choose advanced options in the Ubuntu boot screen and it will show a list of kernels installed, choose a previous one) and then remove the new kernel (the three files you just installed) from synaptic and reboot. It is a lot safer and easier than to upgrade to 14.10 which makes no sense (in my experience 14.10 is buggy and has short support cycle)

It is easy to upgrade manually in the same way. I wouldn't wait for Ubuntu14.04.2 if I were you (besides, enabling the hardware enablement stack may have other issues like the graphic drivers are updated but only supported for the duration for the non LTS releases so when they are out of support you have to do something to make sure they get updated etc, not worth the troubles if graphic is already working)

I am running kernel 3.19-rc4 in 14.04 and cannot be happier. It fixes a very annoying problem of vlc crashing when hardware acceleration is enabled on my intel machine.

---

### Post by craig10x on 2015-01-16
Also, you could upgrade to 14.10 which already has 3.16....you might want to burn an iso of it and run it on live session and see if your wireless would work ok with that kernel...
As far as waiting for the stack for 14.04, i would do that if you can wait....also there will be other stacks available every 6 months as each new point release of 14.04 comes out, so by adding the newest one in, you will always have the latest kernel and hardware if you want to stay on 14.04 LTS...

---

### Post by Mike_Walsh on 2015-01-16
Hiya, Craig.

One question; have you noticed any regressions with the 3.16 kernel? I know you've been on it for a coupla months now.

I'm only asking, 'cos I decided quite a while ago that I shall stay with 'Trusty' probably until 18.04. I knew we'd be getting updates, but I WASN'T aware that we would also be getting kernel UPGRADES during its life cycle...

I had visions of getting up to perhaps, oh, 3.13-0.[COLOR=#ff0000]**95**[/COLOR], or something like that....! (lol) I mean, it's gone from 24 to 44 in just nine months.....I've got at **least** another 39 to go!

I take it February 5th will be the next 'point' release, then?


Regards,

Mike. :)

BTW: I never noticed you'd gone back to 'Trusty'! What was the reason for that? #-o=d>

---

### Post by craig10x on 2015-01-16
Hi Mike :)
Well actually, you won't get the newer kernels in 14.04 unless you put in the terminal command for the HWE (Hardware Enablement Stack) as each one becomes available from 14.04.2 on until the final LTS incremental release (I think that would be 14.04.5 if i am not mistaken). The new kernel and xorg package from the current 6 month version (in the case of Feb 5th that would from 14.10 of course) won't come in on your software updater automatically...you'd remain on 3.13 if you don't install the HWE...

While running 14.10, unlike the 3.13 kernel on my hardware, the 3.16 kernel had no regressions at all as i got each update on it...I went back to 14.04 LTS a few weeks ago because i knew i'd be able to get the 3.16 kernel natively in it as of Feb 5th...so with the short wait i figured i could "put up" with the multimedia problems that 3.13 plagues my computer with...
I figured, that once i had it, 14.04 would be perfect and i could run on an LTS to LTS cycle instead of upgrading every 6 months....instead, i will just add the new stack each 6 months...

I'm counting the days ;) :D

You're going to keep it on to 18.04?  I couldn't wait THAT LONG...for me, 16.04 for sure...and i will even try to do an LTS to LTS upgrade (would be my first one) but have an iso of 16.04 ready (just in case of a major catastrophe) :biggrin:

---

### Post by Mike_Walsh on 2015-01-16
That's interesting you say about multimedia problems, 'cos I've had absolutely NO issues at all with 'Trusty', except for one, very minor one.

Somebody (I forget who; I think it was monkeybrain, or might have been buzzingrobot) mentioned that they were getting a very thin, 1-pixel wide line down the side of the launcher, that didn't match either the launcher OR the desktop wallpaper. At the time I didn't take a lot of notice, 'cos I didn't HAVE the problem; but about a month later (roughly mid-September), guess what? Yep; me too! Yet less than six weeks later, it was gone.....and it's never re-appeared.

I'm not spending quite so much time in Ubuntu these days; I'm dual-booting again! I installed the current version of 'Puppy' Linux, 'Tahrpup' 6.0 (guess what it's based on?!) at the end of October.....and this old girl of mine **flies** now. Puppy in its entirety sits in 200 MB of RAM; which leaves me about 2.8 GB to play with.....it's marvellous; and SO fast.

But I still use Ubuntu, 2 or 3 times a week; there's things I just can't do in 'Puppy', that I need Ubuntu for.....and it'll ALWAYS be my 'go-to' distro in any case, as a fall-back. You just KNOW it's going to work.

'Nuff said!


Regards,

Mike. :D

---

### Post by monkeybrain20122 on 2015-01-18
I see no disadvantage of getting new kernels from mainline. It is less invasive than enabling the HES and a helll lot less work than ungrading to 14.10, not to mention a lot less risky (actually no risk as kernel can be easily removed) So if I have to update manually once in a while by downloading 3 packages and running dpkg I am happy to do it. 

On the other hand enabling the hardware enablement stack may create other problems, I have seen a few of them reported by people still using 12.04. Also there is no advantage to upgrade to 14.10 at this point, at least for me, it is buggier, some third party software I use are tested only on 14.04 and may not install in 14.10, too short maintainance cycle. etc. Unlike previous intremin releases now a lot of work has gone into Unity 8 and Mir so I don't expect much change before 16.04 and I will stick to 14.04 unless there is a compelling advantage to upgrade (e.g 13.04 offered unity 7 whihch is a big improvement over unuty 5 in 12.04)

P.s kernel 3.16 does not solve my problem with vlc but 3.19 rcs fix it completely. So if I rely on Canonical official updates the problem will be fixed only if I buy a new computer. :)

---

### Post by craig10x on 2015-01-18
@monkebrain20122: The only problem i found as far as installing newer kernels from the outside sources is that (at least on my hardware) they tend to run a lot hotter (temp wise) then the native "patched ubuntu kernel with it's proper xorg stack...that is what i observed, anyway ;)

That's why (personally) i prefer to get it in a more "native" way, as it were...:cool:

As far as which way he should go...well i think that would depend on how comfortable he is experimenting...if he upgrades to 14.10 he would get the 3.16 kernel by default, of course and wouldn't have to do anything...
The other choice (if he wants to stay with 14.04 LTS) would be to install the stack after Feb 5th...those are the best "native" solutions...

---

### Post by monkeybrain20122 on 2015-01-18
> **craig10x said:**
> 

As far as which way he should go...well i think that would depend on how comfortable he is experimenting...if he upgrades to 14.10 he would get the 3.16 kernel by default, of course and wouldn't have to do anything...
.

Well upgrading/fresh install risks breaking things  and/or   having to reinstall, retweak a whole bunch of stuffs (if necessary) It is not what I would call "wouldn't have to do anything" ;) It is a drastic move to trade in a working OS for something unknown just because of one piece of software especially when there are other ways (the kernel in this case) The disavdantages compound when the working OS happens to be a LTS and the unknown one has only 9 months of support (5 years are too long but I think using a Ubuntu release for 1.5 -2 years is reasonable with software kept up to date with ppa and self builds. All software that I use regularly on my 14.04 install is newer than 14.10's, including graphic driver and kernel)

 I am sure the Ubuntu patches do something, but probably only required for some rare hardware configurations, I have never noticed any advantage running stock kernel over kernel ppa but kernel ppa often fixes something or improves performance,--otherwise I wouldn't bother to upgrade,--and I have done it on several machines with different specs and Ubuntu releases. 

I would suggest OP to try kernel ppa first and only consider other options if that doesn't work. it is the easiest and safest way tp go,--just login to an old kernek and remove the new one if things don't work.

---

