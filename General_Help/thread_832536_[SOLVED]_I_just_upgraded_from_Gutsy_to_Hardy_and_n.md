---
title: "[SOLVED] I just upgraded from Gutsy to Hardy and now I have no sound."
date: 2008-06-17
forum: General Help
---

### Post by tarheel18 on 2008-06-17
I just started using Ubuntu yesterday so bear with me please.

Gutsy worked fine for me from the start. Even things I thought I would have problems with(wireless network etc.) worked perfectly. When I figured out how to update I did so and it failed the first time while downloading the packages, although this was probably because my internet service isn't too great. Installed Hardy and everything worked fine, other than my sound. The volume icon shows mute and when I clicked on it, I got an error message:

"No volume control GStreamer plugins and/or devices found"

I opened up Synaptic and looked for said plugin but found nothing. I really have no idea what it could be.

In summary: Upgraded from Gutsy to Hardy and now I have no sound, just as the title states.

---

### Post by Bubba64 on 2008-06-17
> **tarheel18 said:**
> I just started using Ubuntu yesterday so bear with me please.

Gutsy worked fine for me from the start. Even things I thought I would have problems with(wireless network etc.) worked perfectly. When I figured out how to update I did so and it failed the first time while downloading the packages, although this was probably because my internet service isn't too great. Installed Hardy and everything worked fine, other than my sound. The volume icon shows mute and when I clicked on it, I got an error message:

"No volume control GStreamer plugins and/or devices found"

I opened up Synaptic and looked for said plugin but found nothing. I really have no idea what it could be.

In summary: Upgraded from Gutsy to Hardy and now I have no sound, just as the title states.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Is a good start assuming your sound card is set up.

---

### Post by tarheel18 on 2008-06-17
> **Bubba64 said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Is a good start assuming your sound card is set up.

I just tried it and that's not my problem. I guess it not recognising my speakers/headphones. I'm using a laptop by the way. Built in speakers.

---

### Post by Bubba64 on 2008-06-17
> **tarheel18 said:**
> I just tried it and that's not my problem. I guess it not recognising my speakers/headphones. I'm using a laptop by the way. Built in speakers.

Right click on the volume-preferences and click on pcm and see if it may be that your not actually controlling the volume.

---

### Post by tarheel18 on 2008-06-17
> **Bubba64 said:**
> Right click on the volume-preferences and click on pcm and see if it may be that your not actually controlling the volume.

Everytime I click prefrences, nothing happens. No window pops up or anything. Perfrences on everything else work fine.

---

### Post by Bubba64 on 2008-06-17
> **tarheel18 said:**
> Everytime I click prefrences, nothing happens. No window pops up or anything. Perfrences on everything else work fine.

Right click on the panel-add to panel-volume control and see if that works.

---

### Post by tarheel18 on 2008-06-17
> **Bubba64 said:**
> Right click on the panel-add to panel-volume control and see if that works.
All that did was add another volume button. Same results.

---

### Post by Bubba64 on 2008-06-17
> **tarheel18 said:**
> All that did was add another volume button. Same results.

Kind of strange have you tried open volume control with a right click on th icon to see what is turned up, it sounds like your getting nothing from the volume icon altogether. have you tried dragging the volume control in sounds & video to the panel and tried any of these same methods. personally this control has never worked for me. So you have installed the Ubuntu restricted extras and gstreamer extras in add remove. here is a link that might help and the page it came from.
[http://ge.ubuntuforums.com/showthread.php?t=822338](http://ge.ubuntuforums.com/showthread.php?t=822338)
[http://ge.ubuntuforums.com/tags.php?tag=volume](http://ge.ubuntuforums.com/tags.php?tag=volume)
I suspect there is something going on with pulse audio but I am not a geek. Good luck

---

### Post by michaelzap on 2008-06-17
This just happened to me also upgrading an HP laptop. I still had sound if I booted using an older kernel, so I imagine that the sound card driver just needed to be updated to work with the new kernel. I fixed it by installing the linux-386 package using Synaptic (when you reboot you'll see 386 kernel options in grub as well as the generic ones).

---

### Post by tarheel18 on 2008-06-17
> **Bubba64 said:**
> Kind of strange have you tried open volume control with a right click on th icon to see what is turned up, it sounds like your getting nothing from the volume icon altogether. have you tried dragging the volume control in sounds & video to the panel and tried any of these same methods. personally this control has never worked for me. So you have installed the Ubuntu restricted extras and gstreamer extras in add remove. here is a link that might help and the page it came from.
[http://ge.ubuntuforums.com/showthread.php?t=822338](http://ge.ubuntuforums.com/showthread.php?t=822338)
[http://ge.ubuntuforums.com/tags.php?tag=volume](http://ge.ubuntuforums.com/tags.php?tag=volume)
I suspect there is something going on with pulse audio but I am not a geek. Good luck
Opening the volume control gets me the same "No GStreamer and/or devices found." I don't have Pulse Audio installed though. should I install that?

---

### Post by Bubba64 on 2008-06-17
> **tarheel18 said:**
> Opening the volume control gets me the same "No GStreamer and/or devices found." I don't have Pulse Audio installed though. should I install that?


In Hardy it is installed, and I have no idea what it does. Look at the post before me and see if that helps, and the links, and installs from add remove you will need. I am not an expert, it may be as simple as a reboot as well with the added lib file. I don't want to give you information that will make things worse.

---

### Post by tarheel18 on 2008-06-17
I just rebooted and when I clicked the volume, I said either the GStreamer  not installed, or my sound card was not configured. GStreamer is installed so it must be my sound card. How would I go about configuring it?

---

### Post by michaelzap on 2008-06-17
> **tarheel18 said:**
> I just rebooted and when I clicked the volume, I said either the GStreamer  not installed, or my sound card was not configured. GStreamer is installed so it must be my sound card. How would I go about configuring it?

Try installing the linux-386 package using Synaptic and rebooting (see my post above).

---

### Post by tarheel18 on 2008-06-17
> **michaelzap said:**
> Try installing the linux-386 package using Synaptic and rebooting (see my post above).
Sorry, I didn't see that one there. I'll try that and reboot, thanks.

---

### Post by tarheel18 on 2008-06-17
That worked perfectly! Thank you both!:)

---

### Post by Bubba64 on 2008-06-17
Yippee.

---

### Post by michaelzap on 2008-06-17
> **tarheel18 said:**
> That worked perfectly! Thank you both!:)

Glad to help. It's a good idea to mark threads like this as Solved (in the Thread Tools menu above). That will help other people with the same problem find the solution faster.

---

