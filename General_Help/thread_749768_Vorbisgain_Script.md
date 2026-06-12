---
title: "Vorbisgain Script"
date: 2008-04-08
forum: General Help
---

### Post by AustinMatherne on 2008-04-08
I'm pretty sure this is possible.

I would like to create a shortcut on the panel that would automatically run a command that would run vorbisgain on all ogg files in my /home/MusicBrainz/ folder.

If anyone knows how to do this, or at lest a script that I could run manually, I would greatly appreciate the enlightenment.

Thank you,
~ Austin

---

### Post by logos34 on 2008-04-10
try creating a bash script.  Like:

> #!/bin/sh
vorbisgain -a -f -s /home/MusicBrainz/*.ogg

(See **man vorbisgain** for more options) 

Name it "run-vorbisgain", for example.

sudo chmod +x run-vorbisgain

sudo mv run-vorbisgain /usr/local/bin

Make a launcher-->Preferences/main menu

Or manually:

sudo gedit /usr/share/applications/vorbisgain.desktop
> 
[Desktop Entry]
Name=run-vorbisgain 
Comment=run vorbisgain on music files
Exec=/usr/local/bin/run-vorbisgain 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;Sound & Video;

---

### Post by AustinMatherne on 2008-04-26
Thank you,
This has worked perfectly for me in the past couple of weeks... But would it be possible to get it to work recursively in every sub folder in "/home/MusicBrainz/"?

For instance, "/home/MusicBrainz/%artist/%album/%0num - %track.ogg

%artist stands for the artists name.
%album stands for the albums name.
%0num stands for the tracks number, padded by zero.
%track stands for the tracks name.


Thanks again,
~ Austin

---

### Post by AustinMatherne on 2008-05-01
Anyone know?

Thanks,
~ Austin

Edit:
vorbisgain -a **-r** -s /home/MusicBrainz/*.ogg

The above works like a charm.

Thanks again,
~ Austin

---

