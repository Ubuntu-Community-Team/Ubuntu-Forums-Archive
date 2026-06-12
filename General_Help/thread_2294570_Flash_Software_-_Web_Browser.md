---
title: "Flash Software - Web Browser"
date: 2015-09-11
forum: General Help
---

### Post by Lori_Imel on 2015-09-11
I have 2 places I NEED to be able to access....  1 is a scrapbook store (Designer) and the other is Cricut Designs Studio (cutting machine).  Both use flash as a part of their site.  

I am wondering if I can install Chrome or Firefox via WINE?  Or if there is another way I can get these 2 areas to work within Ubuntu...

Thank you,
Lori

---

### Post by Frogs Hair on 2015-09-11
Hello

The flash plugin installer is in the software center and if you were to install Chrome pepper flash is included when installing the Ubuntu .deb from their site.

---

### Post by Lori_Imel on 2015-09-11
that does not get it to work - I already have all that on my computer...

I even just tried installing Firefox in WINE - when I click on the parts that use flash - it crashes and closes... on both websites....

---

### Post by monkeybrain20122 on 2015-09-11
links?

---

### Post by SeijiSensei on 2015-09-12
I visited this page, and the video played for me: [https://us.cricut.com/design/#/landing/intro-video](https://us.cricut.com/design/#/landing/intro-video).  Is that the problem you're having?

I use the Windows version of Flash Player via the [pipelight method for Firefox]("http://pipelight.net/cms/install/installation-ubuntu.html").

---

### Post by grahammechanical on 2015-09-12
Both Chrome and Firefox were built for Linux and then ported to Windows. We should not need to install them through Wine to fix this problem. Install Chrome.

[https://www.google.com/chrome/browser/desktop/](https://www.google.com/chrome/browser/desktop/)

Regards.

---

### Post by Lori_Imel on 2015-09-12
SeijiSensei - I am actually trying to go to here.... [https://us.cricut.com/design/#/canvas](https://us.cricut.com/design/#/canvas) I tried Pipelight - does not seem to have fixed it...  :(

I tried the troubleshooting suggested on the site....

I HAVE tried it in linux- Firefox, Chrome, Chromium. Opera.....

The other site is in a private area, so I cannot share the link....  if we can get Cricut to work, I am sure the other will work as well....  but it IS a problem with Flash player - it says that in linux, your browser will crash when you try to upload the zip files.  and it DOES crash....  

Cricut just keeps trying to update  - and won't....  :(

---

### Post by monkeybrain20122 on 2015-09-12
> **Lori_Imel said:**
> SeijiSensei - I am actually trying to go to here.... [https://us.cricut.com/design/#/canvas](https://us.cricut.com/design/#/canvas) I tried Pipelight - does not seem to have fixed it...  :(

Cricut just keeps trying to update  - and won't....  :(

What does it suppose to do? I went there with pipelight flash, I saw a square with a rotating thingy in the middle, then it stops, a download button appears, I click it and it asks me to download CricutDesignSpace-3.1507.2813.3864.exe, which is a Windows program.

P.S. Chrome and pepperflash doesn't work. The download button never appears.

---

### Post by Lori_Imel on 2015-09-12
eventually it should show a work area for creating cutting files -

I am trying iexplorer in play on linux....  nothing so far

---

### Post by Lori_Imel on 2015-09-12
that did not work either....  :(

---

### Post by monkeybrain20122 on 2015-09-12
> **Lori_Imel said:**
> eventually it should show a work area for creating cutting files -

I am trying iexplorer in play on linux....  nothing so far

I tested it in a Win7  VM. Same thing as using pipelight on Ubuntu, asked me to download the .exe file. No work area.

---

### Post by Lori_Imel on 2015-09-12
I understand that they automatically update the software - so I have downloaded the file.... but I can't seem to get it to work properly.....  I HOPE I can find a work around for this....  I just read that MS is forcing Win10 downloads on people who even opt out....  :(

---

### Post by Frogs Hair on 2015-09-12
I see no problem with the flash content , but the Criicut Design Space Plug-in wont load.

---

### Post by Lori_Imel on 2015-09-12
yes, so I might be out of luck?  I also remember that in the other site - private area.... I have to click on exception - "unsafe script" to get it to work properly, even in windows....

---

### Post by monkeybrain20122 on 2015-09-12
> **Lori_Imel said:**
> I understand that they automatically update the software - so I have downloaded the file.... but I can't seem to get it to work properly.....  I HOPE I can find a work around for this....  I just read that MS is forcing Win10 downloads on people who even opt out....  :(

Where are you supposed to install the .exe file? Maybe installing it in wine and use FF in wine would work? If all fail you can use a VM if you have 4 G of ram.

Edited: seeing that you need to get to work for another site maybe VM is the way to go.

---

### Post by Lori_Imel on 2015-09-12
I did try it again in WINE - Firefox crashes - gives me the crash/send email thing when I click on either site areas that I am trying to get to work.  I even re-installed the plug-in....  I need to find about VM.....  I have plenty of RAM, I have an i7 with all of the bells and whistles...

---

### Post by Lori_Imel on 2015-09-12
I can't get Virtual Box to install....

---

### Post by Lori_Imel on 2015-09-12
Well virtual box caused my computer to fail.... everything disappeared...  had to do an ubuntu install.... now it is back fine, but VB is gone....  :(

---

### Post by monkeybrain20122 on 2015-09-12
How did you install VB?

See instructions here
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by SeijiSensei on 2015-09-12
I don't see any way to run this natively in Linux.  It's a Windows executable.  I looked into installing it in the restricted Wine environment that pipelight builds, but I don't see any easy way to do that.  There are methods for a variety of plugins [here](http://pipelight.net/cms/installation.html#section_2), but I don't see any generic method to use the contents of a random .exe file as a pipelight plugin.  

As for Virtualbox, as monkeybrain said, go the Linux Downloads page at virtualbox.org, then follow the instructions for "Debian-based Linux distributions."  It will tell you how to install the Oracle repository and its public key so you can download VirtualBox directly from there.

---

