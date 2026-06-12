---
title: "How to install Elisa music player on Kubuntu 19.04"
date: 2019-05-06
forum: General Help
---

### Post by geovino on 2019-05-06
How to install Elisa music player on Kubuntu 19.04?

Since its a KDE app it should be available. Tried to install Flatpak but it does not find it. Any clues?

---

### Post by Xian on 2019-05-07
What errors (if any) do you get with these commands?

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.kde.elisa
```

---

### Post by geovino on 2019-05-08
Have reinstalled Kubuntu 19.04. So I won't get a accrurate reading. I'll try to install Elisa again.

---

### Post by geovino on 2019-05-08
I get this...
> davek@G580:~$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
davek@G580:~$ 



---

### Post by SeijiSensei on 2019-05-08
There are pretty detailed instructions on what's needed to build this from source, including the dependencies that are required.

[https://community.kde.org/Elisa](https://community.kde.org/Elisa)

---

### Post by Xian on 2019-05-08
> **geovino said:**
> I get this...
[COLOR=#000000]*davek@G580:~$ flatpak remote-add --if-not-exists flathub *[/COLOR][https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
[COLOR=#000000]*davek@G580:~$ *[/COLOR]


This is the expected result. What about the next command? 

```
[COLOR=#000000][FONT=&amp]flatpak install flathub org.kde.elisa[/FONT][/COLOR]
```

---

### Post by geovino on 2019-05-09
> davek@G580:~$ flatpak install flathub org.kde.elisa
Looking for matches&#8230;
Required runtime for org.kde.elisa/x86_64/stable (runtime/org.kde.Platform/x86_64/5.12) found in remote flathub
Do you want to install it? [Y/n]: 

org.kde.elisa permissions:
    ipc      pulseaudio           wayland              x11
    dri      file access [1]      dbus access [2]      bus ownership [3]

    [1] host:ro, xdg-config/kdeglobals:ro, xdg-run/dconf, ~/.config/dconf:ro
    [2] com.canonical.AppMenu.Registrar, org.kde.baloo
    [3] org.mpris.MediaPlayer2.elisa


        ID                                    Arch   Branch Remote  Download
 1. [&#10003;] org.kde.Platform                      x86_64 5.12   flathub 409.6*MB / 425.0*MB
 2. [&#10003;] org.freedesktop.Platform.VAAPI.Intel  x86_64 18.08  flathub   1.8*MB / 1.8*MB
 3. [&#10003;] org.freedesktop.Platform.html5-codecs x86_64 18.08  flathub   2.8*MB / 2.9*MB
 4. [&#10003;] org.kde.KStyle.Adwaita                x86_64 5.12   flathub   4.7*MB / 4.7*MB
 5. [&#10003;] org.kde.Platform.Locale               x86_64 5.12   flathub  17.3*kB / 333.9*MB
 6. [&#10003;] org.kde.elisa                         x86_64 stable flathub   3.3*MB / 3.3*MB
 7. [&#10003;] org.kde.elisa.Locale                  x86_64 stable flathub   3.6*kB / 606.5*kB

Installation complete.
davek@G580:~$ 


installed. thanks

---

