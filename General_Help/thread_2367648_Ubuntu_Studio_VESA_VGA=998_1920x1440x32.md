---
title: "Ubuntu Studio VESA VGA=998 1920x1440x32"
date: 2017-08-01
forum: General Help
---

### Post by helios-cobain-stefani on 2017-08-01
Greetings!

I just tryed out Arch Linux Kernel in order to check inconsistences with the Ubuntu Studio distribution (Trusty 14.04.5 LTS). The fact is the Arch Linux seems to recognize some graphic modes which the Ubuntu Studio distribution simply does not (i.e.: VGA=998 1920x1440x32bits) at the Hardware Test Tool. The graphic window of the video memory seems to use about 64MB, Ubuntu Studio limits the resolution to 1366x768, while stating graphic card is using above 300MB when asked. I upgraded the drivers of the board (AMD Radeon HD 6320 IGP), yet i simply appears to do nothing but to add a couple of setting icons in the setting manager, both of which display this error message:

 There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

  No AMD graphics driver is installed, or the AMD driver is not functioning properly.

 Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

 
I tryed configuring manually through *aticonfig* and it simply remains as is. Is there a way it can use the whole video memory that is being reserved? I would like to increase the video resolution to the maximum it can handle, while it seems to be 1920x1440x32 in Arch Linux, it keeps showing 1366x768 limit over Ubuntu Studio. Is there the possibility that some malicious process is making use of the rest of the reserved video memory to vulnerate the system (i.e.: to take regular screenshots or holding malicious code for execution)? It is a known fact that video memory lacks paging protection as the main memory does, even if making use of a shared memory video window.

Thanks in advance for your time and consideration!

---

