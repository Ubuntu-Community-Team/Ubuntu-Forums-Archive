---
title: "Linux"
date: 2007-02-10
forum: General Help
---

### Post by sauravbhaumik on 2007-02-10
Dear friends, here comes the time to be impartial. I am an ubuntu user. But I see no reason to be confined in only one distribution of linux. So, if you have used other distributions of linux, kindly describe the advantages of theirs over Ubuntu.
One of the advantages of Ubuntu is that it can install online the latest versions of packages. And the c++ compiler it provides is much upgraded.
I am a mathematician. So, I would want a distro that provides an upgraded LaTeX environment. In ubuntu, I use Kile editor; and I have not yet been able to make it spell check. And the help option doesn't work either.
Moreover, I am fond of listening to online classical music. In ubuntu, I can't play the songs from musicindiaonline.com
So, kindly recommend a distro (gnome desktop) that has some advantages over Ubuntu and that fixes the problems said as well.
Thanks

---

### Post by gradedcheese on 2007-02-10
hmm... I use LaTeX all the time, but I don't see the need for an 'editor'

aspell -c my_document

spell checks just fine :)

---

### Post by sauravbhaumik on 2007-02-10
> **gradedcheese said:**
> hmm... I use LaTeX all the time, but I don't see the need for an 'editor'

Then where do you write the source?

---

### Post by gradedcheese on 2007-02-10
vim, a very nice text editor.  run 'vimtutor' to learn how to use it.  With 'syntax on' and some other options set (on by default in Ubuntu, I believe), it hilights LaTeX very nicely.  I'm a programmer, so this sort of setup makes more sense to me.

---

### Post by sauravbhaumik on 2007-02-11
> **gradedcheese said:**
> vim, a very nice text editor.  run 'vimtutor' to learn how to use it.  With 'syntax on' and some other options set (on by default in Ubuntu, I believe), it hilights LaTeX very nicely.  I'm a programmer, so this sort of setup makes more sense to me.

OK I have installed gvim.
See I am not a programmer.  As soon as I have opened the gvim editor and started to stir my fingers on the keyboard I found that I can't write anything on it. Less to speak about compiling.
How do you manage to work with it?

---

### Post by sauravbhaumik on 2007-02-11
OK pressing a I can write. But how to compile and what about the dvi or pdf file I should be able to behold?

---

### Post by sauravbhaumik on 2007-02-11
Compiling using vim is much complicated. I have just compiled a small piece of writing but it seemed in no way more elegant than by kile.

---

### Post by sauravbhaumik on 2007-02-11
Isn't there anyone who can comment on distro's?

---

### Post by ddumanis on 2007-02-11
[www.distrowatch.com](www.distrowatch.com)

---

### Post by gradedcheese on 2007-02-11
I like to use 'make' to compile my LaTeX files into PDF and the like.  This probably sounds odd, but for a programmer again this makes sense :)

Here's the Makefile I use:

```

all: all_pdf all_ps

tex_sources := $(wildcard *.tex)

all_pdf: $(patsubst %.tex,%.pdf,$(tex_sources))
all_ps: $(patsubst %.tex,%.ps,$(tex_sources))
all_txt: $(patsubst %.tex,%.txt,$(tex_sources))

%.ps: %.tex
    latex $*.tex
    dvips -o $*.ps $*.dvi

%.pdf: %.ps
    ps2pdf $*.ps $*.pdf

%.txt: %.tex
    latex $*.tex
    dvi2tty -w80 -o $*.txt $*.dvi

clean:
    rm -f *.aux *.dvi *.log *.ps *.pdf *.toc *.out *.tab

```

(note: the indentation is a tab, not spaces)

So if you have a file called 'document.tex' in the same directory as this Makefile, you just type 'make'  (or from vim, you can just press Escape to get into command mode and then :make to make)

---

### Post by superman on 2007-02-11
I really enjoy suse 10.1. Its easy to install, lots of support as well..

---

### Post by big_gie on 2007-02-16
What is great about linux is the tons of choices you have.

I'm using ubuntu on my laptop at home and gentoo on my desktop at work.

Gentoo is really nice distro. You can choose exactly what you want in your system (using use flags), choose to have a bleeding edge system or a stable one, or a combination of both. You can choose how to compile your program using the best of your processor with cflags. This is the best distro to learn linux I think since all of the config is done on the command line. 98% of linux documentation on the web is about gentoo. The forum is way more active (and more helpful) then ubuntu's.
I do have 2 concerns about gentoo: it can be really slow to compile. On my super fast desktop at work it isn't a problem at all. But on my (3 years old) laptop I don't really like to pass the weekend just compiling X. Also, since you compile from source, you need plenty of disk space. Again, at work this is not a problem since I don't have all my mp3, movies, personnal data, etc, even if both of my disk are the same... A third (personnal) issue is gui polishing. Generally, gentoo ships with "vanilla" apps, meaning they didn't get patch for more feature. For example, gnome logout screen on gentoo is really ugly. This is the kind of details ubuntu is working too on witch is a nice thing.

I like ubuntu on my laptop because it is beautiful. There is many GUI also. The gnome logout screen is beautiful too (using manu cornet patches). This is the kind of details I find important, even if I work 95% of the time on the command line.

But unfortunatly, I don't find ubuntu to be really serious in updating their packages. It seems all the efforts is going into its next release (feisty). Many programs are outdated, even on edgy. I think ubuntu is wainting to much on debian for that. I also find it impossible to create packages with ubuntu/debian. Ok their is checkinstall, but no dependency or serious packaging details. So you must depend on the dev to update everything. 

I used Archlinux a lot also. I think it one of the great distro. I is small, fast, simple, easy, and more open then ubuntu. It is most of the time bleeding edge but as stable, if not more, then ubuntu. A package for a particular apps doesn't exist? Just create a simple PKGBUILD (simply a bash script telling what to do to download, configure, compile, dependency, url, etc) and run "makepkg". Or if the package exist but is outdated, you can just update youself the PKGBUILD, and create the package yourself. If you create a new PKGBUILD, you can give it to the community by posting on AUR which is a kind of repository of user created PKGBUILDs. 
Archlinux is small enough to be able to really help in the developement of the distro. Try to modify something in ubuntu (or many others...)
Arch is quite hard to install though. I never really understood the logic (if their is) of the installer. It really nice. I am considering ditching edgy in favor of arch (again).

Something I want to add to both Archlinux and Gentoo their rolling release. What this means is that their version is not as important as in windows or ubuntu or debian or... Typing "pacman -Syu" or "emerge <i can't remember>" will always give you the up to date distyribution. You never need to upgrade to the latest distro version (like dapper -> edgy, edgy -> feisty, what to do for dapper -> feisty anyway? format? sad...).

This is my experience :) Hope it helped!

---

### Post by Tomosaur on 2007-02-16
I have a DSL (Damn Small Linux) distribution on a USB pen drive. It's a better alternative to cygwin imo, as I can boot into DSL while in Windows, using Qemu, which is provided in the embedded DSL iso. It's a nice little distribution, and I'd recommend it to anyone who needs to use Linux on different machines.

---

