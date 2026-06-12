---
title: "How to search a word within text files"
date: 2019-03-12
forum: General Help
---

### Post by gipsyshadow on 2019-03-12
I've just moved from a very long Windows XP usage to Ubuntu 18.04.2lts and one of the things I missed is the xp "advanced search". I've a huge quantity of txt files and other text files because I note everything there. As someone of you could know in XP you can go to a certain folder and set a very skillful research: you can choose what kind of files to search by their extension (eg. *.txt, *.doc, etc), you can choose to search filtering them by size, by creation date and, the most important filter for me, by typing one or more words included within text.
It's fundamental for me else I'd forget how to tie my shoes :) So can you please suggest my a GUI-ed ubuntu sw to do that? I need it basically for txt file but it could be better if I could use it with doc files and even better with pdf files :)

---

### Post by Tadaen_Sylvermane on 2019-03-12
For plain text files nothing beats command line grep.

*EDIT* Although I have no doubt someone has done a file search gui front end built on grep. I can see the potential.

---

### Post by oldfred on 2019-03-12
I have this in my notes:
       search for text in multiple files.
find . -type f -print | sed 's/ /\\ /g' | xargs grep -i "my text string"
What that does:
Find everything in the current directory or any of its children which is a regular file.
Convert spaces in filenames to escaped spaces so the grep won't fail.
xargs converts the line-separated list of items from the find into a space separated list for the grep.
grep -i is searching while ignoring capitalization for "my text string"

---

### Post by The Cog on 2019-03-12
I have been surprised by the search speed of a search program called **ag**. My impression is that it is many times faster than **grep -r**. Usage is very similar, though ag has many more options for only searching certain file types, ignoring .git folders etc.

To install it: **sudo apt install silversurfer-ag**.

---

### Post by dragonfly41 on 2019-03-12
[ripgrep]("https://github.com/BurntSushi/ripgrep") claims even faster search than silversurfer.

However setting aside search speed, a trusty gui which I often use is [SearchMonkey]("http://searchmonkey.embeddediq.com/").

SearchMonkey is in Software Centre.

---

### Post by The Cog on 2019-03-12
> **dragonfly41 said:**
> [ripgrep]("https://github.com/BurntSushi/ripgrep") claims even faster search than silversurfer.

Ooh! Shiny!
I'll have to try that one out.

---

### Post by gipsyshadow on 2019-03-12
thanks for suggestions!
I don't know if I explained properly my goal anyway I want to add something to avoid any misunderstanding: I want to know if "XYZ # 12<"$" are present within one or more text files WITHOUT opening anyone of them, all right?
I've just seen a screenshot of SearchMonkey and I think I'll try it. I searched the web and found [recoll]("https://www.lesbonscomptes.com/recoll/") and it relies in Software Centre too, do you know it?

---

