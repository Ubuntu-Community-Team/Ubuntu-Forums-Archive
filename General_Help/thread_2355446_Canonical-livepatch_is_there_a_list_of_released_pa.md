---
title: "Canonical-livepatch: is there a list of released patches?"
date: 2017-03-12
forum: General Help
---

### Post by Irihapeti on 2017-03-12
I've installed canonical-livepatch on one of my machines. The installation went without a hitch, but I'm now wondering if it's updating properly.

I've had no patches since it was installed on 4 March. The machine is running kernel version is 4.4.0-64

At this stage, I don't know whether any patches have been released or not. Is there a list anywhere of patches that should have been installed?

---

### Post by DuckHook on 2017-03-13
Hi Irihapeti,

I'm not aware of any published list, but from this: [http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html](http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html) …it seems that you can check for status with:```
canonical-livepatch status --verbose
```At least it should tell you whether you are connecting or not. Of particular interest are Dustin's comments near the bottom: *What happens if I run into problems/bugs with Canonical Livepatches?* …and: *How do I get notifications of which CVEs are livepatched and which are not?*

Note that I don't use Livepatch, so my knowledge is woefully incomplete. My latest kernel is 4.4.0-66 but I don't know how far behind livepatch is, if at all.

---

### Post by Irihapeti on 2017-03-13
Thanks for the links, DuckHook. I had read Dustin's blog but hadn't noticed the links in the comments that you pointed out.

I've since had a look and there's no mention of "this update has been rolled out in canonical-livepatch" on any of the USNs, so not sure what to think.

```
canonical-livepatch status --verbose
```

shows:

```
client-version: "7.21"
machine-id: <redacted>
machine-token: <redacted>
architecture: x86_64
cpu-model: AMD G-T40E Processor
last-check: 2017-03-13T19:17:56.140223979+13:00
boot-time: 2017-02-24T17:26:21+13:00
uptime: 410h8m21s
status:
- kernel: 4.4.0-64.85-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: "" 
```

So I think it's working. It might well be that nothing has been rolled out in the timeframe that I'm talking about.

---

### Post by DuckHook on 2017-03-13
I'd be curious to know what you think of Livepatching, once you've had a longer run with it. I thought about installing it in a couple of servers, but then decided to upgrade them to the HWE stack instead, which isn't supported by Livepatch yet.

---

### Post by Irihapeti on 2017-03-13
I'll be happy to report, when I've got a bit more experience with it. The machine in question is my LAN router, and every time I reboot, I get a new external IP address, so I'm keen on minimising reboots as much as possible.

---

### Post by howefield on 2017-03-15
I'm a little confused, if livepatching updates your running kernel without the need for a reboot (although it doesn't negate the need for a reboot, merely delays it to a convenient time of your choosing),  4.4.0-64 is far from the current version.

Shouldn't you be on 4.4.0.67.xx ?

I don't have any machines left running that kernel series to check.

---

### Post by DuckHook on 2017-03-15
> **howefield said:**
> ...livepatching updates your running kernel without the need for a reboot (although it doesn't negate the need for a reboot, merely delays it to a convenient time of your choosing)...My understanding is that a reboot is not required: [https://en.m.wikipedia.org/wiki/Kpatch](https://en.m.wikipedia.org/wiki/Kpatch)

> Shouldn't you be on 4.4.0.67.xx ?

I don't have any machines left running that kernel series to check.Mine is on 4.4.0-66 so yes, Irihapeti's seems to be behind. I don't know how quickly livepatch tracks to mainline updates though.

---

### Post by Irihapeti on 2017-03-15
I installed livepatch just before 4.4.0-66 was released, so I would expect to get any patches since then.

I did notice on Dustin's blog that someone else had run into a similar situation, but at an earlier time. The answer appeared to be that no patches had come through at that time but did so shortly afterwards.

That's why I'd like a list of patches. Then it will very quickly be clear if I have a problem at my end or not.

---

