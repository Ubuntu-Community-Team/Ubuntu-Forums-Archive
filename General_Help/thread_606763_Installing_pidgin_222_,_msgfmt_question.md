---
title: "Installing pidgin 222 , msgfmt question"
date: 2007-11-08
forum: General Help
---

### Post by age on 2007-11-08
this what I have and I dont know how to proceed, have done alot of reading and upgrading of dev packages  and still I get this. what is msgfmt? how do set path to it? being a newby I dont understand this. this is what I always end up with.
at terminal I get. what should I type in next.

The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.

If you have msgfmt installed, but for some reason this error message
is still displayed, you have encountered what appears to be a bug in
third-party configure macros.  Try setting the MSGFMT environment
variable to the absolute path to your msgfmt binary and trying
configure again, like this:

MSGFMT=/path/to/msgfmt ./configure ...

root@adrian-desktop:/home/adrian/pidgin-2.2.2#

---

### Post by vladan.b on 2007-11-08
msgfmt should come with gettext, so if you install gettext you are bound to have all you need.

gettext is at: 
```
http://www.gnu.org/software/gettext/
```
or you can 
```
sudo apt-get install gettext
```.

Newbie here too...but it seems like all you need.

---

### Post by age on 2007-11-09
I downloaded gettext  already and all the dev stuff in the packages for it. 
I think from the line

MSGFMT=/path/to/msgfmt ./configure ...

I have to point it toward there, I thinking but beening a newbie I need someone to show me the line to do it.

---

### Post by vladan.b on 2007-11-09
I suppose that simplest way (if indeed, that is the only thing that configure needs) is to set the path to MSGFMT either with export:
```
export MSGFMT=/path/to/msgfmt
```
A search of your files should reveal where msgfmt is located, I myself don't know.

---

### Post by age on 2007-11-17
after numerous more downloaded packages I got it working, doing a manual install.
although my buddy list doesnt show all the time, I telnet the msn and shows I'm connected.
theres still some bugs I think or its my slow internet connection.

---

### Post by dynamethod on 2008-02-03
and what numerous packages where they exactly? cause i have the same problem lol

---

### Post by Nerdriot on 2008-02-12
Most likely (and I could be wrong), all you really need is build-essential, and a few other things. This is what I needed (assuming you have build-essential already)

```
sudo apt-get install libxml2-dev
```

And...

```
sudo apt-get install gettext
```

Then, go to the dir, run "./configure", then "sudo make install". Should work nicely.

---

