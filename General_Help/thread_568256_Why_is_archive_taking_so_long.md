---
title: "Why is archive taking so long?"
date: 2007-10-05
forum: General Help
---

### Post by drs305 on 2007-10-05
I right-clicked on a folder containing about 400 songs/1.5GB and selected 'Create Archive'. So far it's been grinding away for about 20 minutes, first adding files and then recompressing them. The machine is not the greatest (P4, 512 RAM) but with winzip this would have taken just a couple of minutes. What's going on and how do I archive a folder quicker?

I did this via nautilus and not via terminal.

Thanks.

---

### Post by southernman on 2007-10-05
I'd suggest to you that while the cpu and ram do have some affect on this process, it also has to do with the speed of your hdd and possibly due to fragmentation of the filesystem... as well as other processes that may be running. More ram would *help* in any event, though "help" is relative.

An archival of 1.5GB of data is no small feat. I'd suggest to you that Winzip would also take more than a couple of minutes as you suggest it would!

Windows/Winzip = .zip (quickest and least compression)
*nix/archiving = gzip (a little more compression and takes a little longer)
*nix/archiving = bzip (even more compression and takes more time than gzip or zip)

---

### Post by drs305 on 2007-10-05
southernman,

you are correct - winzip did take longer than I'd expected - about 13 minutes to do the same job. I guess I've never zipped a folder that large before. with standard compression, the tar.gz and zip files were just about the same size. I only use windows when I need media player, so I'm glad to see that there isn't much advantage to the windows compression progs. thanks for the reply.

---

### Post by southernman on 2007-10-05
> **drs305 said:**
> southernman,

you are correct - winzip did take longer than I'd expected - about 13 minutes to do the same job. I guess I've never zipped a folder that large before. with standard compression, the tar.gz and zip files were just about the same size. I only use windows when I need media player, so I'm glad to see that there isn't much advantage to the windows compression progs. thanks for the reply.
YVW.  :)

Might I also suggest, to help wien you from that last ounce of bad habit you have *grins*, between Mplayer and VLC (and proper codecs of course), there shouldn't be anything you couldn't play/watch in Ubuntu.

---

### Post by p_quarles on 2007-10-05
A couple small additions to what's already been said: one of the many reasons to love the command line is that you can set the level of compression that is used by either zip, gzip, or bzip. -0=no compression (and very quick), and -9 means maximal compression (and will take a long time). 


Also, gzip and bzip don't create archives of directories like zip does. *nix uses the "tar" application to turn a directory (or a set of files) into a single file. The usage is thus:
```
tar -cf music.tar path/to/music/dir
```
You can also combine tar with gzip:
```
tar -zcf music.tar.gz path/to/music/dir
```
or bzip:
```
tar -jcf music.tar.bz2 path/to/music/dir
```

---

### Post by drs305 on 2007-10-06
p_quarles : thanks for the inputs. 

southernman: I look forward to the day when I can leave media player completely for vlc or another program. that will happen when they allow me to playback an internet archive broadcast at any speed I choose and move the slider bar to any point of the broadcast. I won't beat that subject to death in this thread but I've discussed it elsewhere. thanks.

---

