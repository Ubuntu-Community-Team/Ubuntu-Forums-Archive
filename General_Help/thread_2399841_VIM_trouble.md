---
title: "VIM trouble"
date: 2018-08-30
forum: General Help
---

### Post by jerome1232 on 2018-08-30
I use VIM quite frequently and I'm slightly puzzled about what's going on with my vim options.
It seems like VIM auto detects file types and loads language specific settings for different languages. The issue is it seems to always be set at a tabwidth of 8 which is horrendously huge. I want it at 4, and I want them to be spaces. If I set those options it's great, for that instance but I don't want to manually run that everytime I open vim. I tried adding the tab options to my ~/.vimrc and suddenly my syntax highlighting and auto indentation just go *poof*.

I figure there must be somewhere else that configures language specific settings and when I set vimrc it just overrides them. So where the heck is vim getting these from? 

As I understand it autocmds should be in vimrc as well, but I don't even have a vimrc. Is there a way to figure out where the autocmds for the languages I use are hidden away at? All of my google has led to confusing answers.

---

### Post by edadasiewicz on 2018-08-30
There are a number of files & directories under /usr/share/vim -- man vim shows even more.

---

### Post by &amp;KyT$0P# on 2018-08-30
Are you able to make these changes in [FONT=Courier New]/etc/vim/vimrc.local[/FONT] instead of creating a [FONT=Courier New]~/.vimrc[/FONT] ?

---

### Post by jerome1232 on 2018-09-04
> **halogen2 said:**
> Are you able to make these changes in [FONT=Courier New]/etc/vim/vimrc.local[/FONT] instead of creating a [FONT=Courier New]~/.vimrc[/FONT] ?

That seems to have done it!


Kudos to you good sir.

---

