---
title: "Few issues with Ubuntu 12.04"
date: 2013-08-25
forum: General Help
---

### Post by davy jones on 2013-08-25
I've been using Ubuntu 12.04.2 for a couple of months now, and there are few minor issues which are bugging me, and it would be good to have a fix.

1. In Firefox, clicking on a torrent download link does not give me an "Open With Transmission" option.

2. Another Firefox issue, one that I faced in 11.04 as well. Even though in the Preferences->Applications section I've set the preference of what to do with mp3 files as "Always Ask", it never asks me and automatically starts to play the file.

3. Nautilus windows opened from other applications for the purpose of selecting files to open, or folders where I want to save files, are always unmaximised. This is a little annoying because my laptop screen is such that the bottom of these windows, where the "Open" and "Cancel" buttons are, is not visible. If I maximise the window or change the size of the window, these changes are not remembered.

4. Another Nautilus issue is that certain window settings are not remembered. In List View, if I expand one of the columns, this setting is not remembered.

5. Banshee does not update the music library on its own. Now I faced this problem with 11.04 as well but at least there I could just click on "Rescan Library" and it would update it. This does not seem to work in 12.04 and I've to import the whole library every time.

6. In the Brightness and Lock settings, even if I set the "Lock screen after" time to 1 hour, it always locks it according to the time I've set against "Turn screen off after".

---

### Post by tripp98 on 2013-08-25
1 - Open firefox/Edit/Preferences/Applications  magnet set it to use /usr/bin/transmission-gtk

2 - enter **about:config** into the firefox address bar (confirm the info message in case it shows up) & search for the preference named **media.windows-media-foundation.enabled**. double-click it and change its value to **false**.

there is a few answers.

---

### Post by davy jones on 2013-08-29
It was already set to Transmission gtk in the preferences and there is no preference named **media.windows-media-foundation.enabled**. in about:config.

---

### Post by eljw926 on 2013-08-29
How do I set the preference magnet to /usr...???  I click use other and it takes me to "recently used" don't know how to find/set /usr/bin  Ok, got it set, thanks.

---

### Post by speartip on 2013-08-29
1. Check here, the answer is the 5th post down by CoffeeTime.
[http://www.pclinuxos.com/forum/index.php?topic=103267.0](http://www.pclinuxos.com/forum/index.php?topic=103267.0)

3. This Is a bug that some of us have that has not been fixed. 13.04 is ok but not 12.04. All I can suggest is open the app minimized, then drag the edges out so it fills most of your screen. This should be remembered on reopening.

5. Where do your keep your Music? If it is on a seperate partition or drive, this needs to be mounted in fstab to stop the need for rescanning everytime.

Sorry can't help with your other issues.

---

### Post by davy jones on 2013-09-01
I followed the instructions on that post, and magnet links are automatically being opened by Transmission, but when I click on the "download torrent file" option, it still does not give me an "open with" option. It only gives a "Save file" option.

And yes, I keep my music on a separate partition. Can you please guide me on how to mount it in fstab? Because I've already used Mount Manager to make that partition automatically mount on startup.

---

### Post by speartip on 2013-09-01
Magnet problem - Once you have followed the instructions above, go to firefox/edit/preferences/applications. Scroll down to magnet, & set to either "always ask" or to whatever program you want to use to open magnet links.

You 2nd issue is a bit more in depth. First check your fstab file to make sure the partition you're using isn't already being mounted.
If it isn't you could follow this guide:
[http://www.binarytides.com/ubuntu-automatically-mount-partition-startup/](http://www.binarytides.com/ubuntu-automatically-mount-partition-startup/)
If you find this too difficult, if you post back with the partition no. ie sda1/2/3etc... the uuid of the partition, & what format it is, ie NTFS, ext4 etc...
I will post back with the commands you need to use in a terminal to make it mount at boot.
Banshee then shouldn't have a problem.

---

### Post by davy jones on 2013-09-02
The partition actually does mount on boot. I've set it to that using Mount Manager. The partition number is sda12 and the UUID is 365315F110F42CE7. It is an NFTS partition.

And again, while the issue with the magnet link is sorted, clicking on "download torrent file" still does not give me an "Open with" option.

---

### Post by speartip on 2013-09-02
Hi davy,

Just check that the partition is listed correctly in /etc/fstab. It should look something like this. (this is mine of course)
UUID=1c34a1fc-3d30-4fe7-bd1e-174c810e6451 /storage        ext4    defaults        0       0
If it does, then Banshee should have no need to rescan your full library on opening.

You torrent file problem I have looked at again, & that is correct. If you are "downloading" the torrent file, then it will only ask you where you want it downloading to.
You then need to right click the torrent file, & open it with your desired program.

---

### Post by davy jones on 2013-09-03
This is how it looks -

UUID=365315F110F42CE7 /media/Data ntfs-3g defaults 0 0

---

### Post by protoss96 on 2013-09-03
About magnet links, you can copy torrent link location and paste that URL into transmission client, but you should use utorrent for linux.

---

### Post by davy jones on 2013-09-22
There are several more issues that I'm facing with Ubuntu 12.04. 

1. In earlier versions of Ubuntu, there was an "Emblems" option in the Properties of any file, which is not there anymore. Is there any way to get that back?

2. I have a dual boot system with Ubuntu running alongside Windows 8. But I've to go into the BIOS every time and switch between UEFI and Legacy for Windows and Ubuntu respectively. Is there any way to have GRUB ask me on startup which OS I want to boot into without having to reinstall Ubuntu?

3. Because of the dual boot thing, another problem I've been having is that everytime I boot into Windows after having booted into Ubuntu, the time on the clock is reset to UTC.

4. On many occasions, when I boot into Windows 8 after having booted into Ubuntu, the system gives some error and restarts.

---

