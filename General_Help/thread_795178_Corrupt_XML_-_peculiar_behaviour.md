---
title: "Corrupt XML - peculiar behaviour"
date: 2008-05-15
forum: General Help
---

### Post by Robsteranium on 2008-05-15
I've used a java application called Compendium to produce an xml file (export of a mindmap) as attached.

The file can only be read in *vi* (or *head*/ *tail*).  *Less* reports that it "may be a binary file" and *Pico* shows random characters (in what looks like xml structure).  All the gui text editors see a corrupt file, if they don't crash that is!

The peculiar thing is that I can transfer the files exported under linux to a mac and then open them without a problem on OSX.  I can then cut and paste the text into a new file (that has half the file size), transfer it back to linux, and open it up without a problem!

I presume that there is a rogue character lurking in the xml export - and, as such, that this is a problem for Compendium development (hence I've posted there too - [http://compendium.open.ac.uk/bugzilla/show_bug.cgi?id=669](http://compendium.open.ac.uk/bugzilla/show_bug.cgi?id=669)).
Since this problem doesn't happen on my mac, I'm inclined to think that there might be a bug in my linux (hence this post here).

Insight or workarounds (without going via my mac :roll:) most appreciated!

Xubuntu 7.10
Compendium 1.5.2
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)

---

### Post by luisromangz on 2008-05-15
The problem seems to be that the file was saved with a UTF-16 codification, and most prograsm will expect an UTF-8 at most.

---

### Post by Robsteranium on 2008-05-15
Great thanks!

Workaround:
```
iconv -f UTF-16 -t UTF-8 -o input.xml output.xml
```

This is the first time I've ever come across this type of problem.  Is there a more general fix - perhaps relating to the java environment or system's locale settings?

---

