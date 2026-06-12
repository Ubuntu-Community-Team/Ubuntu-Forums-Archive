---
title: "The release of the 3.2.33 Linux kernel."
date: 2012-11-01
forum: General Help
---

### Post by kleenex on 2012-11-01
Hello, on Wed, 31 Oct, Mr Ben Hutchings announced a new 3.2.33 release of the Linux 3.2 kernel series, which is used e.g. in Ubuntu 12.04.1 LTS (currently it is 3.2.0-32 version). In this release: 99 files were changed, there was a 845 insertions([COLOR=Green]+[/COLOR]) and 475 deletions([COLOR=Red]-[/COLOR]). It is just some official information.

My question; does anyone know, why this update is not yet available in Ubuntu 12.04.1 or when it will be available? From what I remember, kernel updates were often available even on the same day when an official kernel was released. I am just a little worried. Maybe this kernel is already available on some servers, but not on all? And I am just using one of them? I hope so... 

All the best!

References:[https://lwn.net/Articles/522205/](https://lwn.net/Articles/522205/)

---

### Post by grahammechanical on 2012-11-01
Have you been turned into a pumpkin yet?

Ubuntu 12.04 is a Long Term Support release. I was guess that things like these kind of kernel updates are tested to make sure that they do not cause regressions, bring back bugs that have previously been fixed. It is important that an LTS remains stable for the user.

Ubuntu 12.10 is using kernel Linux 3.5.0-17 at the moment. But the very latest mainline kernel is 3.6 which came out too late to get into the 12.10 release. Actually, linux 3.6 has moved up to 3.6.5 and work is being done on 3.7.



So Ubuntu is not necessarily as update as you seem to think. Ubuntu 12.04 is scheduled for a 'point' release on January 31st. Please read about Stable Release Updates which is the state that 12.04 is now in.

[http://kernel.org/]("http://kernel.org/")

[https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")



Regards.

---

### Post by jerome1232 on 2012-11-01
Each release gets security patches and bugfixes only. Kernel won't update other than minor revision changes. ie 12.04 uses 3.2, those numbers won't change, only the last part will change (mine is on 3.2.0-33 for example)

---

### Post by kleenex on 2012-11-01
Hello **grahammechanical**. Have I been turned into a pumpkin? Hmm, let's see. No, I do not think so.  And frankly, I do not know why are You asking about it. Nevermind, forget it. You wrote very correct thing, about these kind of kernel updates and testing to make sure, that they do not cause any regressions. There is also an interesting text from Kernel Team, about the process and criteria for kernel updates: [COLOR=blue][_https://wiki.ubuntu.com/KernelTeam/KernelUpdates_]("https://wiki.ubuntu.com/KernelTeam/KernelUpdates")

[COLOR=Black]So, it seems that everything is okay. Goodbye.[/COLOR]
[/COLOR]

---

### Post by SantaFe on 2012-11-01
> **kleenex said:**
> Hello **grahammechanical**. Have I been turned into a pumpkin? Hmm, let's see. No, I do not think so.  And frankly, I do not know why are You asking about it. Nevermind, forget it. You wrote very correct thing, about these kind of kernel updates and testing to make sure, that they do not cause any regressions. There is also an interesting text from Kernel Team, about the process and criteria for kernel updates: [COLOR=blue][_https://wiki.ubuntu.com/KernelTeam/KernelUpdates_]("https://wiki.ubuntu.com/KernelTeam/KernelUpdates")

[COLOR=Black]So, it seems that everything is okay. Goodbye.[/COLOR]
[/COLOR]
Ah..... Halloween Joke perhaps? :)

---

### Post by kleenex on 2012-11-02
Hi **Santa**. Yes, it seems to be a just Halloween joke. By the way, it was even funny. ;- ) Yeah, I'm just kidding...

---

