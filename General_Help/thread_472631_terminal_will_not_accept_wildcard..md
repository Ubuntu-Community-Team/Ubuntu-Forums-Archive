---
title: "terminal will not accept wildcard."
date: 2007-06-13
forum: General Help
---

### Post by kameleon25 on 2007-06-13
I am trying to move some files around since I just setup gnump3. For some odd reason my terminal will not accept an * as the wildcard for any command. No matter what I try it won't work. It gives me "invalid option --". Any ideas?

---

### Post by ikonia on 2007-06-13
show us the exact command your using.

---

### Post by kameleon25 on 2007-06-13
kameleon@ubuntu-pc:/var/music/mp3pc-bak2/$ sudo mv -i *.mp3 /var/music/
mv: invalid option --
Try 'mv --help' for more information
kameleon@ubuntu-pc:/var/music/mp3pc-bak2/$

and even

kameleon@ubuntu-pc:/var/music/mp3pc-bak2/$ ls *.mp3
cp: invalid option --
Try 'ls --help' for more information
kameleon@ubuntu-pc:/var/music/mp3pc-bak2/$

But if I leave off the * it lists everything.


Also if I do the same commands on my other ubuntu box it works fine.

---

### Post by 3rdalbum on 2007-06-13
Which shell are you using?

Wildcards should work fine on Bash. Feisty, I believe, has Dash as the default; there may be some strange incompatibility with wildcards.

---

### Post by kameleon25 on 2007-06-13
I am using bash afaik. It is whatever came default on 7.04. I also have 7.04 on another machine and it works just fine. Weird.

---

### Post by Soybean on 2007-06-13
Try using wildcards in a different directory and see if they work. In both cases you were using "*.mp3" in the same directory... I'm thinking the first thing it's finding a filename that starts with "--", and mv and ls are interpreting it as an option rather than a filename.

Which does sound like a bug of some sort, but it's nice to know what's going on. ;)

Edit: I was able to more-or-less duplicate the problem by creating a file called "--.txt". Of course, this was problematic, since now I had a file that I couldn't convince rm to delete or mv to rename. ;) I was able to rename it with Nautilus, though. I assume there's some shell trick that I'm not aware of that would've allowed fixing it from the command line too.

---

### Post by kameleon25 on 2007-06-13
DING DING DING!!! We have a winner... There was a file names '- filename.mp3'. So I ran 'sudo nautilus' and went to rename it. Worked like a charm. Thanks!

---

