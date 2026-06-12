---
title: "Text editor / file format with group function or minimal note takeing app"
date: 2022-02-07
forum: General Help
---

### Post by semental on 2022-02-07
Hi to all!


First of all. Sorry for my spelling, i'm from Argentina.


I hope you can help me with something i'm lookin for.




I use a keyboard  shortcut to a text file to write any tought, text or quick reminder on my pc.


It can be from a link to a webpage, an app, game or movie that i want to download later, a command to run on terminal once in a while and dont loose it (ej chmod o chown recursive, ssh to a specific pc, etc.


So, anything i need in hand is there and i need it to be fast. I don't have to open a browser or a big app.


Now the text is getting to big and messy, so i'm trying to organize it.


Thats why i'm srarching for a solution to organize this kind of things. In order to have for example, a sidebar with tags, categories or folder (you name it) so i can drop that text in there




example:


structure when i open the note/text/app


movies


linux commands


links


music


work


others




structure when i expand some of the contents




movies
+house of gucci
+download new season form dexter!!!


linux commands


links


music
+iron maiden new album


work


others




1-) I know the fisrt sugested solution will be a note taking app. I use one (evernote), but i mostly use it on my phone or for more complex things (large texts, links, text with embedded files etc.)




The thing i'm looking for is to drop almost just words thes fastes posible way (exj. "chmod 777", or "theres is a director cut of blade runner" or "iron maiden album is out!!!"


So, if it is a note taking app it has to be super lighteight and zero bloated, so if i press the keyboard shortut it will show almost instantly an also, i wanted to be just text, no a thousand of options, logos, menus, popups etc. (maybe theres is some note taking app  like this).


Another down of a note taking app is the long-term support of the database format..




If i use a note taking app, and it has its own note format, maybe in 2 years it doesnt work anymore and i have to export text by text and start from sratch


2-) another solution (is what i am using now)  is using geany programmer text editor, and save the text with "py" extension. Its close to what i want, but still it isnt.


if i write something, and below i start with a space, it recognizes it as a submenu.
I also can fold and unfold that submenu.


The downside is that every time i open the app all the groups are expanded, and another mayor downside, is that i don't have a sidebar with all the groups to find groups easily, so if ai want something in that group i have to search it in the text.


Also. i can't order groups by any criteria.


The upside: its just one text file, with a readable format, so i don't need to use geany exclusively. I f i want to open the file on a text editor it open ok (just not with the subgroups).


I attached a screen recording of an example o what i want created in geany

[IMG]https://drive.google.com/file/d/1ezGWMjku0eql-kegPzgcLF_kMuA1tcS6/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/1ezGWMjku0eql-kegPzgcLF_kMuA1tcS6/view?usp=sharing[/IMG]
[URL="https://drive.google.com/file/d/1ezGWMjku0eql-kegPzgcLF_kMuA1tcS6/view?usp=sharing"]https://drive.google.com/file/d/1ezGWMjku0eql-kegPzgcLF_kMuA1tcS6/view?usp=sharing
[/URL]




So, i hope i made myself clear, i'm sure that theres gotta be some app or any kind of solution out there, i just still can find it or don't know what to to look for






Thanks in advance








greetings!!!

---

### Post by oldfred on 2022-02-07
All my notes that I keep for what seem to be common questions on the forum are in a Zim file.
It uses text files that you can organize as you see fit. And can import your text files if desired.

Zim is a graphical text editor used to maintain a collection of wiki pages.

I like it as if I save a link to a web page, I can click on link and go to web page.
With other text editors I have to copy link & paste into Firefox.

---

### Post by semental on 2022-02-07
thanks so much for your response!!

i'll check it as soon i get back from work

---

### Post by dragonfly41 on 2022-02-07
CherryTree

[https://www.giuspen.com/cherrytree/](https://www.giuspen.com/cherrytree/)

---

### Post by semental on 2022-02-07
thanks a lot, also very helpful

---

### Post by semental on 2022-02-07
Ok, i did a first fast check of the two apps:


first "zim" (thanks oldfred), and i found it great! very close to my goal.


But then dragonfly 41 suggested cherrytree and i think it fit even more to my needs.




The first differences i encounter are:


- cherrytree has an option to protect the file by password


- cherrytree also lets you do a globalsearch  between the nodes/lists/folders


Maybe these option are also in zim, and i dididnt found it yet.


But i'll keep testing the two apps


I hope this helps other in similar needs




You two were very helpful!

---

### Post by oldfred on 2022-02-07
Have seen others suggest CherryTree, have not tried it.

Zim has find for current page & Search for all pages.
Find can use multiple words with a space, but Search really only works on single words. Multiples seem to separately find both.
Do not see encryption as an option in Zim, so if you need that CherryTree or some other app may be better.

---

### Post by dragonfly41 on 2022-02-08
In fact the two tools can work together. And other tools.

In CherryTree > File > Export > Export to HTML > Zim
In CherryTree > File > Import > Import from Zim folder

Finally for the requirement to keep code snippets
In CherryTree  > Insert > Insert Codebox
and multiple scripting languages can be inserted from Bash to whatever.
Set in Preferences > Plain Text and Code
Also in Preferences different shell terminals can be used instead of default term

For example Yakuake (drop down) I like.  Or gnome-terminal. Or PowerShell.
Just change the command (it can be reset to default).

I advocate using tool chains rather than sticking with one chosen tool for everything.


=================================

Later added notes on CherryTree usage.

Post #1 set out some user requirements.

The tree hierarchy is met in CherryTree.
But note further that if the user selects any tree node
and the right click Change Node Properties (or F2), the style of the tree node can be customised. Also note the field &#8220;Tags for searching&#8221;.

Movies and Music could (optionally) be linked to Zotero so that user has a Zotero collection in cloud. Private or group.

Regarding the longevity of database structure this is currently SQLite or XML. The database usage can be either format. If we click File > Save As we see that data can be saved as either SQLite or XML. 

In Preferences > Miscellaneous ensure that AutoSave is set as required.  This allows a time stamped series of backups to be saved. With notation ~, ~~, ~~~. ~~~~.

If a long document is created use the Insert TOC (Table Of Contents) feature at the first node to create an index page.

As explained earlier leverage the Insert CodeBox feature to keep a record of scripts. You can intersperse text between CodeBoxes select the CodeBox and then Execute Code (F5).

This &#8220;polyglot&#8221; approach is similar to Jupyter Notebooks which I also use for some exercises.

CherryTree provides a tool for scouring this ubuntu forum (and other forums), copying and pasting text (and links to forum discussions) and placing terminal commands into CodeBoxes. All in one node per subject. For example there might be a SSH sub node.

There can be multiple CodeBoxes in each node.

[https://github.com/giuspen/cherrytree/issues/1940](https://github.com/giuspen/cherrytree/issues/1940)

You can write multiple CherryTree notes (documents) and import these into a master CherryTree document.

There are other features which can be discovered with usage. I have used this app for years and it is rated highly by other users. I use LifeRea and have added CherryTree RSS subscription to follow developments. Also follow development issues at 

[https://github.com/giuspen/cherrytree/issues/]("https://github.com/giuspen/cherrytree/issues/1940")

---

