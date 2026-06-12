---
title: "Wine with Foxit Reader"
date: 2006-08-06
forum: General Help
---

### Post by futz on 2006-08-06
This is probably simple, but I can't seem to get it right:

Is there a way to build a launcher/shortcut so when I double-click on a PDF file in Nautilus it will open the file with Wine in Foxit PDF Reader?

I hate the crappy, buggy Adobe reader. Foxit's reader is much nicer to use for most PDF's, and runs great under Wine.

What command should I put in the launcher? It'll most likely start with
```
wine /home/futz/FoxitReader.exe
```
I've tried lots of stuff, but can't get it to work.

---

### Post by orb9220 on 2006-08-06
hit alt-f2 and run winecfg then add it to applications by browsing to that location and selecting it. click apply then ok.

also try running from term first to see if it will run.

---

### Post by KyleCardoza on 2006-08-06
Why not just use Evince? It's at least a native application.

If somehow it's not installed, you can just open up a terminal, and type in 'apt-get install evince'.

---

### Post by futz on 2006-08-06
> **KyleCardoza said:**
> Why not just use Evince?
Because I don't like Evince. I use programs that work the way I expect them to and are reasonably bug-free. Foxit Reader runs nice and fast in Wine and is my favorite PDF reader. It's just getting the file association thing to work right that I'm having trouble with.

The day there's a native linux pdf reader as good as Foxit I'll switch immediately.

---

### Post by futz on 2006-08-07
Bump! :mrgreen: 

I can type "wine /home/futz/FoxitReader.exe firstenergy.pdf" in a terminal and it works fine. 

So how do I make it so when I double-click on *firstenergy.pdf* in Nautilus, it runs FoxitReader with Wine and opens *firstenergy.pdf*?

I see things like %U and %S and others used as parameter wildcards in shortcuts (launchers), but I can't seem to find a complete list of them, nor any info on how to use them.

Is there a way to see the actual command line Nautilus is spitting out when I double-click? Or does that even make sense? How does Nautilus pass the filename to an associated program?

---

### Post by orb9220 on 2006-08-07
Right-click on any pdf file select properties and click the open with tab.
insert
"wine /home/futz/FoxitReader.exe"
and see if that does it.

---

### Post by futz on 2006-08-07
> **orb9220 said:**
> Right-click on any pdf file select properties and click the open with tab.
insert
"wine /home/futz/FoxitReader.exe"
and see if that does it.
Ah, a custom command. Essentially what I was already doing, only in a different place. It doesn't work with "wine /home/futz/FoxitReader.exe"(with or without quotes). FoxitReader throws the same error as always. The error message isn't detailed - just gives a list of things it could be. I assume it's not getting the filename passed properly, but I don't know how to fix it unless I can see the command line to see what's wrong (could be one character in the wrong place or no/too many delimiter(s)).

---

### Post by futz on 2006-08-10
Eureka! I found a way to make it work!

After a couple days Googling different things and mostly finding absolutely nothing useful, I stumbled onto this thread:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=355622](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=355622)

The wrapper script from that thread just needed a little massaging to make it work right for my purposes:
```
#!/bin/sh
ROOT_DRIVE="Z:\\"
for arg
do
	wine "/home/futz/FoxitReader.exe" "${ROOT_DRIVE}$(echo "$arg" | sed 's/\//\\/g')"
done

```
Do I know how it works? Hell no! But I'm going to figure that out right now. :mrgreen:

EDIT: First, ROOT_DRIVE = Z:\\ is used to give our windows program a windows type root drive in the path, as it doesn't understand linux drive names. Then SED (Stream Editor) is being used to replace all slashes in the path with backslashes, again so FoxitReader can understand it (being a windows program, it chokes on linux slashes). Makes perfect sense, tho my explanation is probably lacking some.

---

### Post by brucevangeorge on 2006-09-12
> **futz said:**
> Because I don't like Evince. I use programs that work the way I expect them to and are reasonably bug-free. Foxit Reader runs nice and fast in Wine and is my favorite PDF reader. It's just getting the file association thing to work right that I'm having trouble with.

The day there's a native linux pdf reader as good as Foxit I'll switch immediately.

There is supposed to be a Foxit Linux coming out sometime.

---

### Post by TransitMan on 2006-09-12
The beta of Linux Foxit Reader is now available on their website.

---

### Post by Kalidarn on 2007-02-23
It's out, and it's incredibly fast, although not likely to take off because there are plenty of good FOSS PDF readers.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

