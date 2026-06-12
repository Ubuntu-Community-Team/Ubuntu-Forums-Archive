---
title: "Application folder location - ?"
date: 2015-03-06
forum: General Help
---

### Post by michael-piziak on 2015-03-06
If I start at "File System" and begin clicking through folders, which path do I take to get to the Application(s) folder?

Sometimes I just want to pull something out of there and move it somewhere else.  For example, a Full Circle Magazine I've downloaded/installed from the Software Center.

---

### Post by nerdtron on 2015-03-06
you can try "whereis" to determine the location of your programs:

```
:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/share/man/man1/firefox.1.gz

```

Some programs, including firefox, (probably full circle too) have a hidden folder on your home folder like .mozilla that contains user profile, bookmarks etc.
Just show hidden files on your file manager and look at your home folder for possible folder of full circle.

---

### Post by Mark Phelps on 2015-03-06
The link is old, but relevant, nonetheless: [http://askubuntu.com/questions/27213/what-is-the-equivalent-to-the-windows-program-files-folder-where-do-things-g]("http://askubuntu.com/questions/27213/what-is-the-equivalent-to-the-windows-program-files-folder-where-do-things-g")

Also, if you start moving things around, unless the new folder(s) are in your default PATH, they probably won't work anymore.

---

### Post by michael-piziak on 2015-03-06
> **nerdtron said:**
> you can try "whereis" to determine the location of your programs:

```
:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/share/man/man1/firefox.1.gz

```

Some programs, including firefox, (probably full circle too) have a hidden folder on your home folder like .mozilla that contains user profile, bookmarks etc.
Just show hidden files on your file manager and look at your home folder for possible folder of full circle.

Thanks!

---

