---
title: "PDF Downloads Freeze in Firefox"
date: 2008-03-10
forum: General Help
---

### Post by Nrbelex on 2008-03-10
Hi - whenever I download a PDF of the newspaper located here ( [http://www.emorywheel.com/pdfs/](http://www.emorywheel.com/pdfs/) ), the download of the PDF either never starts or freezes early in the download process and never resumes. The counter and download rate also freeze. I am able to download other PDFs in Firefox and these PDFs can be downloaded on any other computer.

Any ideas?

Thanks,
~ Brett

---

### Post by warp99 on 2008-03-11
Are you downloading them, right mouse button then save, or are you viewing them in the window with a PDF viewer? Try the following to see if maybe it's something else. 

Open a terminal and cut/paste the following:
```
wget http://www.emorywheel.com/pdfs/issues/03-03-08.pdf
```

If you can't download the file them something else is wrong. I was able to download and view those files without any problems using Firefox 2.0.0.12.

You could always delete your /home/<user>/.mozilla/firefox directory and have Firefox regenerate a new local directory. Just remember to backup any bookmarks. If that doesn't work then you can reinstall Firefox:

```
sudo apt-get install --reinstall firefox
```

---

### Post by Nrbelex on 2008-03-11
> **warp99 said:**
> Are you downloading them, right mouse button then save, or are you viewing them in the window with a PDF viewer?

I have tried to both click them (giving me a prompt asking if I want to open with a program or save - both of which I have tried) and right clicking to do a save link as. Neither worked.

> **warp99 said:**
>  Try the following to see if maybe it's something else. 

Open a terminal and cut/paste the following:
```
wget http://www.emorywheel.com/pdfs/issues/03-03-08.pdf
```

Interestingly wget locked up and froze too after reaching 7 percent so I guess it's not just Firefox...

Thanks! Any more ideas?

~ Brett

---

### Post by warp99 on 2008-03-11
Set up a new user with admin privileges, then login under that new user. See if the problem persists, if not there you go. ;)

---

