---
title: "File manager - show audio &amp; video file duration"
date: 2015-09-11
forum: General Help
---

### Post by jw37 on 2015-09-11
[LEFT]Hi all,

does anyone know how to show duration (length) of media files in a column or preview widget in one of the most common file explorers? I can choose the "Duration" column to be visible in some file managers but the column stays totally empty for all files. I'd really like to see the duration with none or minimal effort - I don't like running avprobe or opening a properties dialog for every file just to see the duration.

My top favourites in file managers are:

Dolphin
Thunar
Konqueror
Double Commander
Nemo
Xfe
(and similar)

The desktop is Xfce, and Gtk & KDE services are widely used, so the platform probably isn't a prerequisite.

Any help highly appreciated. :) This is no-urgent issue, so kindly please prefer adept answers to fast ones, thank you very much.:D  Also feel free to inquire more details as needed.
[/LEFT]

---

### Post by SeijiSensei on 2015-09-11
I just opened Dolphin to a directory where Matroska video files are stored, right-clicked on the header when in list mode, and chose Audio > Duration.  I get a column that correctly reports 23:45 for the length of those videos.  

I'm using Kubuntu 14.04, not another flavor with KDE parts grafted on, so maybe the platform does matter?

---

### Post by jw37 on 2015-09-11
Well, that's interesting...:-k  Thanks for your kind answer.:cool:

Could some settings be the reason? I've now looked around the various settings but didn't find anything that could affect how media data is read from the files. Could my Xfce or KDE systems be missing some parts, plugins or extension or something? Any idea what that could be? :confused:

Edit. Distro updated.

Edit2. I tried some doplhin and konq plugins and even some kde extra packages but no success... :P   Sorry I can't post the package list here because it may well be that I'm waaay too st. One : D to perform such complex operations...:-\"  Now the weekend starts, and an audio stream on youtube is playing -- it's raining melodic progressive house... :-({|=  Nice and experienceful weekend for everyone!\\:D/

---

### Post by SeijiSensei on 2015-09-11
Kubuntu uses [phonon]("https://en.wikipedia.org/wiki/Phonon_%28software%29") as its multimedia backend.  Dolphin includes phonon as a dependency on my system ("dpkg -s dolphin").  Perhaps you don't have phonon installed?  As it is purely an "abstraction layer," you also need real codecs and such behind it.  The Kubuntu default (and I think the default for all of Ubuntu) is gstreamer.

That's why I don't really mix-and-match desktop environments, particularly one as complex as KDE.  I've used KDE for well over a decade now and have stuck with it on a wide variety of hardware.  I've used Kubuntu since 8.04 or so and see no reasons to switch.

---

### Post by jw37 on 2015-09-12
Thank you so much again for your very high-quality comments!:D  I feel I'm beginning to understand the real meaning of the variety of the deskotop environments. Thinking of this have reached almost biblical scale but let's look at the duration visibilty issue first.

> **SeijiSensei said:**
> Kubuntu uses [phonon]("https://en.wikipedia.org/wiki/Phonon_%28software%29") as its multimedia backend.  Dolphin includes phonon as a dependency on my system ("dpkg -s dolphin").  Perhaps you don't have phonon installed?  As it is purely an "abstraction layer," you also need real codecs and such behind it.  The Kubuntu default (and I think the default for all of Ubuntu) is gstreamer.

Phonon has been installed all the time but I have no idea if I have the "real codecs and such"...:| However, after these installations, the terminal panel in Dolphin got alive which is one awesome feature!:D  Also gstreamer checked...[-( I dare to entertain you guys later with some screenshots about the issue and installed packages.

>  That's why I don't really mix-and-match desktop environments, particularly one as complex as KDE.  I've used KDE for well over a decade now and have stuck with it on a wide variety of hardware.  I've used Kubuntu since 8.04 or so and see no reasons to switch.

Could you say that, in general, you only should install the one flavour of ubuntu with its default DE and not "cross-use" any parts of other DE-s? And this is the weakness of Xfce because there is not a network manager -- no easy internet connection for many users, like me -- if you don't install some Gtk services, let alone with proper AV editors (Kdenlive -> KDE Services, Audacity) and other necessary accesories such as Geany? And GIMP, I also found an interesting history detail:

"""GTK was developed solely for GIMP, initially. Towards the end of the 0.99 development cycle in 1998, GTK was split from being bundled with GIMP to being a separately available library. See [ancient history]("http://www.gimp.org/about/ancient_history.html") for some interesting tidbits from the GIMP perspective.""" [http://www.gimp.org/docs/userfaq.html#Gtk](http://www.gimp.org/docs/userfaq.html#Gtk)

Sorry for OT but do you guys think that, installing the latest stable Ubuntu Studio with it's default DE, is a good idea or would you choose the Ubuntu main flavour or some other?

---

### Post by jw37 on 2015-09-12
My apologies for any inconvenience caused by my expressions in comments. If you wonder, the point with Ubuntu Studio is JACK and if it's more reliable than the current, quite complex mixture of audio software.

Okay, this is still the situation:

[ATTACH=CONFIG]264374[/ATTACH]


I regard this as solved. Thanks.

---

