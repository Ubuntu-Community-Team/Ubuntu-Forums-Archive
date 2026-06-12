---
title: "Somehow accidentally deleted my home directory, can't figure out why this happened"
date: 2015-12-31
forum: General Help
---

### Post by Phillip_Chang on 2015-12-31
(Yes, yes, I now fully understand that using rm -R is a very dangerous thing... will be using trash-cli or something else next time... but I still want to know why it happened)

It all started when I was trying to delete a strange folder in /usr/lib/haxe  (was trying to setup the haxe libraries at that time). There was a folder called "flixel", and it seemed that it was an infinitely recursive folder. Basically, the folder structure was like this:

flixel
&#9492;flixel
&#9492;install.sh (maybe.. don't clearly remember the name of the shell file at that time)

and when I opened the flixel folder, there was the same structure (and it never seemed to end, folder after folder...)
So I tried to delete using "sudo rm -R flixel", and that somehow deleted my home directory. (When I realized something had gone wrong, it was too late.)
So far I can come up with two theories.
1. The folder was so screwed up that deleting it somehow managed to delete the home directory with it
2. I later realized that I have set up an alias in my ~/.bashrc before and it was like this:
    alias flixel="haxelib run flixel-tools"
    So maybe I have done something else instead of actually deleting the flixel folder.

But both theories don't make sense...
Thankfully I have saved most of my work in git repositories, so there wasn't that much damage. But it would be really helpful if someone could explain how the home folder got deleted. Thanks!

Additional info:
Using Ubuntu 15.10 + Gnome Desktop

---

