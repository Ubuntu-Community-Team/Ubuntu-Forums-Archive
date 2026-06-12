---
title: "Custom USB Drive icons in Ubuntu (or any linux)?"
date: 2014-10-13
forum: General Help
---

### Post by myrkat on 2014-10-13
I use several USB sticks and a couple USB hard drives, I would like them to have their own visually-synchronized icons as they are plugged in; I can make or get the icons, but my search-fu has turned up ZILCH for doing this under linux distros (I use Mint 17 KDE on my desktop and Ubuntu 14.04 LTS Unity on my System 76 laptop).  Under Windows, this is easy to accomplish with the autorun.inf "trick".

Is this something that linux does not do, or at least the Desktop Environments do not do at this time?  (Again, I use KDE and Unity)

---

### Post by Vladlenin5000 on 2014-10-13
It's possible but seldom used.

I just checked a multi ISO installation dongle I've made with *Multisystem* and it has a custom icon which is simply a hidden "icon.ico" file (see attachment).

---

### Post by myrkat on 2014-10-14
Thank you for your reply, Vladlenin5000!

When you say "hidden" do you mean as in a microsoft (FAT32/NTFS) hidden attribute?  Or was it named .icon.ico (leading period for *nix hidden)?

Also, where was this icon file on the USB device?  I tried just having one in the root ( / ) of the USB drive/stick, and it doesn't seem to show up in either KDE or Unity (the two DE's I'm using).

My search continues.  One would think something this simple would have more presence on the web...

---

### Post by Vladlenin5000 on 2014-10-14
Hidden as in .icon.ico, indeed. And it was just sitting in the root of the drive.

Now that you the mentioned it, I went there again and found also - surprisingly - an hidden 'autorun.inf' with the following content:
```
[AutoRun] 
ICON=icon.ico 
Label=MultiSystem 
 
[Content] 
MusicFiles=false 
PictureFiles=false 
VideoFiles=false
```


PS - Also a 'multisystem.bat' which I think is irrelevant for the discussion here and probably software specific.

---

