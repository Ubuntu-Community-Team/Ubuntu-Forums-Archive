---
title: "Program for web page creation"
date: 2019-08-04
forum: General Help
---

### Post by mikeavison on 2019-08-04
Hi
I am looking for a program that creates simple web pages, preferably where the code is laid out nice and clearly. My first thought was to use Libre Office Write but it does not support relative addressing (v4.2.8.2). I realise I could still use this but the way I usually do this would be rather awkward and slow with absolute addressing. I usually have a dir on HDD with all the pages and associated files (jpg etc), try it out on disc and when happy ftp the lot. Of course with absolute addressing I would then have to edit every link to point it to the host server! Is there a different way of doing this? I can't make Libre Office save to the server (because it is ftp access)???

Alternatively can anyone recommend a program from the Ubuntu Software Centre which would allow relative addressing?

Alternatively I am just going to have to type all the code manually which admittedly might be good for my soul.

Please accept the following apologies. I may have posted this in the wrong forum area, I looked for web development and even choice of Ubuntu programs but couldn't find such categories. It does seem a really obvious question which must have been answered lots of times but I searched the forum before posting and came up with nothing, probably because I couldn't think of the optimum search terms ('web writing software') etc. Feel free to castigate and point me to the right places!

Thanks

Mike Avison

---

### Post by dragonfly41 on 2019-08-04
Search for solution base href as here for example .. 

[https]("https://stackoverflow.com/questions/24028561/relative-path-in-html")[://stackoverflow.com/questions/24028561/relative-path-in-html]("https://stackoverflow.com/questions/24028561/relative-path-in-html")

But as to recommending tools there are dozens to try. Much depends on what you hope to build.

In my Ubuntu 16.04 I have ... Bluefish editor, Code::Blocks IDE, Brackets, Komodo IDE, AptanaStudio3, Mozilla SeaMonkey  .. all largely unused now.

But I read between the lines that you are starting your journey so try ...

[https]("https://www.seamonkey-project.org/releases/")[://www.seamonkey-project.org/releases/]("https://www.seamonkey-project.org/releases/")

But if you want a more modern editor integrated with github I use [Atom]("https://atom.io") where you can write Electron apps.  You need to research Node.js which is a dependency. There are many, many Atom packages (perhaps too many) to explore. Read the Flight Manual before starting.  It may be too rich a diet.

Another route is to use a simple notes editor - specifically [CherryTree editor]("https://www.giuspen.com/cherrytree/") where you can write pages as hierarchical nodes and export nodes to HTML files.  You can also export TOC (table of contents).  I use this on a regular basis but not for HTML writing.

Cherry tree can be installed thus

```
sudo apt-get update && sudo apt-get install cherrytree
```

You can then edit the exported HTML files to add styles and frameworks.

Another approach is to write in markdown and use pandoc in command line to convert markdown to HTML. In Atom there are markdown editor and markdown-preview-enhanced packages.

---

### Post by NM5TF on 2019-08-04
@mikeavison...

you might take a look at Visual Studio Code  here [https://code.visualstudio.com/](https://code.visualstudio.com/)

tommy

---

### Post by andrew.46 on 2019-08-05
There is always a case for going 'old school' and learning HTML and CSS with a text editor, even if this is only in the early stages. If you go down this road Geany is a good choice (I use this) while Bluefish would give a little more assistance...

---

### Post by TheFu on 2019-08-05
I use vim.  In the hands of an expert, vim is freakin' amazing.  Call it old school, if you like. It works and is available on every system.

There's only a need to use an absolute URL in 1 place. Everywhere else, it should be relative. Let the web server handle that part. It is automatic.

If I need more complex pages, I'll write using a markdown tag language, usually textile, still inside vim, and then run it through a filter to generate HTML.  If I need multiple output formats, I'll use pandoc. That's how I create pdf, text, html and my presentations - pandoc is nice.

As for having a nice layout to the website, setup templates that you copy in or just include for stuff you do all the time.  Be mindful of having too many files on a single page. It impacts performance, perhaps more than appropriate compression "web optimization" for images.  Be certain to use compressed files when sending pages from the webserver.  I use server microcaching to speed things up, since 99% of visitors are just viewing, having a 1 second disk and DB cache doesn't matter, and prevents hitting disk too much.

One more thing - plain FTP should have been killed off in 1999.  Use ssh/scp/sftp/rsync over ssh instead. If the hosting provider only supports plain FTP, it is time to fire them for being inept at security for their customers.  Some teams will deploy to production directly using their DVCS.  I'd rather not have that access on a production server, but everyone has different risk profiles and mitigation methods.

---

### Post by mikeavison on 2019-08-07
Hmm I should have been more specific I am looking for a wysiwyg type of program. (Hence mentioning Libre office writer). I think all the suggestions above are for text editors with many added bells and whistles. Is that correct?

---

### Post by QIII on 2019-08-07
If you should find a bona fide wysiwyg editor, please let us know.  Many are the adventurers who have taken up the quest to discover one.  Few are those who return.  Those that do usually spend the remainder of their days blathering and cackling to themselves in 
 dark corners as they waste away, broken.

---

### Post by dragonfly41 on 2019-08-08
Some of the apps listed in post#2 *are* WYSIWYG editors if you take the time to study them.

Seamonkey (although dated) as listed earlier is WYSIWYG editor.

Click on Composer button.

then you have four modes ..

Normal
HTML tags
HTML source
Preview

Then there is AptanaStudio3.

They all toggle between edit and preview.

One nice editor from my Windows usage days is [SiteSpinner]("https://www.sitespinner.com/"). I might try spinning this up in VirtualBox Windows VM just for the hell of it. It creates HTML and SVG output.

Staying with Ubuntu there is Scribus, designed for quality document layout but you can export as SVG to embed in HTML.

---

### Post by NM5TF on 2019-08-08
> **mikeavison said:**
> Hmm I should have been more specific I am looking for a wysiwyg type of program. (Hence mentioning Libre office writer). I think all the suggestions above are for text editors with many added bells and whistles. Is that correct?

I have used Kompozer in the past for my initial web page that is in my sig...go here [https://sourceforge.net/projects/kompozer/](https://sourceforge.net/projects/kompozer/)

tommy

---

