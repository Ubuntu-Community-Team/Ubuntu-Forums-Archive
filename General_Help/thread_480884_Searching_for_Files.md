---
title: "Searching for Files"
date: 2007-06-21
forum: General Help
---

### Post by Dwood108 on 2007-06-21
How do you do a system wide search using Nautilus?

At the moment if i want to find where my firefox profiles are and search for 'firefox' I just get the shortcuts on the desktop. It doesn't seem to search any where outside of the home folder.

When searching in windows it searches the whole computer, how can you do this on Ubuntu?
thanks

---

### Post by fdrake on 2007-06-21
when u search a file or folder and press enter u have 3 bottons under your search bar, location/filetype, browser botton, and reload botton. this metod allows u to search only files inside your home directory.
to search for a file on your computer type on the terminal "gksudo nautilus" and when u select the location press others and write "/" = root filesystem

---

### Post by mocqueanh on 2007-06-21
Or you can use the command:

locate firefox | less

---

### Post by Dwood108 on 2007-06-21
These buttons don't seem to make a lot of/if any difference.

If I search for Firefox for example the only results are two shortcuts and a mimeinfo.cache file. Yet I know that there are several Firefox folders in the system but I can't find them using the search function.

It is not that I specifically need to find the firefox folders this is just an example. If the search doesn't show these up how will I find any other file?

---

### Post by tgalati4 on 2007-06-21
sudo apt-get install beagle

It will sniff out everything.  Initial indexing takes a long time.

---

### Post by arvevans on 2007-06-21
For those who like the CLI (Command Line Interface), open a terminal window and type this:
[INDENT]sudo find /* -name [filename] -print[/INDENT]

This starts the search with root permissions (sudo) and searches everything (/*) looking for <filename> and sends it's search results as text output (-print) to the text screen.

For more information on the "find" command, do a "man find" in a terminal screen.
_._

---

### Post by fdrake on 2007-06-21
> **Dwood108 said:**
> These buttons don't seem to make a lot of/if any difference.

If I search for Firefox for example the only results are two shortcuts and a mimeinfo.cache file. Yet I know that there are several Firefox folders in the system but I can't find them using the search function.

It is not that I specifically need to find the firefox folders this is just an example. If the search doesn't show these up how will I find any other file?

to tell u the true i just tried to search for firefox in sudo mode and i didn't get any results. it seems like that nautilus cannot search hidden files. why ? mmm......

---

### Post by Dwood108 on 2007-06-21
Searching in nautilus as sudo just brings up the same results.

arvevans - do you have to put the filename in brackets []?

---

