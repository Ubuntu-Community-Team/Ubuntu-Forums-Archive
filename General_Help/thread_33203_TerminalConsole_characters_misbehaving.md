---
title: "Terminal/Console characters misbehaving"
date: 2005-05-09
forum: General Help
---

### Post by lt_kije on 2005-05-09
World-

On Ubuntu boxes installed using the 'server' option, more often than not (in my experience) the terminals seem 'screwed up.' I use the GNU application screen very often, so I'm not sure if that's the root of the issue. In my terminals (multiplexed by `screen`, emulated in Eterm or on the linux console), various characters will display improperly. This is most obvious with ncurses apps (like Elinks), where the border characters turn into weird glyphs. In man pages, characters like the em-dash (--) also get metamorphed into weird glyphs as well. On my recent AMD64 install (which was an awesome experience with Ubuntu!), the characters on the plain console get screwed up as well: if I press the backspace key at the prompt, the terminal screen fills with columns of 'rectangle charcters' (eg empty cursors).

Any ideas? As an aside, I've booted into a graphical session (xorg+openbox) just now and when I press the single-qoute key in Firefox, it opens the find dialog. WTF?

Thanks for the help!

lt_kije

---

### Post by Knome_fan on 2005-05-10
Just guessing here, but iirc ncurses has problems with unicode and as hoary uses unicode this might explain some of your problems.

I don't know if there is a way to avoid this problem in the console, but in X, did you try something else besides Eterm? As great as Eterm is, it was always giving me problems. Maybe give aterm a try or look if you get the same problem with plain old xterm.

---

### Post by lt_kije on 2005-05-10
> **Knome_fan]Just guessing here, but iirc ncurses has problems with unicode and as hoary uses unicode this might explain some of your problems.[/QUOTE]

Seems like a reasonable assumption said:**
> I don't know if there is a way to avoid this problem in the console, but in X, did you try something else besides Eterm? As great as Eterm is, it was always giving me problems. Maybe give aterm a try or look if you get the same problem with plain old xterm.

I thought of the same thing, albeit after I had posted. I installed rvxt (my other old console standby) and don't have the same problem (at least, it doesn't generate a bunch of "empty cursors" when I press backspace. Hmm.

I would *like* to be able to use Eterm, but I'm ok with rxvt for now. Thanks for the suggestions. Also, as another aside, I haven't rebooted or anything, but Firefox no longer appears sensitive to the single-quote key (as in OP).

Thanks!

lt_kije

---

### Post by lt_kije on 2005-05-10
In case anyone stumbles on this thread in the future, I've also added the following line to my ~/.profile (which is sourced by my ~.login file) to set the LANG environment variable:

export LANG="C"

In short, this gets rid of the "weird characters in man pages" problem that I was also experiencing by ignoring the default Unicode setting (in my case, en_US.utf-8).

lt_kije

---

