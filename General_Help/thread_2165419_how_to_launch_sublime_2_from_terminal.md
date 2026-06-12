---
title: "how to launch sublime 2 from terminal?"
date: 2013-08-04
forum: General Help
---

### Post by physman2 on 2013-08-04
I first did [COLOR=#333333][FONT=arial]sudo apt-get-repositories ppa:webupd8team/sublime-text-2, and then 
[/FONT][/COLOR][COLOR=#333333][FONT=arial]sudo apt-get install sublime-text
and then
sudo apt-get autoclean && sudo apt-get auto remove

Now what I'm wondering is, how do i launch sublime 2 and how do I make it my default python ide?

Neither sublime, sublime-text, sublime-text-2 nor subl work, I tried typing all of those in and none launched sublime text 2.[/FONT][/COLOR]

---

### Post by Habitual on 2013-08-05
/home/jj/Downloads/sublime2/SublimeText2/sublime_text/sublime_text works for me.
it's -rwx------ here but I copied it from backup.

Try 
```
find `pwd` -name sublime_text -type f -exec {} \;
```

P.S. ST is NOT an IDE, it IS a text editor.

---

### Post by physman2 on 2013-08-05
Okay found the answer, I just followed these instructions:

[http://community.linuxmint.com/tutorial/view/907](http://community.linuxmint.com/tutorial/view/907)

thanks!

---

