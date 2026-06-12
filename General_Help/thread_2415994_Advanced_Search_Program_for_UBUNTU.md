---
title: "Advanced Search Program for UBUNTU"
date: 2019-04-03
forum: General Help
---

### Post by fmurillo on 2019-04-03
Hello,
I need help. A few weeks ago, we have migrated to Ubuntu (v18 and v16 LTS).
But there is something we are missing of Windows, its search tool. As you know Windows allows search inside the files (.doc, .docx and so on). This is very useful for us.
I looked for tools like this for Ubuntu and I found SearchMonkey, but it doesn't work well, doesn't find strings inside the files (maybe I'm not using the tool correctly).
Please, if somebody knows about a better tool, help me. Do not consider terminal tools (like grep or something like that).

---

### Post by dragonfly41 on 2019-04-03
> [COLOR=#000000]I found SearchMonkey, but it doesn't work well, doesn't find strings inside the files (maybe I'm not using the tool correctly).[/COLOR]

You are not using SearchMonkey correctly. I use SearchMonkey as my first option when scanning directories.

Tick the box next to Containing field and search for files containing the defined string.
If you click on ExpressionBuilder you can specify a regex pattern.

Another tool to explore is [ripgrep]("https://github.com/BurntSushi/ripgrep").

If you are searching corpora then I would suggest concordance analysis.  Here is an excellent tool.

[http://www.laurenceanthony.net/software/antconc/](http://www.laurenceanthony.net/software/antconc/)

And also there is [TextSTAT]("http://neon.niederlandistik.fu-berlin.de/en/textstat/").

[P.S.]  You have mentioned *.docx format which is proprietary format with lots of formatting. I would convert these to text before scanning. Pandoc is another tool in the toolkit for this purpose.

---

### Post by Impavidus on 2019-04-04
I don't know Windows' search tool. I don't use Windows.

There are search tools in Ubuntu that let you search inside files, as dragonfly41 told. It's slow, as the tool has to scan all files, but it works. The problem is that a search tool can only search the contents of a file if it understands the file format. Plain text (like .txt) is easy, some file formats (like .html and .tex) need some additional processing for non-ascii characters, some (like .odf) have an additional layer of compression using a standard compression algorithm, all of which we can design a search tool for. .pdf is quite hard already, as you have to interpret the entire file to see the text, but at least the specifications of pdf are (mostly) freely available.

But no search tool understands every file format ever invented and maintaining such a tool would be practically impossible. The normal course of action is to use a bunch of separate tools to convert various file formats into plain text, then use a simple text search tool to search through that text. I think that's what most search tools actually do behind the scenes. It's not very hard to do this yourself on the command line.

Microsoft invented .doc, which is a very complex format, and they're the only one who fully understand it. It makes sense that Microsoft is the only one who can make a search tool that can reliably search in .doc files.

---

### Post by mrdc76 on 2019-04-04
To be able to search files by content is a functionality necessary for any modern OS. Luckily, this is possible in Ubuntu, if this is what the OP meant. And yes, you can search docx-documents by their content just fine. This functionality is built in Nautilus/Files, but you must install "tracker" first. Another app providing this utility is Recoll, but it is built on QT and the UI will not match GTK-applications. 

Tracker is not installed by default in Ubuntu, because it is not very robust. It could be stuck on corrupted files, for example, and never finish indexing.

---

### Post by fmurillo on 2019-04-09
Hello everyone and thanks for your help.

I've revised your suggestions and I've tested the programs. Recoll program is the best solution for my requirements, I could found different kind of string inside different files (even MS files). Furthermore, it's easy to use.  

Just for record, I had tested TextSTAT and AntConc but I had problems with DOC, XLS and PPT files. I've tried Tracker but I had similar problems, specially in Ubuntu 16. In the case of ripGrep and SearchMonkey, principal problem (considering kind of final users), they aren't easy to use.

---

