---
title: "vim 7.0 slow undo and indenting"
date: 2006-11-27
forum: General Help
---

### Post by fannus on 2006-11-27
So I have a somewhat esoteric problem, but maybe some other people have had it and can enlighten me:

I recently upgraded to Edgy, and now two operations in vim (or gvim), are unreasonably slow:

1.) the last undo in a sequence of undos
2.) auto-indenting in visual mode

to give a typical scenario, fire up vim and type in:

int main()
{
int x = 1;
}

now visual mode, select the text, and autoindent (=), then undo this

On my system (core 2 E6400) the autoindent and the undo lag for about second each.

I messed around with this some more, and pinned it down to my .vimrc file.  I'm using the dvorak keymap, so I map the keys in normal mode back to qwerty, so it contains a lot of:

noremap a a
noremap x b
noremap j c
noremap e d
noremap . e
noremap u f
...
...
...

I've attached the .vimrc file. I'm sure some people have similarly large .vimrc files for other reasons. I've been doing this with vim 6.x for *years* and never had any problems.  Does anyone know of either a better way to do the key remapping (I haven't found one), or maybe some kind of remedy for this speed, because I do both of these operations in vim a *lot* and it is really a dealbreaker.

If none of these, can we at least have access to vim 6.x in the repository, as I think the upgrade to 7.0 isn't unconditionally better, and breaks certain behavior.

---

### Post by fannus on 2006-11-27
so I haven't found any info on *why* vim 7.0 has this annoyance, but if anyone wants the nostalga of vim 6.4 in edgy (and yes, I'm a total noob to package based distros, so the cleanest way to do this actually took me a few minutes to figure out :P)

gedit /etc/apt/sources.list


add the old dapper packages:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

load up synaptic and search for 'vim', then mark the 'vim' package, and go to Package->Force Version, and set it to 6.4 for all 3: vim, vim-common, and vim-runtime, then also 'lock version' on them so it won't keep complaining at you that they are out of date.

hope this helps, I'll see if I can file a bug report or something on the vim mailing list.

---

### Post by fannus on 2007-11-03
seems to be fixed in vim 7.1.56 under Gusty

---

