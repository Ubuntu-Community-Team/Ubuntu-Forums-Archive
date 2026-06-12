---
title: "Setting a WINE app as the default"
date: 2007-03-26
forum: General Help
---

### Post by Stonecougar on 2007-03-26
...As in, can it be done? I've gotten Irfanview to work quite smoothly in WINE, but I'm looking for a way to set it up as the default picture viewer for this system. Is this doable, or a pipe dream? 

Wow, I've been active here all of a sudden... I guess trying to convert a Windows user kind of spurs the learning process. ;)

---

### Post by dcstar on 2007-03-26
> **Stonecougar said:**
> ...As in, can it be done? I've gotten Irfanview to work quite smoothly in WINE, but I'm looking for a way to set it up as the default picture viewer for this system. Is this doable, or a pipe dream? 

Wow, I've been active here all of a sudden... I guess trying to convert a Windows user kind of spurs the learning process. ;)

You can set up anything by editing the "Open with" setting for a particular file type.

For your requirement, it would be something like "wine infranview".

---

### Post by Stonecougar on 2007-03-26
I tried that... it seems to have taken the "wine" command as the program I want to open the file with, e.g., I type in the custom command "wine irfanview" and the "Open with" function sees "wine". I tried to just use the irfanview .exe file, but that didn't work either. Am I entering in the command incorrectly? Or is this just one little sticking point that Ubuntu isn't likely to budge on?

---

### Post by Lord Illidan on 2007-03-26
> **Stonecougar said:**
> I tried that... it seems to have taken the "wine" command as the program I want to open the file with, e.g., I type in the custom command "wine irfanview" and the "Open with" function sees "wine". I tried to just use the irfanview .exe file, but that didn't work either. Am I entering in the command incorrectly? Or is this just one little sticking point that Ubuntu isn't likely to budge on?

You have to put in the entire path to the irfanview .exe, which could be in the depths of your home directory.

---

### Post by Stonecougar on 2007-03-26
Ah ha... I'll go give that a shot, then. Thanks!

Edit: That didn't seem to work... Wine set up its own little run-jobby for it, ./iview. I tried running it off the .exe that it would have used in Windows, but since Wine doesn't recognize that as the primary executable file, it's not working.

---

### Post by dcstar on 2007-03-26
> **Stonecougar said:**
> Ah ha... I'll go give that a shot, then. Thanks!

Edit: That didn't seem to work... Wine set up its own little run-jobby for it, ./iview. I tried running it off the .exe that it would have used in Windows, but since Wine doesn't recognize that as the primary executable file, it's not working.

You will probably need the full wine path to where is it installed, something like:

"c:/program files/infranview.exe" (or whatever it is on your system).

---

### Post by Stonecougar on 2007-03-26
Well, I managed to get it to open Irfanview, but not the file in question. Wine has a special command for Irfanview; for some reason, it's not pointing to the file in the Wine files. The .exe file is "i_view32.exe" but to run it through Wine, I run "./iview". I tried to run the aforementioned .exe file, but it wouldn't work. There's no executable that Wine recognizes to run a path to. So now, when feeding it through the "Open With" section, I can convince it to open Irfanview, but as a blank slate, with no file open. And I still can't do even that as a default application.

Edit: I remember now what I did... I followed a how-to at [http://www.linuxforums.org/forum/suse-linux-help/70387-howto-semipainless-installation-irfanview-suse-10-1-a.html](http://www.linuxforums.org/forum/suse-linux-help/70387-howto-semipainless-installation-irfanview-suse-10-1-a.html) and wound up writing a script to launch the program with. I can get it to open Irfanview alongside the photo, which opens in gThumb. However, the presence or absence of that script doesn't seem to be making much of a difference.

It works fine as long as I'm willing to open IrfanView and then use the File-Open... command. But I'd like to not have to. ](*,)

---

