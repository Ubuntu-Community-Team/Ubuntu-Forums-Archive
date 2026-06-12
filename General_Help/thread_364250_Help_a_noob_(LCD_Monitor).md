---
title: "Help a noob (LCD Monitor)"
date: 2007-02-18
forum: General Help
---

### Post by scottish144 on 2007-02-18
So I've been using Ubuntu 6.06 for a few months now on my notebook, and recently bought a new monitor with a DVI input.  I successfully hooked it up in windows, so I know the hardwares compatable, but ubuntu won't atuomatically detect it, and as I'm still in transition from Windows to Ubunutu (cept for gaming) I have no clue as to how to configure it/set it up.

Hardware Specs:
Laptop: Acer Travelmate 8204WLMi
GPU: ATI Mobility Radeon X1600 256 MB Discrete (has both VGA and DVI outputs)
Monitor: NEC MultiSync 90 GX2, Native Resolution 1280x1204

Thx in advance.

---

### Post by mojoman on 2007-02-18
I think you need to edit your xorg.conf (located in etc/X11/xorg.conf) which is the file where you configure your monitor, graphic card, mouse, keyboard, i.e. most of the stuff related to the X-server system (which is your graphic environment). 

I suppose you want to use the LCD screen instead of the built-in screen, right? Or do you want to run them as a dual monitor setup?

You could try this. Make a back-up of you xorg.conf (yes, this is vital, believe me, I know it the hard way...) and the auto-generate a new xorg.conf with your new LCD monitor connected and powered up.
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X-server by hitting ctrl+alt+backspace or by rebooting the machine. Hopefully, you should have the new LCD running. If not, restore the backup (if you don't know how to restore your xorg.conf backup in console mode it might be a good idea to find before you try this). 

Anyway, if it works (and it should work though I understand if my use of words such as 'hopefully' might put you off the idea ;)  ) you can compare the new xorg and the backup in order to learn what changes you needed to do. Also, you can merge the xorg-files and keep one setting commented out with # in order to be able to switch settings in the future without having to auto-generate a new xorg. Get back to me if you want some tips on this.

Hope this helps.
/Mojoman

---

