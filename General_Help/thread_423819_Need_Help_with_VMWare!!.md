---
title: "Need Help with VMWare!!"
date: 2007-04-26
forum: General Help
---

### Post by kbzona on 2007-04-26
:confused: :confused: 

i installed vmware + vista on feisty... everything was ok... then i reinstalled vista but the ultimate version and now the sound is not recognized in VMWARE  (although the sound works well in ubuntu)..... it doesnt promt me to install sound driver..
whats happeningn?? plz help??

thnx.

---

### Post by gh0st on 2007-04-26
It sounds as if you haven't got the virtual sound card enabled. When you load your virtual machine check that the little sound card icon in the bottom right corner isn't crossed out, ti looks like a speaker and should be next to the hard disk and CD-ROM icons. This happens if you are using the sound device in Ubuntu when you try to load your virtual machine, it's happened to me a few times but it should give a warning, something like "sound device is in use and will be disabled". If this is the case just make sure you have nothing running on the host that requires the sound card and then click the little icon thats crossed out and re-enable it.

The other thing to check is that you haven't deleted the virtual sound device by accident in the VM setup. Stop the VM if it is running and check the hardware list in the VM's properties window, you can add a new virtual sound device if need be easily.

Those aren't the most detailed instructions I know and may not solve the problem, so get back to me if you need anything and I'll try to help. Good luck :)

---

### Post by kbzona on 2007-04-26
:)
Well i managed to get sound... i dont know why the driver didnt promt for an installation.... instead i went to the hardware manager in vista and i installed sound from there and now works like a charm :)

thnx anyway

---

### Post by gh0st on 2007-04-26
Great news glad you got it sorted. I think the forum was really busy b4, I got an email with your comment in but couldn't get onto the forum to reply. It just kept timing out. It was for a couple of hours this afternoon, seems ok now though.

I found this article about installing sound and video drivers for vista in VMware and I though you might wanna check it out [http://www.daniweb.com/techtalkforums/thread61558.html](http://www.daniweb.com/techtalkforums/thread61558.html)

You probably don't need it now though. Never mind :)

---

### Post by Mach1US on 2007-06-04
I have installed vmserver but can't find any way to install sound card in the gest operating system.
I am running XP pro on feisty as a host and no sound card icon is displayed in any of the vmware configurations , i have installed vmware tools and tried all kinds of scripts but  no luck.
Any ideas what am i doing wrong ?

---

### Post by seamuso on 2007-06-04
> **Mach1US said:**
> I have installed vmserver but can't find any way to install sound card in the gest operating system.
I am running XP pro on feisty as a host and no sound card icon is displayed in any of the vmware configurations , i have installed vmware tools and tried all kinds of scripts but  no luck.
Any ideas what am i doing wrong ?

with the guest powered down, double click on any of the hardware items listed .. in the settings menu, you can add ( + ) new hardware .. the soundcard is in there.

[http://info.bluefrogcs.com/images/vmsetting.png](http://info.bluefrogcs.com/images/vmsetting.png)

---

### Post by Mach1US on 2007-06-04
I have just powered it down and items listaed in there are :
Memory , Hard Disk , CD Rom , Floppy 1 , Ethernet 1 , Mouse and Processor .
There is no sound card icon there , any ideas ?

---

### Post by Mach1US on 2007-06-04
I just got what you meant  after looking at the picture #-o
Picture really is worth a thousand words .
Thanks a million .

---

