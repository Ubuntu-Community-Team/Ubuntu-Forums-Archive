---
title: "Windows line endings &amp; dual boot"
date: 2013-03-23
forum: General Help
---

### Post by BravoDelta65 on 2013-03-23
I have Windows 7 & Ubuntu 12.10 on the same Laptop. With my web files I want to develop and on both OS's, but I'm sure I'll run into Windows Line ending / Unix line ending compatibility problems just using straight copy/paste..... what is best way to use same files and avoid line ending issues?

---

### Post by Impavidus on 2013-03-23
Most text editors are aware of the different Unix and Windows style line endings and won't cause any problems (notepad being a notable exception on the Windows side). You can also select the style you want to use in the "save as" window when savig a file in the text editor (at least in gedit, I don't know about many others). Windows support for saving in Unix style may be worse. It's also possible to convert from one style to the other using command line utilities.

Also see [http://en.wikipedia.org/wiki/Newline#Conversion_utilities](http://en.wikipedia.org/wiki/Newline#Conversion_utilities)

The screenshot is of the "save as" window in the linux text editor gedit, the arrow indicating the selection box for line endings.

---

### Post by BravoDelta65 on 2013-03-26
Vim displays my vimrc from my windows 7 drive as ending with ^M's on every line

---

### Post by SeijiSensei on 2013-03-26
I created a couple of files in Wordpad and Notepad and opened them with the jed editor on a Linux box.  Neither had the extraneous ^M characters.  However Wordpad allows you to choose what ending you want and make that the default.  The "MS-DOS" choice will add the extraneous line feeds.

---

