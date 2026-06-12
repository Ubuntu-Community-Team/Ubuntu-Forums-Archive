---
title: "Google Chrome will not stay default."
date: 2013-02-12
forum: General Help
---

### Post by MourningsEnd on 2013-02-12
Hello.  I have had this issue ever since I started using Linux ~3 years ago or so.

I download Google Chrome, but it will **never** stay default no matter what I do.

I set set through the browser, Perferred Applications, etc.

It is not a huge problem, but it is an inconvenience I have had to deal with some time now. 

Any help is appreciated.

Xubutnu 12.10

---

### Post by pqwoerituytrueiwoq on 2013-02-12
have you tried a custom command for default browser
i use chromium and firefox i have had no issues setting the default browser
i use xubuntu 12.10 (well for a few more days anyway, than i am switching to raring; maybe)

---

### Post by unheeding on 2013-02-12
If you have trouble setting it via the GUI, you can edit your mime associations.

The file is located at ~/.local/share/applications/mimeapps.list

Here's what mine looks like (you'll probably want to change chromium-browser.desktop to google-chrome.desktop (I'm not sure if this is 100% correct - check /usr/share/applications/ for the correct file)):

[Default Applications]
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
text/html=chromium-browser.desktop
text/xml=chromium-browser.desktop
application/xhtml_xml=chromium-browser.desktop
x-scheme-handler/about=chromium-browser.desktop
x-scheme-handler/unknown=chromium-browser.desktop

[Added Associations]
x-scheme-handler/http=chromium-browser.desktop;
x-scheme-handler/https=chromium-browser.desktop;
text/html=chromium-browser.desktop;
text/xml=chromium-browser.desktop;
application/xhtml_xml=chromium-browser.desktop;

---

### Post by MourningsEnd on 2013-02-12
> **unheeding said:**
> If you have trouble setting it via the GUI, you can edit your mime associations.

The file is located at ~/.local/share/applications/mimeapps.list

Here's what mine looks like (you'll probably want to change chromium-browser.desktop to google-chrome.desktop (I'm not sure if this is 100% correct - check /usr/share/applications/ for the correct file)):

[Default Applications]
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
text/html=chromium-browser.desktop
text/xml=chromium-browser.desktop
application/xhtml_xml=chromium-browser.desktop
x-scheme-handler/about=chromium-browser.desktop
x-scheme-handler/unknown=chromium-browser.desktop

[Added Associations]
x-scheme-handler/http=chromium-browser.desktop;
x-scheme-handler/https=chromium-browser.desktop;
text/html=chromium-browser.desktop;
text/xml=chromium-browser.desktop;
application/xhtml_xml=chromium-browser.desktop;

I change it to:

```

[Added Associations]
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
application/vnd.oasis.opendocument.text=libreoffice-writer.desktop;
x-scheme-handler/mailto=exo-mail-reader.desktop

[Default Applications]
application/vnd.oasis.opendocument.text=libreoffice-writer.desktop

```


I assume google-chrome.desktop would be the correct value?  It seems to be working, but I will need to reboot to make sure.

---

### Post by unheeding on 2013-02-12
Yes, it looks like google-chrome.desktop is the correct value.  I hope this fixed this issue for you (after three years, wow).  Remember to mark it [SOLVED] if it did. :)

---

### Post by MourningsEnd on 2013-02-12
It is not working anymore. :(

---

### Post by unheeding on 2013-02-12
> **MourningsEnd said:**
> It is not working anymore. :(

Hmm, did the mimeapps.list file change when you rebooted?

You might have to create the global mimeapps.list in /usr/share/applications/

```
sudo cp ~/.local/share/applications/mimeapps.list /usr/share/applications/mimeapps.list
```

---

### Post by MourningsEnd on 2013-02-12
It stays the same this time upon reboot.  Chrome still does not open.

---

### Post by slickymaster on 2013-02-12
Run the following command at a terminal window:
```
gksudo geany /usr/share/applications/defaults.list
```
Note: you have to replace geany with your installed textpad

Then, in the **defaults.list** file, try to find **x-www-browser** and set its value to your **google-chrome.desktop** location.

If you won't find **x-www-browser**, then try to search for
```
text/html=firefox.desktop;google-chrome.desktop
text/xml=firefox.desktop;google-chrome.desktop
application/xhtml_xml=google-chrome.desktop
x-scheme-handler/http=firefox.desktop;google-chrome.desktop
x-scheme-handler/https=firefox.desktop;google-chrome.desktop
x-scheme-handler/ftp=google-chrome.desktop
```
replacing firefox with google-chrome.desktop.

---

### Post by cek on 2013-02-12
This is an interesting bug I've noticed over time in XUbuntu.  After installing google-chrome and setting it to the default browser in Settings->Preferred Applications, starting google-chrome will say it's not the default browser and ask if you want to make it so.  If you say yes here, it will no longer be the default.  If you say no, and check the box to not be asked again it will remain the default.

---

### Post by MourningsEnd on 2013-02-13
It is working now!  Thank you all for the help provided.

---

