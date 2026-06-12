---
title: "Linux web accelerator?"
date: 2007-08-13
forum: General Help
---

### Post by pointyblue on 2007-08-13
Do any of you know of a web accelerator (not a download accelerator) for linux?

When I used win xp I used Google Web Accelerator, but there's no linux version of that program.

---

### Post by p_quarles on 2007-08-13
Never used it, but a quick search of the repos turned this up:
> varnish - A state-of-the-art, high-performance HTTP accelerator

---

### Post by wildkarde on 2007-08-13
that seems to be for server use.

---

### Post by p_quarles on 2007-08-13
> **wildkarde said:**
> that seems to be for server use.
Yeah, that would make more sense I guess. I didn't put much thought into that post.

I did a web search, though, and came up with one Linux-compatible service similar to Google's:
[http://www.toonel.net/](http://www.toonel.net/)

The similarities are limited, though. Google uses a caching proxy, whereas Toonel *only *compresses files. This will improve some performance in some areas, but not as many as Google's service can.

If you really wanted to geek out, though, I'm sure it's possible to setup a home server that can be used a caching proxy.

---

### Post by pointyblue on 2007-08-14
Thanks for the input. Toonel sounds like the thing to try.

---

### Post by Offoffoff on 2007-09-21
How to make mail port mappings work well without root privileges? I am so tired to print my root password every time I have to connect into Internet....

---

### Post by psusi on 2007-09-21
"Web Accelerator" is just another type of crapware that only exists on windows because it sucks so much.  Close cousin of the "Memory Optimizer".  They generally do nothing, or at best, tweak some default settings that default to silly values for the average home user.

---

### Post by last1 on 2007-09-21
Why not use the FasterFox firefox add-on? It'll work as good as any of the so-called accelerators, which, as psusi mentioned, don't affect the system for the better in any case.

Or even better, you could try getting more bandwidth :)

---

### Post by p_quarles on 2007-09-21
> **psusi said:**
> "Web Accelerator" is just another type of crapware that only exists on windows because it sucks so much.  Close cousin of the "Memory Optimizer".  They generally do nothing, or at best, tweak some default settings that default to silly values for the average home user.
Google's web accelerator actually does what it's supposed to, and the way it works has little to do with Windows. Essentially it hooks your browser to a caching proxy, and stores quite a bit of data there. No, it won't increase your downstream bandwidth, but it can do a lot to increase the upstream speed of the sites you visit.

---

### Post by GadgetsGuy on 2007-09-22
> **psusi said:**
> "Web Accelerator" is just another type of crapware that only exists on windows because it sucks so much.  Close cousin of the "Memory Optimizer".  They generally do nothing, or at best, tweak some default settings that default to silly values for the average home user.

100% agreed!!

If anything, download your processor specific version of Swiftfox, and then google 'how to tweak Firefox' for optimal settings in the about:config section (although I dont find this part neccessary, YMMV)

I am running only a PIII - 1Ghz machine with 512MB of RAM, and Swiftfox is very responsive right out of the box for me.

Accelerators and file compressors are totally unneccessary for Linux IMHO.

---

### Post by psusi on 2007-09-22
> **p_quarles said:**
> Google's web accelerator actually does what it's supposed to, and the way it works has little to do with Windows. Essentially it hooks your browser to a caching proxy, and stores quite a bit of data there. No, it won't increase your downstream bandwidth, but it can do a lot to increase the upstream speed of the sites you visit.

A pointless waste of effort: the browser already does its own caching.

---

### Post by p_quarles on 2007-09-22
Sure, but your browser is running on a computer with significantly less power and storage space than Google's network. 

The "point" is really determined on a case by case basis, and is not for you to judge for anyone but yourself. If you visit a lot of sites that tend to get more traffic than the servers can handle at full speed, a caching proxy makes a lot of sense.

---

### Post by kerry_s on 2007-09-22
Google Web Accelerator can be run in wine and you just setup the proxy with 127.0.0.1:9001(i think) you use the setting for other browser, check the google instructions.

---

### Post by pointyblue on 2007-10-25
Thanks Kerry_S, I'll try Google Web Accelerator in Wine.

---

