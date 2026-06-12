---
title: "Viber doesn't work"
date: 2022-07-20
forum: General Help
---

### Post by 16fo12 on 2022-07-20
[COLOR=#232629][FONT=-apple-system]Viber doesn't work on Jammy Jellyfish. I used to have Focal Fossa and it worked without problems but now when I try to start it, it either claims that I have no internet connection or after I enter my mobile phone number it simply doesn't recognise it. On askubuntu there is a proposed solution ([/FONT][/COLOR]https://askubuntu.com/questions/1403319/viber-no-connection-on-ubuntu-22-04-even-i-have-an-internet/1409882#1409882) [COLOR=#232629][FONT=-apple-system]for this problem that involves downloading libssl1.1_1.1.1l-1ubuntu1.3_amd64.deb but that file seems to be gone so I downloaded libssl1.1_1.1.1l-1ubuntu1_amd64.deb instead. When I try to launch viber now it says that Ubuntu has encountered an error and offers to send a report. Any suggestions?[/FONT][/COLOR]

---

### Post by mIk3_08 on 2022-07-20
> **16fo12 said:**
> Viber doesn't work on Jammy Jellyfish. I used to have Focal Fossa and it worked without problems but now when I try to start it, it either claims that I have no internet connection or after I enter my mobile phone number it simply doesn't recognise it. On askubuntu there is a proposed solution ([https://askubuntu.com/questions/1403319/viber-no-connection-on-ubuntu-22-04-even-i-have-an-internet/1409882#1409882](https://askubuntu.com/questions/1403319/viber-no-connection-on-ubuntu-22-04-even-i-have-an-internet/1409882#1409882)) for this problem that involves downloading libssl1.1_1.1.1l-1ubuntu1.3_amd64.deb but that file seems to be gone so I downloaded libssl1.1_1.1.1l-1ubuntu1_amd64.deb instead. When I try to launch viber now it says that Ubuntu has encountered an error and offers to send a report. Any suggestions?
How or where did you download the viber application? Do you have any link of viber application you download? Regards and cheers.

---

### Post by 16fo12 on 2022-07-21
I have tried the following downloads:

- viber-mtd from snap 
- viber-unofficial from snap
- viber for Ubuntu from [https://www.viber.com/en/download/](https://www.viber.com/en/download/)

The result is always the same

---

### Post by #&amp;thj^% on 2022-07-21
> **16fo12 said:**
> 
The result is always the same
Yep no matter what arch you try it will end badly.
You might try: 
step-by-step instruction for folks, who don't know how to fix this:
```

wget http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb

dpkg -i libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb
```

Edit this file:
```
sudo nano /usr/share/applications/viber.desktop

```
Change the exec line to:
```

Exec=LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libssl.so /opt/viber/Viber %u
```
Unfortunately it's on Viber to release a new version for 22.04 that is compatible with **libssl 3.0**, until then you have to live with this workaround.
Good Luck

---

### Post by deadflowr on 2022-07-21
Maybe try the flatpak version: [https://flathub.org/apps/details/com.viber.Viber]("https://flathub.org/apps/details/com.viber.Viber")
(Follow the setup guide link to setup flatpak support on Ubuntu.)

I'd also check if running wayland and maybe try an Xorg session.
Just in case that is an issue.

---

### Post by #&amp;thj^% on 2022-07-21
> **deadflowr said:**
> Maybe try the flatpak version: [https://flathub.org/apps/details/com.viber.Viber]("https://flathub.org/apps/details/com.viber.Viber")
(Follow the setup guide link to setup flatpak support on Ubuntu.)

I'd also check if running wayland and maybe try an Xorg session.
Just in case that is an issue.

Flatpaks are broken as well on jammy>>>it needs libssl1.1.1 and Ubuntu 22.04 uses libsssl3 
Although it would be nice if it was backwards compatible. :) 
Works just fine on wayland and fedora.

---

### Post by mIk3_08 on 2022-07-22
> **16fo12 said:**
> I have tried the following downloads:

- viber-mtd from snap 
- viber-unofficial from snap
- viber for Ubuntu from [https://www.viber.com/en/download/](https://www.viber.com/en/download/)

The result is always the same
I have tried to download the Ubuntu debian viber app package last week but the link is lost for Ubuntu now. Maybe there is a problem in the debain viber package for Ubuntu. Sorry I can't help you. Maybe you can contact the viber support for your concern. Or maybe you can try the other package like the rpm as long as its for Linux maybe it will run smoothly in your system. Regards and cheers.

---

### Post by 16fo12 on 2022-07-26
1fallen, thanks for the suggestion, in fact I had tried this, the problem is [COLOR=#000000][FONT=&amp]libssl1.1_1.1.1l-1ubuntu1.2 is not there anymore. There are only versions starting with 2.1. Any idea if I can download 1.2 somewhere else?[/FONT][/COLOR]

---

### Post by Paddy Landau on 2022-07-26
I have both Ubuntu 20.04 and Ubuntu 22.04. I get the same as you: It works on 20.04, but not on 22.04 (I tried the AppImage and the Ubuntu deb).

It's possible that Viber hasn't yet modified its app for 22.04, because 22.04's first point-release isn't yet due; it's due 4th August, just a few days away!

I suggest that you contact Viber to sort this out. In the meantime, you'll have to use your phone's app — unless you want to go the whole hog and install a VM with an older version of Ubuntu!

---

### Post by #&amp;thj^% on 2022-07-26
Ok Ok so they broke that link, more than one way to skin a cat. ;)
I used this first:
```
 wget https://mirror.rcg.sfu.ca/mirror/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1-1ubuntu2.1~18.04.20_amd64.deb

```
Then:
```
dpkg -i libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb

```
Now we get the appimage via:
```
wget -P ~/Downloads https://download.cdn.viber.com/desktop/Linux/viber.AppImage
```
now extract from AppImage & move to /opt
```
chmod +x ~/Downloads/viber.AppImage
~/Downloads/viber.AppImage --appimage-extract
sudo mv ~/squashfs-root /opt/viber

```

Then I moved the application folder & edit viber.desktop to point to the actual Viber executable via:
```
sudo cp /opt/viber/viber.desktop /usr/share/applications
sudo sed -i "s/Exec=.*/Exec=\/opt\/viber\/Viber/" /usr/share/applications/viber.desktop
sudo sed -i "s/Icon.*/Icon=\/opt\/viber\/viber\.png/" /usr/share/applications/viber.desktop

```
Now you should see it in your menu...

---

### Post by Claus7 on 2022-08-15
Hello,

> **Paddy Landau said:**
> ...

It's possible that Viber hasn't yet modified its app for 22.04, because 22.04's first point-release isn't yet due; it's due 4th August, just a few days away!

...

indeed, a new viber for ubuntu has been released. The new version is 18.2.0.2 and is available as deb, with its size 127MB reported during download, compared to the previous 16.1.0.37 of 105MB.

In order to install it remove the previous version first.

Trying to open it, three problems arose:
1) from xorg sessions an error reported:
> FATAL: xkb_keyboard_layout_engine.cc(640)] Keymap file failed to load: us-extended
(without space between : and x)
so changing the language prior to opening viber this error disappears.

2) from wayland session it might need the command:
```
QT_QPA_PLATFORM=wayland /opt/viber/Viber
```

3) when trying to make a call, an error shows up:
> QHttpNetworkConnectionPrivate::_q_hostLookupFinished could not de-queue request, failed to report HostNotFoundError
and no calls are made. No solution for the time being for this one though. (edit3: there are other messages displayed as well, like "bottom margin" error and close error, yet I do not know if they are related with this problem, since many of them are shown even when viber is working reasonably)
edit: tested the AppImage and is working though.
edit2: I found out that by changing user viber works.
edit3: actually I tested it in two different places. In one it was working, in the other I had to remove mime contents under ~.local/share, for both deb and Appimage to work.

Regards!

---

### Post by Claus7 on 2023-04-15
Hello,

> **Claus7 said:**
> ...
1) from xorg sessions an error reported:

(without space between : and x)
so changing the language prior to opening viber this error disappears.

...

The command from terminal for viber was:
```
/opt/viber/Viber

```

the error message was:
> qt.webenginecontext: 

GLImplementation: desktop
Surface Type: OpenGL
Surface Profile: NoProfile
Surface Version: 3.1
Using Default SG Backend: yes
Using Software Dynamic GL: no
Using Angle: no

Init Parameters:
  *  allow-loopback-in-peer-connection  
  *  application-name ViberPC 
  *  autoplay-policy no-user-gesture-required 
  *  browser-subprocess-path /opt/viber/libexec/QtWebEngineProcess 
  *  disable-features DnsOverHttpsUpgrade,ConsolidatedMovementXY,InstalledApp,BackgroundFetch,WebOTP,WebPayments,WebUSB,PictureInPicture,AudioServiceOutOfProcess 
  *  disable-setuid-sandbox  
  *  disable-speech-api  
  *  enable-features NetworkServiceInProcess,TracingServiceInProcess,NetworkServiceInProcess 
  *  enable-threaded-compositing  
  *  enable-usermedia-screen-capture  
  *  in-process-gpu  
  *  use-gl desktop 

xkbcommon: ERROR: Couldn't process include statement for 'us(extended)'
xkbcommon: ERROR: Abandoning symbols file "(unnamed)"
xkbcommon: ERROR: Failed to compile xkb_symbols
xkbcommon: ERROR: Failed to compile keymap
[2559:2593:0415/113151.697030:FATAL:xkb_keyboard_layout_engine.cc(640)] Keymap file failed to load: us-extended
Trace/breakpoint trap

The solution to the problem is:
```
setxkbmap -variant ' ,extended'

```
mind the space between first ' and comma.

Helpful link:
[https://forums.linuxmint.com/viewtopic.php?t=379565](https://forums.linuxmint.com/viewtopic.php?t=379565)

Regards!

---

### Post by Claus7 on 2023-06-21
Hello,

with the latest version (20.3.0.1) both the language problem is solved, as well as the ability to close viber from panel.

Regards!

---

