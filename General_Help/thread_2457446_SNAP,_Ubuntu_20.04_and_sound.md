---
title: "SNAP, Ubuntu 20.04 and sound"
date: 2021-02-02
forum: General Help
---

### Post by Dr._B on 2021-02-02
Due to changes in our works IT setup I had to upgrade to a version 78 of Thunderbird, which in the current LTS instillation appears to only be available as a SNAP distribution. While I had no issues installing the SNAP and transferring over my old profile, I am having one issue - I no longer get audio notifications for things like new emails and calendar alerts. I've tried changing from the default sound to a custom sound file (both MP3 and WAV formatted), with no luck.

When I run the command "snap interface audio-playback", thunderbird is in the list of apps. When I run the command "snap connections thunderbird" I get the following output:
```
Interface                 Plug                         Slot                             Notes
audio-playback            thunderbird:audio-playback   :audio-playback                  -
avahi-observe             thunderbird:avahi-observe    -                                -
browser-support           thunderbird:browser-sandbox  :browser-support                 -
camera                    thunderbird:camera           -                                -
content[gnome-3-34-1804]  thunderbird:gnome-3-34-1804  gnome-3-34-1804:gnome-3-34-1804  -
content[gtk-3-themes]     thunderbird:gtk-3-themes     gtk-common-themes:gtk-3-themes   -
content[icon-themes]      thunderbird:icon-themes      gtk-common-themes:icon-themes    -
content[sound-themes]     thunderbird:sound-themes     gtk-common-themes:sound-themes   -
cups-control              thunderbird:cups-control     :cups-control                    -
desktop                   thunderbird:desktop          :desktop                         -
desktop-legacy            thunderbird:desktop-legacy   :desktop-legacy                  -
gpg-keys                  thunderbird:gpg-keys         -                                -
gsettings                 thunderbird:gsettings        :gsettings                       -
home                      thunderbird:home             :home                            -
network                   thunderbird:network          :network                         -
network-control           thunderbird:network-control  -                                -
opengl                    thunderbird:opengl           :opengl                          -
removable-media           thunderbird:removable-media  -                                -
wayland                   thunderbird:wayland          :wayland                         -
x11                       thunderbird:x11              :x11 
```

I'm pretty sure the second line means that it should have access to sound. I've also checked my sound settings in ubuntu and the system sounds volume is at 100%. Audio from other programs also work properly, including audacity and vlc; both of which are installed via SNAP and which show in the list of SNAPs given access to the audio-playback interface.

Any ideas how to make it work? The pop-up notifications for thunderbird are working properly.

Thanks

Bryan

---

### Post by howefield on 2021-02-02
I don not use Thunderbird but just wondering if the sandboxing feature of snap packages means that it cannot see the media file.

Have you tried placing the media file according to what the snap can see, as it were.

---

### Post by Dr._B on 2021-02-02
That was an interesting thought, so I moved the file into the sandbox and redirected thunderbird to the new file location. It doesn't seem to work, but also the file location is bizarre. After selecting the file, thunderbird shows it in:

```
 file:///run/user/1000/doc/e985a51/emailAlert.wav
```

Its actually located in
```
/home/bryan/snap/thunderbird/common/.thunderbird/emailAlert.wav
```

Maybe that's the issue?

---

### Post by dinkidonk on 2021-02-02
I'm not sure how Thunderbird plays audio, but there are interfaces specifically for "alsa" and "pulse-audio" which may need to be added. Also, the interface "personal-files" may be required to access an audio file in you home folder. If Thunderbird uses an external program (other than xdg-open) to play the sound files this is AFAIK restricted.

---

### Post by Dr._B on 2021-02-02
If I try to connect to alsa or pulse audio using "sudo snap connect thunderbird:alsa :alsa" (or pulse-audio) I get the same error:

snap "thunderbird" has no plug named "alsa"

---

### Post by dinkidonk on 2021-02-02
The [interfaces exists](https://snapcraft.io/docs/supported-interfaces), if TB has no plug for them TB does not use them.

---

### Post by ajgreeny on 2021-02-02
It is possible to add and enable a PPA repository to get T'Bird 78 and install it in the usual .deb package manner.
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)
I have never used this PPA but I do have others enabled, eg LibreOffice PPA which gives me LO 7.0.4.2; this works very well.

I have to admit that I have no idea about sound notifications from T'Bird as I have never used them nor wanted them so I can't help with that problem, but the PPA may be worth trying; if it works for you that's great, if it doesn't work you can always disable the PPA and revert either to the snap version of the default repository version.

Just in case you were not aware of this, you can also download and use the .tar.bz2 archive version of T'Bird by running it directly from the executable file in the extracted archive.
[https://download.mozilla.org/?product=thunderbird-78.7.0-SSL&os=linux64&lang=en-GB](https://download.mozilla.org/?product=thunderbird-78.7.0-SSL&os=linux64&lang=en-GB)
This will unfortunately not upgrade automatically but can be managed manually by replacing the extracted archive.

---

### Post by Dr._B on 2021-02-03
The PPA saved the day! Sound works, accounts work, everything is good.

B

---

### Post by ajgreeny on 2021-02-04
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

