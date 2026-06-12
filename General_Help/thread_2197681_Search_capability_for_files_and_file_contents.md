---
title: "Search capability for files and file contents"
date: 2014-01-04
forum: General Help
---

### Post by ron177 on 2014-01-04
Dear all,
 
I wonder if someone can help me find a way to search for files and  file contents. I have a lot of notes and documents on my computer and I  really need a way to do keyword searches for their contents.

 
More preferably I would need a way to do what softwares such as  DevontThink Pro do for Mac users: which is an intelligent search in the  contents of lots and lots of documents, pdfs, etc.

 
Any thoughts?

 
Thanks,

 
Ron

---

### Post by varunendra on 2014-01-05
Perhaps the most popular and most efficient way to search for strings in Linux/Unix is the "**grep**" command. For example, to search for the keyword "ron" in a directory "Mydirectory" (assuming it is in the current directory)-
```
grep ron Mydirectory/*
```

To search for "ron177", in "Mydirectory" and its subdirectories -
```
grep -R ron177 Mydirectory
```

To search for Ron177 while ignoring the case of alphabets and being unsure of the numbers after it -
```
grep -iR ron[0-9]* Mydirectory
```
Now from here, we started using 'Regular Expressions' ([0-9] is a regexp), and these are the real power of grep. Endless power in fact, in terms of scope and flexibility of search terms.

Unfortunately, as far as I know, grep works reliably only on simple text files. It can (and does) search in binary and other file formats, but not in the way we expect and is not reliable there. For example, it can't search a keyword in a .doc or .pdf file. There seem to be a few dedicated tools to do that (e.g. "pdfgrep" for pdf files), but I haven't tried any and so can't recommend any in particular. Just do a search in Synaptic (or Software Center) and maybe you could find something useful.

For file search based on filenames and/or properties, "**find**" command is probably the best tool available on 'Any' platform. Its downside is that its proper and efficient usage requires a lot of practice and frequent reading of its man page (it's too rich for those who have no experience of command line tools).

Now there is a GUI program "**searchmonkey**" in the repos that is a good mixture of both 'find' and 'grep'. But it also seems to suffer the same limitations like grep (not being able to search in more than simple text files).

A quick search on the net turns this page up : [http://www.tuxradar.com/content/best-linux-desktop-search-tools](http://www.tuxradar.com/content/best-linux-desktop-search-tools)
I haven't tested any of the tools listed there, so can't comment on their quality and efficiency.

Hope someone else may be able to let us know of some more advanced tools that may be able to do everything you want. If not, you may be able to use 'Windows' tools on wine. Just like I frequently use some duplicates finding/removal tools on wine.

---

