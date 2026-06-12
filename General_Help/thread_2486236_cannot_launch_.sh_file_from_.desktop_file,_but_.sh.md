---
title: "cannot launch .sh file from .desktop file, but .sh launches okay from the terminal"
date: 2023-04-23
forum: General Help
---

### Post by salamilimos on 2023-04-23
I'm running Xubuntu 22.04.

I've installed mycroft-mimic3-tts with this command:

```
pip3 install --upgrade mycroft-mimic3-tts
```

And I've installed xsel to generate a text file whenever I copy and paste stuff to my clipboard so it can be read aloud by mimic3-tts:


```
sudo apt-get --no-install-recommends install xsel
```
Here's my shell script so that mycroft-mimic3-tts can read my clipboard aloud:


```
#!/bin/bash

xsel -b >> /home/salamilimos/.local/share/mycroft/clipboard.txt

/home/salamilimos/.local/bin/mimic3 --voice 'en_US/ljspeech_low' < /home/salamilimos/.local/share/mycroft/clipboard.txt --play-program "/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=mpv --file-forwarding io.mpv.Mpv --geometry=352x240-0-0 --lavfi-complex='[aid1]asplit[ao][a1];[a1]showwaves=mode=cline:colors=02d1d2:rate=25,format=rgb0 [vo]' --on-all-workspaces --no-border --ontop --player-operation-mode=pseudo-gui -- @@u %U @@"

rm /home/salamilimos/.local/share/mycroft/clipboard.txt
```

It runs when I run it through the Terminal:


```
~$ /home/salamilimos/.local/bin/read-clipboard-aloud.sh
```

But when I put it in a .desktop file like this, it doesn't run at all:


```
[Desktop Entry]
Version=1.1
Type=Application
Name=Read Clipboard Aloud
Comment=
Icon=/home/salamilimos/.icons/play.png
Exec=bash -c "/home/salamilimos/.local/bin/read-clipboard-aloud.sh"
Categories=
Path=
Terminal=
StartupNotify=
```

But when I specify "Terminal=Yes", my bash script runs, however, a Terminal window pops up next to the mpv window though. Is there a way to fix my bash script where the Terminal window doesn't pop up at all?

Thanks.

---

### Post by ActionParsnip on 2023-04-24
Try
```

chmod +x /home/salamilimos/.local/bin/read-clipboard-aloud.sh

```
also do the same with your launcher file

You have the shebang in your script so you don't need the "bash -c" part, marking the script as executable removes the need for that part

Should help

---

### Post by salamilimos on 2023-04-24
Doesn't work, I still need to add Terminal=Yes in order for my bash script to run.  What I'm trying to accomplish here is to remove the terminal from appearing alongside the mpv video window.

---

### Post by yancek on 2023-04-24
Have you tried "Terminal=false" rather than true or leaving it blank?  Same result?
Have you tried without the double quotes in the Desktop file exec line?  This is what I have with a Desktop file that executes with no terminal pop up.  I'm not using Xubuntu but Ubuntu so I'm not sure this will work.

---

### Post by salamilimos on 2023-04-24
Good news, managed to figure out how to fix my issue:

```
#!/bin/bash

xsel -b >> /home/salamilimos/.local/share/mycroft/clipboard.txt

/home/salamilimos/.local/bin/mimic3 --voice 'en_US/ljspeech_low' < /home/salamilimos/.local/bin/mimic3 --voice 'en_US/ljspeech_low' < /home/salamilimos/.local/share/mycroft/clipboard.txt >> /home/salamilimos/.local/share/mycroft/clipboard.wav

flatpak run io.mpv.Mpv --geometry=352x240-0-0 --lavfi-complex='[aid1]asplit[ao][a1];[a1]showwaves=mode=cline:colors=02d1d2:rate=25,format=rgb0 [vo]' --on-all-workspaces --no-border --ontop --player-operation-mode=pseudo-gui /home/salamilimos/.local/share/mycroft/clipboard.wav

rm /home/salamilimos/.local/share/mycroft/clipboard.txt

rm /home/salamilimos/.local/share/mycroft/clipboard.wav
```

No more terminal window popping out alongside mpv.

---

