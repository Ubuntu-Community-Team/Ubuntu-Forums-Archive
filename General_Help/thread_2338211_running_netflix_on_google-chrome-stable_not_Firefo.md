---
title: "running netflix on /google-chrome-stable/ not Firefox 49 with xenial"
date: 2016-09-25
forum: General Help
---

### Post by ventrical on 2016-09-25
The new firefox49 version is out and downloaded from the repositories.  I checked off the new option "DRM Content" Play DRM content and it downloaded the plugin Widevine but client still cannot get netflix to work.

most recent info ...  [http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm](http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm)

Any hints or tips or do we just have to wait.

Regards..

Ventrical..

---

### Post by SeijiSensei on 2016-09-25
Netflix only seems to work with Pipelight+Silverlight for me using FF 50.0b1.  Widevine doesn't seem to help despite the fact that Netflix plays fine using Chrome.  I have UA Control installed and spoof my User-Agent string as if I were using Windows, too.

---

### Post by ventrical on 2016-09-25
> **SeijiSensei said:**
> Netflix only seems to work with Pipelight+Silverlight for me using FF 50.0b1.  Widevine doesn't seem to help despite the fact that Netflix plays fine using Chrome.  I have UA Control installed and spoof my User-Agent string as if I were using Windows, too.

Where do I get Chrome? I know Chromium Browser is in repos but Chrome is not. Are they not two different browsers or one of the same?

---

### Post by bearlake on 2016-09-25
> **ventrical said:**
> Where do I get Chrome? I know Chromium Browser is in repos but Chrome is not. Are they not two different browsers or one of the same?

Hi,

This may help. [Chrome]("https://www.google.com/chrome/browser/desktop/index.html")

---

### Post by ventrical on 2016-09-26
I figured it out. 

thanks everyone.

---

### Post by SeijiSensei on 2016-09-26
Might we ask how?  It could help others with the same problem.

---

### Post by ventrical on 2016-09-26
> **SeijiSensei said:**
> Might we ask how?  It could help others with the same problem.

In all honesty I do not subscribe to netflix but one of my prospective clients does and that client wants to have netflix work out of the box. Ubuntu 16.04 is presenting some real challenges with networking and (getting netflix to work out of the box). In my reply "I figured it out" is I mean to say that I figured out how to install google-chrome-stable. You first have to go to a download site (mentioned in the above link provided), download the linux/ubuntu version and then it automagically installs it into Ubuntu Software (no longer Ubuntu Software Center). This is a big surprise for me (and probably a lot of noobs mirgrating to ubuntu during this current mass exodus from Windows 10). How can it get any worse..and I have no one but myself to blame (as team admin of Ubuntu Development Version Testing).

  Now I am in the process to instruct a client how to install google-chrome-stable who is a complete noob. The research of the new Firefox ver 49 explains that clients have to wait for netflix to throw an enabling agent switch .. etc.. so there is a lot of conflicting information out there.

 I am waiting for client to get back and report if netflix is working with google-chrome-stable.

At this stage of the game I am going to mark this thread  back to <unsolved> meaning to say .. remove the <solved> tag.

Sensei... thank you for your reply .. I will  contribute whatever I can  to this thread to help others get this netflix problem solved as information is forthcoming. Mind you I am working only on ubuntu-desktop stack.

Regards..

---

### Post by ventrical on 2016-09-26
Netflix Resolution: per Ubuntu-Desktop 16.04 xenial

Go  here : [https://www.google.com/chrome/browser/desktop/index.html](https://www.google.com/chrome/browser/desktop/index.html)

and download latest google-chrome-stable. It should automatically install the .DEB into Ubuntu Software. If it does not install into Ubuntu Software it WILL be in the Downloads folder.

Right-click on the google-chrome-stable-current.deb and choose 'install package'.

You then have to open Ubuntu Software and search for Google-Chrome-stable and then click the install dialog box.

This method allows for  netflix to run out of the box with no scripts or UA plugins.

Regards..

---

