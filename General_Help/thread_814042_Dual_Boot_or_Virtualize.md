---
title: "Dual Boot or Virtualize"
date: 2008-05-31
forum: General Help
---

### Post by sparkguitar05 on 2008-05-31
I've been running Ubuntu for a few months now, but there are times when I need to boot into Windows.  Would running Virtualbox be a better option for me?  Here's what I need to do....

-- I need to use Internet Explorer.  I know it sucks, but I develop websites as a hobby and I need to test them with multiple browsers, including IE.
-- I need to edit videos.  I use Sony Vegas.
-- I need to use iTunes to sync with my iPod.  I haven't found any linux apps that handle video podcasts.

Would running Windows in a virtual machine be a better option for me, or should I continue to dual boot?

3.0 GHz Processor, 1GB of RAM

---

### Post by diablo75 on 2008-05-31
I'd dual boot.  Windows will perform faster.  I've been providing support to a couple clients who set their systems up using VMware Server... I can't endorse it's use anymore.  Why?  Because every time a kernel update comes out, we have to re-install VMware using a patch.

Now, there's a potential security drawback with dual-booting, and that is the fact that, while Windows can't read the Linux partition on your hardware, it might be able to delete it.  I'm not certain, but it might be one of those fundamental vulnerabilities you can't do much about in a dual-boot setting.

Overall, it's worth keeping Windows around if you think you'll need it to perform.  Setting Windows up on a Virtual Machine is.... fun .... but also a bit of a pain in the *** from time to time, if not restrictive on what you can actually do with the VM, because the hardware is virtualized.  But on the bright side, you can backup the entire VM by just copying some files; your virtual machines are portable.

Just some thoughts...

---

### Post by quelx on 2008-05-31
Given what you need to do in Windows (especially the video editing) dual booting is probably the best option, unfortunately.

Have you looked at Cinelerra/Kino/KDEnlive or the other video editing apps?

there is ie4linux which uses Wine to run IE 6

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

If you could get the video editing moved to Ubuntu, virtualization would be plausible for the other two purposes, but editing video in a vm would probably not be fun (*read* slow)

---

### Post by sparkguitar05 on 2008-05-31
I've tried many video editing apps in linux, and nothing comes close to the professional apps in Windows.

Thanks for the advice.  I think I'll dual boot.

---

### Post by Zorael on 2008-05-31
To put it simple, you could probably be well enough off by virtualizing, *provided* that you don't want to use programs that need special hardware access. In other words; anything that requires graphics acceleration (games, video editing, accelerated video playback) = no go. Anything that requires special USB access (iTunes, other media players) = no go. Etc.

Don't forget, though, that you can manage an iPod well enough with open source alternatives to iTunes. However, you can't buy music from the online iTunes page with those.

You could probably virtualize iTunes and buy songs that way, assuming that they're not DRMd anymore? I've never used the service.

---

### Post by sparkguitar05 on 2008-05-31
I think I'll just dual boot for video editing and iTunes.

I have a ton of money on my iTunes account so I might as well continue to use that.  And I haven't found any open source linux programs that can sync video podcasts to the iPod.

---

### Post by dagnabit dang doohickey on 2008-05-31
I handle this by doing both. Sometimes booting directly into Windows is the best option, but for other tasks I use windows to complement something I'm doing in linux.

---

### Post by sparkguitar05 on 2008-05-31
How do you do both?  How do you get around the Microsoft activation issues?  Doesn't it count as two machines when you have a copy of Windows in one partition and another copy of Windows in a virtual machine?

---

### Post by dagnabit dang doohickey on 2008-05-31
I have never had a problem doing it. As to whether running Windows in a linux VM on a computer that can also boot Windows counts as two machines, I have no clue. Just throwing this out there: does dual booting two copies of Windows count as two machines?

---

### Post by diablo75 on 2008-05-31
Activation of Windows on your own legit copy doesn't present a problem until you've done it about 4 or 5 times, and they gradually increase the scrutiny of their questions to determine if you are violating your terms of usage agreement...

---

### Post by frenchn00b on 2008-05-31
> **sparkguitar05 said:**
> I've been running Ubuntu for a few months now, but there are times when I need to boot into Windows.  Would running Virtualbox be a better option for me?  Here's what I need to do....

-- I need to use Internet Explorer.  I know it sucks, but I develop websites as a hobby and I need to test them with multiple browsers, including IE.
-- I need to edit videos.  I use Sony Vegas.
-- I need to use iTunes to sync with my iPod.  I haven't found any linux apps that handle video podcasts.

Would running Windows in a virtual machine be a better option for me, or should I continue to dual boot?

3.0 GHz Processor, 1GB of RAM

Check the benow site:
[http://benow.ca/misc/caps/browsers.png](http://benow.ca/misc/caps/browsers.png)

---

### Post by frenchn00b on 2008-05-31
> **sparkguitar05 said:**
> I've been running Ubuntu for a few months now, but there are times when I need to boot into Windows.  Would running Virtualbox be a better option for me?  Here's what I need to do....

-- I need to use Internet Explorer.  I know it sucks, but I develop websites as a hobby and I need to test them with multiple browsers, including IE.
-- I need to edit videos.  I use Sony Vegas.
-- I need to use iTunes to sync with my iPod.  I haven't found any linux apps that handle video podcasts.

Would running Windows in a virtual machine be a better option for me, or should I continue to dual boot?

3.0 GHz Processor, 1GB of RAM

Check the benow site:
[http://benow.ca/misc/caps/browsers.png](http://benow.ca/misc/caps/browsers.png)
cross internet verfi for web creation

---

### Post by sparkguitar05 on 2008-05-31
> **diablo75 said:**
> Activation of Windows on your own legit copy doesn't present a problem until you've done it about 4 or 5 times, and they gradually increase the scrutiny of their questions to determine if you are violating your terms of usage agreement...

I have a legit copy of Windows XP Pro installed on it's own partition.  I used my disc to install Windows in a virtual machine in Ubuntu.  It told me I needed to activate Windows.  So I typed in my product key and it wouldn't let me activate online.  It said I needed to call a phone number.  If I activate this way in the virtual machine, will I still be able to also boot into my original copy of Windows in it's own partition?

---

### Post by the8thstar on 2008-05-31
Yes, you will.

From what I've read, it is legal to run a VM of Windows if the VM and the original Windows are on the same partition.

So if you want to respect the EULA, you can either:

create the VM on the Windows partition (accessible within Ubuntu at /media/disk or /media/Windows or /media/Vista, etc.) So, in other words, you install the same Windows twice.

OR

Run the EXISTING RAW partition of Windows as a VM in Ubuntu with your favorite VM manager. You need to follow a special HOW-TO for that. The upside is you'll only have one Windows, so you're saving some useful disk space.

FOR THE RECORD: don't tell the MS representative what you are doing with the VM thing, whatever you decide to do. It might hurt more than help IMO, because they may get confused, it can take longer, etc. Tell them you had to reinstall Windows because you screwed up your computer for instance. This way you omit, but you don't lie. It is only my opinion.

---

