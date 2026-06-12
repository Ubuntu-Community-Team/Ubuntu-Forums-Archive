---
title: "Help finding &quot;pretty RST&quot;"
date: 2019-07-01
forum: General Help
---

### Post by Drenriza on 2019-07-01
Hi all!
In the past i have used a program as i recall being named "pretty RFC", i have not been able to find it again now that i need it,
and i dont have it installed anymore either to look up the exact name.

The functionality of the program was that it took lines such as 

headline1
=======

headline2
^^^^^^

paragraphs

anchors

and made them into a HTML page that was easy to comprehend and understand for none IT people or
as documentation.

<h1>headline1</h1>

<h2>headline2</h2>

<p>paragraph</p>

<a href="#">anchor</a>

It could also add images, links to other pages and so on.
Anyone know such a program available for Ubuntu / Debian?

Thanks in advance
Best regards!

Edit: So i started searching and i found what i had forgot "Sphinx-doc"
[https://www.sphinx-doc.org/en/1.5/tutorial.html](https://www.sphinx-doc.org/en/1.5/tutorial.html)

So the question is now, is this the best tool for the job?
Ease of use, ease of installation, ease of configuration and so on

---

### Post by TheFu on 2019-07-01
**pandoc** is what I use to convert "markdown" layout text files into different formats.  I prefer Textile as my markdown variant.

From the manpage:
```
DESCRIPTION
       Pandoc  is  a  Haskell library for converting from one markup format to
       another, and a command-line tool that uses this library. [COLOR="#FF0000"] It  can  read[/COLOR]
       Markdown, CommonMark, PHP Markdown Extra, GitHub-Flavored Markdown, and
       (subsets of) Textile, reStructuredText, HTML, LaTeX, MediaWiki  markup,
       TWiki  markup, Haddock markup, OPML, Emacs Org mode, DocBook, txt2tags,
       EPUB, ODT and Word docx; and [COLOR="#FF0000"]it can write[/COLOR] plain text, Markdown, Common-
       Mark,  PHP  Markdown Extra, GitHub-Flavored Markdown, reStructuredText,
       XHTML, HTML5, LaTeX (including beamer slide shows), ConTeXt, RTF, OPML,
       DocBook,  OpenDocument,  ODT, Word docx, GNU Texinfo, MediaWiki markup,
       DokuWiki markup, Haddock markup, EPUB (v2 or  v3),  FictionBook2,  Tex-
       tile,  groff  man  pages,  Emacs Org mode, AsciiDoc, InDesign ICML, and
       Slidy, Slideous, DZSlides, reveal.js or S5 HTML slide  shows.   It  can
       also produce PDF output on systems where LaTeX, ConTeXt, or wkhtmltopdf
       is installed.

```
Pretty amazing.  But it has a command line that only a Unix nerd could love. For example, below takes a textile.md input file and creates 2 output files.
a) pretty text - good for handing out to students
b) [S5 html slide deck]("https://meyerweb.com/eric/tools/s5/s5-intro.html") - ready to use for presentations  

```
#!/bin/bash -x

TITLE="LPI-1 Wk 04 Access Controls"
ROOT=101-Wk04-Access_Control

pandoc -s -T "$TITLE" --standalone --slide-level=3 -f textile \
    -t plain $ROOT.md -o $ROOT.txt
pandoc -s -T "$TITLE" --toc --standalone --slide-level=3 -f textile \
    -t s5 $ROOT.md -o $ROOT.html
```

Enjoy.

---

### Post by Drenriza on 2019-07-02
Hi TheFu

Thanks for the suggestion! i have looked into Pandoc and it sure does have a lot of features for all kinds of input / output.
I have installed both Pandoc and Sphinx to test them out, there is a lot of information (current / outdated) to sift through to understand what they can and can't.
And just understanding what they are.

Again thanks for the suggestion!

---

### Post by TheFu on 2019-07-02
Please mark the thread as solved using the "thread tools" button near the top.  I'd wait a few more days so others might post their favorite solutions too.  I used to use a small perl script to read textfile and generate S5-html, before discovering pandoc.  Perl CPAN (now cpanminus) has lots and lots of parsing tools for all sorts of inputs and output formats.  The main part of that script is just 10 lines or so.  This should work - assuming you can install the module dependencies.
```
#!/usr/bin/env perl 
use strict;
use Text::Markup;
my $file = $ARGV[0];
my $textile = Text::Markup->new(
                default_format   => 'textile',
                default_encoding => 'UTF-8',
                );
my $html = $textile->parse(file => $file);
print $html ;
```

There are 11 input formats supported by the Text::Markup module.  *Markdown* and *MultiMarkdown* included. Only HTML output is supported.  The module figures out what the input is automatically and produces HTML.  That's it. Nothing more.  Use it as a filter. Might want to change the default_format, or not. Shouldn't matter.

Usage:
```
./md-2-html.pl   input.md > output.html
```

---

### Post by Drenriza on 2019-07-02
@TheFu

If we say i would like to use Sphinx or Pandoc for future documentation of code, infrastructure setup and so on.
Are Sphinx and Pandoc what would be consider secure? For example, i could imagine people putting what could be considered
sensitive information into their documentation and than securely store them on a private server some where.

But Pandoc or Sphinx being in the middle of that process could be in a prime position to push a copy to themselves / anywhere else,
it would not be my first goto thought of a realistic situation. **But** i have tried to look through FAQ for both to see if they say _anything_ about security, and have
not been able to find any information regarding that.

Is it a totally unrealistic situation, and both platforms are considered secure in the sense that private documents created with either framework
stay private unless one self publish them?

Thanks in advance
Best regards!

---

### Post by TheFu on 2019-07-02
I wouldn't worry.  I don't know sphinx, but any text processing program has the same issue when it comes to security.  

sort, cat, more, less, tee, tac, awk, perl, javac, php, ruby, python, .... these all take text in and put something out.  There are hundreds more commands built-into every Unix just like them.   They are just filters.  Any command output can be piped into a tool like nc, then sent almost anywhere.  

Getting files off a networked system is trivial with or without encrypted tunnels.  Even going through corporate proxy servers isn't hard at most companies.

I would worry about other things, but if you like, grab the source code and audit away.

---

### Post by dragonfly41 on 2019-07-02
**++1 **for Pandoc recommendation.


> [COLOR=#000000]If we say i would like to use Sphinx or Pandoc for future documentation of code, infrastructure setup and so on.[/COLOR]

My current setup is to use [Atom]("https://atom.io") as my editor (although I do use other editors).
The Atom packages to install should include [markdown-preview-enhanced]("https://atom.io/packages/markdown-preview-enhanced") where you can pipe output to custom pandoc command which draws on the "frontmatter" (yaml) at the top of any markdown document.

---

