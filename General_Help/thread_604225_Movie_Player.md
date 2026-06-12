---
title: "Movie Player"
date: 2007-11-05
forum: General Help
---

### Post by ploik on 2007-11-05
Hi, i've downloaded .mkv videos and theyve worked already, but the last one i downloaded and tried to play, asked if i wanted to look for a compatible codec, so i thought it had an extra audio file or  whatever, so i downloaded the extra codec, and now all my videos play in black and white, even the old ones that used to work. Please help me, is there a way to undo recent installations, or see the most recent ones and uninstall them? It is really annoying and i cant stand to watch videos in black and white. If it helps, the codec was a gstreamer one, not sure which one though.
thanks in advance for all your help. 
Ploik

---

### Post by kshane on 2007-11-05
> **ploik said:**
> Hi, i've downloaded .mkv videos and theyve worked already, but the last one i downloaded and tried to play, asked if i wanted to look for a compatible codec, so i thought it had an extra audio file or  whatever, so i downloaded the extra codec, and now all my videos play in black and white, even the old ones that used to work. Please help me, is there a way to undo recent installations, or see the most recent ones and uninstall them? It is really annoying and i cant stand to watch videos in black and white. If it helps, the codec was a gstreamer one, not sure which one though.
thanks in advance for all your help. 
Ploik

Sounds like the best thing for you to do is to go into Synaptic and and find that codec and remove it or reinstall the others.

---

### Post by ploik on 2007-11-05
i dont know exactly which one it was, so if i reinstall some or most of them, could it help?

---

### Post by mpierce on 2007-11-05
What player are you using?

You can always remove a package you just installed using the command:
   sudo dpkg -P <package name w/o extension>

If you are using mplayer to play your movies. All the codecs you need are in the w32codecs codecs packages. 
   sudo apt-cache search w32codecs
   sudo apt-get install w32codecs

You may need to enable the universe repo in your sources.list e.g.
# Ubuntu supported packages
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy main restricted universe multiverse                                                                               deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy-updates main restricted universe multiverse                                                                       deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy-security main restricted universe multiverse                                                                                                                                                      deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy main restricted universe multiverse                                                                           deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy-updates main restricted universe multiverse                                                                   
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy-security main restricted universe multiverse

Hope this helps...

---

### Post by Maestro23 on 2007-11-05
> **ploik said:**
> i dont know exactly which one it was, so if i reinstall some or most of them, could it help?

You can:

1. Go into your movie player and check the settings (color, contrast, etc...) see if that helps.

2. Go into Synpatic, search for your player and its codecs.  Delete the codecs and re-install.

For Future reference:

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29)

---

### Post by ploik on 2007-11-05
OK, i think i figured this out, but i wanna ask you guys so i dont mess up my computer again. So far, i went into movie player preferences, and uppped the saturation, so the color came back, but now the same .mkv file wont play, and it needs a codec... the same one i downloaded. that codec is th gstreamer plugin for aac, xvid, faad  popularity 1 star. i didnt uninstall anything previously, so why is it asking to install the same codec, and should i, or does anyone know why it isnt playing in the first place. Thank you guys for your help again, your all a HUGE help.
Ploik

---

