---
title: "Snap Program can't access USB stick."
date: 2020-01-30
forum: General Help
---

### Post by denverdecoy on 2020-01-30
I added a 64GB USB Stick to one of my USB ports for additional storage and one of my snap programs cannot access it.  The USB seems to be located in "/Media/User/" and when I click on "Media" from within the snap program I get a "Permission denied" message.

I read online that you can change the permission for the snap program within the Ubuntu Software app, but the only permission that shows up is "Access files in your home folder" which I have enabled. There is no additional permission to "Read/Write files to removable storage" permission at all, as some have suggested.

Is there a manual way I can specify a particular Snap I would like to have access to the removable USB?

Thanks

**Note: I am running Ubuntu 19.10**

---

### Post by TheFu on 2020-01-30
[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)
# Hook up snaps to access removable-media
    # snapd v2.36+.
```
snap connect chromium:removable-media
```
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface) has more

Whether any snap will allow connections to removable media is controlled by the snap package team.
Currently, there is no way to allow a snap package to access data in other directories or over NFS mounts that aren't mounted either under /mnt/ or /media/ directories.  This is a huge failure in the snap deployment capabilities.

---

### Post by denverdecoy on 2020-01-30
Thanks for the quick response, and if it says

  error: snap "liteide-tpaw" has no plug named "removable-media"

What does that mean? Thanks again

---

### Post by Dennis N on 2020-01-30
You can check it removable-media access is available:

Run "snap connections" in terminal, and look for "removable-media" under "Interface". If your application is shown in the "Plug" column, it is capable of access.
```
dmn@Tyana:~$ snap connections
Interface                 Plug                                       Slot                             Notes
audio-playback            chromium:audio-playback                    :audio-playback                  -
avahi-observe             firefox:avahi-observe                      :avahi-observe                   -
browser-support           chromium:browser-sandbox                   :browser-support                 -
browser-support           firefox:browser-sandbox                    :browser-support                 -
browser-support           gnome-characters:browser-support           :browser-support                 -
camera                    chromium:camera                            :camera                          -
camera                    firefox:camera                             :camera                          -
[lines omitted]
removable-media           chromium:removable-media                   :removable-media                 manual
removable-media           firefox:removable-media                    :removable-media                 manual
[more lines omitted]

```
On this computer, only chromium and firefox can have this kind of access.
If the third column isn't blank, then it's connected. 'Manual' means it was manually connected (enabled) by the user.
If your application is not shown in the "Plug" column, you are out of luck.

"removable-media" also now includes access to /mnt

---

### Post by denverdecoy on 2020-01-30
Ok, I ran that and "removable-media" doesnt appear anywhere, so I guess none of my snap programs can access the USB? That seems silly.

I guess I have to figure out how to install LiteIDE manually? I got it working once before but I was unable to attach it to the "favorites" launcher, Ubuntu is great but some of the simple stuff seems overly complicated.

---

### Post by Dennis N on 2020-01-30
```
Ok, I ran that and "removable-media" doesnt appear anywhere, so I guess none of my snap programs can access the USB? That seems silly.
```
Not unless you can mount the USB in your home folder. Then you would have access provided your application has a plug for the "home" interface.

---

