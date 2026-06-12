---
title: "Issues trying to install Blender"
date: 2008-03-26
forum: General Help
---

### Post by LoRD_TRiFLe on 2008-03-26
Hey everyone.  I'm having trouble installing blender and was hoping someone could help me.  I'm running 7.10 (32 bit version, even though I have a 64 bit CPU - I couldn't get 64 bit version to install, but that's a whole other issue).

No matter how I go about trying to install blender (synaptic, terminal, etc.) I always get this error:

The following packages have unmet dependencies:
  blender: Depends: libavcodec0d (>= 0.cvs20060823) but it is not installable
           Depends: libavformat0d (>= 0.cvs20060823) but it is not installable
E: Broken packages


Any ideas?  I've searched and can't seem to find anyone else having the same issue (though I apologize if I overlooked it).  Thanks for the help!

---

### Post by LoRD_TRiFLe on 2008-03-28
Sorry to bump this up, but I'd love to get this working.  Let me know if you have any suggestions!

---

### Post by FluffyElmo on 2008-03-28
It installs for me here, make sure that you have all the repositories are enabled, then update and try installing again. Open your sources.list and remove any comments (# characters) in front of repositories, or you could do it in Synaptic.
```

sudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get install blender
```

I also have the medibuntu  repository added, so if the above doesn't work you may want to add that. Shouldn't be necessary though. 
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")

---

### Post by LoRD_TRiFLe on 2008-03-28
I've tried that before, but tried it again and still no go.  Any other suggestions?

---

