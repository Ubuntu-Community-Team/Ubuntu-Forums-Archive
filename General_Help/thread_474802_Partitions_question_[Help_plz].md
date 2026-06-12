---
title: "Partitions question [Help plz]"
date: 2007-06-15
forum: General Help
---

### Post by OutCell on 2007-06-15
Hi,

I had WinXP, SUSE & Ubuntu (Ubuntu is my last install). I wanted to get rid of SUSE so i delete the partitions for suse and now i have free space (~33gb). But now i can't add this space to Ubuntu by resizing the Ubuntu partition :(  I am using GParted. I took a screenshot of my desktop with GParted open so you can see what is happening. The Ubuntu partition is the one with the lock icon (sda4)..

[IMG]http://i169.photobucket.com/albums/u233/OutCell/Screenshot.png[/IMG]

---

### Post by miLl3niUm on 2007-06-15
I am really sorry, I can't help, hope someone else can :(

But I want to ask you, how does your Ubuntu look like this?

EDIT: I mean the panels

---

### Post by Jose Catre-Vandis on 2007-06-15
To do this you need to have your ubuntu partition unmounted, and preferably not in use.

I know some Windows partitioning tools allow you to work on an active partition, but gparted doesn't, and in my opinion its not a good idea anyhow! :D

Google for and download the Gparted live cd, burn it to a CD, and boot up with it. You should then be able to expand your ubuntu partition without any problems

---

