---
title: "Hardy Heron ... Kinda Sluggish?"
date: 2008-04-27
forum: General Help
---

### Post by AaronCW on 2008-04-27
Hi. Brand new Linux user here. Umm, I just installed Ubuntu HH and my question is... why is it so sluggish? TBH, I don't have a great system.. Celeron 2.7Ghz with 1GB Ram and a Generic nVidia 256MB Video Card. But even my Windows XP SP2 OS runs quite a bit faster.

For instance, a few minutes ago I was running (for the first time) Rythembox (which is Great by first impression), but while listening to Guns N Roses and attempting to remove some software via Synaptic Package Mgr the MP3's started to "skip" BADLY. And all I was doing was listening to MP3 and removing a few programs. Oh, and I might of had Firefox open (but not in use). 

So, is there a program or some settings I could check to figure out the performance issue? I did a standard / generic Install with the CD ISO I downloaded from Ubuntu.com. Also, I have one Hard Drive that is partitioned with WinXP and Ubuntu / GRUB Boot Loaded. (Also I think there is a Linux Swap somewhere...) 

I like the OS so far, just having some problems with performance a bit.

TIA! Aaron

---

### Post by mrsteveman1 on 2008-04-27
It's not your system, its a bug somewhere.

A 2.7ghz system should be able to encode high def video while playing garry kasparov in a chess match without you noticing anything.

---

### Post by mister_pink on 2008-04-27
Sounds like somethings wrong there, my computer is older than that and I can multitask quite happily with multiple programs open, even windows XP running virtually as well.

Do you have desktop effects on? Wobbly windows and that? And do you know which graphics driver you're using? 

The command "top" in a terminal will let you know whats using up cpu and memory too, or theres the System monitor too (System, Admin, System Monitor, Processes and View, all)

---

### Post by AaronCW on 2008-04-27
Well I placed 2 screenshots... one from System Monitor and one from TOP on my flickr page here: [http://www.flickr.com/photos/aaroncaleb/](http://www.flickr.com/photos/aaroncaleb/)

I'm not familiar with the system monitor in ubuntu... anyone see anything wrong here? 

Thanks for looking! Aaron

Edit: BTW, I tested by doing the same thing I did earlier... Running Rythembox AND trying to Install / Uninstall some programs from Add/Remove Programs. Same slow down, same MP3 Skipping. (The MP3's are located on my External FreeAgent Drive btw) ... and it seems that the system has continued to be very very slow, even  after I closed Rythembox and went about putting up my screenshots. The whole time the system was sluggish, windows took forever to open, etc.

---

### Post by mister_pink on 2008-04-27
Firefox seems to be using a lot of cpu, but to be honest cpu usage in quite dynamic, so a second after you took that it may have calmed down again. It probably easiest if you watch top for a bit and see if firefox always seems to use that much. On mine firefox rarely uses more than 5% cpu unless its  currently doing something. xorg always uses quite a bit. 

Do you find it sluggish still if you multitask but not including firefox? Unfortunately even if you identify the issue I have no idea how to do anything about it really

---

### Post by mrsteveman1 on 2008-04-27
You might be able to get more information by running powertop or latencytop which both give you more low level information on what is using resources.

Top itself and the system monitor can only tell you if the CPU is being spiked, but thats not the only thing that can cause problems.

I know powertop is supported already but im not sure about latencytop.

Heres some info on them: 

[http://latencytop.org/](http://latencytop.org/)

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

EDIT: I checked the kernel changelog and it seems latencytop is only available in 2.6.25 which hardy isn't using. This is what angers me about the way Linux kernels are handled with updates, it shouldn't be necessary to compile an entirely new kernel just to do stuff like this.

I don't see latencytop in the repos for hardy right now though, hopefully they will add it to a kernel update. grrrrr

---

### Post by affert on 2008-04-27
I found this to be the case for me as well.  I do have a slightly older computer (Dell Latitude, PIII 1.2 GHz with 512 MB RAM), but it worked fine for running WinXP, earlier versions of Ubuntu and PCLOS.  The best example specifically was trying to watch a youtube video:  It was so choppy I couldn't watch it.  Firefox was the only thing program I had running.  I also tried using Epiphany, just in case it was a Firefox problem, but no difference.  I also noticed sluggishness when changing windows.  

When I open the system monitor, it lists the CPU as being 100% used pretty much all of the time.  

The options to view all processes (as opposed to viewing just my processes) are grayed out.  How can I tell what is eating up the CPU?

What can I do to make things run more quickly?

*edit*
Ok, I missed the previous post: I will give those tools a try.

---

### Post by mrsteveman1 on 2008-04-27
Powertop can at least show you what is causing the kernel to wake up repeatedly, which might show you something.

Its a shame about latencytop not being supported yet in hardy, if it ever will be, because this issue is what latencytop is for. Even the project page specifically talks about skipping audio.

---

### Post by affert on 2008-04-27
Running top while watching the video yeilded this:
>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                          
  5906 david     20   0  192m  95m  25m R 51.1 18.9   1:55.60 /usr/lib/firefox-3.0b5/firefox                                                                                   
 5296 root      20   0 59756  34m 8392 R 41.8  6.9   2:24.16 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7                                         

as the top two results when sorted by CPU usage.  Why are they taking so much?

---

### Post by mrsteveman1 on 2008-04-27
X is taking so much because of the screen draws, though that shouldn't happen.

Firefox is anyones guess, some things cause firefox to spike the CPU, like javascript or flash on some websites, not all but some of them really spike the cpu and lock firefox.

---

### Post by cometa2k7 on 2008-04-28
Firefox is a massive resurce hog in Hardy.

I was using Opera, Emesene, CheckGmail, System Monitor, and Guake, and my computer was running at about 25% processor. I opened Firefox, and it shot straight to 100%, and is staying well about 80% whilst I'm not using it.

However, it seems that most of that was Flash applications on the page that I was on. It uses no processor power really when on Google.

In contrast to you, I have found Hardy to be slightly lighter on resources than Gutsy, and a lot more responsive. I have even left the effects on, and I turned them off in Gutsy.

---

### Post by JRoDDz on 2008-04-29
Firefox is still in BETA.  I'm sure it's been answered here before but why would they put in a beta software for 8.04?  It seems Firefox is hogging your cpu.

---

### Post by Nunu on 2008-04-29
> **JRoDDz said:**
> Firefox is still in BETA.  I'm sure it's been answered here before but why would they put in a beta software for 8.04?  It seems Firefox is hogging your cpu.

Reason is because FF2 is coming to end of life soon and that the upgrade from beta to full would be easier. I downgraded to FF2 as soon as i got the os going. Made a huge difference to my machine. :guitar:

---

### Post by sports fan Matt on 2008-04-29
Has anyone tried Swiftfox to see if it encours the same results?

---

### Post by cometa2k7 on 2008-04-29
> **JRoDDz said:**
> Firefox is still in BETA.  I'm sure it's been answered here before but why would they put in a beta software for 8.04?  It seems Firefox is hogging your cpu.

They used BETA software, because Firefox 2 will soon be out of date, and the BETA is very stable, it's just a bit of a CPU hog for now.

Personally, I don't use Firefox, I use Opera, and if I just want to do something quick, or use a flash application, I use Epiphany, it has the Gecko engine in it.

---

### Post by affert on 2008-04-29
I got the same results when using epiphany instead of firefox, so I don't think it is a firefox-specific issue.  Unless epiphany has the same problem.

---

### Post by cometa2k7 on 2008-04-30
> **affert said:**
> I got the same results when using epiphany instead of firefox, so I don't think it is a firefox-specific issue.  Unless epiphany has the same problem.

When I use Epiphany, I get a spike in CPU to 100%, but it soon drops to about 10%. But raises to 50% on flash intensive pages.

---

