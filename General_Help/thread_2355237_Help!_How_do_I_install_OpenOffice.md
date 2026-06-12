---
title: "Help! How do I install OpenOffice?"
date: 2017-03-10
forum: General Help
---

### Post by raventhh-rs on 2017-03-10
So, I looked it up and one person said to type sudo apt-get install openoffice.org, but when I did that, I got the error: 
Package "openoffice.org" has no installation candidate

So I was hoping someone knew of a way for me to install it on my Lubuntu system. I mainly need it as a replacement for word and powerpoint, and I know people say LibreOffice is better, and I do believe that, however every time I open LibreOffice, it crashes upon opening. Not sure what to do here. :/.

---

### Post by QIII on 2017-03-10
Moved to General Help.

Hello!

Lubuntu is an officially recognized flavor of Ubuntu, so your question properly belongs in the general support sections of the Forums.

Cheers!

---

### Post by nevertellmetheodds on 2017-03-10
Why not use Libreoffice ? It's a fork of open office.

---

### Post by justen_m on 2017-03-10
Go to [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html)
Pick the installation from the drop down that you need. Probably Linux 64-bit (x86-64) (DEB), English, 4.1.3.
Once you get the .deb file, just install it.
sudo dpkg -i whateverdownloaded

Sorry, I don't know the actual filename. I'm running LibreOffice.
I'm curious, if LibreOffice crashes, what make you think OpenOffice will work?

---

### Post by HermanAB on 2017-03-11
In my experience Libre/Open Office usually crashes due to a lack of RAM / Swap space on the machine.

---

### Post by howefield on 2017-03-11
> **raventhh-rs said:**
> ... however every time I open LibreOffice, it crashes upon opening. Not sure what to do here. :/.

If you try opening it from the command line, you'll get more of a clue as to what's wrong ?

Eg..

```
libreoffice --writer
```

---

### Post by vasa1 on 2017-03-11
> **justen_m said:**
> ...
I'm curious, if LibreOffice crashes, what make you think OpenOffice will work?
OpenOffice is older. Current LibreOffice versions use gtk3 and *could* be more resource-heavy.

---

### Post by howefield on 2017-03-11
> **vasa1 said:**
> OpenOffice is older. Current LibreOffice versions use gtk3 and *could* be more resource-heavy.

Have seen that with several old Windows machines, openoffice will work where LibreOffice won't, unfortunate as that is, imho.

---

### Post by Impavidus on 2017-03-11
> **justen_m said:**
> Go to [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html)
Pick the installation from the drop down that you need. Probably Linux 64-bit (x86-64) (DEB), English, 4.1.3.
Once you get the .deb file, just install it.
sudo dpkg -i whateverdownloaded

Sorry, I don't know the actual filename. I'm running LibreOffice.
I'm curious, if LibreOffice crashes, what make you think OpenOffice will work?

Keep in mind you have to uninstall libreoffice before installing openoffice. They can't be installed at the same time.

---

### Post by Hagar Delest on 2017-05-13
Here is a tutorial to install on GNU/Linux: [[Tutorial] Installing Apache OpenOffice on GNU/Linux]("https://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=50119")

---

