---
title: "How can I make screenshot file's size smaller?"
date: 2007-08-25
forum: General Help
---

### Post by clevin on 2007-08-25
this is excessive. I dont understand why OSX and windows can generate a high quality screenshot whose file size is about 200~300KB size. while all my Ubuntu's screenshot is 2.1MB!!

any idea?

---

### Post by jordanmthomas on 2007-08-25
gnome-screenshot uses pngs, which are higher quality than the jpgs I guess you're using in Windows.  
```
sudo apt-get install scrot
```

I use scrot to take my screenshots.  Here's how you'd take a simple screenshot with it
```
scrot /path/to/save/in.jpg
```

```
scrot --help 
```
will show you all the options

Once you have it set up the way you want, you can just bind it to a key on your keyboard, type it in a terminal whenever you want, add a launcher for it, etc.

---

### Post by clevin on 2007-08-25
thanks for the reply

well, I don't think its format issue, OSX's default screenshot is in png, and I saved windows vista's screenshot as png too, they are all small.

---

### Post by jordanmthomas on 2007-08-25
PNG has compression options, and you can actually use them with scrot.  Gnome-screenshot is just one of the many examples of why I think Gnome has headed the wrong direction.  Stripping functionality to make it less complicated is a bad idea in my opinion.  

Oddly, though, upon inspection my gnome-screenshot takes shots that are about 200 KB, so maybe your issue lies elsewhere.  2.1 MB seems more like the size of a bitmapped screenshot.  :|

Does scrot work for you?  Or does it produce huge files as well?

---

### Post by clevin on 2007-08-26
thank you!

I tried scrot, when taking jpg, it produces a file around 200KB, but once I tried to use it to generate a png screenshot, it preduced a 1.8MB file.....

This is so strange...


EDIT, I found some clue, but I need some explanation.

I found the filze size is directly related to the wallpaper I use, I tried taking screenshot with 3 different wallpapers, the file i got are 2.2MB, 1.1MB, and 478KB, respectively. Is this what it supposed to be? that 2MB still looks excessively large to me.

---

