---
title: "network videoi"
date: 2007-03-17
forum: General Help
---

### Post by bruce1354 on 2007-03-17
I have not been able to play avi files across my wireless network in Ubuntu.

Two players that should work do nothing when asked to open the file.

I do this easily in windows currently on the same machine. Copy the file to the local machine and it is no problem for Totem.

Any advice?


Thanks,

bruce

---

### Post by pt123 on 2007-03-17
Have your tried VLC?

---

### Post by bruce1354 on 2007-03-17
I'm not sure what that is. Where do I go to read all about a VLC please?

---

### Post by r4ik on 2007-03-17
Try,

[http://www.videolan.org/](http://www.videolan.org/)

Good luck !

---

### Post by bruce1354 on 2007-03-17
Same exact problem. I can browse graphically to the file I want to open, select the file, open with other applications.....vlc.....open....and then it blinks and does nothing. 

I'm not sure how to browse to this file from the File..Quick Open File screen. Can I? Its on another machine on my network.

---

### Post by peabody on 2007-03-17
This seems to be an issue with how Gnome works with smb shares.  As far as I can tell, if you mount a share under the GNOME connect to remote server tool, it doesn't actually mount it anywhere in the VFS.  I don't know how it actually works.

If one does a "sudo aptitude install smbfs" and then a "mount -t smbfs //netbiosname/share mountpoint -o username=blah,password=blah" this does actually mount the share in the VFS, and every program has access to it.

How does GNOME's connect to server thingy work anyway?

EDIT: I wonder if it is at all related to this?
[http://www.ubuntuforums.org/showthread.php?t=315333](http://www.ubuntuforums.org/showthread.php?t=315333)

---

### Post by pt123 on 2007-03-17
Use Xine Video player

Choose Open Location

Click on SMB (Samba window sharing)

Then you can browse to the computer the video is, and play it as a stream.

It worked for me just then

---

### Post by bruce1354 on 2007-03-17
Would someone help me edit smb-module.conf? I have a permissions problems saving and cant seem to log in as root or use sudo properly.

I'm feeling pretty noobe right now. Whats the line editor called in the terminal windo?

---

### Post by peabody on 2007-03-17
> **bruce1354 said:**
> Would someone help me edit smb-module.conf? I have a permissions problems saving and cant seem to log in as root or use sudo properly.

I'm feeling pretty noobe right now. Whats the line editor called in the terminal windo?

from within a terminal

sudo gedit /path/to/file

Although, I tried that and it didn't fix the problem for me.

---

### Post by bruce1354 on 2007-03-17
Well I got that far with xine...but it won't play xvid.

there is no mrl...missing codec

Do I look for a codec? Install from synaptic mebbe??

---

### Post by pt123 on 2007-03-18
Install all the extra codecs 

sudo aptitude install xine-ui libxine-extracodecs

---

### Post by bruce1354 on 2007-03-18
woop!

ladies and gentlemen...we have just replaced windows

Thank yee very much

bruce

---

