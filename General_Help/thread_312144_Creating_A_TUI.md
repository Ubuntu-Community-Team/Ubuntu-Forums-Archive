---
title: "Creating A TUI"
date: 2006-12-03
forum: General Help
---

### Post by doogy2004 on 2006-12-03
How does one create a TUI(Text User Interface)?

Thanks

---

### Post by ciscosurfer on 2006-12-03
I believe you need ncurses to do that: [http://www.gnu.org/software/ncurses/ncurses.html](http://www.gnu.org/software/ncurses/ncurses.html)

EDIT: I know this is one way of doing it (using curses) but there are probably many more.

---

### Post by po0f on 2006-12-03
doogy2004,

Ncurses isn't your only option; there is also [Slang](http://www.jedsoft.org/slang/), which is available in the [repos](http://packages.ubuntu.com/edgy/base/libslang2-dev).

---

### Post by SuperMike on 2006-12-04
If you know Bash, you can download a sample of a starter project with [**ust.sourceforge.net**]("http://ust.sourceforge.net"). It's an incomplete menu system written in Bash that uses VT100 characters to pop the cursor around the screen, create scroll regions, etc. That's what ncurses does, but in a much more complex way, interfaced through C. For ncurses, you'd have to learn C or find some module to load into some other language.

Another way to build a TUI is to do it in PHP-cli (cli=command line). If you install php5-cli, you can read the stuff on [**php.net**]("http://us3.php.net/features.commandline") to find out how to interact with command line.

---

### Post by doogy2004 on 2006-12-04
Thanks for the info everyone.  The reason that i'm asking about how to accomplish this is that i'm doing some research on it so that Automatix can be adapted from a GUI to something that could be run on a server using a TUI.

---

### Post by lamego on 2006-12-04
You could also do it with any kind of scripting language and using the "dialog" utility.

---

### Post by doogy2004 on 2006-12-04
I found instructions for

bash dialog here:
[http://linuxgazette.net/101/sunil.html](http://linuxgazette.net/101/sunil.html)

python
[http://pythondialog.sourceforge.net/](http://pythondialog.sourceforge.net/)

thanks lamego for the "dialog" recomendation.

---

