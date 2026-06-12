---
title: "Odd File Permissions on my DVD.... :("
date: 2006-12-25
forum: General Help
---

### Post by WinterWeaver on 2006-12-25
Hiya, and happy solstice to everyone!

Anyway.... I have a odd problem here.

I have written some AVI's, MPG's and GVI's (Google Video) files to a DVD at work. The files were written from a IMac (Max OS X).

Here is the thing. I bring the DVD home to my Ubuntu box, and I can copy all the avi's and mpg's, but not the gvi's.... It reckons that I don't have the file permissions to do so. I have tried to, copy the files via 'sudo' and even 'sudo nautilus', but it doesn't work.

This has happened before, and it's easilly solved if I boot into my windoze and copy the files from the DVD there, but this is just a nusance cause I generally avoid windoze, except for me games.

so..... does anyone have any clue on how I can tackle this wee problem ?

Thanks

WW

---

### Post by WinterWeaver on 2006-12-25
Oops... my bad.... I thought I tried 'sudo cp' before.....

Just did that and it works.

```
sudo cp /media/cdrom/*.gvi ~/
```

... and after a quick permission change... all is normal.

```
sudo chmod a=rwx ./*.gvi
```

^_^

---

