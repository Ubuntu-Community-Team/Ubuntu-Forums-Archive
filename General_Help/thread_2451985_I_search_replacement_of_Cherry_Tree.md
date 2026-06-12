---
title: "I search replacement of Cherry Tree"
date: 2020-10-14
forum: General Help
---

### Post by petrogromovo on 2020-10-14
Hello, 
I use Cherry Tree under Kubuntu 18 and wonder are there some replacement of it with features:
1) Similar tree view organization
2) In one page search without modal dialog (like kate does)
3) text validation. At least english, but if can also work with other languages - very nice
4) Import from Cherry Tree CherryTreeFile.ctd 
5) Working with rather big files. Now my CherryTreeFile.ctd has size about 12Mib and it seems rather slow...


Are there something like that ?


Thanks!

---

### Post by dragonfly41 on 2020-10-14
You will find it difficult to find anything better than CherryTree. It is locked into my workflow.
Current version 0.99.15 in Ubuntu 20.04.
I use CherryTree in a toolchain. I would consider breaking down "big files" into multiple ctd files and 
then use CherryTree command line to launch specific *.ctd files.
The new version allows import from other *.ctd files.
Regarding text validation consider parsing CherryTree text using concordance tool as
in corpus linguistics.
Regarding search I use ripgrep in command line to search through all CherryTree files (I have many and I search for *.ctd).
In short it is a superb tool from the author.

---

### Post by petrogromovo on 2020-10-15
I found KeepNote and tried to test it. But I did not find if there is a way to import into KeepNote from Cherry Tree?

---

### Post by dragonfly41 on 2020-10-15
KeepNote build - 2012
CherryTree build - 2020

But if you are determined to migrate I would use export HTML in CherryTree then import HTML in KeepNote.

---

### Post by The Cog on 2020-10-15
I moved from CherryTree to Zim now that CherryTree has been discontinued. They are quite similar, but I don't think you can convert between them very easily. I just opened both and did a manual select-all, copy, paste between them. But that's going to be a pain with that much info.

---

### Post by dragonfly41 on 2020-10-16
> [COLOR=#000000]CherryTree has been discontinued[/COLOR][COLOR=#000000]

In defence.

[/COLOR]That is not quite the case. True, the old Python2 based CherryTree is discontinued but the new GTK3 version emerges.
In fact I continue to use both on Ubuntu 20.04 .. and Windows 10.

The author of CherryTree recently wrote .. 

-----------------------------------------------------------------
[GIUSPEN]("http://www.giuspen.com/")
[14 October 2020 at 11:25]("https://www.giuspen.com/2020/10/cherrytree-0-99-15-issued/comment-page-1/#comment-36486")
[COLOR=#6B6B6B][FONT=&amp]Should be backward compatible but anyway the old Pygtk2 version is getting discontinued
[/FONT][/COLOR]
-----------------------------------------------------------------

There is an opportunity to fine tune the GTK3 version, and to submit issues for the developers to act on, but jumping ship is not the best way forward.
Point me to any editor which has the features of CherryTree including feature to embed blocks of 
multiple language code:

c, cpp, go, html, js. markdown, perl, php, powershell, python, python3, r, sh. yaml .. and any others to add.

Regarding the migration of data, as I commented earlier you can export all CherryTree nodes as HTML, but if KeepNote cannot import these exported HTML file a*s a block* there is little point. If a user can parse XML then CherryTree *.ctd content (which is XML code and can be viewed in XMLCopyEditor) can be parsed to extract content using python script (xmltree).

---

### Post by petrogromovo on 2020-10-16
I tried Zim, and first what I payed attention :1) Can I change font settings of pages content 2) has page editor some rtf functionality ?

---

