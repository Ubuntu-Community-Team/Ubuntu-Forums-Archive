---
title: "Problems with Audio and video playback"
date: 2023-05-10
forum: General Help
---

### Post by tomposton on 2023-05-10
Ever since the latest updates, my VLC and Parole media players do not play DVD's and they playback cd audio with clicks and skips. The official explanations were that "your discs are encrypted and you need to download the libdvd package. Well I did all that and no joy.  Would someone please explain to me how a dvd that played perfectly fine 3 months ago suddenly became "encrypted" in a manner that the VLC player could no longer decrypt?
This is all hogwash and I suspect due to Microsofts "contributions" to the linux code. Bill Gates is a Digital Rights Management extremist and this all smacks of his desire to track every thing you put into your player. This kind of nonsense is the whole reason I switched to linux from windows in the first place. As proof of what I am saying, I wiped my system and did a reinstall from a DVD I made years ago (Ubuntu Studio) and what do you know, my dvd worked again!  But later in the week, I noticed after a shutdown these words on the screen; "unattended Update in progress, please do not shut off your computer".  And, you guessed it, dvd no longer loads to vlc or parole media players. Since WHEN does linux update without permission? (This also smacks of Windows) The problems are not limited to DVD's either, in audacity now when I import an audio track from a cd, clicks and pops are added to the audio. NEVER had this problem before. If you like Windows, just continue to allow Microsoft to "contribute". Is ANYONE checking the thousands of lines of code they are adding?

---

### Post by monkeybrain20122 on 2023-05-10
You need libdvdread, libdvdnav and libdvdcss2, libdvdcss2 is not in the repository due to DRM issue, you need to download libdvd-pkg (in the repo) and run

```
sudo dpkg-reconfigure libdvd-pkg
```

This will fetch libdvdcss2 from videolan (the guys who make vlc), compile and install it.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by tomposton on 2023-05-10
Hi,
Thanks for your reply! Entering the above into the terminal returns "libdvd-pkgsudo' is not installed and
 no information is available"

---

### Post by tomposton on 2023-05-10
When I follow the link you gave me and enter "sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg' into the terminal, I then get a message saying "libdvd-pkg is already the newest version (1.4.2-1-1).
0 upgraded, 0 newly installed, 0 to remove and 231 not upgraded.
libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed."     What gives? is it installed or not?

---

### Post by ajgreeny on 2023-05-10
So now just run the second part of that command, ie,
***sudo dpkg-reconfigure libdvd-pkg***
and see if that works.

Your dual command with the && separating the two parts means the second part is executed only if the first part of the command is successful.
In your case the install failed as it was already installed so everything ground to a halt with no reconfiguration carried out.

---

### Post by tomposton on 2023-05-10
Did that and now the terminal says "libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed."     Makes no sense, and why is the terminal calling it a "guest package"?  By the way, when this whole thing started, before I started this thread, I had already tried this procedure to try and get libdvdcss2 and after entering the commands a screen pops up asking if  I want it to be able to automatically update and I chose no because I do not want anything to update without me knowing what and why. That is the main reason I left windows, if my computer works for me, then please leave it alone and don't cause bugs and non-functionality by updating codes or drivers.

---

### Post by ajgreeny on 2023-05-11
I see you have 231 packages that need updating so run command```
sudo apt update && sudo apt full-upgrade
```to make sure your system is fully up to date.

You should make sure this or equivalent GUI method is carried out regularly to keep everything updated.
If this is not succesful I am jot sure what is wrong; I haven't used a commercial DVD for many years and my machines no longer have working DVD drives.

---

### Post by tomposton on 2023-05-11
While I appreciate the attempts to help me, I guess my question really is "how can I install my old version of Ubuntu and have it be left alone by the powers that be?"  The previous version of VLC that was in the Old Ubuntu knew how to decrypt all my dvds, it doesn't need an update to do something it already is capable of! I don't want updates, that is how I got here. My version of Ubuntu was fully functional and great at doing all the tasks I need it to do, but now clicks and pops are added to audio that I import. I am a recording engineer, and I regularly send audio tracks to my customers, different mixes of the songs they record with me for approval. (for which, I might add, they pay a licensing fee if the songs are not original, so no violation of intellectual property). These buggy updates are a never-ending treadmill of functionality problems that I cannot afford to to get on. This was the whole reason I switched to Ubuntu Studio to begin with. Since microsoft became the largest contributor to the Linux code, things are progressing rapidly toward an operating system that is controlled by others who could care less if their "update" crashes a program that the user needs to work in order to make a living.  It still amazes me that developers cannot grasp the consequences of their actions for the end user.  On a side note, how can you "see" that I have 231 packages that need updating?  That is disturbing on a number of levels. I am just going to remove the internet card from my computer, wipe the hard drive, reinstall and never, ever let my workstation access the internet again.

---

### Post by ajgreeny on 2023-05-11
It wasn't VLC that decrypted the DVD  videos but libdvdcss that allowed it to do so.

I am not aware that a reboot is required in order to allow libdvdcss to do its job but it may be worth doing so before anything further.
Using an older version of Ubuntu or VLC is very unlikely to help you.

---

### Post by tomposton on 2023-05-11
I already stated above, that when I do a fresh install from a DVD that I made years ago, VLC and Parole media players immediately work as intended, they only failed after I caught the machine saying "unattended update in progress, please don't shut off your computer." after I had shut down. libdvdcss is only a library that evidently came preinstalled in the older version I have, it is not a program that actually does any decrypting ,but a library of keys. This IS an update problem and an older version DOES fix things if I can keep the powers that be from messing it up.

---

