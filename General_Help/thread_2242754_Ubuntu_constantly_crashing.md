---
title: "Ubuntu constantly crashing"
date: 2014-09-03
forum: General Help
---

### Post by mayurpathak6 on 2014-09-03
Hello, I'm fairly new to Linux and could use some help please. Google Chromium keeps crashing every time I do one of two things: when I right-click and try to save an image, and when I simply try to execute a Google search. I started Chromium from terminal, tried running a Google search, and got this:

~$ chromium-browser
[25617:25617:0903/200022:ERROR:desktop_window_tree_host_x11.cc(1497)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension agfmabgjbaeidpfpbpedpbabhfeccadg
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension kkkaddaeppcdjbnlnldpbncidgcbkcee
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension ihfofpbnbdibpheecoafahbcpjdfeidp
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension jdheeblenjmceeppomdgokgilmkonced
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension cemknpokkpnacjgejbbaojlhcggpimea
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension bfpfdjclhabpjncikdngdoldjjjegnbe
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension hlffpiiabmdgalaoebphhpkhadofhgmd
[25617:25617:0903/200023:ERROR:extension_downloader.cc(679)] Invalid URL: '' for extension dgkpeoeiobibaemecccfdaedeoppoggl
[25617:25654:0903/200054:FATAL:url_request.cc(709)] Trying to send secure referrer for insecure load
Aborted (core dumped)

Can someone please help me fix this problem? Thank you!!

---

### Post by Colin_Deisenroth on 2014-09-04
What version of ubuntu are you running? I'm not sure how it got there, but I have the google chrome repo in /etc/apt/sources.list.d/google-chrome.list

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

The package I have installed is called "google-chrome-stable"

---

### Post by mayurpathak6 on 2014-09-05
> **Colin_Deisenroth said:**
> What version of ubuntu are you running? I'm not sure how it got there, but I have the google chrome repo in /etc/apt/sources.list.d/google-chrome.list

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

The package I have installed is called "google-chrome-stable"

Hello, I'm running Ubuntu 14.04.1 LTS. I just deleted Chromium and installed Chrome; works fine now.

---

