---
title: "evince dvi strange margins"
date: 2008-07-03
forum: General Help
---

### Post by tacutu on 2008-07-03
Hi all!
I just noticed that when I view a dvi file in evince, the margins are all wrong. If I convert the dvi into postscript, then evince shows it with the correct margins.

Have a look at the attached screenshots, it will be obvious what I refer to.

The source document is a simple LaTeX file with no fancy options:
\documentclass[a4paper]{article}

Anyone knows how to tackle this problem?

Thanks.

---

### Post by tacutu on 2008-07-03
bump

---

### Post by tacutu on 2008-07-04
bump...
anyone?

---

### Post by unutbu on 2008-07-04
When you print out the dvi file does the result look like what you see from the postscript viewer, or like evince?

---

### Post by tacutu on 2008-07-05
The margins are correct when printing (i.e. as in the postscript viewer)

---

### Post by unutbu on 2008-07-05
I'm not seeing the same behavior on my machine.

Please post
```
COLUMNS=150 dpkg --list evince*
```

and a dvi file that shows the problem.

---

### Post by tacutu on 2008-07-05
Here you go: 
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  evince                          2.22.2-0ubuntu1                 Document (postscript, pdf) viewer
un  evince-gtk                      <none>                          (no description available)

```

And I also attached a dvi file. Thanks for your help!

---

### Post by unutbu on 2008-07-05
I have the same problem you do when viewing lorem.dvi. I wonder if the problem has to do with its A4 paper size. It appears, at least for printing, evince does not respect paper size as defined by the document. Instead, reads the LC_PAPER environment variable to infer what paper size you must be using. See
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/224882](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/224882)
[https://answers.launchpad.net/ubuntu/+source/evince/+question/6846](https://answers.launchpad.net/ubuntu/+source/evince/+question/6846)

I think that is a terrible idea, since it assumes no American would ever want to view a paper from Europe (and vice versa). If it does not respect paper size for printing, it probably does not respect paper size for viewing either.

I'm guessing that's the problem. I haven't been able to find a fix.

I do know however, that xdvi works fine. Or another workaround would be to use dvips to convert to ps and then use a ps viewer. Or use pdflatex (or pdftex) to create pdf files and bypass dvi entirely.

---

### Post by tacutu on 2008-07-05
Thanks a lot. Well, I mostly go the dvips route anyway, since I often use pstricks in my papers. But still, one'd expect evince to work better :(

I'll try to see what happens with the default paper size and report the results.

Yes, I know xdvi shows the correct output, but... well, xdvi is so damn ugly! :)


Thanks again for your help.

---

### Post by August Karlstrom on 2008-08-22
Actually, Evince does not seem to use LC_PAPER either. On my machine LC_PAPER is sv_SE.UTF-8 and the margins in Evince are still wrong for the A4 format.

---

### Post by tacutu on 2008-08-22
aha, so I'm not the only one w/ this problem! :)

---

