---
title: "Toshiba L750d/755d kernel &amp; ACPI issues"
date: 2013-04-29
forum: General Help
---

### Post by C0NFU53D2 on 2013-04-29
i have a Toshiba L755D (exact same bios (Insyde H2O and hardware as 750d (750d has bluetooth), hence the title) and the Fn keys don't work, no surprise there.  i see a bunch of threads in google on other forums, but i cannot find a solution.  apparently one that works, is compiling a new kernel, but the most recent one i have seen to do this with is kernel version 2.6.  there don't seem to be any other fixes for this problem.  i have tried everything else i have see, but if you have seen/see something that i missed please reply. 

i have tried: 
[LIST]
[*]FnFx (way outdated for older toshiba computers) 
[*]Toshset (also outdated, but not as much) 
[*]editing the grub menu (no change, but idk if i did it right, all seem to be for other ubuntu versions/grub versions) 
[/LIST]
if you know of anymore, or have seen a fix, please post here.

Im running Ubuntu 13.04 (have same issues on openSUSE 12.3, Ubuntu 12.04, 12.10) running 64 bit versions, all hardware (except battery) work fine. 

problems: 
[LIST]
[*]no battery icon (have tried 3rd party software, battery isn't even detected.) but lasts for ~4 hours 
[*]Fn Keys don't work except Mute(Fn+Exc) volume up/down (Fn+3/4 respectivly). (the brightness down (Fn+F6) has a keycode, but up (Fn+F7) does not, also wifi toggle (Fn+F8) does not return a keycode) 
[*]brightness control via menu works, untill you install AMD Fglrx (one from additional software/drivers gives Unspported Software in bottom right, but the one from AMD's site works fine) the brightness control bar is still there, but no change when you change it. 
[/LIST]


if you need me to post terminal outputs or other information, just ask. 

thanks in advance!

---

### Post by C0NFU53D2 on 2013-05-01
anyone know of ***any*** fixes? 
i hope i don't seem impatient, i am still looking, but if anyone comes across something...
i would like to not have to use windows

---

### Post by MassStash on 2013-05-22
l645d-s4056 been looking for battery support fix for about 2 months to no avail. All my fn keys and functions seem to be working fine to my knowledge tho....

---

### Post by C0NFU53D2 on 2013-08-17
my apologies for bumping my old thread. but i am still searching, and if in this amount of time anyone has come up with any info would be great.  
or link to a insyde bios fix if there is one, i have not seen one.  but others may have.  

im confident that the problem is with the h20 insyde bios because i have a toshiba netbook 2010 with a phoenix bios and it works 100% with linux

---

### Post by kvanberendonck on 2013-10-01
Hi @C0NFU53D2,

This is an ACPI table typo. For the fix (applied above the existing ACPI table) see here:
[https://gist.github.com/kvanberendonck/4049776](https://gist.github.com/kvanberendonck/4049776)

I contacted Toshiba approximately 3 weeks ago requesting they do something on their end (with the fix attached). Unfortunately, it's really hard to do ACPI mods under Ubuntu, and when you do your kernel becomes tainted. I think the best bet might be to just wait it out for Toshiba to respond.

Regards,

Kyle

---

### Post by MassStash on 2013-12-04
> **kvanberendonck said:**
> Hi @C0NFU53D2,

This is an ACPI table typo. For the fix (applied above the existing ACPI table) see here:
[https://gist.github.com/kvanberendonck/4049776](https://gist.github.com/kvanberendonck/4049776)

I contacted Toshiba approximately 3 weeks ago requesting they do something on their end (with the fix attached). Unfortunately, it's really hard to do ACPI mods under Ubuntu, and when you do your kernel becomes tainted. I think the best bet might be to just wait it out for Toshiba to respond.

Regards,

Kyle
Did they ever respond? I'm on a l645d-s4056 and still have yet to find a fix for battery to be recognized. On 13.10. It's recognized plugging in and out ac adapter tho, really weird.

---

