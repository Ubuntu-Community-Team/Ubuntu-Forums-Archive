---
title: "PDF in Chromium"
date: 2013-05-02
forum: General Help
---

### Post by Dummy Plug on 2013-05-02
Hello there. Everytime I try to open a PDF link, Chromium downloads it (without asking) instead of just opening it in a new tab. How can I fix this?
This happens with Ubuntu 12.04 LTS, using Chromium. Evince is the default pdf reader.

---

### Post by Sef on 2013-05-02
> **Downloads**[COLOR=#303942][FONT=Ubuntu]Download location:  Change...[/FONT][/COLOR]
[COLOR=#303942][FONT=Ubuntu]Ask where to save each file before downloading[/FONT][/COLOR]
[COLOR=#303942][FONT=Ubuntu]You have chosen to open certain file types automatically after downloading.

[/FONT][/COLOR]


To get to downloads, click on the 3 bars on the far right, then click advanced settings. You will have to set PDFs to open automatically, but once you do they will open automatically after downloading.

---

### Post by vdubeau on 2013-05-02
Sounds like what you are looking for is to have Chromium itself open the PDF like Firefox and Chrome. The PDF viewer is included because of distribution restricts. I did find this though on a Google search,
[I]
Mozilla's [PDF.js]("http://mozilla.github.org/pdf.js")  is included in Chromium Portable as of v26.0.1410.5, so Google's PDF  viewer is not necessary anymore.  You will have to enable PDF.js in chrome://extensions on the first post-update run, though.[/I]

I don't use Chromium but give it a try.

---

### Post by vasa1 on 2013-05-02
> **vdubeau said:**
> Sounds like what you are looking for is to have Chromium itself open the PDF like Firefox and Chrome. The PDF viewer is included because of distribution restricts. I did find this though on a Google search,
[I]
Mozilla's [PDF.js]("http://mozilla.github.org/pdf.js")  is included in Chromium Portable as of v26.0.1410.5, so Google's PDF  viewer is not necessary anymore.  You will have to enable PDF.js in chrome://extensions on the first post-update run, though.[/I]

I don't use Chromium but give it a try.
Source please!

Edit: [http://crportable.sourceforge.net/](http://crportable.sourceforge.net/) seems to be an MS Windows thing?

---

### Post by vasa1 on 2013-05-02
> **Sef said:**
> To get to downloads, click on **the 3 bars on the far right**, then click advanced settings. You will have to set PDFs to open automatically, but once you do they will open automatically after downloading.
A couple of people here mocked me when I posted about the demise of the **Wrench**.

---

### Post by Stonecold1995 on 2013-05-02
The problem is that Chromium doesn't come with the PDF plugin by default, so you need to "steal" the plugin from Google Chrome and give it to Chromium.

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo cp /opt/google/chrome/libpdf.so /usr/lib/chromium-browser/
sudo apt-get purge google-chrome-stable
rm google-chrome-stable_current_amd64.deb
```

Now restart Chromium, go to "about:plugins" (just put it in the URL bar and press enter) and enable the PDF viewer from there.

That's basically how you transfer any plugin from Chrome to Chromium.

---

