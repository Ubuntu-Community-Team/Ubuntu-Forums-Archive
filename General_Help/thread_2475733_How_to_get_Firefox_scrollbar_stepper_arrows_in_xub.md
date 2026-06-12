---
title: "How to get Firefox scrollbar stepper arrows in xubuntu 22.04"
date: 2022-06-06
forum: General Help
---

### Post by Ralph L on 2022-06-06
I am installing Xubuntu 22.04 jammy. Once again a new version of Firefox doesn't show the stepper arrrows on the top/bottom of the vertical slide. I have fought this problem a few times on earlier systems and am getting tired of the constant effort to stifle stepper arrows. I use them!!!! The latest solution that worked on Xubuntu 18.04 (latest firefox update for that system) was to add to about:config the statement "widget.non-native-theme.gtk.scrollbar.allow-buttons" and set to "true". This didn't work for me in Firefox 101.1 (snap version) that comes with Xubuntu 22.04. I also tried setting up ~.config.gtk.css with 2 different contents. Neither of these worked.
Configuration 1```
scrollbar,
.scrollbar
{
    -GtkScrollbar-has-backward-stepper: TRUE;
    -GtkScrollbar-has-forward-stepper: TRUE;
}
```

Configuration 2```
.scrollbar {
-GtkScrollbar-has-backward-stepper: 1;
-GtkScrollbar-has-forward-stepper: 1;
-GtkRange-slider-width: 15;
-GtkRange-stepper-size: 15;
}

```
Anybody know how to get stepper arrows back on latest firefox????????

---

### Post by Ralph L on 2022-06-14
Haven't had any replies on this yet..... Somebody else must have had this same problem, or am I the only one that uses the stepper arrows that (at least "used to") appear at either end of the vertical scroll bar.
Any help very much appreciated.....

---

### Post by ajgreeny on 2022-06-15
I will have to get back to you for this but you can certainly get back to a sensible scrollbar and stepper buttons on a ,deb installed version of firefox; no idea about the snap version as I've removed all snap infrastructure from my machines and use the direct download of the Firefox .tar.gz archive from mozilla instead.

Watch this space!

---

### Post by ajgreeny on 2022-06-15
OK, here we go.

Firstly you need to create another css file but not where you had your version.  It now needs to be  ~/.config/gtk-3.0/gtk.css

Here is the content of mine which you are welcome to try though you may have to edit some of the size values on your system.
```
# File created to enable steppers on scrollbars of gtk3 applications.
#
/* Scrollbar width fixes */
scrollbar.vertical slider,
scrollbar.slider.vertical
{
    min-width: 1em;
}
scrollbar.horizontal slider,
scrollbar.slider.horizontal
{
    min-height: 1em;
}

/* Steppers */
* {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
    min-width: 1em;
    min-height: 1em;
}

scrollbar.vertical button.down {
    -gtk-icon-source: -gtk-icontheme("pan-down-symbolic");
}

scrollbar.vertical button.up {
    -gtk-icon-source: -gtk-icontheme("pan-up-symbolic");
}

scrollbar.horizontal button.down {
    -gtk-icon-source: -gtk-icontheme("pan-end-symbolic");
}

scrollbar.horizontal button.up {
    -gtk-icon-source: -gtk-icontheme("pan-start-symbolic");
}

/* Set thickness of scrollbars */
.scrollbar.vertical slider,
scrollbar.vertical slider {
    min-width: 12px;
    background-color: #34a853;
}

.scrollbar.horizontal.slider,
scrollbar.horizontal slider {
    min-height: 12px;
    background-color: #34a853;
}

.scrollbar.vertical.slider:hover,
scrollbar.vertical:hover slider {
    min-width: 12px;
}

.scrollbar.horizontal.slider:hover,
scrollbar.horizontal:hover slider {
    min-height: 12px;
}

/* Include scrollbar steppers */
.scrollbar,
scrollbar {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
min-width: 20px;
min-height: 20px;
}

.xfce4-panel {
  -XfcePanelWindow-popup-delay: 0;
  -XfcePanelWindow-popdown-delay: 0;
}


```
You also need to change some more entries in the about:config settings in firefox.

[B][U]widget.non-native-theme.gtk.scrollbar.allow-buttons    true
widget.non-native-theme.scrollbar.active-always-themed	false
widget.non-native-theme.scrollbar.size	20
widget.non-native-theme.scrollbar.size.override	20[/U][/B]

Give those a try and you may find you get a scrollbar just like in my screenshot.

---

### Post by Ralph L on 2022-06-16
ajgreeny:
Thank you very much for responding.  I really appreciate it. I have been busy the last few days so I just got around to trying your suggestions. They didn't work. I installed your suggested  ~/.config/gtk-3.0/gtk.css file, and I entered in about:config the 4 directives you specified, but still no stepper arrows. I restarted the computer after I did the installation. Actually I already had 3 of 4 directives you suggested. I tried the 4th directive "widget.non-native-theme.scrollbar.active-always-themed false" as both true and false, but I could see no effect on firefox. 
I had all this working under Xubuntu 18.04 using just the directives you specified, but I have been unable to get the stepper arrows with the same directives under Xubuntu 22.04 Snap. Maybe there is a bug in the Snap version only.
Any other ideas on this?????????

---

### Post by ajgreeny on 2022-06-17
I suspect the inability to get those things working maybe due to your firefox being the snap version but I am unable to check that as I do not, and will not, use any snaps on my system at present; there are just too many disadvantages and problems with them for me to feel comfortable using any of them.

I know other users feel differently from me but firefox was so slow opening the first time on my older systems that I was never sure if it was going to start or not, so looked for alternative ways to use it and now simply download the .tar.gz from Mozilla, extract it and run firefox directly from the executable file in that extracted archive.

---

### Post by Ralph L on 2022-06-17
Thanks again for responding. I have never downloaded and installed firefox. If I did download and install, would I have to delete the snap stuff first, or could I have 2 different firefoxes on my system? I hate to get rid of the snap version, until I know the non-snap version works. Also, are there directions for how to install it in the .tar.gz version?

Thanks again....

---

### Post by ajgreeny on 2022-06-18
Go to [https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release](https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release) and download the ***Linux-64-bit*** version from the middle of the three boxes showing.
Extract the .tar.gz file that you will now see in your Downloads folder and you will then get a ***firefox*** folder in Downloads, in which you will see an executable file named ***firefox***.
Double clicking on that file will open the browser looking exactly as it always has; it will find your current profile so all bookmrks and extensions will show as in your current snap version, and depending on your settings it will either tell you an upgrade is available or will update automatically.

---

### Post by speartip on 2022-06-18
You could alternatively uninstall completely the snap version of Firefox and then add the Mozilla team ppa.
[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

---

### Post by speartip on 2022-06-18
A good guide to doing that can be found here:
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

