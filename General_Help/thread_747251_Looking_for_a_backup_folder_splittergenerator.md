---
title: "Looking for a backup folder splitter/generator"
date: 2008-04-06
forum: General Help
---

### Post by ginjabunny on 2008-04-06
Maybe someone can help, I have been looking for a while now, searching for something like this is difficult because you need to get the wording spot on, which either I can't or it doesn't exist.

What I want is a program which will take a large folder (e.g. 30GB) which is full of files and subfolders and I tell it to reorganise it and split it into DVD sized folders so I can easily back them up to lots of DVDs, it doesn't have to include the burning software, just the ability to split the data into DVD sized chunks.
My manual endevours have not been helped by Nautilus vaguely rounding up file sizes when  I do properties on folders, which is frustrating, hopefully they will sort it out in Gnome 2.22, which is why I have been looking.

Any ideas if anything like this exists? :confused:

---

### Post by chewearn on 2008-04-07
I don't have the exact thing you are looking for.

But, if I'm in the same situation as you, I will be using a dual-pane file manager, e.g. krusader.  Compare to single pane, mouse oriented nautilus, you should be able to work faster with dual-pane.

To illustrate, I have the source directory on the left pane.  On the right pane, I created a few empty subdirectories (press F7 in krusader) in preparation.  Then I open the first subdir.

Next, press TAB to go to left pane, start pressing SPACEBAR to select files or subdir.  As I select, the total filesize selected is displayed on the statusbar.  Once I reached 4GB (leave some slack space), I press F6 to move the selected files to the right pane.

Press TAB to go to right pane, navigate to the next empty subdir, repeat above.

Once you get the hang of it, it's definitely more efficient that drag drop in nautilus.

---

### Post by tamoneya on 2008-04-07
why dont you just use tar with the --tape-length option.  This will allow you to make tar archives of fixed length.
it would look something like this 
```
tar -c -M --tape-length=40960 --file=part1.tar myfile
Prepare volume #2 for `part1.tar' and hit return: n part2.tar

```
make sure to type ```
n part2.tar
```
at the prompt so that it changes the file name

Look here for more details as well as in man tar
[http://www.cgi-interactive-uk.com/splitting_large_files.html](http://www.cgi-interactive-uk.com/splitting_large_files.html)

---

### Post by ginjabunny on 2008-04-11
thanks for the suggestions, I'm pretty sure there are professional archiving tools out there but I was wondering if anyone had come across any open source?

---

### Post by PointyWombat on 2008-04-11
> **ginjabunny said:**
> thanks for the suggestions, I'm pretty sure there are professional archiving tools out there but I was wondering if anyone had come across any open source?

BTW, tar has been around since Christ was born and is native to most if not all *nixes.

Do you want the data to be browsable/usable on each individual DVD's, or can it be part of a larger binary dataset that is mostly unusable until it is restored?

---

