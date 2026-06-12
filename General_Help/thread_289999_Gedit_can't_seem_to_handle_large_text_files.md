---
title: "Gedit can't seem to handle large text files"
date: 2006-10-31
forum: General Help
---

### Post by JarG0n on 2006-10-31
Right now, Windows notepad is outperforming Gedit on my Ubuntu Dapper Drake installation.  I open a large sql file, approximately 2.5MB, and the program just stalls, and eventually stops responding.  

What gives?  Gedit should be more powerful than this. ](*,)

---

### Post by matthewstory on 2006-10-31
Do you have the proper permission to edit the file, and also what is the charecter encoding on the file.  

Gedit in general . . . however . . . is terrible, I'd recommend at least bumping up to bluefish, or trying your hand at vim.  With a .vimrc file, vim is extremely powerful, and features syntax highlighting and tabbed file editing.

---

### Post by Qew on 2006-10-31
Although I do agree with matthewstory about the power of vim, and it's the text editor I turn to, if you don't like it and find it too hard to use, then may I suggest mcedit, an editor that'll let you edit when you start it, which you'll find in the mc package (Midnight Commander). It has syntax highlighting and can also handle large file sizes with ease. Still, vim is well worth learning to use and isn't maybe as hard as is made out to be.

---

### Post by JarG0n on 2006-11-01
I have permissions to edit the file, since I had created it in \home\username\ somewhere just moments before.  Not sure on the encoding though, whatever the default is I guess when MySQL creates an sql file.

If Gedit is so bad, why is it included in the Ubuntu distribution to begin with?  If GNU\Linux has the image of being a powerful OS, this is certainly no testimony to that fact.  A simple text editor is probably one of the first things a new user sees when migrating.  This kind of bug may just steer him or her away from GNU/Linux entirely, since notepad just works.

> **matthewstory said:**
> Do you have the proper permission to edit the file, and also what is the charecter encoding on the file.  

Gedit in general . . . however . . . is terrible, I'd recommend at least bumping up to bluefish, or trying your hand at vim.  With a .vimrc file, vim is extremely powerful, and features syntax highlighting and tabbed file editing.

---

### Post by Qew on 2006-11-01
Thing is, there are plenty of text editors to choose from. Gedit works for most people doing the usual type of text editing, but for some it's quite bloated and, arguably, lacking (as you've found out). Ubuntu is just giving what it considers to be the best tools for the "normal" user, and Gedit works for most people most of the time. Do be aware that they also install vim and nano, and other text editors are easily within reach.

---

### Post by skymt on 2006-11-01
You may want to check out Leafpad if you want something notepad-like. A lot of people also swear by Scite. Both are available in Synaptic.

---

### Post by ejket on 2006-11-01
Gedit is probably the default because the default use is to edit config files, which gedit is likely good for.  In some other distros, the default is nano, which is also not an editor likely to be put to serious use.

More serious general-purpose editors amenable to coding are (g)vim, emacs, and jedit, to name a few.  I like gvim, though it does take a little getting used to.  There's a variant of gvim called cream that I recommend you try out.  It's gvim on training wheels, and it's in the repo.

edit:
I agree that scite is also good.

---

### Post by JarG0n on 2006-11-01
Thanks guys !

---

### Post by ehird on 2006-11-01
Nano not used seriously? Load of crap. It's very powerful.

---

### Post by matthewstory on 2006-11-01
hehe, nano!  I love nano, don't get me wrong, I'm a sysadmin, and for performing small tweaks to config files nano is a fine editor.  It's just useless for everything else, much like gedit.  Gedit comes with Ubuntu because it's the standard GUI text editor for gnome, and it's alot like notepad, in that it's good for tiny stuff and it usually gets the job done, but at the end of the day it's weak sauce.  If you really need something GUI based for text editing, if that's what you're more comfortable, the recommendation of JEdit is a really good one, assuming of course you can get the java virtual machine installed.  JEdit is pretty sexy, but the rest of us will probably just sit here and re-open the holy war of emacs v. vim if this thread continues.

---

### Post by JarG0n on 2006-11-01
*rubs salt in holy war wound* :mrgreen:

---

