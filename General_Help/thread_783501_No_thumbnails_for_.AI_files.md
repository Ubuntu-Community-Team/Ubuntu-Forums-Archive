---
title: "No thumbnails for .AI files"
date: 2008-05-05
forum: General Help
---

### Post by cr33dog on 2008-05-05
Hello Ubuntians :)

After a fresh install of Hardy, I do not get thumbnail icons for .AI (Adobe Illustrator) files.  I'm pretty sure this Just Worked in Gutsy, and I can't figure out how to make it happen.  The "Properties" in Nautilus correctly identify the files as PDF files, and running the "file" command also returns the application/PDF mimetype with is correct - so I'm stumped.  "Regular" PDF files have thumbnail icons, and if I change the extension from .AI to .PDF the thumbnail is created and remains when I change it back to .AI.

Any clues?

Thanks,
Chris

---

### Post by Anduu on 2008-05-06
Try deleting your /home/<username>/.thumbnails directory.Sometimes the thumbnailer gets hung up with a certain file or filetype and this will force all thumbnails to be regenerated.

Not guaranteed to work but does in a lot of cases.It's worth a shot.

---

### Post by cr33dog on 2008-05-06
No dice  - that's one of the first things I tried :)  Thanks for the suggestion though.

Chris

---

### Post by Anduu on 2008-05-06
Well I fished around and found an ai file to download and no thumbnails here either.

If it worked in Gutsy but not now I would file a bug report.

---

### Post by cr33dog on 2008-05-07
Hmm - anyone still running Gutsy out there?  I'd really appreciate them downloading this AI file:
[http://download.yousendit.com/ACF40ED435652330](http://download.yousendit.com/ACF40ED435652330)

Does nautilus create a thumbnail icon?

Thanks,
Chris

---

### Post by cr33dog on 2008-05-08
This is the bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/227589](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/227589)

And this is a work-around:
```
gconftool-2 --set  /desktop/gnome/thumbnailers/application@illustrator/command -t string "evince-thumbnailer -s %s %u %o"

/etc/gconf/schemas$ gconftool-2 --set  /desktop/gnome/thumbnailers/application@illustrator/enable -t boolean "True"
```


Too bad they bumped it down to "wishlist" importance...

Chris

---

### Post by Anduu on 2008-05-08
Good find there .

I love getting to fix things I didn't even know were broken :p

---

