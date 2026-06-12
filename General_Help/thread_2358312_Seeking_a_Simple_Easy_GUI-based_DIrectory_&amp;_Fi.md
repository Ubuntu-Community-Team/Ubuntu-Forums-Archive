---
title: "Seeking a Simple Easy GUI-based DIrectory &amp; File Compare Program"
date: 2017-04-12
forum: General Help
---

### Post by skanger on 2017-04-12
I need a simple GUI-based program to compare SD and other memory cards content with the same files copied to a hard drive. 

So far I've tried meld-diff and Konqueror/Kompare/md5deep. Konqueror (and all of its allied programs) is way beyond the scope of what I need. While I am impressed with the depth of the program. its organization (or lack of it) and endless array of features are overwhelming to the point that I have almost lost many important files. Meld-diff is simpler but more of a programmers tool.

I manage a non-profit organization with people in the field conducting and recording interviews and taking photos and video stored on SD and CF cards. These come back to me and need to be copied into their respective folders with all sub-folders and directories intact. I need a simple GUI program for my colleagues and myself to check that the copies were good so we can erase the cards and get them back into the digital cameras, audio recorders and camcorders for use again. We're not Linux command-line oriented (yet!), so a simple GUI program would be great. I don't think we need hashes and checksums for this task but if there is a simple program that can do what I described above using hashes and checksums I wouldn't object. We just want to know that the critical directory structure and files were coped intact and without error so we can rest easy. Most of the interviews are one time events that sadly can never happen again, so we are very concerned that the copies are completed properly.

Thank you for any suggestions.

---

### Post by Bucky Ball on 2017-04-12
You could simply check the file size of the original with that of the copy by right-clicking each file and 'Properties. If they're the same size, delete the original and the SD is good to go (this is the way I do it, but I make two copies of the original). Not sure why you need to do anything more than that. What are you looking to compare apart from size?

Apart from that, tried Midnight Commander? Think that compares files. It's in the repos (as 'mc').

---

### Post by HermanAB on 2017-04-12
Well, a better approach may be to use rsync to copy the files.  Rsync uses a CRC to check file integrity and is 'a better kind of copy' program.

If you use rsync to copy the data from the SD card to the HDD, then it will only copy whatever changed, it will finish quickly and you can rest assured that the data was copied correctly.

There are GUIs for rsync but making a little one line script is probably better.  I have never encountered an rsync GUI that really makes it any easier to use.

---

### Post by again? on 2017-04-12
Have a look at [FreeFileSync]("https://www.freefilesync.org/download.php").
It has a compare function and simple interface.
I used this years ago and found it easy to use.
To run, just extract the downloaded archive and click on the "FreeFileSync" executable.
You can drag and drop folders to compare.
Comparing by filetime and size it shows files to be copied over.
[ATTACH=CONFIG]274523[/ATTACH]

Had a quick look on youtube for a tutorial
[https://www.youtube.com/watch?v=oj-GcR7OZkk](https://www.youtube.com/watch?v=oj-GcR7OZkk)
[https://www.youtube.com/watch?v=CpJDHsD8_-w](https://www.youtube.com/watch?v=CpJDHsD8_-w)

---

### Post by skanger on 2017-04-12
Thanks for your suggestions. I'll check them out later today.

---

