---
title: "Suggestions for photo organization?"
date: 2005-04-20
forum: General Help
---

### Post by ignavia on 2005-04-20
I'm looking for a good photo organization program. I've heard good things about digiKam, but I'd like something GNOME-native.

I've also heard that Picasa2 runs well under WINE. I could live with a non-native program for something as good as Picasa. Has anyone tried it?

---

### Post by gunnyman on 2005-04-21
just downloaded and installed Picasa 2. Works perfectly under WINE.

---

### Post by ignavia on 2005-04-21
I *aspire* to be a WINE newbie. ;) Care to share the details of the process?

---

### Post by Monkey_See on 2005-04-21
Hi ignavia,

I just tried using Picasa2 under wine as gunnyman suggested  and it works very well.

Goto [http://www.winehq.org/site/download](http://www.winehq.org/site/download)
and follow the instruction on the Ubuntu link (basically adding the repository and installing using apt-get).

then run wine in the terminal (as user) this will create the ~./wine directory.

then Download Picasa2, and simply run wine /where/your/file/is/Picasa2-setup.exe

thats it, it will install to a folder in your ~./wine directory in under the fake c: drive as per M$'s directory structure.

---

### Post by Bob D. on 2005-04-21
You might want to take a look at F-Spot. It is the future of the Gnome photo organizing application. GTK+ based, written in Mono, still in early development but works fine for me for organizing photos.

Activate the Universe repository and you can download the application.

Bob

---

### Post by sebgate20 on 2005-04-21
[QUOTE=Bob D.]You might want to take a look at F-Spot. It is the future of the Gnome photo organizing application. GTK+ based, written in Mono, still in early development but works fine for me for organizing photos.

Activate the Universe repository and you can download the application.

Bob[/QUOTE]
 I find F-Spot is great. It provides the same sort of features as Apple's iPhoto. It intergrates well with GNOME (interface wise) and is another bread of the excellent Mono applications that pull GNOME above KDE ;-)

I believe F-Spot is available in 'univerise' APT repo. I think this would pull it in:

sudo apt-get install f-spot

Seb

---

### Post by ignavia on 2005-04-21
[QUOTE=Monkey_See]Hi ignavia,

I just tried using Picasa2 under wine as gunnyman suggested  and it works very well.

Goto [http://www.winehq.org/site/download](http://www.winehq.org/site/download)
and follow the instruction on the Ubuntu link (basically adding the repository and installing using apt-get).

then run wine in the terminal (as user) this will create the ~./wine directory.

then Download Picasa2, and simply run wine /where/your/file/is/Picasa2-setup.exe

thats it, it will install to a folder in your ~./wine directory in under the fake c: drive as per M$'s directory structure.[/QUOTE]
 Wait... that's it? When did wine get that easy? Last time I used it was in 2000 or 2001, and I couldn't get anything to run with it except notepad.

And thanks for the tips about F-spot. I'll have to check that out.

---

### Post by andy_cowman on 2006-04-13
Couldnt agree more, I just did that and it was installed!!! Was thinking about upgrading my old crossover package (4.2) but reall cant be bothered now. That was incrediably easy. Now I just need to work out how to use picassa to do what i want!

Cheers for the idea

Andy

---

### Post by mGee on 2006-04-21
I just installed F-Spot. It's just what I was looking for. More ubuntu goodness!

---

