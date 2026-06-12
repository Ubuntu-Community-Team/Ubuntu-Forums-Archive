---
title: "How to manage Tex Live packages with Ubuntu?"
date: 2013-08-23
forum: General Help
---

### Post by lads on 2013-08-23
Dear all,

Tex Live is conceived to help manage LaTeX packages through a little command line app called *tlmgr*. In Ubuntu *tlmgr* is not available from the repos and can only by installed manually. The idea is for the user to install required LaTeX packages (*latex-**) from the Ubuntu repos and not from CTAN. So far so good.

But this week I started working on an article whose template requires all sorts of exotic LaTeX packages that do not seem to be available from the repos. Two examples: *europs.sty* and *flushend.sty*; they are actually listed as being part of certain Ubuntu *latex-** packages, but although these are installed on my system, the aforementioned files are nowhere to be found.

So the question is how to get these LaTeX packages without manually installing *tlmgr*.

Thank you.

---

### Post by Impavidus on 2013-08-23
Indeed many LaTeX packages are not present in the Ubuntu repos, or only as outdated versions. Sounds like you need to install tlmgr manually or (as I do) install the LaTeX packages manually (in /usr/local/share/texmf/). I don't know tlmgr, but it *might* cause conflicts by handling files in the same directory as the Ubuntu package manager. It may be possible to let it use /usr/local/share/, where no problems should occur.

---

### Post by lads on 2013-08-23
> **Impavidus said:**
> or (as I do) install the LaTeX packages manually (in /usr/local/share/texmf/). 

Hi Impavidus, could you please detail a bit more how you do it? Do you just download the packages from CTAN to that folder?

Thank you.

---

### Post by Impavidus on 2013-08-23
Most packages are available as a .zip archive. In there you'll usually find a file with installation instructions. It usually involves running **latex package.ins**, copying the files this produces to some subdirectory under /usr/local/share/texmf and running **sudo texhash** to update some caches. If there are fonts involved thing may get a bit more complicated. I didn't check the packages you mentioned.

---

### Post by GwL3eNC on 2013-08-23
Hello,

if you decide to install  the newest  texlive [http://www.tug.org/texlive/](http://www.tug.org/texlive/) you can use the tlmgr [http://www.tug.org/texlive/doc/tlmgr.html](http://www.tug.org/texlive/doc/tlmgr.html)
to install packages in an easy way.

---

### Post by lads on 2013-08-26
Folks thank four your answers. We have two options here, both work, but both have a down side too.

**Manual install** - you won't get updates, neither from the Ubuntu repos nor from Tex Live. Besides this you have to make sure the package version you are installing matches the Tex Live version installed.

**tlmgr** - you need to manually install Tex Live, thus foregoing whatever is available from the Ubuntu repos. Both Tex Live and its packages are updatable, but you have they you have to do it yourself (outside of the regular Ubuntu updates).

I don't get the logic behind the Ubuntu management of Tex Live any more.

---

### Post by lads on 2013-08-26
I just found that [Ubuntu 12.04 is packaged with an outdated version of Tex Live]("http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012"), this may be the cause of some of my woes. At least *siunitx* is working properly after upgrading to Tex Live 2012.

---

### Post by lads on 2013-08-27
After some more it seems all problems are gone; basically, Tex Live and the packages it used where too old. I hope future LTS versions can ship with up to date versions of Tex Live.

---

### Post by Impavidus on 2013-08-27
I agree.
But the difficulty is that Ubuntu 12.04 comes with what was the latest Tex Live when it was released – Tex Live 2009, already a few years old by then. The packages in TeX Live aren't always the latest versions available when Tex Live is released, giving additional delays. As a result, I have seen LaTeX packages in the Ubuntu repos that were six years behind in updates. The two-stage packaging procedure is inherently slow.
Fortunately most packages are rarely updated and rarely depend on specific versions of other packages, so most of the time you can just manually install later versions and manually check for updates only when you need a new feature present in the latest version.
[quote=tug.org]By the way, a native TL, which is typically installed under /usr/local, and a TeX from your operating system can happily coexist, each with their own completely independent trees and programs. (Do not try to merge them!)  So you could install a native TeX Live if your vendor is not keeping up[/quote]Don't worry too much about this. Plugging in the latest versions of simple LaTeX packages should work >90% of the time.

---

### Post by lads on 2013-08-28
> **Impavidus said:**
> I agree.
But the difficulty is that Ubuntu 12.04 comes with what was the latest Tex Live when it was released – Tex Live 2009, already a few years old by then. 

Here's the [Tex Live release log]("http://www.latex-community.org/forum/viewtopic.php?f=12&t=6685&p=69224"):

[LIST]
[*]Tex Live 2009 - November of 2009
[*]Tex Live 2010 - September of 2010
[*]Tex Live 2011 - July of 2011
[*]Tex Live 2012 - July of 2012
[*]Tex Live 2013 - June of 2013
[/LIST]

When Ubuntu 12.04 was released Tex Live 2009 was already 3 years and 3 releases behind. That's quite a bit don't you think?

---

### Post by Impavidus on 2013-08-28
> **lads said:**
> When Ubuntu 12.04 was released Tex Live 2009 was already 3 years and 3  releases behind. That's quite a bit don't you think?

Quite a bit. I think Ubuntu 12.10 and 13.04 use TeX Live 2012.

---

### Post by Feathers McGraw on 2013-08-28
I feel your pain, went through this in a rush last year with a deadline to meet!
 
Initially (when I was running 12.04) I ended up using a backport to get a more up to date version (source: askubuntu question [here]("http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012")). Basically:

```
sudo add-apt-repository ppa:texlive-backports/ppa
sudo apt-get update
sudo apt-get install texlive-full
```

NB: texlive-full is important for all the exotic packages.

I had also tried installing vanilla texlive, including tlmgr, but found it was more fuss than it was worth.

Thankfully, after upgrading to 13.04, I have had zero problems :D.

Feathers

---

