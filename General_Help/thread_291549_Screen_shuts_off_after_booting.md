---
title: "Screen shuts off after booting"
date: 2006-11-02
forum: General Help
---

### Post by dboot on 2006-11-02
I just installed nvidia drivers on my laptop so I can use Beryl. After upgrading nvidia-glx through my update manager, I rebooted my laptop to find that my screen turns off after Ubuntu loads. At first I thought my laptop shutdown, but then I heard the login screen audio. After typing in my username and password (still with my screen turned off), the desktop audio started.

Any ideas?? Thanks!

---

### Post by chriscando on 2006-11-02
If you can boot to a terminal I would try to install different nvidia drivers, either ones off of their website or the ones you previously had.

OR

Actually before you do that see if you can edit your /etc/X11/xorg.conf file and change the resolution listed under Section "Screen" because it sounds like the resolution you have set is out of your range.

here is what mine looks like:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
```

---

### Post by dboot on 2006-11-02
Thanks, I panicked for a bit until I realized I could get to the command line by ctrl+alt+F2. I replaced my current xorg.conf file with my original and my screens were recognized again. 

I'm not sure if installing nvidia-glx stopped me from seeing my screen but it might have changed my xorg.conf file to something that doesn't work.

Thanks for the suggestion!

---

