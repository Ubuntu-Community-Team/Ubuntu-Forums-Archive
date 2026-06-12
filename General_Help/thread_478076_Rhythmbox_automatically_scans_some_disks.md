---
title: "Rhythmbox automatically scans some disks"
date: 2007-06-18
forum: General Help
---

### Post by vadania on 2007-06-18
Hello I use Ubuntu 7.04 with gnome 2.18 and KDE 3.5.6.

I have a problem with Rhythmbox: every time I use Rhythmbox application and I plug in my usb stick, Rhythmbox starts to scan automatically all the files on the stick, thinking I want to Import some music from the stick to its music library.

The problem is I have no music on the stick, but large quantities of data (about 8GB). This scanning takes quite some time to process and I is a big halt to system performance. Also I cannot safely unplug the stick while Rhythmbox is running.

I have to choose now between listening to music and using my stick.

By the way, how do I see what processes use the usb stick at a given time?

---

### Post by forger on 2007-07-27
menu: system > preferences > removable drives and media
click on multimedia tab > uncheck (untick, remove the checkmark) where it says "Play music files when connected"

oh the usb unplugging takes some time, because linux caches a lot of files when you're done doing everything you want, so when you want to unmount/unplug the usb, you have to right click on its desktop, click unmount volume and wait until the icon is gone

---

### Post by vadania on 2007-08-05
That setting is unticked! Please see below:
[[IMG]http://img460.imageshack.us/img460/5383/screenshotremovabledrivma3.th.png[/IMG]](http://img460.imageshack.us/my.php?image=screenshotremovabledrivma3.png)

Here's the effect: Rythmbox still scans my usb, finds lots of PDF files and reports the PDF files as unrecognized:
[[IMG]http://img460.imageshack.us/img460/1629/screenshotrythmboxjq0.th.png[/IMG]](http://img460.imageshack.us/my.php?image=screenshotrythmboxjq0.png)

Please note I have 8 GB data on my stick so it takes a lot of time to scan all those files.
It would be nice if Rythmbox could just take into account the extension of the files (scanning a .pdf is useless anyway, so why do it?)

Now I'm pretty sure it's a problem related to Rythmbox, not the configuration of my Desktop.

---

### Post by .Ix on 2008-02-05
BUMP

i really need an answer to this too, because it scans my 80gb DAP every time i plug it in, and there's a whole ton of files in there so it takes an eternity to scan.

the problem is not with rhythmbox opening whenever the drive is plugged in. here's how it happens:

1. Rhythmbox is running and i'm listening to music.
2. i plug my DAP in.
3. Rhythmbox scans the drive and basically freezes.
4. i have to force quit Rhythmbox or else i'll never get anything done.

is there a way to disable this auto-scan feature? i can't find it in the Preferences.

---

### Post by BadElvis on 2008-05-02
This is really annoying, i face the same problem. I only want to listen to a few music tracks from my external HD.

If I plug in my external HD, Rhythmbox starts scanning tons of music files and I am unable to use the program, because it is busy.

Then again, after scanning: if I happen to use Rhythmbox without my external HD being plugged, removes all the files, that ar eno longer present -> freezes again.

Please, does anybody know how to disable this or is there a good alternative? I use Ubuntu Hardy. Thanks in advance!

---

