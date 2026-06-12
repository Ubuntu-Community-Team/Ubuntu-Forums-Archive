---
title: "Fed up with updates breaking things... (Which repositories won't break my system?)"
date: 2006-11-27
forum: General Help
---

### Post by Demon012 on 2006-11-27
Hi Guys,

Sorry about the title of this thread but it is just how I am currently feeling. Earlier today I installed some updates just before I went to college and when I get back and want to chill out I find that both vmware player and my sound is not working. 

I have gotten the vmware player working but am still having problems with finding out what broke the sound and how to fix it (sound card is detected fine with aplay -l). Anyway that is not what this thread is about. 

Which repositories am safe to update with? Recently updates have been giving me big problems and I am even contemplating not updating at all when I get my system working properly again and only updating small things like applications but I would prefer not to resort to this as I hate having bugs and love to have new features.

I am using Edgy and until today I was ok with everything working perfectly.

Thanks,

Demon012

---

### Post by 23meg on 2006-11-27
> Which repositories am safe to update with? Short answer: the official ones.

---

### Post by Demon012 on 2006-11-27
Thanks for the reply but define official ones because the only ones I use are to my knowledge "official" however I am referring to should I be updating from the universe, multiverse and restricted repos? and which are safe to update from.

Thanks again for the reply 23meg

---

### Post by 23meg on 2006-11-27
To be more specific, support for Universe apps isn't guaranteed, and Multiverse is totally unsupported, though all are official. Are you sure you're not making any other changes to your system that may be causing the failures? From what you say I infer that you may mean something other than the regular security updates, maybe *upgrading* to newer versions of some apps and libraries from non-official repositories?

I did hear that official kernel updates can break things like VMWare, but I haven't seen a kernel update to Edgy, so neither should you have.

---

### Post by Demon012 on 2006-11-27
I am not completely sure what updates installed today but all I know that is I only currently have Official repos selected (all of the official ones) and in the Internet updates section of the software sources selector I have the following ticked....

Important security updates
Recommended Updates
Backported updates

I am not too bothered about vmware-player because I have sorted that (found a post saying to uninstall dbus-1.2 because it conflicts with dbus-1.3) however I cannot find anything that could be causing my sound to not work (works fine in windows, ubuntu is detecting it via aplay, it is selected as the default sound card as there is no other sound card available (turned off the onboard in the BIOS while still in Dapper), reinstalled the entire sound system etc).

However if you would know of any way of finding out what updates installed earlier on today (is there a log I do not know of?) and reverting them back to the older versions that would be great as it would also allow me to reverse any problems like this in the future.

Thanks,

Demon012

---

