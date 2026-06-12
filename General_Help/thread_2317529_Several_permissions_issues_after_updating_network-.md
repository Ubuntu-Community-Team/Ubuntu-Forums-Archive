---
title: "Several permissions issues after updating network-manager in Kubuntu"
date: 2016-03-17
forum: General Help
---

### Post by CaptainSpam on 2016-03-17
My apologies if this has already been posted; any relevant search terms I could think of turned up nothing.

I'm running Kubuntu 15.10 (Wily) on a System76 Oryx Pro laptop.  A recent update to network-manager (and its associated libnm libraries; network-manager upgraded from 1.0.4-ubuntu5.2 to 1.0.4-ubuntu5.3) came in and I installed it via Discover, the normal way these things go on a Kubuntu install.  However, upon reboot and logging back in, I noticed several issues, all seemingly regarding permissions:


[LIST]
[*]Solaar immediately throws up a window saying it can't open /dev/hidraw0 to read status on the Logitech Unifying Receiver I use.  The devices associated with it still otherwise provide input, though.
[*]The only audio device accessible to my user account is the Dummy.
[*]If I plug in a removable drive and tell Plasma to mount it, I get a sudo prompt before it'll do so.  When I tell it to unmount, I get the same prompt.
[*]When I tell Kubuntu to shut down or reboot the laptop, it instead dumps me back to SDDM, as if I only logged out.  I CAN shut down from there.
[/LIST]

There's probably other things I haven't noticed yet, but it just seems as if the system forgot that I'm an administrator on the box (sort of; sudo prompts, including the graphical one Plasma threw at me when I mounted a removable drive, still accept me as root).  Some of these issues can at least be worked around: udev rules can force /dev/hidraw0 to be world-readable so Solaar can get hold of it again and explicitly adding myself to the audio group (usermod -a -G audio USER) and rebooting gives me my audio devices back.  However, since this all worked before the network-manager update, I'm thinking I shouldn't have to do that.

I'm quite sure either network-manager or something it updated along the way is doing this, as this is the second time it's happened on this laptop.  The first time, I simply chalked it up to the pre-installed unity-desktop and the kubuntu-desktop I installed not getting along well together and just wiped and reinstalled fresh Kubuntu.  This time, it's purely a Kubuntu machine, so I was clearly wrong there.

One other thing I just discovered: If I log in, log out, and log back in, it seems to fix most of the problems (besides the audio; I still have to be in the audio group presumably from the point PulseAudio starts to be accepted there).  But, again, that's more a workaround, not really a fix.

Anybody have any clue what happened?

Thanks!

---

