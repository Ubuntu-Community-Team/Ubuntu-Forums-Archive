---
title: "Ext3 &amp; File Extensions"
date: 2007-10-03
forum: General Help
---

### Post by Geekkit on 2007-10-03
I have an question about ext3 ...

I'm using Ubuntu 7.04 and I have a Web-based e-mail application that allows me to download attachments. Sometimes when I do this the Web-based e-mail application (Domino Notes) doesn't provide the actual name of the file being downloaded (e.g., src.zip). Specifically the download does not include a file extension.

And yet, in Nautilus it shows up as the original type, for example a zip file. Archive manager knows what to do with it ... and yet, no file extension. As far as I know ext3 is a low-level file system (i.e, stream-block transfer), not a high-level file system (i.e., providing record-stream translation) like the Mac FS.

Or is ext3 doing something with the journaling? Just curious.

:)

---

### Post by dcstar on 2007-10-03
> **Geekkit said:**
> I have an question about ext3 ...

I'm using Ubuntu 7.04 and I have a Web-based e-mail application that allows me to download attachments. Sometimes when I do this the Web-based e-mail application (Domino Notes) doesn't provide the actual name of the file being downloaded (e.g., src.zip). Specifically the download does not include a file extension.

And yet, in Nautilus it shows up as the original type, for example a zip file. Archive manager knows what to do with it ... and yet, no file extension. As far as I know ext3 is a low-level file system (i.e, stream-block transfer), not a high-level file system (i.e., providing record-stream translation) like the Mac FS.

Or is ext3 doing something with the journaling? Just curious.

:)

AFAIK Linux/Unix files contain things called "Magic Numbers" which identify what the file actually is - File Types had to be used by brain-dead OSs like DOS because they weren't sophisticated enough to use the *nix way of doing things, and Windows kept this "legacy".

You can rename a *nix text file to .zip (or whatever), but it is still a text file (try it!).

---

### Post by mcduck on 2007-10-03
Yes, dcstar is right. Linux doesn't care about the file name extensions, it checks the file itself to determine what kind of file it is.

(Well, actually Gnome gives you a warning if the file name extension says one thing but the contents of the file other. This is to protect you from trojans and such. So if somebody sends you executable file that's been renamed to .jpg and you click the file it won't run or try to open in image viewer, but you get a warning window instead.)

edit: the 'file' command in terminal will try to find the type of a file. Just run 'file nameofyourfile' an it will tell you the type of the file + some other information.

---

### Post by Geekkit on 2007-10-03
Thanks dcstar, mcduck. I thought about it after and it's most likely something like how you said: some process is going in and looking at file headers and trying to "guess" what type it is. It explains how PDF and images get rendered in Nautilus.

Thanks again!

:)

---

