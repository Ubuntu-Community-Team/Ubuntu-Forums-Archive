---
title: "Icons get &quot;maxed out&quot; in panels"
date: 2008-03-14
forum: General Help
---

### Post by jakupl on 2008-03-14
every once in a while, the icons on the panels get werd and impossible to read. 

Here is a screenshot



[IMG]http://i228.photobucket.com/albums/ee289/jakupl/Screenshot-1.jpg[/IMG].

---

### Post by jakupl on 2008-03-28
bump

---

### Post by forrestcupp on 2008-03-28
Did you try removing that applet and putting it back on there?

---

### Post by BDNiner on 2008-03-28
When that happens i remove the applet and put it back. it is kinda annoying sometimes but it hasn't happened in a while on my computer. How did you get utorrent to run. I use deluge now but i miss utorrent.

---

### Post by jakupl on 2008-03-28
well when they max , I remove it at put it back, that is a fine temporary solution.... but it happens completely randomly and gets quite irritating. I was looking for a temporary solution??
[QUOTE="BDNiner"]
How did you get utorrent to run. I use deluge now but i miss utorrent.[/QUOTE]

[_[color=cyan]I think it was on wine[/color]_]("http://www.howtoubuntu.com/2007/10/21/how-to-install-utorrent-in-ubuntu-with-wine.html") ;) I have reinstalled ubuntu since then... still have the same problem though. Now I use ktorrent... It's ok.

---

### Post by jakupl on 2008-03-28
btw. I did not have this problem when I reinstalled ubuntu... _Until I installed skype_... (hint hint),

that's maybe a clue... I dont know?

---

### Post by erginemr on 2008-03-28
This happens with or without Compiz?

---

### Post by jakupl on 2008-03-28
well i have it on "no effects"

---

### Post by jakupl on 2008-04-04
'bump' :guitar: getting really annoying and a huge turnoff when looking at the desktop :mad:

---

### Post by jakupl on 2008-04-04
this is how it looks right now.

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/Untitled.jpg[/IMG]

---

### Post by erginemr on 2008-04-04
I think we should turn our attention to the graphics card and its driver. So:

1- What brand and model is your graphics card?

2- What is the output of the following command from the terminal?
```
lspci | grep -i vga
```

3- What says in Section "Device" in your /etc/X11/xorg.conf file? Please post the contents of this file:
```
gedit /etc/X11/xorg.conf
```

4- Do you keep experiencing the problem without Skype running in the foreground/background?

---

### Post by jakupl on 2008-04-05
Hi :) sorry it took so long.

2. 
```
jakup@bobby:~$ lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
```

3.
```
Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection
```

4. Yes. always.:confused:

1. 
[QUOTE="erginemr"]What brand and model is your graphics card?[/QUOTE]

hehe :) how do I actually see that ? :oops:\\:D/

---

### Post by erginemr on 2008-04-05
Your graphics card is ATI Radeon Xpress 200M.

OK. I want you to do an experiment with your system. We shall first try to reconfigure your desktop settings. And if it doesn't work, we shall temporarily replace your binary "fglrx" driver with the open source "ati" driver to pinpoint the source of the problem, and check whether the icons on the panels are still distorted or not.

------------------------------------------------------------------
FIRST TRY: RECONFIGURING YOUR X SERVER:
------------------------------------------------------------------
1. First disable Compiz. Right click on your desktop -> Change background -> Effects -> None.

2. Logout and back in to check if it is disabled consistently between sessions.

3. Now, change to a virtual terminal with Ctrl+Alt+F1 (till F6). Your desktop is in Ctrl+Alt+F7 by the way.

4. Login with your user name and password, and kill the Gnome session with this command:
```
sudo /etc/init.d/gdm stop
```

5. Now take a backup of your current /etc/X11/xorg.conf file, which keeps all important settings for your X server (i.e. graphical desktop). This step is crucial:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

6. Reconfigure your X config file with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This comand will reconfigure your X server automatically. 

7. Restart your X server with:
```
startx
```

8. If the desktop you are greeted with is not optimal, or worse, if you cannot reach the desktop at all, then restore your previous backup with:
```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```
and restart the X server with:
```
startx
```

---

### Post by jakupl on 2008-04-05
cool :popcorn: gonna grab a smoke before I begin. ;)

---

### Post by erginemr on 2008-04-05
--------------------------------------------------------------------
SECOND TRY: RECONFIGURING YOUR X SERVER:
--------------------------------------------------------------------

We shall try replacing "fglrx" (binary ATI driver) with "ati" (open source ATI driver) and check if the icon problem persists:

1. Pass to another virtual terminal and stop the X server as I have explained above.

2. Edit the file xorg.conf with:
```
sudo nano -w /etc/X11/xorg.conf
```

3. Find the line under Section "Device" with:
```
Driver "fglrx"
```
and change it to 
```
Driver "ati"
```

4. Save the file with Ctrl+O and exit the nano editor with Ctrl+X. 

5. Restart your desktop with "startx", use it for a while for the presence of the icons problem.

6. If it persists, then this is not a ATI driver issue. You may restore your origina file with:
```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```
and then, enable Compiz again.

Good Luck on the text screen. ;)

---

### Post by erginemr on 2008-04-05
**Well, if you are still with me, forget about all I have said before!! I'll explain in a moment.**

---

### Post by erginemr on 2008-04-05
Although it was completely reversible, I am very sorry to have mis-directed you. Stupid me... :oops:

Contemplating over your problem now in depth, I am sure that it has nothing to do with your graphics driver. For God's sake, how could it be? With everything working flawlessly, your desktop, desktop icons, menus, videos (I guess) with or without Compiz...

The only thing that doesn't work right is the gnome-applet icons on your gnome bars. So, there should be something wrong with the **gnome-applets**, not with the graphics driver.

Skype may have broken something important for **gnome-applets** package, I don't know. But I am beginning to believe that you should try uninstalling and reinstalling gnome-applets.

---

### Post by erginemr on 2008-04-05
The following command from the terminal (i.e. Gnome terminal, no need to pass on to the real terminal any more):
```
 sudo aptitude remove gnome-applets
```
will remove that package along with a meta-package (i.e. an empty pointer to other packages) **ubuntu-desktop**  with it.

Now, you should reinstall the same with:
```
 sudo aptitude install gnome-applets
```
and
```
 sudo aptitude install ubuntu-desktop
```

I am not sure whether such a cheap trick will solve your problem, but is worth a try...

---

### Post by jakupl on 2008-04-05
I managed to get through nr. 1. but it was pretty ugly :D so I cp mybackup to xorg.conf again :) 
> Skype may have broken something important for gnome-applets package, I don't know. But I am beginning to believe that you should try uninstalling and reinstalling gnome-applets.

yeah. I tried to take notice when I reinstalled ubuntu some time ago. I had this problem on my first install, but when I reinstalled, the problem didn't come until I installed skype, so it's probably skype's fault.

---

### Post by jakupl on 2008-04-05
No luck. :( still the same problem. Many thanks for the great help though

---

### Post by erginemr on 2008-04-05
My pleasure. 

It is really hard to find out, but may I suggest you to remove Skype temporarily and use it for a while? If it goes away, then we can conclude that Skype is the culprit and may search for another Skype version, which will not conflict with Gnome applets.

---

### Post by jakupl on 2008-04-05
when I installed skype, this is what was put on the computer according to the terminal.

packages:

libqt4-gui
libqt4-core
libaudio2

Included files:

./
usr/
usr/share/
usr/share/pixmaps/
usr/share/pixmaps/skype.png
usr/share/doc/
usr/share/doc/skype/
usr/share/doc/skype/README
usr/share/doc/skype/changelog.Debian.gz
usr/share/doc/skype/copyright
usr/share/icons/
usr/share/icons/skype.png
usr/share/skype/
usr/share/skype/lang/
usr/share/skype/lang/skype_et.ts
usr/share/skype/lang/skype_pt_br.qm
usr/share/skype/lang/skype_lv.ts
usr/share/skype/lang/skype_zh_s.ts
usr/share/skype/lang/skype_zh_t.ts
usr/share/skype/lang/skype_fr.ts
usr/share/skype/lang/skype_it.qm
usr/share/skype/lang/skype_bg.ts
usr/share/skype/lang/skype_ro.qm
usr/share/skype/lang/skype_tr.qm
usr/share/skype/lang/skype_zh_s.qm
usr/share/skype/lang/skype_pt_pt.ts
usr/share/skype/lang/skype_fr.qm
usr/share/skype/lang/skype_tr.ts
usr/share/skype/lang/skype_ru.qm
usr/share/skype/lang/skype_de.qm
usr/share/skype/lang/skype_de.ts
usr/share/skype/lang/skype_ko.qm
usr/share/skype/lang/skype_zh_t.qm
usr/share/skype/lang/skype_it.ts
usr/share/skype/lang/skype_es.ts
usr/share/skype/lang/skype_lt.ts
usr/share/skype/lang/skype_pl.qm
usr/share/skype/lang/skype_en.qm
usr/share/skype/lang/skype_pl.ts
usr/share/skype/lang/skype_lv.qm
usr/share/skype/lang/skype_es.qm
usr/share/skype/lang/skype_et.qm
usr/share/skype/lang/skype_pt_br.ts
usr/share/skype/lang/skype_en.ts
usr/share/skype/lang/skype_ko.ts
usr/share/skype/lang/skype_th.ts
usr/share/skype/lang/skype_ro.ts
usr/share/skype/lang/skype_th.qm
usr/share/skype/lang/skype_ja.ts
usr/share/skype/lang/skype_bg.qm
usr/share/skype/lang/skype_lt.qm
usr/share/skype/lang/skype_ja.qm
usr/share/skype/lang/skype_pt_pt.qm
usr/share/skype/lang/skype_ru.ts
usr/share/skype/sounds/
usr/share/skype/sounds/CallResume.wav
usr/share/skype/sounds/CallRingingOut.wav
usr/share/skype/sounds/SkypeLogout.wav
usr/share/skype/sounds/CallConnecting.wav
usr/share/skype/sounds/CallHangup.wav
usr/share/skype/sounds/CallBusy.wav
usr/share/skype/sounds/ContactAdded.wav
usr/share/skype/sounds/ContactOnline.wav
usr/share/skype/sounds/CallRingingIn.wav
usr/share/skype/sounds/CallRemoteHangup.wav
usr/share/skype/sounds/VoicemailReceived.wav
usr/share/skype/sounds/ChatOutgoing.wav
usr/share/skype/sounds/ChatIncomingInitial.wav
usr/share/skype/sounds/ContactOffline.wav
usr/share/skype/sounds/ContactAuthRequest.wav
usr/share/skype/sounds/ChatIncoming.wav
usr/share/skype/sounds/CallFailed.wav
usr/share/skype/sounds/TransferFailed.wav
usr/share/skype/sounds/CallHold.wav
usr/share/skype/sounds/SkypeLogin.wav
usr/share/skype/sounds/TransferRequest.wav
usr/share/skype/sounds/TransferComplete.wav
usr/share/skype/avatars/
usr/share/skype/avatars/Empire Skype.png
usr/share/skype/avatars/Behind Skype.png
usr/share/skype/avatars/Skype Brrr... .png
usr/share/skype/avatars/Ninja Skype.png
usr/share/skype/avatars/Skype Cola.png
usr/share/skype/avatars/Skype-ahoy.png
usr/share/skype/avatars/Skype Candy.png
usr/share/skype/avatars/Designer Skype.png
usr/share/skype/avatars/Skype Time.png
usr/share/skype/avatars/Travel Skype.png
usr/share/skype/avatars/Make Skype Not War.png
usr/share/skype/avatars/Skype 502.png
usr/share/skype/avatars/Skype in a Bag.png
usr/share/skype/avatars/Architect Skype.png
usr/share/skype/avatars/Skype Safety.png
usr/share/skype/avatars/DJ Skype.png
usr/share/skype/avatars/Fax Skype.png
usr/share/skype/avatars/Devil Skype.png
usr/share/skype/avatars/Hula Skype.png
usr/share/skype/avatars/Sushi Skype.png
usr/share/skype/avatars/Skype Goaaaaal.png
usr/share/skype/avatars/Skype Cool Shades.png
usr/share/skype/avatars/Skypahontas.png
usr/share/skype/avatars/Skype Beauty.png
usr/share/skype/avatars/Rice Skype.png
usr/share/skype/avatars/Skype-in-one.png
usr/share/skype/avatars/Carnaval Skype.png
usr/share/skype/avatars/Skypers of the Caribbean.png
usr/share/skype/avatars/Star Skype.png
usr/share/skype/avatars/Angel Skype.png
usr/share/skype/avatars/Pop Skype.png
usr/share/skype/avatars/Skype Boarder.png
usr/share/skype/avatars/Chic Skype.png
usr/share/skype/avatars/College Skype.png
usr/share/skype/avatars/Call Me.png
usr/share/skype/avatars/Earbud Skype.png
usr/share/skype/avatars/Beach Skype.png
usr/share/skype/avatars/Business Skype.png
usr/share/skype/avatars/DIY Skype.png
usr/share/skype/avatars/Skype Headset.png
usr/share/skype/avatars/Skype Artiste.png
usr/share/skype/avatars/Metal Skype.png
usr/share/skype/avatars/Skype Extreme.png
usr/share/skype/avatars/Skype Jyve.png
usr/share/skype/avatars/Call Me Sweetheart.png
usr/share/skype/avatars/Skype.png
usr/share/skype/avatars/Skype Bling.png
usr/share/skype/avatars/Skype-a-Manger.png
usr/share/skype/avatars/The Skypeness.png
usr/share/skype/avatars/Yin Yang Skype.png
usr/share/skype/avatars/Wetsuit Skype.png
usr/share/skype/avatars/Skype Jah.png
usr/share/skype/avatars/Desert Skype.png
usr/share/skype/avatars/Party Skype.png
usr/share/skype/avatars/Skype San.png
usr/share/skype/avatars/Skype Aid.png
usr/share/skype/avatars/Skype Smiley.png
usr/share/skype/avatars/Geisha Skype.png
usr/share/skype/avatars/Christmas Skype.png
usr/share/skype/avatars/Skype Shorty.png
usr/share/applications/
usr/share/applications/skype.desktop
usr/bin/
usr/bin/skype
etc/
etc/dbus-1/
etc/dbus-1/system.d/
etc/dbus-1/system.d/skype.conf

where would the sinner be?

---

### Post by jakupl on 2008-04-05
Dont ask me why I saved it... I probably felt that I would need it :lolflag:

---

### Post by erginemr on 2008-04-05
:lolflag:

Well, looking at the file list, Skype seemed pretty innocent to me. I have also googled for your problem, but no joy either. So, I guess it is time to do the head bang: :guitar:

No no, not that one! This one: ](*,)

---

### Post by jakupl on 2008-04-05
yeah.. I think i'll just wait and see if Hardy makes a difference. thanks :popcorn:

---

