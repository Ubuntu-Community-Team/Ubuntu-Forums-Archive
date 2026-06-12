---
title: "How to correctly change the default browser via xdg-settings in Ubuntu 22.04"
date: 2022-05-12
forum: General Help
---

### Post by makem2 on 2022-05-12
[COLOR=#000000]I am using Ubuntu 22.04 LTS, Xfce version 4.16 and Thunderbird 91.8.0 (64-bit).

[/COLOR][COLOR=#000000]This is a fresh default install having moved from 22.10, keeping my /home settings.[/COLOR]

I find that I am using Xfce and not GNOME. I suppose that must be because I kept my /home settings.

However, that is an aside, what I actualy need to do is set my default browser for xdg-mime to Brave which is my default web browser.

I searched and tried many options which did not work but I found this web page:

[https://feeding.cloud.geek.nz/posts/set-default-web-browser-debian-ubuntu/](https://feeding.cloud.geek.nz/posts/set-default-web-browser-debian-ubuntu/)

It outlines the Standard MIME tools available and their use.

I tried them:

```

makem@makem2204:~$ xdg-settings get default-web-browser
brave-browser.desktop
makem@makem2204:~$ xdg-mime query default x-scheme-handler/http
firefox.desktop
makem@makem2204:~$ xdg-mime query default x-scheme-handler/https
firefox.desktop
makem@makem2204:~$ ls -l /etc/alternatives/x-www-browser
lrwxrwxrwx 1 root root 29 Apr 30 20:50 /etc/alternatives/x-www-browser -> /usr/bin/brave-browser-stable
makem@makem2204:~$ ls -l /etc/alternatives/gnome-www-browser
lrwxrwxrwx 1 root root 29 Apr 30 20:50 /etc/alternatives/gnome-www-browser -> /usr/bin/brave-browser-stable
makem@makem2204:~$ sudo update-alternatives --config x-www-browser
There are 3 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).


  Selection    Path                           Priority   Status
------------------------------------------------------------
* 0            /usr/bin/brave-browser-stable   201       auto mode
  1            /usr/bin/brave-browser-stable   201       manual mode
  2            /usr/bin/chromium-browser       40        manual mode
  3            /usr/bin/firefox                40        manual mode


Press <enter> to keep the current choice
[*], or type selection number: 1
makem@makem2204:~$ sudo update-alternatives --config gnome-www-browser
There are 3 choices for the alternative gnome-www-browser (providing /usr/bin/gnome-www-browser).


  Selection    Path                           Priority   Status
------------------------------------------------------------
* 0            /usr/bin/brave-browser-stable   201       auto mode
  1            /usr/bin/brave-browser-stable   201       manual mode
  2            /usr/bin/chromium-browser       40        manual mode
  3            /usr/bin/firefox                40        manual mode


Press <enter> to keep the current choice
[*], or type selection number: 1
makem@makem2204:~$ xdg-settings set default-web-browser brave-browser.desktop
makem@makem2204:~$ xdg-settings get default-web-browser
brave-browser.desktop
makem@makem2204:~$ xdg-mime query default x-scheme-handler/http
firefox.desktop
makem@makem2204:~$ 


```

It can be seen that no change has been effected. Am I doing something wrong or is this not the correct way to change these settings in 22.04 today?

---

### Post by &amp;KyT$0P# on 2022-05-12
Is anything set in [FONT=Courier New]~/.config/mimeapps.list[/FONT] for those MIME types?  If so, and if it's not set the way you want, does it help to change it editing that file with your favorite text editor?

---

### Post by makem2 on 2022-05-13
> **halogen2 said:**
> Is anything set in [FONT=Courier New]~/.config/mimeapps.list[/FONT] for those MIME types?  If so, and if it's not set the way you want, does it help to change it editing that file with your favorite text editor?

The following is set:

[Added Associations]
text/vcard=libreoffice-writer.desktop;
x-scheme-handler/mailto=userapp-Thunderbird-VXMM40.desktop;
message/rfc822=userapp-Thunderbird-VXMM40.desktop;
video/mp4=org.xfce.Parole.desktop;vlc.desktop;
video/mpeg=vlc.desktop;
image/png=ristretto.desktop;
text/x-log=libreoffice-writer.desktop;
image/jpeg=gimp.desktop;ristretto.desktop;nomacs.desktop;display-im6.q16.desktop;
application/vnd.debian.binary-package=gdebi.desktop;
application/octet-stream=mousepad.desktop;
x-scheme-handler/http=exo-web-browser.desktop;
x-scheme-handler/https=exo-web-browser.desktop;
x-scheme-handler/chrome=firefox.desktop;
text/html=google-chrome.desktop;firefox.desktop;
application/x-extension-htm=firefox.desktop;
application/x-extension-html=firefox.desktop;
application/x-extension-shtml=firefox.desktop;
application/xhtml+xml=firefox.desktop;
application/x-extension-xhtml=firefox.desktop;
application/x-extension-xht=firefox.desktop;
video/x-matroska=vlc.desktop;org.xfce.Parole.desktop;
application/x-desktop=mousepad.desktop;notepadqq.desktop;libreoffice-writer.desktop;
application/gzip=mousepad.desktop;
application/x-yaml=mousepad.desktop;notepadqq.desktop;
application/x-shellscript=geany.desktop;notepadqq.desktop;
application/x-trash=org.kde.kmymoney.desktop;
text/plain=mousepad.desktop;
application/x-xpinstall=userapp-brave-browser-stable %U-XFUVL1.desktop;brave-browser.desktop;


[Default Applications]
x-scheme-handler/mailto=userapp-Thunderbird-VXMM40.desktop
message/rfc822=userapp-Thunderbird-VXMM40.desktop
video/mp4=vlc.desktop
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/chrome=firefox.desktop
text/html=firefox.desktop
application/x-extension-htm=firefox.desktop
application/x-extension-html=firefox.desktop
application/x-extension-shtml=firefox.desktop
application/xhtml+xml=firefox.desktop
application/x-extension-xhtml=firefox.desktop
application/x-extension-xht=firefox.desktop
image/jpeg=nomacs.desktop

Do you suggest replacing all instances of firefox.desktop with brave.desktop?

/home/makem/.local/share/applications/ also contains an empty mimeapps.list

---

### Post by &amp;KyT$0P# on 2022-05-13
> **makem2 said:**
> Do you suggest replacing all instances of firefox.desktop with brave.desktop?

Yes, unless you still have Firefox installed, in which case only do the ones in the [FONT=Courier New][Default Applications][/FONT] section.  And your output suggests that Brave is [FONT=Courier New]brave-browser.desktop[/FONT]

> /home/makem/.local/share/applications/ also contains an empty mimeapps.list

I think that one can safely be deleted.

---

### Post by makem2 on 2022-05-13
Working :-)

Thank you, marked as solved

---

