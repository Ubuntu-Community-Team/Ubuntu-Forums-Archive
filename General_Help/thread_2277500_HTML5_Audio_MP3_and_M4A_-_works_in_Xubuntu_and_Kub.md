---
title: "HTML5 Audio MP3 and M4A - works in Xubuntu and Kubuntu - fails in other variants"
date: 2015-05-09
forum: General Help
---

### Post by Robert_Carroll on 2015-05-09
[IMG]https://lh5.googleusercontent.com/-Tnmp4aP4b8Y/VU-zl32qoRI/AAAAAAAAD8E/5xKo0cbscgU/w316-h117-no/html5test.png[/IMG]

I have a hobby radio jukebox web site. It does not use Flash but does rely on HTML5 audio compatibility. It works in Chrome/Chromium on any platform. It works on all major web browsers in Windows except Opera. It works in Xubuntu Firefox and Kubuntu Firefox. It fails in Firefox for Ubuntu, Ubuntu-Mate, Ubuntu-Gnome and Lubuntu.

[http://www.gooplusplus.com/jukebox](http://www.gooplusplus.com/jukebox)

I am trying to find out why it works great in Xubuntu and Kubuntu but not in the other Ubuntu variants.

I checked the audio section of [https://html5test.com/](https://html5test.com/) and discovered that MP3 and AAC (M4A) codecs are turned on in Xubuntu and Kubuntu but not in other variants.

I checked [http://hpr.dogphilosophy.net/test/](http://hpr.dogphilosophy.net/test/) to verify (playing the audio MP3, WAV, OGG, and WEBA links) the HTML5 audio compatibility.

I checked to see any obvious related difference between Xubuntu (works) and Ubuntu-Mate (fails) from the INSTALLED column in the Ubuntu Software Center.

I noted that codec "extras" are not installed by default in any Ubuntu variant so that is not the source of the HTML5 audio failure.

I would like to able to suggest improvement to HTML5 audio support in the variants that fail plus derivatives like Linux Lite that also fail the HTML5 audio test.

Who can tell me why some (Xubuntu and Kubuntu) Ubuntu-based distros support Firefox HTML5 MP3 streaming but most do not?

 [IMG]https://lh6.googleusercontent.com/-xKe1Hwwmy9M/VU4DO9C6OfI/AAAAAAAAD7o/Bc07Vj7TaZA/w446-h493-no/html5-audio.png[/IMG]

---

### Post by Robert_Carroll on 2015-05-09
SOLVED:


using SYNAPTIC, add **gstreamer1.0-plugins-ugly**


or from Ubuntu Software Center, add **Gstreamer extra plugins**

---

### Post by Robert_Carroll on 2015-05-09
[SIZE=3][COLOR=#000000][FONT=Roboto]After some more testing, a better solution may be to install **gstreamer1.0-libav** and not **gstreamer1.0-plugins-ugly**. Both solutions worked when tested with Ubuntu-Mate.[/FONT][/COLOR][/SIZE]

---

