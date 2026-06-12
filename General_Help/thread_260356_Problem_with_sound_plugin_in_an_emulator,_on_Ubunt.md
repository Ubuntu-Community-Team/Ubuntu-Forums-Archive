---
title: "Problem with sound plugin in an emulator, on Ubuntu"
date: 2006-09-18
forum: General Help
---

### Post by muffinhead on 2006-09-18
I know this is a forum for Ubuntu, and this problem sort of relates to Ubuntu. I'm trying to use the N64 Emulator Mupen64 for Linux, and am having a couple of problems.

It was all working fine before I installed/Uninstalled something, and I have no clue as to what I did. The Only new thing I installed is XGL, and I Uninstalled that today because it was giving me graphics problems with Rice's Video Plugin on Mupen64.

However My Problem is, I get No sound using the Default Mupen64 Audio plugin. The sound however works fine using other Plugins, or other emulators. System Sounds and Log Off/Log On Sounds work fine as well. I have absolutely no problems with sound except when using this emulator with that specific plugin.

When running Mupen64 as root, I get the following output in the terminal:

```
 "Error opening /dev/dsp"

"Error Resetting Sound Card"

"Error Setting Fragment Size",

"Error Setting Stereo Mode",

"Error Initializing Format", 

 and lastly, 

"Error Initializing Frequency: 32000"
```

I think the problem lies in, that I may of accidently Uninstalled a dependencie, that the plugin depended on or messed something up in the process.

Hopefully someone will know what I'm talking about, or has encountered something similar, and has solved it.

I would appreciate it if someone could help me, Thank You:)

Btw, the reason I uninstalled Xgl, was that it gave me texture problems with Rice's Video Plugin, and Caused white and grey textures without any color. After I uninstalled Xgl, I did not encounter that problem again.

---

### Post by muffinhead on 2006-09-18
Sorry to bump this thread back up so quickly, but can someone please help me.

The last thing I ever want to do is do a reformat/reinstallation of Ubuntu, after spending time getting things set up on it once again.

I would really appreciate someones help, or a solution to what I just described, and the error I posted.

I've spent time searching google, other forums, to see if there was a solution before I posted here.

I apologize for double posting, and bumping my thread back up so quickly, I'm just not sure what to do.

Thank You if anyone can help me solve my problem :wink:

---

### Post by muffinhead on 2006-09-19
Bump!

---

### Post by po0f on 2006-09-19
Does /dev/dsp exist?  I have only tried using Mupen64 once, and I believe I used some ALSA plugin to get sound.  Is there any reason you're trying to get the default one to work?

---

### Post by muffinhead on 2006-09-19
Yes /dev/dsp exists, I've already checked that. 

There is only no sound in the emulator with that paticular plugin, which I wasn't having any problems with before.

I know it's not a problem with the emulator, as it was working before with that plugin, and I have also tried downloading mupen64 again to make sure, it wasn't a problem with the emulator.

Yes there is a reason I want to use this plugin, Is because the Sound is much better. with jttl's SDL plugin the sound seems scratchy, sorta like when you grind your fingernails on a chalkboard. But the default plugin worked great and flawlessly, before I started having sound problems, with that paticular plugin.

I'm sorry for triple posting. I'd really hate to reformat or reinstall ubuntu, because I spent a great deal of time downloading/installing ubuntu freeware apps.

I'd appreciate it if anyone has a solution, and can help me. Thank You:)

---

### Post by muffinhead on 2006-09-19
Nevermind, I solved my problem. I had to reinstall Alsa-OSS from the repository. I must of accidentally uninstalled it along with something else. All is working fine again:)

However That still doesn't explain why my Graphics were all messed up in Mupen64 with Rice's video Plugin, after installing Xgl????:confused:

Anyway's I uninstalled Xgl till I can figure out why it was doing what it was doing with Mupen64, as well as Xgl causing epsxe to crash when starting a game.

---

### Post by muffinhead on 2006-09-21
Bumping this thread!!!

Please answer or help me with my last question Thank You;)

[quote=muffinhead]However That still doesn't explain why my Graphics were all messed up in Mupen64 with Rice's video Plugin, after installing Xgl????[/quote]

---

