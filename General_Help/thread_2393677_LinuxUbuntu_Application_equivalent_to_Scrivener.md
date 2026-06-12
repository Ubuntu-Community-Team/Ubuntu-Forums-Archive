---
title: "Linux/Ubuntu Application equivalent to Scrivener"
date: 2018-06-06
forum: General Help
---

### Post by bobnutfield on 2018-06-06
Hello Everyone

I just wanted to ask if anyone knows of an application which is equivalent to Scrivener, an author's software which is very useful.  I am currently using it in Windows 10 (paid for version), but my Windows laptop is extremely slow and unreliable.  There used to be a Linux version of Scrivener, but they have discontinued it.  Ideally, I would like to find one that is compatible and will let me transfer files to it.   I have searched the net, but have not found anything.

Any help appreciated.


Bob

---

### Post by #&amp;thj^% on 2018-06-06
Here is a few to view: [https://alternativeto.net/software/scrivener/?platform=linux](https://alternativeto.net/software/scrivener/?platform=linux)

---

### Post by ajgreeny on 2018-06-06
There have been versions of Scrivener that would work in Wine, so that could be a worthwhile search for you.

Look at the webpages at [https://www.winehq.org/search?q=Scrivener](https://www.winehq.org/search?q=Scrivener) which may help you run it indirectly through Wine.

---

### Post by dragonfly41 on 2018-06-06
> [COLOR=#000000]There used to be a Linux version of Scrivener, but they have discontinued it[/COLOR]

That is not quite the case.   I have Scrivener Linux working on Ubuntu 16.04.
The developers have simply decided to *donate* the Linux version and not charge licence fee as in the Windows version.

Personally I would avoid wine.  If you are looking for an alternative editor take a look at Atom editor plus plugins.  And for authoring I would look at Markdown and convert to any other format using pandoc.

Another approach would be to look at scribus.

[COLOR=#b22222][Later edit][/COLOR]

I am adding reference to a trusty little note editor - cherrytree - found in Ubuntu software centre.
Cherrytree allows a tree structure of chapters and sections to be moved around in an xml tree.  You have to use it to see how useful it can be for many applications; from authoring to coding (see embedded code boxes in tree nodes).   You can export the entire document or parts to various formats.

---

### Post by bobnutfield on 2018-06-07
> **1fallen said:**
> Here is a few to view: [https://alternativeto.net/software/scrivener/?platform=linux](https://alternativeto.net/software/scrivener/?platform=linux)

Thank you that is useful.

Bob

---

### Post by bobnutfield on 2018-06-07
> **1fallen said:**
> Here is a few to view: [https://alternativeto.net/software/scrivener/?platform=linux](https://alternativeto.net/software/scrivener/?platform=linux)

> **dragonfly41 said:**
> That is not quite the case.   I have Scrivener Linux working on Ubuntu 16.04.
The developers have simply decided to *donate* the Linux version and not charge licence fee as in the Windows version.

Personally I would avoid wine.  If you are looking for an alternative editor take a look at Atom editor plus plugins.  And for authoring I would look at Markdown and convert to any other format using pandoc.

Another approach would be to look at scribus.

[COLOR=#b22222][Later edit][/COLOR]

I am adding reference to a trusty little note editor - cherrytree - found in Ubuntu software centre.
Cherrytree allows a tree structure of chapters and sections to be moved around in an xml tree.  You have to use it to see how useful it can be for many applications; from authoring to coding (see embedded code boxes in tree nodes).   You can export the entire document or parts to various formats.

Thank you for your reply.
  
Yes, I have Scrivener 1.9 Linux installed on 18.04.  However, when I import the project that I started in the Windows version, it results in a number of formatting errors that I have to go back and correct, very time consuming.  I am a member of the Scrivener forum and a number of Linux users report the same issue.  If I had started the project in Linux in the first place, I probably would not have had any issues.  When I installed it, it was missing some dependencies and wouldn't run at first, but that was sorted.  Scrivener (paid version) works great in Windows, its just Windows that is terrible.  That laptop is fairly meaty (AMD A10 with 8GB RAM) and Windows is still slow at molasses and very unstable.  

This is a pretty large project, a novel I have written which totals a little over 250 manuscript pages.  Scrivener in Windows will compile the book in several different formats so that I can preview what the finished product will look like.  I have not tried that in the Linux version.  Ideally, that is what I would like: to be able to import my work keeping the formatting as close to original as possible with the ability to compile in Epub or Paperback formats.

I am going to take a look at Cherrytree.  That looks very interesting.

Many thanks to everyone who replied it is very helpful

Bob

---

### Post by dragonfly41 on 2018-06-07
If you decide to export your document as HTML here is a thread explaining how to convert HTML to epub.

[https://stackoverflow.com/questions/21626219/convert-html-files-to-epub-files-programmatically-command-line-ubuntu](https://stackoverflow.com/questions/21626219/convert-html-files-to-epub-files-programmatically-command-line-ubuntu)

I would take a look at pandoc and scribus as well as part of your toolchain.

And of course the old AbiWord and Calibre (ebooks).

---

### Post by bobnutfield on 2018-06-07
> **dragonfly41 said:**
> If you decide to export your document as HTML here is a thread explaining how to convert HTML to epub.

[https://stackoverflow.com/questions/21626219/convert-html-files-to-epub-files-programmatically-command-line-ubuntu](https://stackoverflow.com/questions/21626219/convert-html-files-to-epub-files-programmatically-command-line-ubuntu)

I would take a look at pandoc and scribus as well as part of your toolchain.

And of course the old AbiWord and Calibre (ebooks).

Thank you, that is very helpful.  I wrote the entire book in LibreOffice then imported it to Scrivener.  I am not very familiar or good at this type of software.  It has taken me years to write (with research).  The book is complete now and I am editing.  I have had a look at Calibre and that looks good.  I have installed it and I will compile the book into an Epub and see what it will do.  I have a publisher who is interested in looking at it (I sent them three chapters), but professional editors are so expensive I just can't afford it so I am trying to do it myself.

Thank you for your help.  I really appreciate it.

Bob

---

### Post by dragonfly41 on 2018-06-07
Just adding an idea. You appear to have had problems opening a Scrivener (Windows) document in Scrivener (Linux).

I would try in stages.
Export (not save) document from Scrivener (Windows).
Import (not open) the above exported document into Scrivener (Linux).

This might avoid clashes.

And if you need to add references/citations look at zotero.org.

Always keep a backup.

---

### Post by micbil38 on 2018-12-15
Scrivener for Linux is now available as an Appimage. Its developers removed all feature restrictions and registration requirements. It is no longer being actively developed and it isn't the newest version but it works very well and has all the features and functionality of the Windows and Mac versions. The only problem I found is that it isn't open source.

If you prefer FOSS then I highly recommend Bibisco. I like it even more than Scrivener. It has an intuitive, elegant interface, is easy to use, and has plenty of features. Scrivener does not have anything on Bibisco. I honestly believe that Bibisco is probably the best-kept secrets in novel authoring software because it is that good.

Another that is really good is Manuskript. It is just as good as Bibisco. I started using Bibisco before learning of Manuskript. I am used to Bibisco but Manuskript is every bit as capable and intuitive. Like Bibisco, Manuskript has a really nice interface and is also easy to get the hang of. Manuskript has options for novels, novellas, stories, and research papers so is a bit more flexible in scope. Bibisco focuses on novel writing, although it is adaptable it does one thing and does it well in true Linux fashion.

Plume Creator is another function-filled open source alternative. I found it a bit harder to use but its clearly quite capable. There are some others, like oStoryboard. Bibisco and Manuskript are both top-notch, highly capable options.

---

