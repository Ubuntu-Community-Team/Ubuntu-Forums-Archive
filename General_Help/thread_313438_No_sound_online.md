---
title: "No sound online"
date: 2006-12-06
forum: General Help
---

### Post by cjax1 on 2006-12-06
Hi all,

I have no sound from the web. No sound with youtube, no sound playing in realplayer while watching online stuff. The videos play but no sound. One thing I watch is NASA tv. Real player opens and the video plays but no sound. I can play music on the hard drive. System sounds work like normal. Even the sounds in GAIM Internet Messenger work. I tried some suggestions in another thread posted by someone evidently having the same problem. All other posts seem to be to do with the sound card not being detected. Mine is. I've tried restarting Firefox and the computer. I was watching videos on line last night about this time. It was working fine. The only thing different was I installed some Ubuntu updates earlier today but don't know what they were. I am going to start writing these updates down unless there is a way to check the update history.

Here's what I tried from this post,
[http://www.ubuntuforums.org/showthread.php?t=310292&highlight=no+sound](http://www.ubuntuforums.org/showthread.php?t=310292&highlight=no+sound)

This is the only post I found that even came close to the problem I'm having. I tried everything suggested. Downloaded something called alsa. Made the changes suggested. It didn't help. I restarted at least twice. I checked the sound mixer controls. I checked System>Preferences>Sound. Looks OK.

Any ideas anyone? Maybe this is a Firefox issue?

Thanks

---

### Post by Delkster on 2006-12-06
If you go to System > Preferences > Sound, do you have software mixing (ESD) enabled? If you do, that may be causing some issues.

I have ESD turned off and everything set to use either ALSA or Autodetect in the sound preferences, and things work. (My sound card and driver support mixing in hardware, though, but ALSA should do it with software without ESD anyway if needed.)

---

### Post by cjax1 on 2006-12-06
Ok. Update. I feel kind of stupid. I seem to have it working.

Earlier when I double clicked on the volume control by the clock. I tried several changes. Like changing File>Change>Device. It gave me two options. One was _0_:HDA Intell (alsa mixer). Don't know if that was there before. Maybe because of what I downloaded before with the suggestion from the other thread. The other option was _1_:SigmaTel STAC9200 (OSS Mixer). That's my sound card. I had already tried both of those just before my post here. Didn't work.

I started thinking I used Kaffeine Player once last night. Believe me I was checking all the other players too. I opened Kaffeine and tried to change the volume. Actually I had to open a music file first, otherwise the volume control was grayed out. Like my hair now:) The volume in Kaffeine was all the way down and muted. After I changed those settings I was able to get sound on line. Afterwords I had to turn the volumes up in Realplayer playing NASA TV. I know they were all the way up before. Kaffeine must have overidden the sound settings. Nothing was turned down in the volume control or muted before. Also in the sound settings it does not matter what I set in File>Change>Device. It works on either setting now.

Well, I'm just glad I got it working. Thanks for your reply. Maybe I'll try to duplicate it now that I suspect Kaffeine.

Naw, better leave well enough alone.:) 

Thanks

---

### Post by mitchbones on 2006-12-06
> **Delkster said:**
> If you go to System > Preferences > Sound, do you have software mixing (ESD) enabled? If you do, that may be causing some issues.

I have ESD turned off and everything set to use either ALSA or Autodetect in the sound preferences, and things work. (My sound card and driver support mixing in hardware, though, but ALSA should do it with software without ESD anyway if needed.)

This worked for me, thanks! It was odd cause it felt like sometimes youtube would work, and others it wouldn't. What does ESD do anyways?

---

### Post by Delkster on 2006-12-06
> **mitchbones said:**
> What does ESD do anyways?

If multiple sound sources want to output some sound at the same time, the sounds need to be mixed together at some point. Nowadays this can be done on a lower level, either in the sound hardware (if the sound card and the driver support that) or by ALSA in software, but it used to be so (in the older system called OSS) that only one process (program) could reserve the sound system at a time. Sound daemons such as ESD could help with that: applications would use ESD as their sound output, and the daemon would mix the sounds and pass it on to the sound system.

However, as you may be already thinking, this also causes problems with programs that don't support ESD. If they try to use OSS directly for their sound output and ESD is already reserving it, the other applications fail.

ALSA can emulate OSS, so applications that only support OSS, not ALSA, can still work -- that's why you can also see two "devices" in the volume settings, one for the "ALSA device" and another for the "OSS device", although they're actually one and the same. However, it seems that there are still problems when ESD is running and some applications try to use OSS directly. Since nowadays the mixing can also be done on a lower level and that doesn't really even require application support like ESD does, it's better done that way.

ESD can still be useful because it provides network transparency (it would be possible to run an X session remotely over the network and have ESD stream the sound from the remote machine so that they'd be heard on the local machine), but in most situations there's no need for it anymore. However, as a practical note, I'm not sure if Gnome will play its desktop sound effects through anything but ESD, so if you disable it, you won't be hearing the desktop sounds anymore.

---

