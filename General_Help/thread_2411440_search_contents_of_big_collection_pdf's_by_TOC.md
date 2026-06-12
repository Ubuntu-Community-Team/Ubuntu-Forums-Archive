---
title: "search contents of big collection pdf's by TOC"
date: 2019-01-30
forum: General Help
---

### Post by Bartje on 2019-01-30
Hello,

I have been searching for a tool to search the TOC entries of a large collection of pdf's.

I know about recoll, and am trying it out. It does a good job in searching the text of pdf files, but according to my tests, it leaves out searching the TOC, which is what I need to do.

Is there any other option to scan and search the TOC's of pdf collections?

thanks,
Bart

---

### Post by dragonfly41 on 2019-01-30
I use [ripgrep]("https://github.com/BurntSushi/ripgrep") for searching content in large collections. It does refer to searching PDF text but I have not tried that.

[Later thoughts added}

There is [this pape]("http://jaimejim.github.io/research-tips/")r which suggests converting PDF into txt .. poppler-utils is mentioned.
Or you might look at Pandoc for PDF conversion.
Or pdf2txt.  But do these pickup TOC?

---

