---
title: "Access to local files? Through Firefox 2?"
date: 2008-04-30
forum: General Help
---

### Post by zspace on 2008-04-30
I have an online game that I like to play and it comes with a graphics pack. I know how to convince firefox to give access to local files (at least on windows), but I was wondering if ubuntu was blocking its access to the files. They are stored in my home folder.
Also I was wondering how I would have to enter the locations of the files into the game (it needs a directory, but I have no idea how ubuntu's file system works)? 
I'm completely new to all of this (windows user), but I am not bad with computers so if you could just explain I'm sure I can get it.

I'm using ubuntu 8.04 if it matters.

---

### Post by Monicker on 2008-04-30
> **zspace said:**
> I have an online game that I like to play and it comes with a graphics pack. I know how to convince firefox to give access to local files (at least on windows), but I was wondering if ubuntu was blocking its access to the files. They are stored in my home folder.
Also I was wondering how I would have to enter the locations of the files into the game (it needs a directory, but I have no idea how ubuntu's file system works)? 
I'm completely new to all of this (windows user), but I am not bad with computers so if you could just explain I'm sure I can get it.

I'm using ubuntu 8.04 if it matters.

Just use the Firefox menu to navigate to the file.  File -> Open File.

---

### Post by zspace on 2008-04-30
> **Monicker said:**
> Just use the Firefox menu to navigate to the file.  File -> Open File.
No that's opening local files, I know how to do that, I'm asking about how to allow a web page access non html documents on my hard drive (mostly photos and CSS documents).

---

### Post by Monicker on 2008-04-30
> **zspace said:**
> No that's opening local files, I know how to do that, I'm asking about how to allow a web page access non html documents on my hard drive (mostly photos and CSS documents).

So you want to reference local files in an html page that is also local?

Try using the file:// URI.

For example:
```

<img src="file:///home/username/image.jpg">
```

---

### Post by zspace on 2008-04-30
ok that was what I needed, thanks.

---

