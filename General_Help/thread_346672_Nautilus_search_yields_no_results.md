---
title: "Nautilus search yields no results"
date: 2007-01-26
forum: General Help
---

### Post by mover47 on 2007-01-26
Hi there,

When I run a search from Nautilus or use Places-->Search, my queries always come back with no results found ('0'). Examples of searches I have run:

boot
bin
etc
fstab
menu
names of files

I'm a noob, and I don't know where a lot of files or folders are, so I want to use a search instead of wandering around the file system. Why doesn't the search bring back results? Isn't this a "file search"? Whether in Beagle or the Gnome-based search, the result is the same: 0 items. I have /root as a path in Beagle, no change. 

What am I doing wrong?

Thanks!

---

### Post by MoLE on 2007-02-02
Are you still having this problem?  If so, when you go to Places --> Search and entering the search term, are you selecting "File System" as the location for a whole-of-system search?  Can you give us the output of "sudo locate fstab" as an example?

---

### Post by fragos on 2007-02-03
File search in Nautilus can take a while.  When you're looking for files by name there are fast simple ways on the command line.  For example "locate fstab".  All your files are indexed daily so the response is instantanious.  In the example you'd get every file with "fstab" andwhere in the the full file name.  "whereis fstab" is also useful.  There is a "which" command which only looks for executable in your $PATH.  I favor the GUI but for searching I go strait to the command line.

---

### Post by ricardisimo on 2007-02-10
Same here, by the way. "Search" almost always produces PDFs and text files that contain my keyword - e.g., "fstab" returned desktopguide.pdf. <locate> returned about a dozen items, which is cool; thanks for the tip. Still, Beagle, or Nautilus, or something is using up a [COLOR="Red"]_LOT_[/COLOR] of memory indexing files so as to be able to find them in the future, but then it never finds anything. What is up with that? Why wouldn't the GUI search incorporate the results of <locate> along with whatever it's currently returning? Thanks.

---

### Post by 4cpo on 2007-02-19
I hade the same problem firts time around since I entered the search terms like *.jpg and not  just jpg.



Hopefully this helps.

---

### Post by allwin on 2007-02-19
I encountered the SAME PROBLEM.  

Uninstall the BEAGLE package, unless you know you have specific need for Beagle!

It messes up the search for file names.  I think it relies upon a separately created index of your files...and you most likely do not have that job set up to generate the index and keep it up to date.

Go into Synaptic and mark it for uninstallation and then get rid of it.  Worked for me.

---

### Post by Asnem on 2008-04-02
When I use the search feature in Nautilus, I get no results.  When I use Places | Search for Files, it works as expected...

What can cause this?  I've tried removing Beagle, and other things mentioned here....

---

### Post by fragos on 2008-04-02
For finding files fast there is no substitute for the command "locate." Daily an index of filenames is built and the result is instantanious file find. It's included in the default Ubuntu build.

---

### Post by Asnem on 2008-04-02
I don't want to "find files fast".  Why do people answer questions that were not asked, instead of trying to help solve a problem?

I want the GUI search to work.  This can do things that are difficult or impractical to do with locate.  What I was trying to do is find all of the instances of a certain file under my home folder (~100), and be able to CTRL-click to select the ones to delete, then hit the delete key.  This I can do in a few seconds in the GUI.  To do it with locate is a several step process, outputting to text, editing, and running it back through other commands...

I like the command line as much as anyone - it is NOT the best solution to every problem, however.

Locate is not faster on my machine either..  I have a Quad Core Processor with 4 GB RAM, and GUI searches are instant... you can't get faster than instant...

---

### Post by Ralph L on 2008-05-31
I just want to say that I agree with you that Nautilus search is inadequate.  Because of that I am giving up on Linux and going back to Windows.  Any system I use should have a search function at least as good as XP.  Maybe I'll wait a year or two and try again, or maybe I'll try Kubuntu.

Ralph

---

### Post by s_raiguel on 2008-06-04
Been having the same problem. No matter what I put in as "location", the only thing that ever gets searched by Nautilus is my home directory. I tried any number of things, but finally gave up and installed a separate file search program (that works fine, by the way).

---

