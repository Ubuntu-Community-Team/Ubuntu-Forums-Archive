---
title: "Identifying URLs to download scripts via wget"
date: 2013-02-09
forum: General Help
---

### Post by epikvision on 2013-02-09
Hello,

On an Archlinux computer, I haven't installed GUI yet, but at the moment, I don't intend to.  I installed irssi, vim, and wget in it.  I am following the [quadpoint's guide to irssi ]("http://quadpoint.org/articles/irssi/").  But I can't download scripts with mouse clicks because I will need to use wget.  And to use wget, I need to know the URLs for the scripts. 

It is tedious to have to write the URLs every single time to download a script.  Via the terminal, what other tools will I need to identify the URL of an irssi script, and paste it for wget to download from?  

Thank you.

---

### Post by Impavidus on 2013-02-09
If you don't want a GUI, consider using a text based browser. **elinks** allows you to browse to the script and download it using just the keyboard. It runs in a terminal.

---

### Post by epikvision on 2013-02-09
How about using lynx?  Do you find elinks more superior?

To add on to my question, I was actually referring to download links that are not conventional.  For instance:

http://scripts.irrsi.org/scripts/<script-name>

is rather easy to follow, but not something that gives a random last name:
[http://www.vim.org/scripts/download_script.php?src_id=7701How](http://www.vim.org/scripts/download_script.php?src_id=7701How) could I know what name the script was beforehand?

---

### Post by Impavidus on 2013-02-10
I've used both lynx and elinks, but so rarely that I can't tell which one is better. It was just to have a browser available when I'm stuck to a terminal or an ancient (*really* ancient) monitor. I mean those black-and-white (or green-and-white ...) monitors that don't even have greyscale.

Concerning that type of links: there may be a way but I've no idea besides using a browser.

---

### Post by codemaniac on 2013-02-10
Hi,

sciptassist.pl is a script that makes life easier in installing, managing irssi scripts. 

[http://scripts.irssi.org/scripts/scriptassist.pl](http://scripts.irssi.org/scripts/scriptassist.pl)

---

