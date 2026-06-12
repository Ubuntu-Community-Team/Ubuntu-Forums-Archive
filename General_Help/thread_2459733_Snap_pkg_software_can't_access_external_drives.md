---
title: "Snap pkg software can't access external drives"
date: 2021-03-24
forum: General Help
---

### Post by Brent_Santin on 2021-03-24
I have a newly setup Lubuntu 20.04 computer with two internal hard drives. One is the main drive that Lubuntu installed itself on. That drive is one large partition. The second physical hard drive is my "media" drive, which contains all my videos, music, etc. (hundreds of files).

On my previous Lubuntu 18.04 computer (which I just retired last week after setting up this new computer and transplanting the "media" drive into the new computer) I was always able to use Puddletag (an mp3/mp4 tag editor) to edit the metadata on any of the media files stored on the media drive.

I installed Puddletag from the software centre on this new computer (it was a Snap package), and tried to do the same. I was surprised to find that not only could Puddletag not access files from the media drive (with a drag and drop of the file), but neither could it even "see" the media drive through its "load files" dropdown menu file browser. The only way I was able to edit a file was to first copy it to my home directory, but this is awkward and not feasible when working with larger numbers of files.

Doing a bit of reading online, I learned that any software installed using a snap package only has permission to access files in the "home" directory.

Wow! Maybe that's good from a security standpoint (I don't know) but it makes it super awkward to use Snap installed software for me. I guess I was able to do it on my previous 18.04 computer because the version of Puddletag there was not a Snap package.

Is there any way around this awkward limitation?

Thanks.

---

### Post by CatKiller on 2021-03-24
[https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)

---

### Post by Brent_Santin on 2021-03-24
Thanks. That article was very helpful. Lubuntu uses the package manager "store" called "Discover" which appears to be a bit buggy. When I try to use the "Configure Permissions" button in it for the snap package I've installed Discover hangs.
I'll have to learn how to do it through the command line, apparently using the command:

**[FONT=courier new]snap connections puddletag-snap[/FONT]**

which shows me the following:
```
[FONT=courier new]
[/FONT][B][FONT=courier new]brent@i5tower:~$ snap connections puddletag-snap
Interface                             Plug                                  Slot                                                  Notes
content[icon-themes]                  puddletag-snap:icon-themes            gtk-common-themes:icon-themes                         -
content[kde-frameworks-5-core18-all]  puddletag-snap:kde-frameworks-5-plug  kde-frameworks-5-core18:kde-frameworks-5-core18-slot  -
content[sound-themes]                 puddletag-snap:sound-themes           gtk-common-themes:sound-themes                        -
desktop                               puddletag-snap:desktop                :desktop                                              -
desktop-legacy                        puddletag-snap:desktop-legacy         :desktop-legacy                                       -
home                                  puddletag-snap:home                   :home                                                 -
network                               puddletag-snap:network                :network                                              -
wayland                               puddletag-snap:wayland                :wayland                                              -
x11                                   puddletag-snap:x11                    :x11                                                  -
[/FONT][/B]
```
I'm not new to the command line but this is just slightly foreign territory to me...I'll learn.

---

### Post by Dennis N on 2021-03-25
> I'll have to learn how to do it through the command line...

Many snaps can optionally access usb drives which mount under /media/<user>, and access other partitions mounted under /mnt. These snaps all support the '**removable-media**' interface. It would show in the first column. Your display doesn't show that interface, and I don't believe the end-user can add it.

Note: sometimes, an interface is supported, but not connected. But, even if not connected, the command you used would still show it under 'Interface'. That's not the case with puddletag-snap.

[B]snap connections <snap>
[/B]Lists connected and unconnected plugs and slots for the specified snap.

---

### Post by CatKiller on 2021-03-25
The snap is listed as "unofficial," so it's not provided by the developers, just by someone who wanted a snap. It could be worth contacting the packager to get them to implement the removable-media interface, or contacting the developers to get them to take over the packaging of the snap.

---

### Post by TheFu on 2021-03-25
In the meantime, you can use **EasyTag**.  Just be certain to install the non-Snap version. Life will be good.
Or find a version of the program you like that isn't a snap. I'd check whether the project team makes packages and try to use one of those. A PPA would be preferred, but for a tag editor, I'm not really worried about internet hacks any more than I would be for a calculator.

From the current _Linux File System Hierarchy Standards_ document:
[LIST]
[*]/media: [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html)
> This directory contains subdirectories which are used as mount points for **removable media** such as floppy disks, cdroms and zip disks.

[*]/mnt: [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s12.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s12.html)
> This directory is provided so that the system administrator may **temporarily mount** a filesystem as needed.

[/LIST]

The way that snap packages limit extra storage to those two places shows clearly that they haven't read or don't understand or don't care about standards.  Don't get me started about hard coding /home/  - any place can be a HOME directory as long as the **getent passwd** returns the location. Snaps shouldn't be hard-coding /home or preventing NFS from being used for HOME directories which is the current situation with all snaps.

Bad news. [https://docs.puddletag.net/download.html#installing-on-ubuntu](https://docs.puddletag.net/download.html#installing-on-ubuntu) says to get the current version from Software Center.
```
$ sudo apt search puddletag
Sorting... Done
Full Text Search... Done
```
So there isn't any normal APT package. Booooo.

```
$ sudo snap search puddletag
Name            Version  Publisher   Notes  Summary
puddletag-snap  2.0.1    tschlaeppi  -      puddletag is an audio tag editor for GNU/Linux
```
shows that the snap is the way they want people to use it.

In theory, after they modify the snap package to allow removeable-media permissions, you'll get the updated snap, probably will need to enable that connection, and will need to mount your media files into the locations approved, regardless of standards, by the snap design team.
[https://github.com/puddletag/puddletag/issues/585](https://github.com/puddletag/puddletag/issues/585) has the issue opened for the snap package already.  A "me too" in that issue would probably help. I think the problem is purely a packaging issue, not something internal to their code - but I didn't look at the code.

I do know that EasyTag doesn't have that problem.

---

