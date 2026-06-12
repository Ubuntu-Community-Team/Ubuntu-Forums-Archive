---
title: "&quot;Media library&quot; for .pdf and .ps academic papers"
date: 2008-06-20
forum: General Help
---

### Post by adking80 on 2008-06-20
Hi everyone.  This is a long shot, but I'm dying to know if there's an application that suits my needs.

I have one or two hundred academic journal articles in .pdf and .ps format and the number is only going to get bigger.  I want to be able to organize these like I organize my music library!

Is there an application (maybe an xpdf frontend or something) that will let me tag organize these articles by year, journal, author names (multiple), etc.?  Being able to organize these like songs in Amarok, for example, would be an absolute dream!

Thanks for any suggestions.

ak

---

### Post by manfer on 2008-06-20
You can try alexandria. Open Synaptic and install it or just from a terminal.

prompt:~$ **sudo apt-get install alexandria**

After install you will find it under Applications -> Office

If you don't like that one look for book collection managers for linux.

---

### Post by manfer on 2008-06-20
Alexandria is for books but you can use it for what you want.

It has an automatic add book feature in which you enter the ISBN of the book and retrieves automatically all data from the net.

For articles, which ones I suppose don't have ISBN, you would have to use the manual add.

---

### Post by adking80 on 2008-06-21
Thanks for that tip.  Alexandria is not what I'm looking for because it's just information on books, not a file library.  Apparently gpapers is what I want (and hopefully I'll be able to install it soon).

see
[http://ubuntuforums.org/showthread.php?t=674210](http://ubuntuforums.org/showthread.php?t=674210)

---

### Post by manfer on 2008-06-21
Looks nice. Nice research.

It is a pity not on repositories for easy install. Post the OS version you are using and maybe someone is kind enough to prepare a package for easy install if you don't want to go on building it.

---

### Post by manfer on 2008-06-21
It seems it is not easy make gpapers work.

There's another application you could like to try, Referencer. It is a gnome application available on repositories so it is very easy to install.

prompt:~$ **sudo apt-get install referencer**

---

### Post by marialice on 2008-06-26
> **manfer said:**
> There's another application you could like to try, Referencer. It is a gnome application available on repositories so it is very easy to install.

prompt:~$ **sudo apt-get install referencer**
The Referencer site advises to use [the version on getdeb](http://www.getdeb.net/app.php?name=referencer):
> It is not advisable to "apt-get install referencer", since the version in the ubuntu repositories is significantly out of date.

At the moment I still use [Jabref](http://jabref.sourceforge.net/). I have a bibliography of a couple of hundred papers, and the bibtex files are ideal for latex. I used this program on Windows. The linux version is exactly the same, but somehow I don't like the java interface that much when I use it on Ubuntu.

---

### Post by manfer on 2008-06-26
I have installed jabref. Looks a great application.

Could you explain what is exactly a bibtexkey? Is it something like the code in a library? If it is that, I don't like very much the autogenerate key feature, any easy convention to create them?

---

### Post by sancho panza on 2008-06-26
Does anyone not use Zotero(firefox plugin)? Its way more powerful than jabref/referencer. It automatically captures all relevant details about an article and can store a local copy of pdf files, all in just a single click.
But I'm sorry that Zotero is not too useful when organizing an existing collection, but then, nor are any of the other softwares.

---

### Post by adking80 on 2008-07-25
Bibtex is a bibliography typesetting/management system for LaTeX.  If you're writing a paper in LaTex then you can compile a bibliography by referencing a file that contains your Bibtex tags.  It's just kind of metadata for the article you're citing.

Take a look at [http://en.wikipedia.org/wiki/LaTeX](http://en.wikipedia.org/wiki/LaTeX) if you have no idea what I'm talking about.  LaTeX is very awesome but it takes a long time to learn and it's mostly of interest to people in math / computer science / physics.

EDIT:  Ah looking at a jabref screenshot I see that the "bibtexkey" is the key of the reference that you point to in your latex file, using \cite{bibtexkey}.

---

### Post by adking80 on 2008-07-25
I really didn't like the jabref interface so I went to the trouble of installing gpapers.  We'll see how it is.

Installation tips:  [http://ubuntuforums.org/showthread.php?t=762761](http://ubuntuforums.org/showthread.php?t=762761)

---

