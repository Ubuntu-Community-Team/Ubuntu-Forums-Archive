---
title: "bash completion restrict filetypes for specific commands"
date: 2014-01-09
forum: General Help
---

### Post by waitingroomsnap on 2014-01-09
Hello,

I'm trying to figure out how tell bash to only autocomplete certain filetypes for specific commands.  I've been finding some articles and answers related to this, but I don't think I've found exactly what I want.  I'm still rather ignorant when it comes to my .bashrc file, so some of what I've found has been a bit over my head.

I use vim a lot to edit tex files, and using autocomplete on compiled tex files is kind of annoying because there are always a bunch of files with the same filename, but different extensions, .aux, .log, etc.   I can add a FIGNORE= to my bashrc file to ignore these, which is useful.  But I don't want to add .pdf to this list (so that vim will always autocomplete with the .tex filename) because then .pdfs are ignored for all commands I use.

It looks like the complete command can do it, but I haven't understood anything well enough to decipher what to do.  And man complete doesn't have an entry.  :(  Can bash be configured like this?  And if so, can someone provide some help, or point me to an article with a good tutorial on using this feature?

Thanks!

---

### Post by CharlesA on 2014-01-09
This might help.
[http://www.manpagez.com/man/1/complete/](http://www.manpagez.com/man/1/complete/)

---

### Post by waitingroomsnap on 2014-01-10
Thanks for the link. I think I've found the solution inside /usr/share/bash-completion/bash_completion

there is a _install_xspec function which is a custom function based upon complete, and below this are numerous uses of the function with various common commands, such as vim. I can add in the tex extension here and I get the behavior I want (I think, I've only fiddled around a little bit so far).

Somewhere, I saw mention of a ~/.bash_completion which I do not already have. Instead of editing the file in /usr/share/bash-completion/ , can I create a ~/.bash_completion that bash will use? If so, does having this ~/ file need to just have the additional options I want, or should it be an entire copy of /usr/share/bash-completion/bash_completion with my edits?  Is the /usr version overwritten when I update ubuntu versions, which would then lose all my changes (if I changed that version of the file)

Thanks again.

---

