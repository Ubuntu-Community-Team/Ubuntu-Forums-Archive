---
title: "Booting from Live Ubuntu USB, what PC components are *not* being used?"
date: 2024-08-28
forum: General Help
---

### Post by rickncn on 2024-08-28
I'm using Ubuntu 24 Live on a usb stick to troubleshoot a relatively new HP AIO Windows 11 PC that freezes with no warning. It has to be forced off. It freezes pretty reliably running a youtube video for a while.
[LIST]
[*]No crash dumps
[*]no BSOD
[*]tested the RAM- 4 passes with Memtest - all passed.
[*]booted from Ubuntu 24 live USB drive and it hasn't frozen running youtube videos all night
[/LIST]


What components *aren't* being used when running Linux off a thumbdrive? only the SSD? I'm wondering if this is some confirmation that the problem is in the SSD or related components?
Anything else that's *not* potentially being actively used on the motherboard when running live Linux from usb stick? I realize the internal SSD is mounted and readable but if I open Firefox and run a youtube video, the SSD isnt being actively used, correct?

---

### Post by grahammechanical on 2024-08-28
Do not consider me for an expert. It is my understanding that whatever OS we use any application we load will be loaded into and run from system memory. It seems to me that playing a Youtube video in Firefox on Windows is not different to playing the same video in Firefox in a Ubuntu live session. Both applications run in system memory. Both applications will make use of a hardware memory cache if available and video adapter memory to avoid staggering of the video stream.

Does the Windows OS have a utility similar the Ubuntu System monitor? It could be that some aspect or service of the Windows OS is slowly consuming more and more system memory. 

Regards

---

### Post by tea for one on 2024-08-28
> **rickncn said:**
> I realize the internal SSD is mounted and readable but if I open Firefox and run a youtube video, the SSD isnt being actively used, correct?
Yes, correct, but to be sure:-
(a) Unmount the internal SSD and run your test again
(b) Physically remove the internal SSD and then you will know that it is not active

---

### Post by sudodus on 2024-08-28
After reading your description of the problem, I think the problem can be caused both by hardware and software, for example some bad memory cell in the SSD or some bad (corrupted or buggy) file or a corrupted file system in the SSD.

But we (at the Ubuntu Forums) are not very good at troubleshooting Windows - we can help you test the hardware, but you will probably get better help with the software at some Windows User Forum.

---

### Post by rickncn on 2024-08-28
Ok, those are good points. thanks

---

### Post by rickncn on 2024-08-28
I was asking more about the Linux environment I've got going from the USB stick. Since the Windows problem isnt happening using the same HP AIO hardware system, but in a Live Ubuntu environment, I'm wondering what the differences are. It seems that only the SSD is taken out of the equation. The live environment is using my USB stick as its root drive, and knows nothing or cares nothing about Windows' C: except to know it's there. So anything I would do - Firefox, LibreOffice, Thunderbird mail, all bypasses the Windows internal C: drive. So that seems to indicate to me I've proved the internal drive is what is causing Windows' problem. Stated a different way, If I were to instead install Ubuntu on the internal hard drive, I would expect the PC to freeze up - possibly- if the SSD has a physical problem. If the SSD simply has corrupted Windows files, then that wouldn't correlate with affecting a Linux system of course.

---

### Post by rickncn on 2024-08-28
Of course - that's reasonable. I wasn't asking for any Windows troubleshooting per se. I wanted to know whether the live linux environment, run from my usb stick would have used the internal SSD drive at all for anything- my guess would be "no" since I am "trying out" the Linux OS and not installing it on the internal SSD, the SSD shouldn't have even any temporary files on it from Ubuntu, correct? It just *seemed* like a proof to me that the Windows problem was based around the SSD in some way, since Linux is running just fine without utilizing it (the SSD).

---

### Post by werewulf75 on 2024-08-28
I doubt that your problem is in any way directly related to your SSD drive. It is far more likely that the problem is either Windows 11 itself - it is, despite what MS might tell users, after all just a buggy beta the first 2-4 years after release - or possibly with your web browser. As a previous reply suggested, try having a look at Windows Taskmanager to see if anything comes up with what may look like excessive resource use. And seek further help in a Windows user forum.

---

