---
title: "tab autocomplete with tar command stopped working in 13.10"
date: 2014-02-13
forum: General Help
---

### Post by captainentropy on 2014-02-13
I recently upgraded to 13.10 and I'm no longer able to use the auto-complete function in the tar command (bash). It worked fine until the upgrade. The auto-complete works in all other commands that I normally use it with. So far, this seems to be specific to tar. 

Is this a bug perhaps? I can't find any other threads on this (re: tar). I've tried all the suggestions in this thread [http://ubuntuforums.org/showthread.php?t=1865538](http://ubuntuforums.org/showthread.php?t=1865538), obviously to no avail. Any ideas how to fix this?

Thanks!

---

### Post by captainentropy on 2014-02-18
OK, so it looks like I can use the option -o in tar to use a file name  in making the tarball. So, before if I had a bunch of .txt files that I  wanted to archive that all began with, say, "log_files" and I wanted to use  that as the base for the name of the tar file then I would do

```
$ tar czvf log<Tab>.tar.gz *.txt
```

the file log_files.tar.gz would then be made. 

But something happened with autocomplete in my last upgrade and I can no longer do this.

I can achieve the desired outcome by instead using 

```
$ tar czvf_***o***_ log<Tab>.tar.gz *.txt
```

The "-o" refers to some deprecated option for --no-same-owner, which I don't understand, but according to this readme of the bash-completion program "-o filename" is then default (which isn't working for me):

> It's more important to have proper completion of paths to tar files    than it is to have completion for their contents...and '-o filenames' is used with complete instead.

[http://anonscm.debian.org/gitweb/?p=bash-completion/bash-completion.git;a=blob_plain;f=README](http://anonscm.debian.org/gitweb/?p=bash-completion/bash-completion.git;a=blob_plain;f=README)

And though I'm not sure how related bash-completion is between debian and redhat, I found this (emphasis added): 

> Wed Jun 26 12:00:00 2002 Ian Macdonald
- make tilde expansion work during chown completion
**- *make tar completion '-o filenames' by default*.**
[http://packages.atrpms.net/dist/common/bash-completion/bash-completion.spec.html](http://packages.atrpms.net/dist/common/bash-completion/bash-completion.spec.html)

Unless I'm completely misunderstanding something about this, my tar is broken. A reinstall didn't fix it either.[URL="http://packages.atrpms.net/dist/common/bash-completion/bash-completion.spec.html"]
[/URL]

---

### Post by Impavidus on 2014-02-19
Sometimes bash autocomplete is really smart. For example, when I type **evince h<tab>** bash autocompletes to *hevelkraan.eps*, even though *hyphenation.tex*, *hz.tex* and *hz.aux* are present too. Apparently bash knows that evince is used to open .eps files, but not .tex or .aux files. **evince ar<tab>** doesn't give any results, even though two file names starting with *ar* are present in the current directory, because they have .tex and .aux extensions.

My bash autocompletes to any file extensions after a tar command, but I am on 12.04. Maybe bash on 13.10 is smart enough to only autocomplete to .tar, .tar.gz and .tgz extensions after a tar command. From the FAQ you linked I see that using alt-/ instead of tab will autocomplete regardless of file extension.

---

### Post by captainentropy on 2014-02-19
Thank for the tip Impavidus. Although I'm not sure where on the page you saw "alt-/" mentioned, it worked exactly as <tab> used to, although, it's more keystrokes. 

And yes, I was upgrading from 12.04. I'm not sure why subsequent releases needed to get "smarter", it was fine the way it was. Unless I can find a rationale where the change improves the use for the majority of people (i.e. why was it broken?), I'm gonna call it a dumb change ;)

I guess using tar cvzfo isn't a big deal, though.

---

### Post by Impavidus on 2014-02-19
It was in the README you linked, line 102.

Glad you solved it. Happy Ubuntu'ing.

---

### Post by captainentropy on 2014-02-19
Oh wow, thanks for the clarification. I saw that but thought it was referring to something else because hitting M-/ in a bash terminal just gives me M/. I had to google that. Looks like emacs mapped/maps the "Alt" key to "M". Diving deep in the Unix notation weeds here hahaha.

---

