---
title: "[SOLVED] Make command"
date: 2008-04-30
forum: General Help
---

### Post by rolodoom on 2008-04-30
Sometimes I need to change file extensions from JPG or jpeg to jpg, so I can use them on my website. I'm using this script that I found on internet and works perfectly

```
$ for x in *.JPG; do n=${x/.JPG/.jpg}; mv $x $n; done
```Is there anyway to make this script available on my system, I mean like making a command that I can run from the terminal, something like JPG2jpg, or right click folder on nautilus?

---

### Post by Monicker on 2008-04-30
Create a file with this in it:

```
#!/bin/bash

for x in *.JPG; do n=${x/.JPG/.jpg}; mv $x $n; done
```

Save it as JPG2jpg, and then do "chmod +x JPG2jpg".  As root I would then cp it to /usr/local/bin, so that you can execute it no matter what directory you are in.

Dunno how you would do it in Nautilus myself.  I'm sure someone else here does.

---

### Post by guraknugen on 2008-08-28
> **rolodoom said:**
> Sometimes I need to change file extensions from JPG or jpeg to jpg, so I can use them on my website. I'm using this script that I found on internet and works perfectly

```
$ for x in *.JPG; do n=${x/.JPG/.jpg}; mv $x $n; done
```Is there anyway to make this script available on my system, I mean like making a command that I can run from the terminal, something like JPG2jpg, or right click folder on nautilus?

Well, I saw that you got an answer to this already. I just wanted to point out the alias feature. In your .bashrc file (or .cshrc or .tcshrc etc, depending on which shell we are talking about) you can add aliases, and I am sure there already are some pre defined. Add this line:

alias JPG2jpg="for x in *.JPG; do n=${x/.JPG/.jpg}; mv $x $n; done"

I think, however, that this would b a lot faster:
alias JPG2jpg="find . -exec rename -v "s/.JPG$/.jpg/" {} +"

This one works recursively from your current folder. Skip the -v if you don't want to see what happens.

If you want to make sure only files are changed, not links, folders etc:
alias JPG2jpg="find . -type f -exec rename -v "s/.JPG$/.jpg/" {} +"

Type man find for more information.

Oh, the rename thing only exists in Debian based systems, but on the other hand, that's what Ubuntu is. Just thought you want to know, in case you wanted to try this on a non Debian machine. Non Debian machines may also have a rename, but that's not the same rename. If your system doesn't have rename, I think you need to install Perl.

I made an alias like this myself, mine removes the annoying &#8221;Link to &#8221; från link names (created by Nautilus when you drag and drop files as links) recursively. My solution was like that .JPG one above, and it was very fast compared to some other methods I tried, among them a method involving &#8221;while&#8221;, &#8221;mv&#8221; and &#8221;sed&#8221;. I changed the name of 342 links (out of almost 22000 objects totally) in about 0.14 s with the method above. The &#8221;while&#8221; thing took about 2.3 s.
If I replaced -type l (in my case, since I renamed links) with -name "Link to *", I thought it would be faster, but it wasn't. It was slightly slower (0,16 s).

I don't know about your method, but I would guess the one I suggested above is faster.

To test yourself, try the time command:
time find . -type f -exec rename -v "s/.JPG$/.jpg/" {} +
then try
time for x in *.JPG; do n=${x/.jpg/.JPG}; mv $x $n; done
which will switch them back to JPG again (otherwise that command doesn't have anything to do, since we already changed it to jpg&#8230;

---

