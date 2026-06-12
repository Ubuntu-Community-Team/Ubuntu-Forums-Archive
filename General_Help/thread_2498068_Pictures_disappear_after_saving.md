---
title: "Pictures disappear after saving"
date: 2024-05-29
forum: General Help
---

### Post by mussassa on 2024-05-29
Hello
I recently installed Ubuntu 24.04 and I have a portable drive that has an nfts partition. When I save pictures/images to the nfts partition they disappear. I search for them in the folder and I can't find it but I can open from the download section of the browser. The older images are still there just the new ones that I have tried to download that disappeared.

---

### Post by Impavidus on 2024-05-30
I've often heard of files disappearing from removable NTFS filesystems, but usually when you remove the drive and plug it back later, in particular when moving between Ubuntu and Windows. But from your post I get the impression that the files disappear without removing the drive: you use the webbrowser to save a downloaded file there, then the file manager never sees it. Could it be that the webbrowser actually saves the file somewhere else? I could be wrong, but I thought that on recent Ubuntu releases the standard webbrowser, Firefox, being a snap package, can't even save files on removable drives.

---

### Post by mussassa on 2024-05-31
> **Impavidus said:**
> I've often heard of files disappearing from removable NTFS filesystems, but usually when you remove the drive and plug it back later, in particular when moving between Ubuntu and Windows. But from your post I get the impression that the files disappear without removing the drive: you use the webbrowser to save a downloaded file there, then the file manager never sees it. Could it be that the webbrowser actually saves the file somewhere else? I could be wrong, but I thought that on recent Ubuntu releases the standard webbrowser, Firefox, being a snap package, can't even save files on removable drives.
I used Brave browser to save the images, it is snap (but I don't know what that means). I have checked the folder path and it is on the nfts drive. I also downloaded to the images to the linux partition and copied to the nfts drive and I was asked if I want to replace the files, so the files are there but they are not visible. I also tried on the terminal/command line, I used dir and ls and it doesn´t show the files.

---

### Post by HermanAB on 2024-05-31
Hmm, don’t use snap packages.  The people who make snaps are lazy to test it properly so they never work quite right.

---

### Post by The Cog on 2024-05-31
Snap packages can't read or write outside of your home directory, and cannot read or write a different partition even if it is mounted inside your home partition. But they don't bother to tell you that anything didn't work when you try - they just leave you to find out later. They call it a "security feature", I gather. It's not that it's NTFS in this instance, it's just that it's not the drive that your home directory lives on.

---

### Post by Impavidus on 2024-05-31
So it's suggested that the files are there. Does ls -a show the files?

No snaps on my system, but I understand that snaps can be configured to be able to write to stuff mounted in /media – configured by the creator of the snap package.

---

### Post by mussassa on 2024-06-01
> **Impavidus said:**
> So it's suggested that the files are there. Does ls -a show the files?

No snaps on my system, but I understand that snaps can be configured to be able to write to stuff mounted in /media – configured by the creator of the snap package.
No it doesn't show the files.

---

### Post by mussassa on 2024-06-01
> **Impavidus said:**
> So it's suggested that the files are there. Does ls -a show the files?

No snaps on my system, but I understand that snaps can be configured to be able to write to stuff mounted in /media – configured by the creator of the snap package.
I uninstalled the snap installation and installed from the terminal and now is saving.

---

