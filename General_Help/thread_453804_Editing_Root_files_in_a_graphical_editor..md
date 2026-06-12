---
title: "Editing Root files in a graphical editor."
date: 2007-05-24
forum: General Help
---

### Post by whill1 on 2007-05-24
Hi,
I am creating a web site on a Ubuntu machine. The problem I am having is that once I put the files on the web server (Apache), I can no longer figure out how to access them without using vi or vim.
When I copy the files back to a folder on the desktop, the files are read-only and I can't edit them in my editor. 

I am trying to find out how to either:

configure an editor to access the files directly on the server or change ownership of them once they are back on the desktop.

I want to do this because I often need to open multiple files so I can reference them as I modify other pages etc...  I just do not like to use vi or vim as an editor for this type of work.

Thanks for any suggestions.
whill1

---

### Post by disposable on 2007-05-24
This is a good question and the answer lies with larger websites/corporate entities.

It's common for larger sites to have separate development (dev), quality (qual) and production (prod) servers, each with their respective purpose. Just scale that down for your needs and your set.

It sounds like your developing on the web server itself and that's ok. Just do your development within a mirror of your site in your home directory (dev), test the site in your home directory with Firefox (qual), and when you're satisfied, upload the file (prod). So, you never edit the files in /var/www directly. (Personally, I automate the upload process with [http://www.getdual.com/linux/perl/bak.pl]("http://www.dualisanoob.com/linux/perl/bak.txt").)

Does that make sense? And if you are indeed working on the same machine, make sure to make an external back up of your site! (bak.pl above does this.)

---

