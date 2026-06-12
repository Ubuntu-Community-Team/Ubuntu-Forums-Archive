---
title: "Geda &amp; ngSPICE &amp; Oregano"
date: 2005-06-21
forum: General Help
---

### Post by Dave_is_sexy on 2005-06-21
OK, maybe this was a bit ambitious, but they seemed kinda like multisim (windows) and i need something like that.

Synaptic install all Geda packages (from my repositories)
& ngSPICE & Oregano

Now, normally when there's nothing new in the Gnome menu, i've done something wrong. Yep

```
dave@D5:~$ geda
```

Ah that works. Schematics is there. Nothing else is. For example, Clicking around makes this:

```
dave@D5:~$ geda

Gtk-WARNING **: horizontal scrolling not implemented

Gtk-WARNING **: horizontal scrolling not implemented
sh: pcb: command not found
sh: --: invalid option
Usage:  sh [GNU long option] [option] ...
        sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)
        -abefhkmnptuvxBCHP or -o option
sh: gerbv: command not found
sh: easy_spice: command not found
sh: gwave: command not found
gEDA/gschem version 20040111
gEDA/gschem comes with ABSOLUTELY NO WARRANTY; see COPYING for more details.
This is free software, and you are welcome to redistribute it under certain
conditions; please see the COPYING file for more details.
```

and in the actual dialog window we have:

```
Read system-gschemrc file [/etc/gEDA/system-gschemrc]
Did not find optional ~/.gEDA/gschemrc file [/home/dave/.gEDA/gschemrc]
Did not find optional local gschemrc file [./gschemrc]
Read init scm file [/usr/share/gEDA/scheme/gschem.scm]
```

Fab! lol

So, if anyone knows about this stuff, help'd be much appreciated.

I'm also curious to know more about the frontend / backend and if i'm using the best combos? Thanks

---

### Post by Dave_is_sexy on 2005-06-22
OK given up on Geda, but Oregano starts and works up to the point of simulating. 


```
### Too few or none analysis found ###
```

---

### Post by NRios on 2005-10-26
By the way, where is ngSPICE in Breezy?
It is nowhere to be seen ... has it been dropped from ubuntu?

Thanks!

---

### Post by thevoice on 2005-10-27
This iis interesting, this is an issue a few of us are having with breezy regarding geda, I had it working in hoary though, and you seem to be using hoary, judging by your choice of forum.

I wonder if that means something to someone...

[see here]("http://www.ubuntuforums.org/showthread.php?t=78787&highlight=geda")

---

### Post by estratos on 2005-11-09
Hi all.

For those interested in a good PCB software under Linux (open source), I recommend KiCad. It's far supperior to geda regarding its appearence and ease of installation. It's based on WXWIDGETS, so it works under Windows too. It

I've installed it in my breezy machine without problems. The graphical environment is quite good and there is a young yahoo group ([http://groups.yahoo.com/group/kicad-users/](http://groups.yahoo.com/group/kicad-users/))

KiCad home page:
[http://www.lis.inpg.fr/realise_au_lis/kicad/](http://www.lis.inpg.fr/realise_au_lis/kicad/)

Daniel.

---

### Post by mathiasv on 2006-02-02
Hey!
I could not make gEDA work on Breezy, even though the installer finally seemed to do something.
So I gave Oregano a go, and the drawing part works ok. But does anyone know a tutorial or some examples of Oregano simulations?
Mathias

---

### Post by RLovelett on 2008-01-21
I'm getting close to getting a working simulation.  You're going to need to install GnuCap.

```
sudo apt-get install gnucap
```

More when I get it!

---

