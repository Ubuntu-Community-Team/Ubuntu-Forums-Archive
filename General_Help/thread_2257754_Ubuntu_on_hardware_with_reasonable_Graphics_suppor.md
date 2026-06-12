---
title: "Ubuntu on hardware with reasonable Graphics support"
date: 2014-12-22
forum: General Help
---

### Post by mechgt on 2014-12-22
Hi :)
I'm looking for a Desktop replacement that will run Ubuntu and offer reasonable graphics support.  Specifically what I need is to be able to stream YouTube, hulu, Netflix, things of that nature fullscreen over hdmi without a bunch of choppy business going on; (and it should also support dual monitors if that's relevant).  I almost want a Chromebox, except I'd still like a full Ubuntu OS.  My current PC runs Ubuntu, but I can barely look at a little YouTube window without it being unbearable.  I don't need gaming capability, however it'd be nice to run XBMC sometimes.

2 questions:
1) Is this a Linux graphics problem?  Am I trying to use Ubuntu where it's not the right tool for the job?  For years I've understood that Linux was horrible at handling graphics (which agrees with my observation).  Is that still the case or am I misinformed?  Maybe my existing hardware is the problem...?

2) Would something like a Zotac box suit my needs?  If I install Ubuntu on this, will it stream YouTube, Netflix, etc. full screen well?  Would it run XBMC well (no need to go over XBMC compatibility with these services)?

This would be my desktop where I'm primarily in a web browser, but it's also connected to a TV via HDMI and I'd like to stream stuff there periodically.

---

### Post by grahammechanical on 2014-12-22
I notice that you do not give the hardware specification of this machine. You want to do stuff that most likely requires more than "reasonable" graphic support. There is not an operating system in existence that can make up for hardware deficiencies.

> [COLOR=#000000]Specifically what I need is to be able to stream YouTube, hulu, Netflix, things of that nature fullscreen over hdmi without a bunch of choppy business going on; (and it should also support dual monitors if that's relevant).[/COLOR]

> [COLOR=#000000]Maybe my existing hardware is the problem...?[/COLOR]

That is always a possibility. I get by with an Intel Core 2 Duo running at 2.40GHz with 1GB of RAM and a graphic adapter that has 1GB of its own memory. But then again I am not using my machine to do the stuff that you want to do. I would imagine that trying to run full screen high definition video would require a more powerful graphic adapter then I presently have.

I am using a High Definition TV as a monitor with a HDMI connection to the graphic adapter at the highest screen resolution available (1920 x 1080) and I have no problem watching a YouTube video at full screen.  There is also another factor to consider when wanting non-choppy video streaming over the Internet and that is the data download rate of our internet connection.

You post also seems to blend more than one question. And that makes for confusion. Are you asking about your present machine? Or a Chromebox? or a Zotac Box?

Regards.

---

### Post by nerdtron on 2014-12-22
> This would be my desktop where I'm primarily in a web browser, but it's  also connected to a TV via HDMI and I'd like to stream stuff there  periodically.

Intel Processors like the i-series, (i3, i5, i7) plays well on external HDMI 1080p vidoes. Not using any dedicated video cards.

---

### Post by raptir on 2014-12-22
So, as grahammechanical said, I'm a bit confused at the details of your question.

First, you say you're looking for a desktop replacement, which means a powerful laptop meant to replace a desktop, yet you mention the Zotac Zbox and the Chromebox as possibilities, which are mini PCs. I'm going to assume you're looking for a mini PC for the rest of my post.

As far as handling media goes, graphics hardware is more of a "backup solution" than a primary one, simply because standard support is not widespread. Even in Windows, Netflix is purely CPU dependent because they didn't implement the GPU decoding that is available in Silverlight (note that this was remedied in the Windows App version of Netflix, but the issues with the website still stand). GPU decoding for locally stored videos is a bit more reasonable, but it is still not usually the best solution and limits the formats your player will support based on your hardware. Right now I'm running a laptop with a core i3 2367m, and I really only use GPU decoding when I'm trying to watch a video and I am running on battery power, which is rare. It saves you a little juice, but the experience is typically more seamless if you're using CPU decoding.

Hardware-wise, my recommendation would be to focus on getting a CPU that will handle the multimedia you want to play. Yes, you may be able to get by with something with an Atom, but you'll always have trouble making sure that everything you want to play handles GPU decoding. If you want it to be as power efficient as possible, look at something like the Intel NUC that runs a modern laptop processor. Any Haswell i3 or better will handle 1080p media playback without a problem in software alone. You don't mention the resolution of your displays but the HD 4400 or HD 5000 should have no problem outputting to two 1080p displays at once assuming one is playing media and the other is being used for something less intensive like browsing.

As far as the OS goes, Ubuntu is a great OS for playing your own files (with kodi [the new name of xbmc] or any number of other applications) but only OK for streaming media. Chrome will get you a bit better compatibility than Firefox due to the updated Flash player, but I've still run into issues. Xfinity's website will not allow me to watch any of their shows despite working fine in Windows on the same version of Chrome. Amazon Instant Video, Google Play Movies, etc... typically only work in SD due to content restrictions (Amazon will only do HD in Silverlight, Google Play will only do HD on "some videos" on PC, while it is locked to other devices for other videos). Netflix and Youtube will work fine though, if that's your main concern. And again, this is all on a i3 2367m which is weaker than anything you'd be buying today. My guess is that your issues are hardware related and not with the OS itself. For Linux-native games, I get the same performance in Linux as I do in Windows out of the Intel HD 3000 in my laptop. Nvidia and AMD should also get you comparable performance if you're okay with using the closed-source drivers.

---

### Post by mechgt on 2014-12-24
Thanks for the replies; think I'm getting somewhere.  First, to clarify my initial question
To me "Desktop" = A computer which is stationary and sits at my desk (as opposed to a laptop).  Mini-PC sounds exactly like what I'd prefer.

My existing machine is a Dell Dimension E521 with AMD Athlon 3800+ (2.4 GHz 64-bit CPU).  Based on your replies, I concluded that youtube, netflix etc. runs off CPU, not GPU so I checked

```
cat /proc/cpuinfo
```

to get 

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 79
model name	: AMD Athlon(tm) 64 Processor 3800+
stepping	: 2
**cpu MHz		: 1000.000**
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy
bogomips	: 2004.21
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

Notice the 1000 MHz shown when I have a 2.4 GHz processor.  I think this is my problem.  I installed and ran ```
cpufreq-selector --governor="performance"
``` which set my cpu to 2.4 GHz.  I toggled back and forth while youtube was running and this made night and day difference.  So... in conclusion, I've been running with a CPU throttled back to 1998 for quite some time.

---

### Post by raptir on 2014-12-24
Interesting, by default your processor's speed should scale depending on CPU demand. It seems like that is not working in your case. The performance governor keeps the CPU locked at the maximum frequency, in contrast to the ondemand governor that allows it to scale up and down. You may run into some heat issues with the processor maxed all the time, so keep an eye on that. I'm not really sure how to address the root issue of ondemand not scaling your CPU properly.

---

### Post by nerdtron on 2014-12-25
If that happens probably temperature issues, clean the heat sink and the fan thoroughly. Be sure to apply thermal paste between the CPU and heat sink too. I have an Athlon II X2 running at hot 73C, when gaming with no thermal paste and using the stock heat sink. I bought a new heat sink and fan (from themaltake) since I definitely knew that I need to lower my temps. Max temp is not 46C and definitely gives me consistent full power performance.

---

### Post by mechgt on 2014-12-28
I'll dig on the cpu governor issue separately, but thanks for the replies.  Wrapping back to the original question, the conclusion I'm going with is that any PC hardware with sufficient CPU (maybe 2.4 GHz or better) will adequately render online streaming video such as youtube, Hulu, etc. on a single monitor because your CPU is typically what will be used for the decoding which is the heavy lifting in this case.  ... and also that I'm not so concerned with a fancy graphics card except that it has the proper video outputs I'm after.

Thanks!

---

### Post by Yellow Pasque on 2014-12-29
> the conclusion I'm going with is that any PC hardware with sufficient CPU (maybe 2.4 GHz or better) will adequately render online streaming video such as youtube, Hulu, etc. on a single monitor because your CPU is typically what will be used for the decoding which is the heavy lifting in this case
Ideally, the GPU will assist the CPU with the task of decoding video, because the GPU hardware does that more efficiently. Instead of building a completely new system, you may be able to get by with a new video card. BTW, you don't even say what your current video card is...

---

