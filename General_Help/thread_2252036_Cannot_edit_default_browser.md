---
title: "Cannot edit default browser"
date: 2014-11-08
forum: General Help
---

### Post by nmyrick on 2014-11-08
I would like to use Google Chrome as my default browser, but it keeps showing up incorrectly in the default applications screen, and therefore no links will open properly.  I have tried uninstalling, rebooting and reinstalling Google Chrome, but it still shows up incorrectly in the drop down menu in default applications. See the attached screenshot.

Can anyone help me with how to correct this issue?  I am running Ubuntu 14.04 amd64.

---

### Post by sammiev on 2014-11-08
Works great here.

---

### Post by nmyrick on 2014-11-08
> **sammiev said:**
> Works great here.

Thanks, but since this post is listed under general help what I'm looking for is an answer to my issue, not whether or not it works for everyone else. Do you know how I can fix this?

---

### Post by nerdtron on 2014-11-08
Open Settings in google chrome, scroll down the bottom and see the Default Browser section.

---

### Post by nmyrick on 2014-11-08
> **nerdtron said:**
> Open Settings in google chrome, scroll down the bottom and see the Default Browser section.

Thank you for your reply. I've already tried that and it didn't work. I even tried uninstalling and reinstalling chrome. There must be a config text file somewhere that contains this information, but I can't find it.

---

### Post by nmyrick on 2014-11-08
I figure the drop down menu must pull information from a file somewhere that I need to edit, but I don't know what file.

---

### Post by sammiev on 2014-11-08
> **nmyrick said:**
> I figure the drop down menu must pull information from a file somewhere that I need to edit, but I don't know what file.

I just went into Details and select default programs and select google chrome. That's all that is needed to do, thought else is required.

---

### Post by nmyrick on 2014-11-08
Thank you, but the whole issue is that Google Chrome is not what is showing up in my details section. It shows the chrome icon, but the wrong information.

---

### Post by Bashing-om on 2014-11-08
nmyrick; Hello:

What results:
```

sudo update-alternatives --config x-www-browser

```
See:[http://manpages.ubuntu.com/manpages/precise/man1/update-desktop-database.1.html](http://manpages.ubuntu.com/manpages/precise/man1/update-desktop-database.1.html)
See: man update-alternatives for more information.

[INDENT][INDENT]maybe now Yes 
[/INDENT][/INDENT]

---

### Post by nmyrick on 2014-11-08
In my troubleshooting, when I completely remove chrome using the synaptic package manager, the information in the drop-down menu goes away. But then when I reinstall chrome, the same bad information comes back.

---

### Post by sammiev on 2014-11-08
> **nmyrick said:**
> Thank you, but the whole issue is that Google Chrome is not what is showing up in my details section. It shows the chrome icon, but the wrong information.

It should only show Google Chrome and any other web browser. Not any http:// address. I have 5 Linux OS running on the same SSD and they all work the same.

---

### Post by nmyrick on 2014-11-08
> **Bashing-om said:**
> nmyrick; Hello:

What results:
```

sudo update-alternatives --config x-www-browser

```
See:[http://manpages.ubuntu.com/manpages/precise/man1/update-desktop-database.1.html](http://manpages.ubuntu.com/manpages/precise/man1/update-desktop-database.1.html)
See: man update-alternatives for more information.
[INDENT][INDENT]maybe now Yes 
[/INDENT]
[/INDENT]


Here is what I get when entering sudo update-alternatives --config x-www-browser

There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).


  Selection    Path                           Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome-stable   200       auto mode
  1            /usr/bin/firefox                40        manual mode
* 2            /usr/bin/google-chrome-stable   200       manual mode


Press enter to keep the current choice
[*], or type selection number:

---

### Post by nmyrick on 2014-11-08
I just tried switching to '[COLOR=#000000]0 /usr/bin/google-chrome-stable 200 auto mode' in the terminal, and it still shows the wrong info in the default applicatons drop-down.[/COLOR]

---

### Post by Bashing-om on 2014-11-08
nmyrick; Humm,

Beyond my experience to explain /auto/manual; But we can try and see what we can learn.

What returns from:
```

ls -al /usr/bin/google-chrome-stable

```
A symlink to ??
```

ls -al /opt/google/chrome/google-chrome

```
IF there is but the one path, what then results when in " update-alternatives --config " you choose the option '0'  for "auto" mode ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by nmyrick on 2014-11-08
FYI: My Chrome updates are coming from the repository 'http://dl.google.com/linux/chrome/deb/stable main', not from the ubuntu software center.  This way I always get the latest stable updates for chrome.

---

### Post by sammiev on 2014-11-08
> **nmyrick said:**
> I just tried switching to '[COLOR=#000000]0 /usr/bin/google-chrome-stable 200 auto mode' in the terminal, and it still shows the wrong info in the default applicatons drop-down.[/COLOR]

I would uninstall all Google Chrome on your computer and then remove all directories and files within. Then reboot and install Google Chrome from there.

---

### Post by nmyrick on 2014-11-08
Here is what returns:

nmyrick@Aquarius2:~$ ls -al /usr/bin/google-chrome-stable
lrwxrwxrwx 1 root root 32 Oct 21 20:59 /usr/bin/google-chrome-stable -> /opt/google/chrome/google-chrome

---

### Post by nmyrick on 2014-11-08
When I chose the option 0 for auto mode, it still doesn't work.

---

### Post by mc4man on 2014-11-08
Post the contents of ~/.local/share/applications/mimeapps.list

---

### Post by nmyrick on 2014-11-08
> **mc4man said:**
> Post the contents of ~/.local/share/applications/mimeapps.list

There was alot of information in there, but I think these are the lines that have to do with the browser:

text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
x-scheme-handler/ftp=firefox.desktop
x-scheme-handler/chrome=firefox.desktop

---

### Post by nmyrick on 2014-11-08
> **nmyrick said:**
> There was alot of information in there, but I think these are the lines that have to do with the browser:

text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
x-scheme-handler/ftp=firefox.desktop
x-scheme-handler/chrome=firefox.desktop

Here is the whole file:

```
[Default Applications]
x-scheme-handler/mailto=thunderbird.desktop
message/rfc822=userapp-Thunderbird-QD6RDX.desktop
application/x-extension-eml=userapp-Thunderbird-QD6RDX.desktop
text/plain=gedit.desktop
audio/x-vorbis+ogg=banshee.desktop
audio/3gpp=banshee.desktop
audio/AMR=banshee.desktop
audio/AMR-WB=banshee.desktop
audio/ac3=banshee.desktop
audio/ape=banshee.desktop
audio/avi=banshee.desktop
audio/basic=banshee.desktop
audio/flac=banshee.desktop
audio/midi=banshee.desktop
audio/mp=banshee.desktop
audio/mp2=banshee.desktop
audio/mp3=banshee.desktop
audio/mp4=banshee.desktop
audio/mp4a-latm=banshee.desktop
audio/mpc=banshee.desktop
audio/mpeg=banshee.desktop
audio/mpeg3=banshee.desktop
audio/mpegurl=banshee.desktop
audio/musepack=banshee.desktop
audio/ogg=banshee.desktop
audio/vorbis=banshee.desktop
audio/wav=banshee.desktop
audio/wave=banshee.desktop
audio/x-amzxml=banshee.desktop
audio/x-ape=banshee.desktop
audio/x-flac=banshee.desktop
audio/x-it=banshee.desktop
audio/x-m4a=banshee.desktop
audio/x-matroska=banshee.desktop
audio/x-mod=banshee.desktop
audio/x-mp=banshee.desktop
audio/x-mp3=banshee.desktop
audio/x-mpc=banshee.desktop
audio/x-mpeg=banshee.desktop
audio/x-mpeg-3=banshee.desktop
audio/x-mpegurl=banshee.desktop
audio/x-ms-asf=banshee.desktop
audio/x-ms-asx=banshee.desktop
audio/x-ms-wax=banshee.desktop
audio/x-ms-wma=banshee.desktop
audio/x-musepack=banshee.desktop
audio/x-ogg=banshee.desktop
audio/x-pn-aiff=banshee.desktop
audio/x-pn-au=banshee.desktop
audio/x-pn-wav=banshee.desktop
audio/x-pn-windows-acm=banshee.desktop
audio/x-s3m=banshee.desktop
audio/x-sbc=banshee.desktop
audio/x-scpls=banshee.desktop
audio/x-speex=banshee.desktop
audio/x-tta=banshee.desktop
audio/x-vorbis=banshee.desktop
audio/x-wav=banshee.desktop
audio/x-wavpack=banshee.desktop
audio/x-xm=banshee.desktop
image/jpeg=firefox.desktop
image/gif=firefox.desktop
image/png=firefox.desktop
image/bmp=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/tiff=eog.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
image/x-pcx=eog.desktop
image/svg+xml=eog.desktop
image/svg+xml-compressed=eog.desktop
image/vnd.wap.wbmp=eog.desktop
x-content/video-dvd=brasero.desktop
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
x-scheme-handler/ftp=firefox.desktop
x-scheme-handler/chrome=firefox.desktop
application/x-extension-htm=firefox.desktop
application/x-extension-html=firefox.desktop
application/x-extension-shtml=firefox.desktop
application/xhtml+xml=firefox.desktop
application/x-extension-xhtml=firefox.desktop
application/x-extension-xht=firefox.desktop
video/x-msvideo=vlc.desktop
application/pdf=evince.desktop
x-content/audio-player=banshee-media-player.desktop
video/3gpp=totem.desktop
audio/aac=kde4-amarok.desktop
audio/vnd.rn-realaudio=kde4-amarok.desktop
audio/x-oggflac=kde4-amarok.desktop
audio/x-pn-realaudio=kde4-amarok.desktop
x-content/blank-cd=brasero.desktop
video/x-ogm+ogg=vlc.desktop
video/dv=vlc.desktop
video/mpeg=vlc.desktop
video/x-mpeg=vlc.desktop
video/msvideo=vlc.desktop
video/quicktime=vlc.desktop
video/x-anim=vlc.desktop
video/x-avi=vlc.desktop
video/x-ms-asf=vlc.desktop
video/x-ms-wmv=vlc.desktop
video/x-nsv=vlc.desktop
video/x-flc=vlc.desktop
video/x-fli=vlc.desktop
video/x-flv=vlc.desktop
video/vnd.rn-realvideo=vlc.desktop
video/mp4=vlc.desktop
video/mp4v-es=vlc.desktop
video/mp2t=vlc.desktop
video/x-matroska=vlc.desktop
video/webm=firefox.desktop
x-content/image-dcf=shotwell.desktop
text/xml=firefox.desktop
application/xml=firefox.desktop
application/rss+xml=firefox.desktop
application/rdf+xml=firefox.desktop
application/x-xpinstall=firefox.desktop


[Added Associations]
x-scheme-handler/mailto=thunderbird.desktop;userapp-Thunderbird-QD6RDX.desktop;
message/rfc822=thunderbird.desktop;userapp-Thunderbird-QD6RDX.desktop;
application/x-extension-eml=thunderbird.desktop;userapp-Thunderbird-QD6RDX.desktop;
text/plain=libreoffice-base.desktop;apturl.desktop;nautilus-autorun-software.desktop;gedit.desktop;
audio/mp4=banshee.desktop;kde4-amarok.desktop;
audio/mpeg=banshee.desktop;kde4-amarok.desktop;
audio/mpegurl=banshee.desktop;kde4-amarok.desktop;
audio/ogg=banshee.desktop;kde4-amarok.desktop;
audio/vorbis=banshee.desktop;kde4-amarok.desktop;
audio/x-flac=banshee.desktop;kde4-amarok.desktop;
audio/x-mp3=banshee.desktop;kde4-amarok.desktop;
audio/x-mpegurl=banshee.desktop;kde4-amarok.desktop;
audio/x-ms-wma=banshee.desktop;kde4-amarok.desktop;
audio/x-musepack=banshee.desktop;kde4-amarok.desktop;
audio/x-scpls=banshee.desktop;kde4-amarok.desktop;
audio/x-speex=banshee.desktop;kde4-amarok.desktop;
audio/x-vorbis=banshee.desktop;kde4-amarok.desktop;
audio/x-wav=banshee.desktop;kde4-amarok.desktop;
image/gif=eog.desktop;
image/png=eog.desktop;
image/bmp=eog.desktop;
image/jpg=eog.desktop;
image/pjpeg=eog.desktop;
image/tiff=eog.desktop;
image/x-bmp=eog.desktop;
image/x-gray=eog.desktop;
image/x-icb=eog.desktop;
image/x-ico=eog.desktop;
image/x-png=eog.desktop;
image/x-portable-anymap=eog.desktop;
image/x-portable-bitmap=eog.desktop;
image/x-portable-graymap=eog.desktop;
image/x-portable-pixmap=eog.desktop;
image/x-xbitmap=eog.desktop;
image/x-xpixmap=eog.desktop;
image/x-pcx=eog.desktop;
image/svg+xml=eog.desktop;
image/svg+xml-compressed=eog.desktop;
image/vnd.wap.wbmp=eog.desktop;
x-content/video-dvd=brasero.desktop;
application/pdf=wine-extension-msp.desktop;firefox.desktop;evince.desktop;
x-scheme-handler/http=userapp-Firefox-IN0ABX.desktop;
x-scheme-handler/https=userapp-Firefox-IN0ABX.desktop;google-chrome.desktop;webbrowser-app.desktop;
x-scheme-handler/ftp=userapp-Firefox-IN0ABX.desktop;
x-scheme-handler/chrome=userapp-Firefox-IN0ABX.desktop;
text/html=userapp-Firefox-IN0ABX.desktop;google-chrome.desktop;webbrowser-app.desktop;
application/x-extension-htm=userapp-Firefox-IN0ABX.desktop;
application/x-extension-html=userapp-Firefox-IN0ABX.desktop;
application/x-extension-shtml=userapp-Firefox-IN0ABX.desktop;
application/xhtml+xml=userapp-Firefox-IN0ABX.desktop;webbrowser-app.desktop;
application/x-extension-xhtml=userapp-Firefox-IN0ABX.desktop;
application/x-extension-xht=userapp-Firefox-IN0ABX.desktop;
application/vnd.oasis.opendocument.text=gedit.desktop;
application/x-cd-image=vlc.desktop;
application/x-ms-dos-executable=nautilus-autorun-software.desktop;
inode/directory=nautilus.desktop;
application/octet-stream=gedit.desktop;
video/3gpp=totem.desktop;
audio/aac=kde4-amarok.desktop;
audio/vnd.rn-realaudio=kde4-amarok.desktop;
audio/x-oggflac=kde4-amarok.desktop;
audio/x-pn-realaudio=kde4-amarok.desktop;
application/x-executable=kde4-amzdownloader.desktop;
x-content/blank-cd=brasero.desktop;
application/x-trash=gedit.desktop;
video/dv=vlc.desktop;
video/mpeg=vlc.desktop;
video/x-mpeg=vlc.desktop;
video/msvideo=vlc.desktop;
video/quicktime=vlc.desktop;
video/x-anim=vlc.desktop;
video/x-avi=vlc.desktop;
video/x-ms-asf=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/x-nsv=vlc.desktop;
video/x-flc=vlc.desktop;
video/x-fli=vlc.desktop;
video/x-flv=vlc.desktop;
video/vnd.rn-realvideo=vlc.desktop;
video/mp4=vlc.desktop;
video/mp4v-es=vlc.desktop;
video/mp2t=vlc.desktop;
video/x-matroska=vlc.desktop;
video/webm=vlc.desktop;
x-content/image-dcf=shotwell.desktop;
application/x-sharedlib=gedit.desktop;
text/xml=webbrowser-app.desktop;firefox.desktop;
```

---

### Post by nmyrick on 2014-11-08
> **sammiev said:**
> I would uninstall all Google Chrome on your computer and then remove all directories and files within. Then reboot and install Google Chrome from there.

I just tried uninstalling chrome and all related files and folders that I could find in /usr/share and in /home/<username>/.config, and then rebooted and reinstalled, and I still have the same issue.

---

### Post by Bashing-om on 2014-11-08
nmyrick; Well;

I do not know:
```

sysop@1404mini:~$ cat ~/.local/share/applications/mimeapps.list
[Added Associations]
x-scheme-handler/http=exo-web-browser.desktop
x-scheme-handler/https=exo-web-browser.desktop
application/x-sharedlib=thunar-settings.desktop;
application/x-trash=gedit.desktop;
x-scheme-handler/file=exo-file-manager.desktop
x-scheme-handler/trash=exo-file-manager.desktop
application/msword=thunar-settings.desktop;gedit.desktop;
application/x-bzip=gedit.desktop;
application/vnd.openxmlformats-officedocument.wordprocessingml.document=gedit.desktop;
application/pgp-encrypted=gedit.desktop;
application/gzip=gedit.desktop;

[Default Applications]
application/x-sharedlib=thunar-settings.desktop
application/x-trash=gedit.desktop
application/msword=gedit.desktop
application/x-bzip=gedit.desktop
application/vnd.openxmlformats-officedocument.wordprocessingml.document=gedit.desktop
application/pgp-encrypted=gedit.desktop
application/gzip=gedit.desktop

sysop@1404mini:~$

```
from my minimalistic system with google-chrome as the only web browser installed.

Let's do try and follow mc4man's train of thought, as mine is a hack to make this work. I would prefer a clean solution. ( and to understand  that solution)

Off topic: Use code tags to retain the formatting for readability of terminal outputs. please:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by nmyrick on 2014-11-08
To everyone who tried to help, thank you very much! I just stumbled across the fix. I found the bad entry in my Gnome Main Menu settings.  I selected the 'Restore System Configuration' option at the bottom of the main menu settings, and then re-launched Chrome.  At that point, Chrome said that it was not the default browser, and I selected to set chrome as the default from within the browser, and it is working now, as you can see in the attachment!

---

### Post by Bashing-om on 2014-11-08
nmyrick; Great !

Pleased you have and did provide the solution. Others too I am sure will benefit .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

