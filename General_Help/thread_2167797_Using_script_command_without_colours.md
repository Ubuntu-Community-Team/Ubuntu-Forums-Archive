---
title: "Using script command without colours"
date: 2013-08-15
forum: General Help
---

### Post by CaptainMark on 2013-08-15
I'm trying to use the script command to record an entire terminal session to a text file but the bash colouring system totally messes up the output, it prints the literal colour symbols to the output file, see here:```
Script started on Thu 15 Aug 2013 08:21:07 BST[1m[37mmark@[34mdesktop [37m~/ [34m$ (B[msudo f[K[K[K[K[K[Klsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0  47.7M  0 part 
&#9500;&#9472;sda2   8:2    0  23.3G  0 part /
&#9500;&#9472;sda3   8:3    0 207.7G  0 part /home
&#9492;&#9472;sda4   8:4    0   1.9G  0 part [SWAP]
sdb      8:16   0 465.7G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465.7G  0 part /media/passport
sr0     11:0    1   4.3G  0 rom  /media/mark/LXFDVD175
[1m[37mmark@[34mdesktop [37m~/ [34m$ (B[mls -l
total 76
drwxr-xr-x  3 mark     mark 24576 Aug 15 08:21 [0m[01;34mDesktop[0m
drwxr-xr-x 12 mark     mark  4096 Jul 18 21:34 [01;34mDocuments[0m
drwxr-xr-x  4 mark     mark  4096 Aug 12 12:53 [01;34mDownloads[0m
drwxr-xr-x  7 mark     mark  4096 Aug 15 07:31 [01;34mDropbox[0m
drwxr-xr-x 58 mark     mark  4096 Jul  8 18:14 [01;34mMusic[0m
drwxr-xr-x 13 mark     mark 12288 Aug 11 14:10 [01;34mPictures[0m
drwxr-xr-x  4 mark     mark  4096 Nov 22  2012 [01;34mPodcasts[0m
drwxr-xr-x  2 mark     mark  4096 Mar 31 14:08 [01;34mPublic[0m
drwxr-xr-x  1 lorraine 1002  4096 Jul 21 22:14 [01;34mRaspberrypi[0m
-rw-r--r--  1 mark     mark   146 Aug 15 08:16 typescript
drwxr-xr-x  6 mark     mark  4096 Jul 21 10:47 [01;34mVideos[0m
drwxr-xr-x  1 mark     mark  4096 Jul  8 00:00 [01;34mXbmc[0m
[1m[37mmark@[34mdesktop [37m~/ [34m$ (B[mexit


Script done on Thu 15 Aug 2013 08:21:32 BST
```Does anyone know a way to make script record without the colour symbols, I've tried starting xterm with the -cm flag to disable colours but that didn't work.
Note: I can view the file fine in a terminal by using the cat command but I want to transfer the output to a .txt file to be read on any other system.

---

### Post by Vaphell on 2013-08-15
[http://www.commandlinefu.com/commands/view/3584/remove-color-codes-special-characters-with-sed](http://www.commandlinefu.com/commands/view/3584/remove-color-codes-special-characters-with-sed)

---

### Post by CaptainMark on 2013-08-15
Thanks, works pretty well but still leaves a few weird characters that must be related not to colour but something else

---

### Post by Habitual on 2013-08-15
check out [http://showterm.io/](http://showterm.io/)

example:
```
showterm ls -lF
showterm recording finished.
Uploading...
http://showterm.io/97223a3886cde107b055d

```

you can then play in online in a browser.

if you 'need' the script file for later use **or with sensitive material** I'd use it like so

```
showterm
do stuff
exit
```
it will bomb most likely (does here interactively every time) with a similar message:
DON'T PANIC
your work is safe in "/tmp/showtime.21021.script" and "/tmp/showtime.21021.times"
To try uploading manually, use:
showterm --retry "/tmp/showtime.21021.script" "/tmp/showtime.21021.times"

then check out /tmp/showtime.21021.script

it will be stripped of any such markups


HTH.

---

### Post by CaptainMark on 2013-08-15
Thanks but this isn't exactly what I was looking for, I really needed to be able to keep a simple text file log, the keyword being simple, I can't really be dealing with that everytime. I notice also that the cat command has no problem viewing the typescript output but the less command totally fails with it, weird. I notice after extensive googling that I'm not the only person who has fallen foul of the same issue, it's a surprise no one has made a version of script or an option flag for script that outputs only plain text and wipes out these 'control characters' in real time

---

### Post by Vaphell on 2013-08-15
indeed, first thing i looked at was the *script*'s list of parameters :-)
examples of these weird chars? It should be easy to extend the regex to strip them too.

---

### Post by CaptainMark on 2013-08-16
Yeah go figure, ```
Script started on Fri 16 Aug 2013 15:20:48 BST
mark@desktop ~ $ (Bls
Desktop  Documents  Downloads  Dropbox  Music  Pictures  Podcasts  Public  Raspberrypi  typescript  Videos  Xbmc
mark@desktop ~ $ (Bexit


Script done on Fri 16 Aug 2013 15:20:50 BST
```Thanks

EDIT: It's no copy&pasting correctly either so heres a gedit screenshot, it has like these box type characters which you get sometimes when you don't have the correct font installed

---

### Post by Vaphell on 2013-08-16
try this
```
s/\x1B[[)]([0-9]{1,2}(;[0-9]{1,2})?)?[mKB]//g
```

```
$ test=$'abc\x1B)Bdef'
$ echo $test | od -c
0000000   a   b   c 033   )   B   d   e   f  \n
0000012
$ echo $test | sed -r 's/\x1B[[)]([0-9]{1,2}(;[0-9]{1,2})?)?[mKB]//g' | od -c
0000000   a   b   c   d   e   f  \n
0000007
```

---

