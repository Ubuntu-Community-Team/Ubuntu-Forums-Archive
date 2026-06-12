---
title: "password protect a file"
date: 2008-04-04
forum: General Help
---

### Post by RJ Hythloday on 2008-04-04
So I found a few posts about this, problem is if I encrypt it in terminal I can only open it in terminal.
 
I have one file I don't want the kids to mess up, it's a checking register spreadsheet. I'd like to put a shortcut in the task bar that points to it, and when the icon is clicked it asks for the pw. Everything I've tried just says can't open it, or doesn't exist. I tried moving it to a protected area /etc and also from home encrypted it w/ mcrypt but none of those work if I point the shortcut to it.
 
Any ideas?

---

### Post by TeoBigusGeekus on 2008-04-04
If your kids don't know how to make hidden folders to show up, put it in a folder with a dot (.) in front of its name i.e. (.important_folder) and hide hidden folders in Nautilus (Ctrl+H).

---

### Post by jakupl on 2008-04-04
I found a really easy and nice encryption program a few days ago, ccrypt

'sudo apt-get install ccrypt'

to encrypt simply write in terminal

ccrypt -e "filename"

do decrypt write:

ccrypt -d "filename"

---

### Post by kpkeerthi on 2008-04-04
I use [cryptkeeper]("http://www.ubuntu-unleashed.com/2007/08/howto-encrypt-your-private-files-with.html")  to keep sensitive documents secured.

[http://www.gnomefiles.org/app.php?soft_id=2006](http://www.gnomefiles.org/app.php?soft_id=2006)

---

