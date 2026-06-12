---
title: "Flash is not working with Firefox, but it is installed"
date: 2014-12-27
forum: General Help
---

### Post by walth2 on 2014-12-27
I recently installed Xubuntu and tried to start using it for the first time.
I have Firefox installed and then proceeded to install Flash through the Ubuntu Software Center that is bundled with the O/S.

When I go to YouTube and Vimeo, the videos won't play. The area of the screen shows a grey/black box.

I opened a new broswer tab and went to the URL "about:plugins".

I see the following:
[h=2]Shockwave Flash[/h]File: libflashplayer.so
Path: /usr/lib/flashplugin-installer/libflashplayer.so
Version: 11.2.202.425
State: Enabled
Shockwave Flash 11.2 r202
[TABLE="class: contenttable"]
[TR]
[TH="class: type"]MIME Type
[/TH]
[TH="class: desc"]Description[/TH]
[TH="class: suff"]Suffixes[/TH]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD]swf[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD]spl[/TD]
[/TR]
[/TABLE]


(Looks good so far...)

When I go to the Youtube site and try to load a video, within the task maanger I see multiple instances of 


plugin-container /usr/lib/flashplugin-installer/libflashplayer.so  -greomni/usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/ (and  someother stuff that I can't see)


I've read a lot of other threads that offer suggestions about how to resolve this and none of them seem to work and some just don't make sense.
I reinstalled Xubuntu a second time, thinking I corrupted something the first time. I still have the same issue.

Any ideas? This really shouldn't be this hard.

---

### Post by Yellow Pasque on 2014-12-27
What CPU do you have?
```
cat /proc/cpuinfo
```

---

### Post by Impavidus on 2014-12-27
If your cpu is too old, it may not be capable of running flash. Temüjin's command will tell us.

When I enable my Flash player in Firefox and play a youtube video, it plays nicely using Flash 11.2.202.425. If I disable the flash player and watch the same youtube video, it still plays, now using html5, and even more responsive than before. Ergo, I don't need flash. Maybe your video will play if you disable the flash player.

---

### Post by walth2 on 2014-12-28
Here is my CPU information:
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 8
model name    : AMD Athlon(tm) XP  2600+
stepping    : 1
cpu MHz        : 2087.500
cache size    : 256 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips    : 4209.45
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts



I think this takes a stranger turn for the weird... I decided to reinstall Xbuntu a 3rd time. And still no luck with Firefox, Flash, and Youtube.
I decided to uninstall Flash using the Lubuntu Software Center becasue of the HTML5 idea.

Youtube videos started working but the audio is out of sync with the video.Its unwatchable. It's a very minor improvement.
Vimeo now give me the error " Aargh! This video can’t be played with your current setup.". I didn't see anything before.
I think I'm 1/2 way there, but this still isn't what I would consider good enough.

Any more ideas? Should I ditch Firefox?

---

### Post by Yellow Pasque on 2014-12-29
Your CPU doesn't support SSE2. You might have to hack in an older version of Flash. See the link here: [http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189](http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189)

---

### Post by walth2 on 2014-12-31
Thanks. I just ran into a similar error with Chrome. It's too bad there isn't some type of error message or notification that would steer you in the right direction.
I might have to look into an older version OF Flash or just repurpose the machine for another use.

Thanks.
Walt

---

