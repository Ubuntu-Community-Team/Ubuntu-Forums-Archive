---
title: "50% usage problem, can't use 100% cpu per program"
date: 2008-01-03
forum: General Help
---

### Post by savagenator on 2008-01-03
Hello everyone. I have somewhat of an unusual problem. When I use firefox, and I have many flash windows open, and they are cpu intensive, together they max out at 50% of my cpu usage. I do not know if this is becuase they are using only one core of my cpu, but one cpu is under a higher load (about 20% looking at the graph) than the other.

Please help me, I would like to be able to use the full potential of my computer. I have an AMD 4400+ X2.

---

### Post by PurposeOfReason on 2008-01-03
Are you using the 64bit Ubuntu? If not, that's your problem.

---

### Post by savagenator on 2008-01-03
No I am not using 64-bit, but i can assure you that is not the problem. The same problem has happened in 64-bit when I used it, and I recently switched to x86 becuase of more programs support and I could actually use flash.

Another thing: firefox lags a lot when the flash problem happens, and if I use Devede to burn a movie, or wine to extract something, it all uses 50% of the CPU, and same with compiling. Most of these things were done in 64-bit too.

---

### Post by PurposeOfReason on 2008-01-03
How long ago did you use 64bit? Flash is no fixed and easy to do and when I used 64bit Gutsy it would always use 100% of my CPU when it could or was that intense.

---

### Post by savagenator on 2008-01-03
i switched to x86 3 weeks ago. Could it be something to do with my hardware?

---

### Post by PurposeOfReason on 2008-01-03
It won't be your hardware. That is a dual core. With 32bit it'll use one core per application getting you to 50% with one application. However, since you say you're doing a few things open at once, it should take more. Unless all your flash windows are in firefox.

---

### Post by savagenator on 2008-01-03
well, if thats the case, thank you, you answered my question. Is there any way to treat the dual cores as one core though?

---

### Post by rubicon on 2008-01-04
> **savagenator said:**
> well, if thats the case, thank you, you answered my question. Is there any way to treat the dual cores as one core though?
E.g. Downgrade? :) HyperThreading, Dual Core, parallel execution and pipelines -- that is progress of technology -- allows you and your programs to use your single processor like 2 or 4 or even 8 virtual processors. Believe me, you don't need to **'merge' your CPU into one**, you need programs that are able to utilize multiple virtual CPUs equally effective.

The only one way (that I know) for application to utilize all CPU resources is to create a number of threads/fibers/processes equal to number of virtual CPUs and divide calculations between them equally. Well, if you try to encode some video, you may notice that your CPU is 90-100% used by codec app (or may not, it depends).

---

### Post by savagenator on 2008-04-07
I'm going back to this thread. Since I last made and posted this thread, I was not such an experienced Linux user, and Now here I am, completely different distro, same problem. I have virtualbox running, only using 50% cpu max, when I would like it to use more. Same with firefox. Same with flash (npviewer.bin. Same with decoding videos. You get the drift. 

If there is a program that is asking for a lot of CPU power, I want it to be able to use all of it, so if it uses 100% on one core (which it does) I want it to leak some of the energy onto the second core.

---

### Post by mcduck on 2008-04-08
> **savagenator said:**
> I'm going back to this thread. Since I last made and posted this thread, I was not such an experienced Linux user, and Now here I am, completely different distro, same problem. I have virtualbox running, only using 50% cpu max, when I would like it to use more. Same with firefox. Same with flash (npviewer.bin. Same with decoding videos. You get the drift. 

If there is a program that is asking for a lot of CPU power, I want it to be able to use all of it, so if it uses 100% on one core (which it does) I want it to leak some of the energy onto the second core.
That's simply not possible, unless the program you use is made to run on multiple threads it can only run on one CPU/core at a time.

Virtualbox, Firefox and Flash all only support one thread. Same applies to majority of programs available, and it's the same problem on all operating systems. Some tasks simply are very hard to separate into multiple threads.

Actually apart from some rare games, I've only found some professional audio/video editors and graphics apps that support multiple threads, and Grip (music ripper) has the option to run on multiple threads as well.

---

### Post by savagenator on 2008-04-08
> **mcduck said:**
> That's simply not possible, unless the program you use is made to run on multiple threads it can only run on one CPU/core at a time.

Virtualbox, Firefox and Flash all only support one thread. Same applies to majority of programs available, and it's the same problem on all operating systems. Some tasks simply are very hard to separate into multiple threads.

Actually apart from some rare games, I've only found some professional audio/video editors and graphics apps that support multiple threads, and Grip (music ripper) has the option to run on multiple threads as well.

what you say makes sense. I am inclined to believe you except for one thing which I base my problem off of: windows. When I use windows I never have only one core stay at 100% using any program. If anything, I could blame it on the fact that there are many different threads of programs running, but I do remember firefox using 100% CPU at one point.

---

### Post by dcstar on 2008-04-09
> **savagenator said:**
> what you say makes sense. I am inclined to believe you except for one thing which I base my problem off of: windows. When I use windows I never have only one core stay at 100% using any program. If anything, I could blame it on the fact that there are many different threads of programs running, but I do remember firefox using 100% CPU at one point.

Windoze runs crap like anti-virus etc., so when you use one app others are also constantly at work in their (sometimes vain) attempts to keep you PC "safe", no wonder you get 100% utilisation spikes in that OS.

---

### Post by savagenator on 2008-04-09
> **dcstar said:**
> Windoze runs crap like anti-virus etc., so when you use one app others are also constantly at work in their (somestimes vain) attempts to keep you PC "safe", no wonder you get 100% utilisation spikes in that OS.

Well, lets put it this way. My antivirus (gah), avast, does not take much cpu at all compared to other random stuff like explorer.exe and other weird crap that is part of windows in the background, but at least it idles under 15% CPU. Firefox uses 100% (cuz it hangs for some odd reason when i'm using a certain flash heavy site) CPU, which the same site uses 50% in linux. Same computer. 

I work in an IT environment, that is where you see the worse in operating systems. Try updating the newest shock wave v11 through Firefox (you can't), but it only works through IE. Also try completely removing java from windows (you can't) you have to manually delete files under Doc. And Set. and Program Files

Linux: sudo rm -rf /opt/java && sudo rm -rf /usr/java would be the equivalent.

---

### Post by savagenator on 2008-04-10
giving a gentle bump

---

