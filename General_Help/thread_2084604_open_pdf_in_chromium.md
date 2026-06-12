---
title: "open pdf in chromium"
date: 2012-11-15
forum: General Help
---

### Post by qunqun on 2012-11-15
Right now when I click on a pdf document in chrome the save dialog shows up, instead I would like to use evince to open pdf documents instead. Is there a way to do it? I have found solutions that involve changing mailcap / xdg-mime but none of them seems to work. Thanks!

---

### Post by Frogs Hair on 2012-11-15
When I open a pdf in Chrome it opens in the browser window and then I can save it if I want from the tool bar that appears in the browser window. This appears to be default behavior. Is this what you want or do you want the pdf to open in the document viewer with out saving it ?

---

### Post by Frogs Hair on 2012-11-15
This is what I see when I open a pdf in chrome.

---

### Post by qunqun on 2012-11-15
> **Frogs Hair said:**
> When I open a pdf in Chrome it opens in the browser window and then I can save it if I want from the tool bar that appears in the browser window. This appears to be default behavior. Is this what you want or do you want the pdf to open in the document viewer with out saving it ?

I would like it to open in an external document viewer rather than needing to first save it somewhere and then open it. I am hoping that there is a way to do so without installing a plugin since that would open the document inside the browser (which is not what I want).

---

### Post by vasa1 on 2012-11-16
Which version of Chrome are you using?

---

### Post by qunqun on 2012-11-16
> **vasa1 said:**
> Which version of Chrome are you using?

I am using the latest nightly chromium builds

---

### Post by slickymaster on 2012-11-16
*"This is what I see when I open a pdf in chrome."*. That's the Chrome default behavior.

But you can try this extension: [Docs PDF/PowerPoint Viewer]("https://chrome.google.com/webstore/detail/docs-pdfpowerpoint-viewer/nnbmlagghjjcbdhgmkedmbmedengocbn?hl=en")

---

### Post by vasa1 on 2012-11-16
> **qunqun said:**
> I am using the latest nightly chromium builds
Okay, that's why I was confused. Chrome has a pdf viewer whereas Chromium doesn't.

---

### Post by slickymaster on 2012-11-16
If that's your case, all you have to do is to download a Google Chrome release that matches your processor architecture (x86/x86_64):

# wget [http://dl.google.com/linux/direct/google-chrome-unstable_current_i386.deb](http://dl.google.com/linux/direct/google-chrome-unstable_current_i386.deb)
# wget [http://dl.google.com/linux/direct/google-chrome-unstable_current_amd64.deb](http://dl.google.com/linux/direct/google-chrome-unstable_current_amd64.deb)
[LIST]extract the .deb:[/LIST]
# ar vx <previously downloaded .deb>
[LIST]extract the data payload:[/LIST]
# tar --lzma -xvf data.tar.lzma
[LIST]copy the plugin to destination folder:[/LIST]
(note: /usr/lib/chromium-browser is valid for my Ubuntu PPA version, might be /opt/chromium-browser or something on other distributions)
# sudo cp opt/google/chrome/libpdf.so /usr/lib/chromium-browser/
[LIST]restart any open Chromium processes[/LIST]
[LIST]check about: plugins for the Chrome PDF Viewer, should not need any enabling[/LIST]

---

### Post by Frogs Hair on 2012-11-16
> I am using the latest nightly chromium builds This is why there is difference in behavior.

---

### Post by qunqun on 2012-11-16
> **Frogs Hair said:**
> This is why there is difference in behavior.

Thanks for all the responses. I am actually trying to not use any plugins as I am trying to open the file *externally* not inside chrome.

---

### Post by oldos2er on 2012-11-16
Chrome is not the same as Chromium, so I've changed your thread title.

---

### Post by fullmoonguru on 2012-11-22
I would also like to know the answer to this.  I am using chromium stable.  I was able to do it in the past by making changes to the mozplugger files but that doesn't seem to work now.

I would like to just have it open in evince, not use a plugin or install chrome.

---

