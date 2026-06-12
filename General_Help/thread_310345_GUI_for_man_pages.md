---
title: "GUI for man pages"
date: 2006-12-01
forum: General Help
---

### Post by charlie. on 2006-12-01
I'm not averse to browsing through all those man (manual) pages in console windows, but every now and then I think it would be really cool if I had a nice, modern-like GUI for them.

Here's all I want:

* Everything can be exactly the same as the "man" command, but I want a proper scroll bar and the use of my scroll wheel. Arrow keys just don't cut it these days.
* As far as navigation goes, I just want a text box to type in the name of the page to view and an optional section number.
* If links to other man pages were hyperlinked, that would be nice.

Does anyone out there know of such a thing?

---

### Post by nikhilk on 2006-12-01
I believe Konqueror does a great job of it.

---

### Post by ciscosurfer on 2006-12-01
> **charlie. said:**
> I'm not averse to browsing through all those man (manual) pages in console windows, but every now and then I think it would be really cool if I had a nice, modern-like GUI for them.

Here's all I want:

* Everything can be exactly the same as the "man" command, but I want a proper scroll bar and the use of my scroll wheel. Arrow keys just don't cut it these days.
* As far as navigation goes, I just want a text box to type in the name of the page to view and an optional section number.
* If links to other man pages were hyperlinked, that would be nice.

Does anyone out there know of such a thing?[You might be interested in the following link]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=man2html&searchon=names&subword=1&version=edgy&release=all") (describes man2html and will let you browse your man pages through your web browser)...you can download it at the link I provide or enable your universe repo and download it via your favorite package manager.

---

### Post by CatKiller on 2006-12-01
Or if you Google for **man <command>** you'll find one of the many many mirrors that have the man pages as HTML.

There was the [info]("http://en.wikipedia.org/wiki/Texinfo") way of laying out documentation, but most projects don't seem to use it. Although a lot of projects don't even provide man pages - they need to be created by the person that packages them instead.

---

### Post by matthew on 2006-12-01
If you are using a standard Ubuntu installation then look in the menu at

System->Help->System Documentation
and on the left of the window that comes up click "Manual Pages"

browse away!

---

### Post by charlie. on 2006-12-04
Thanks Matthew, that works rather nicely.

---

### Post by ciscosurfer on 2006-12-04
> **matthew said:**
> If you are using a standard Ubuntu installation then look in the menu at

System->Help->System Documentation
and on the left of the window that comes up click "Manual Pages"

browse away!This only covers man pages that come with your base install.  Any apps that you add to your system will not show up there.

---

### Post by drphilngood on 2006-12-04
Many thanks, ciscosurfer.

---

### Post by 23meg on 2006-12-04
> **ciscosurfer said:**
> This only covers man pages that come with your base install.  Any apps that you add to your system will not show up there.However, when you type "man app-name" as usual in the Yelp search box, as you do in the terminal, the man page for the app does show; it's only absent from the list.

Also, if it's an app with its own Yelp pages as well as a man page, those come up in the search as well. Quite practical.

---

### Post by DonS on 2006-12-04
> **ciscosurfer said:**
> This only covers man pages that come with your base install.  Any apps that you add to your system will not show up there.

If this is the case, it is a bug.  Please file it and include examples (if possible).  Many thanks.

---

### Post by ciscosurfer on 2006-12-04
> **DonS said:**
> If this is the case, it is a bug.  Please file it and include examples (if possible).  Many thanks.It's not a bug, it was my mistake.  [23meg comes to the rescue]("http://ubuntuforums.org/showpost.php?p=1842748&postcount=9")!

---

### Post by charlie. on 2006-12-05
Firstly, I've learned that "Yelp" is the app that runs this Gnome based help. That's cool.

I've also tested out the "man pagename" in the search box, it works.

Additionally, additional man pages that I added (manpages-dev) DO show in Yelp.

Now, two issues: firstly, you cannot choose the section number in the Yelp search box. Typing "man 2 kill" fails to show the documentation on the kill() system call, as it would in the terminal. That page, in particular, is tricky to find because you have to search for "kill" and then go through the list of results.

Secondly, references to other man pages, including those in the SEE ALSO section at the end of nearly all man pages, are not hyperlinked. This is not a big issue, but it would be nice if they were.

---

### Post by Emblem Parade on 2007-03-31
I found [tkman]("http://tkman.sourceforge.net/") to be a very functional GUI substitute for the CLI man. TkMan is available in the Ubuntu repositories, of course!

---

