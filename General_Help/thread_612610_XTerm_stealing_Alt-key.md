---
title: "XTerm stealing Alt-key"
date: 2007-11-14
forum: General Help
---

### Post by trevorv on 2007-11-14
I've recently set up a new box that I mostly just run an xterm at. However, the Alt key will not function in programs like Emacs, as the xterm seems to be using it to insert foreign characters - M-v gives me an o with an umlaut.

How can I stop this ridiculousness?

And please don't tell me to use a different terminal emulator, I'm sticking by xterm.

Cheers :-)

---

### Post by slackorama on 2007-12-04
I started having this same problem today. rxvt and konsole are fine.  xterm not so much.

Did you find a resolution to it?

---

### Post by slackorama on 2007-12-05
I found this:
<[http://www.emacswiki.org/cgi-bin/emacs-en/MetaKeyProblems#toc15]("http://www.emacswiki.org/cgi-bin/emacs-en/MetaKeyProblems#toc15")> 

Changes to my ~/.inputrc and ~/.Xresources seem to have fixed my problems after I logged out and back in again.

---

### Post by octoberdan on 2008-03-26
I made the suggested changes;

```

~ $ cat .Xdefaults
XTerm*metaSendsEscape: true
XTerm*eightBitInput: false
~ $ cat .inputrc
set meta-flag on
set convert-meta off
set output-meta on
~ $ 

```

but I'm still getting that damn character when I try to use alt! As a work around I can just use escape, but I'd prefer not to. Any other suggestions? Thanks for the help so far...

---

### Post by octoberdan on 2008-03-26
> **slackorama said:**
> I found this:
<[http://www.emacswiki.org/cgi-bin/emacs-en/MetaKeyProblems#toc15]("http://www.emacswiki.org/cgi-bin/emacs-en/MetaKeyProblems#toc15")> 

Changes to my ~/.inputrc and ~/.Xresources seem to have fixed my problems after I logged out and back in again.

~ $ cp .Xdefaults .Xresources

Didn't see the discrepancy at first between the post and wiki, but when I accommodated it still didn't work. :-(. Any other suggestions?

---

### Post by octoberdan on 2008-03-26
My settings for xterm weren't being loaded, but I found the solution! 

```

xrdb -load ~/.Xdefaults

```

---

