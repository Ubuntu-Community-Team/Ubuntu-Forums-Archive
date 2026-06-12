---
title: "RealPlayer 10.0 binary mysteriously hangs (brand new Ubuntu installation)"
date: 2005-09-02
forum: General Help
---

### Post by Blueshell on 2005-09-02
I just installed Ubuntu 5.04 on a brand-new disk; this is the first time I've tried to install Ubuntu, but I've used other Debians.

However, I can't get RealPlayer 10.0 to do -anything-.  (I'm installing RP because every time I try to use Totem, it says "Totem could not startup.  Resource busy or not available" [and googling for that string hasn't yielded anything useful at -all-; what's going on with -that-?)], and I'm installing RP 10.0 because 5.04's default of RP 8 doesn't work---it claims it's downloaded rp8_linux-etc, but I can't find it in the filesystem, and Synaptic then blows up saying it can't find it, either---I think it actually got handed RP10 by Real's site, put it on the desktop, and then couldn't find it because it wasn't named what it expected.  [and googling for that string hasn't yielded anything useful at -all-; what's going on with -that-?)],

So I went to Real.com, downloaded RP10, ran the installer as myself (not root), and had it install everything in ~/Bin/RealPlayer.  (After various unsuccessful stuff later, I realized that maybe I shouldn't have had Firefox running at the time, so I quit Firefox, removed ~/Bin/RealPlayer, and reran the installer.  No change.)

But realplayer.bin simply -hangs- under all circumstances, which means I can't play any audio.  It hangs from Firefox (and about:plugins there claims it's running the plugin, and I can see it in the process table), it hangs if I try ./realplay some-file (even if some-file doesn't exist!), and it hangs if I run the binary directly, e.g., ./realplay.bin some-file (again, even if the file doesn't exist).  The binary simply never exits.  So I've now got several hung copies of it in my process table from attempts under Firefox, for example.

I tried rebooting.  Same behavior.  I'm surprised that the binary doesn't at least tell me if its file argument doesn't exist before hanging; I'd expect it would get there before trying to frob with the audio hardware, for example.

I also tried running the binary directly as root, in case it was some sort of permissions problem.  No change in behavior; it still just hangs.

Audio on the machine -does- work; for example, I can hear various sounds from desktop events if I connect the machine's audio-out to my stereo, and I had no trouble ripping a track from a CD and then playing it back.  (And I'm sure the audio was indeed being played from the filesystem, and not through some analog-out of the CD player or whatever.)  So audio on the machine works; it's just RP that doesn't.

What do I do now?  Is there somewhere I can download RP8 to see if it's RP10 that's the problem?

uname -a says 
Linux darkstar 2.6.10-5-k7 #1 Thu Aug 18 23:14:40 UTC 2005 i686 GNU/Linux
...and this is on some modern (1.5 years old) AMD CPU; motherboard details upon request, but it's hard to believe -that- matters, since audio works on the machine.

Thanks!

---

### Post by jameswilhelm on 2005-09-02
I don't know if this is your problem, but if the sound server is running, Realplayer won't start properly. It also won't start if any other program is using audio.

You will see some Realplayer processes if you look in the system monitor, but it won't appear on the desktop.

Disable the sound server under "System -> Preferences -> Sound" by unselecting the 'Enable sound server startup' tickbox. I never use ESD and everything works fine.

Make sure that all instances of Realplayer have been killed off before doing any of this - just to be sure.

Audio is one of the few things on Linux that still makes me want to smash the PC!

---

### Post by Blueshell on 2005-09-03
[QUOTE=jameswilhelm]I don't know if this is your problem, but if the sound server is running, Realplayer won't start properly. It also won't start if any other program is using audio.

You will see some Realplayer processes if you look in the system monitor, but it won't appear on the desktop.

Disable the sound server under "System -> Preferences -> Sound" by unselecting the 'Enable sound server startup' tickbox. I never use ESD and everything works fine.[/QUOTE]

Bingo!  The instant I unchecked it (even before I'd closed the window), a RealPlayer window popped up that said "Welcome to RealPlayer" and ran me through the license agreement, after which the player immediately popped up and started playing one of the URLs I'd been trying.  (I probably should have heeded your advice  below and killed off all the leftover processes, but oh well.  I -did- reboot later to make sure everything was hunky-dory (since several license-agreement windows had tried to open and I didn't know if one might have left the system in an inconsistent state :), and everything's fine, even after reboot.

> Make sure that all instances of Realplayer have been killed off before doing any of this - just to be sure.

Audio is one of the few things on Linux that still makes me want to smash the PC!

Amen!  This is one of the major reasons I was reluctant to switch away from an old and decrepit other release, because I remembered what a PITA it was to get AV stuff to work---but enough other things were getting too creaky that I decided to risk it, finally.

It would be a -really- good idea for this interaction to be prominently mentioned in release notes for both Ubuntu (and maybe Debian generally), -and- for RealPlayer.  If you have good ideas about how to submit these bug reports, please do (and let me know); otherwise, I'll hunt around for how to do it so they'll get noticed.  It would -never- have occurred to me on my own, and considerable web searching failed to turn it up.

If you're ever in the Boston area, ping me & I'll buy you the beverage of your choice.  Thanks!

---

### Post by jameswilhelm on 2005-09-03
Glad to help.

I suspect this is a problem with Realplayer for Linux and not with Linux itself, but I'm no expert. I had the same problem when still using Redhat 9. I did not have this problem when still using Windows 98 at home or currently with Windows XP at work.

Enjoy!

---

