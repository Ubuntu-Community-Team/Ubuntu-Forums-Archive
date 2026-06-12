---
title: "Using grep to search for a keyword in a bunch of .odt files"
date: 2017-07-29
forum: General Help
---

### Post by John_Patrick_Mason on 2017-07-29
To be clear, I'm not looking for a script, since I don't feel comfortable enough writing one, just yet. I was thinking of typing:

```

cd Documents
grep -ri 'keyword' .

```

but the command returns nothing, and I know the file exists, I just don't know its location. I'd like grep to search all files within the standard "Documents" directory, including its subdirectories. I'm 90% sure the file is in a .odt form, but there a slight possibility the file could also be in a .txt form, so I'd like grep to search for both formats.

Your help is much appreciated.

---

### Post by TheFu on 2017-07-29
ODT files aren't text. They are compressed xml, so you'll need to use a tool that understands how to access that.
There are multiple ways to solve this, but the easiest would NOT be to use grep.  It would be to install an indexer that already understands 99% of the file types on your system.

Recoll - it is like having google for your computer.  Recoll has addons for other types of documents which can easily be installed too.  [http://www.techradar.com/news/software/applications/6-of-the-best-desktop-search-tools-for-linux-666158/6](http://www.techradar.com/news/software/applications/6-of-the-best-desktop-search-tools-for-linux-666158/6) has more.  A simple apt-get install will get it.

BTW, the grep you want is probably

```
$ egrep -iw 'keyword' ~/Documents/*  # to search just the documents directory
```
or to search all files below it, you'll need a "find" first, so 
```
$ find ~/Documents -type f -exec egrep -iw 'keyword' {} \;   # will search all files
```
You can limit the filenames, if you like - just add a **-iname \*txt** to the find before the -exec part.  You'll discover that ODT (or any ODF) files don't really work with grep.

Another method to get text information out is to use tools like "strings" or "pdftotext" ... if you are looking inside PDF files.  A friend of mine wrote an article a long time ago ... *How to index anything* that will provide more ideas [https://www.linuxjournal.com/article/6652](https://www.linuxjournal.com/article/6652)  Just beware that the tools used in 2003 have been mostly replaced by the apache search/indexing tools.

---

### Post by John_Patrick_Mason on 2017-07-29
Thanks for the prompt reply TheFu. I'm going to try out Recoll. I'm marking this thread as solved.

---

