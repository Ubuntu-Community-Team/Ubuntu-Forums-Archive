---
title: "[SOLVED] Rename multiple files"
date: 2007-07-06
forum: General Help
---

### Post by boweeb on 2007-07-06
_Situation:_
I have dig camera pics named IMG_1615.jpg, IMG_1616.jpg, IMG_1617.jpg, etc. I'd like to rename them to 001.jpg, 002.jpg, 003.jpg, etc. from the command line.

This [-site-]("http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal") was a little useful since it explained how "rename" works, but it doesn't give me a relevant example for renaming files with consecutive numbers.

_Question:_
Could someone help me figure out the correct perl expression to use with rename?
Or offer a better method?

Thanks

---

### Post by Lolicon on 2007-07-06
Theres a Thundar bulk renamer.

---

### Post by boweeb on 2007-07-06
Thunar is Xfce's file manager (which can, like you said, bulk rename) but since I'm renaming files on a remote server through ssh, I need to be able to rename through the command line.

Thanks, though

---

### Post by stylishpants on 2007-07-06
```
ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'
```

---

### Post by boweeb on 2007-07-06
Perfect, thank you.

---

### Post by boweeb on 2007-10-30
```
ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'
```
That worked for me 6 months ago when I first posted this - thanks stylishpants.

Now I've returned to use that code and I can't get it to work again!

Can someone please help me to understand the components of the perl expression so I can deduce what's wrong/different?

(I'm once again working with a list of IMG* jpegs - I'm aware of the function of "ls IMG* | sort -n")

---

### Post by stylishpants on 2007-10-31
Here's some debug code.  It should just print out the old filename and the new filename without actually renaming anything.

```

ls IMG* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "'$_' => '$new'";'

```

What error or problem are you seeing?  Do you have some sample filenames, or are they the same as before? 

For info in sprintf: do perldoc -f sprintf
For info on the flags to perl: do man perlrun

---

### Post by boweeb on 2007-11-01
I already renamed them by hand, so I touched 4 files named img23534.jpg, img23534.jpg, img23534.jpg, and img23534.jpg in a different test folder. Here's my shell log:```
[jesse@hcqserv:oahio/test]$ ll                                    (11-01 14:48)
total 0
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:46 img23534.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:47 img23535.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:47 img23536.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:48 img23537.jpg
[jesse@hcqserv:oahio/test]$ ls IMG* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "'$_' => '$new'";'
zsh: no matches found: IMG*
[jesse@hcqserv:oahio/test]$ ls img* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "'$_' => '$new'";'
-n =>
-n =>
-n =>
-n =>
[jesse@hcqserv:oahio/test]$ ll                                    (11-01 14:51)
total 0
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:46 img23534.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:47 img23535.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:47 img23536.jpg
-rw-r--r-- 1 jesse jesse 0 2007-11-01 14:48 img23537.jpg
[jesse@hcqserv:oahio/test]$
```You may notice that I use zsh but I get the same output with bash.

---

### Post by minus198 on 2007-11-01
It is case sensitive.. Use "img*" instead of "IMG*".

---

### Post by boweeb on 2007-11-01
look at the next line

---

### Post by minus198 on 2007-11-01
Ow, totally missed that ^^

Maybe you should try doing a shellscript instead?

---

### Post by stylishpants on 2007-11-01
I screwed up that debug code.  Try this one.  The only difference is that I used () to bracket the old and new names in the output string, instead of ' '.  Using ' was not working because my entire string of perl code was bracketed in single quotes.  

```
ls img* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "($_) => ($new)";'
```

---

### Post by boweeb on 2007-11-02
```
[jesse@hcqserv:oahio/test]$ ls                                    (11-02 11:16)
img23534.jpg  img23535.jpg  img23536.jpg  img23537.jpg
[jesse@hcqserv:oahio/test]$ ls img* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "($_) => ($new)";'
(img23534.jpg) => (000.jpg)
(img23535.jpg) => (001.jpg)
(img23536.jpg) => (002.jpg)
(img23537.jpg) => (003.jpg)
[jesse@hcqserv:oahio/test]$ ls                                    (11-02 11:16)
img23534.jpg  img23535.jpg  img23536.jpg  img23537.jpg
[jesse@hcqserv:oahio/test]$ 
```
Makin' progress. Not there yet, though. Thanks for working with me on this.

---

### Post by stylishpants on 2007-11-02
Everything looks fine there.  It's clearly receiving each filename correctly, and generating the new one properly.

What's the problem here?  What happens when you run the original command?
```

ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'

```

---

### Post by boweeb on 2007-11-05
You're right. The new names are being generated correctly but the files aren't actually being renamed. Hence the next "ls" line that shows no change.

---

### Post by mali2297 on 2007-11-05
A **bash** solution:
```

x=0; for i in IMG_*.jpg; do let x++; mv -v $i $(printf "%03d.jpg" $x); done

```

---

### Post by stylishpants on 2007-11-06
> **boweeb said:**
> You're right. The new names are being generated correctly but the files aren't actually being renamed. Hence the next "ls" line that shows no change.

I assume you're referring to the output you posted earlier.  That output was from perl code that was only supposed to print filenames, not rename them.  There was no 'rename' command issued within that perl code.  It was just for debugging purposes.

I expected to see some problem show up with that command and have some revealing output to illustrate where the problem is, but instead it worked fine.  Now I have no idea what problem you're experiencing.

Could you please try the original renaming command, which I'll reproduce again below, and post the result, and explain what the problem is?

```
ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'

```

---

### Post by boweeb on 2007-11-08
@ mali2297 - That worked great. Thanks.

However I'd like to continue conversing with stylishpants for education's sake.

@ stylishpants > There was no 'rename' command issued within that perl code. It was just for debugging purposes. Oh. That makes sense. I'm an idiot.> I expected to see some problem show up with that command and have some revealing output to illustrate where the problem is, but instead it worked fine.True. I had missed the point of that code.> Could you please try the original renaming command ... and post the result, and explain what the problem is?Sure. The issue is that your posted command worked two months ago :) - now it doesn't :(. Now I'm trying to understand why. Your debug showed that perl is working at least up to a point :). But the mystery hasn't yet been solved :(.

(Also I did as you asked and retried the original, checking spelling, capitalization, etc. I also brought up "man rename" and verified that it hasn't been replaced with a different "rename" or something crazy like that.)

I appreciate your patience with me and I hope you won't misinterpret my dry humor for sarcasm.

---

### Post by stylishpants on 2007-11-08
> **boweeb said:**
> @ mali2297 - That worked great. Thanks.

However I'd like to continue conversing with stylishpants for education's sake.

@ stylishpants  Oh. That makes sense. I'm an idiot.True. I had missed the point of that code.Sure. The issue is that your posted command worked two months ago :) - now it doesn't :(. Now I'm trying to understand why. Your debug showed that perl is working at least up to a point :). But the mystery hasn't yet been solved :(.

(Also I did as you asked and retried the original, checking spelling, capitalization, etc. I also brought up "man rename" and verified that it hasn't been replaced with a different "rename" or something crazy like that.)

I appreciate your patience with me and I hope you won't misinterpret my dry humor for sarcasm.

I'd like to help but I still don't have anything to work with here.  Is there an error message?  Please post the output from the original command.

---

### Post by boweeb on 2007-11-08
```
[jesse@hcqserv:oahio/test]$ ls                                    (11-08 19:24)
IMG1234.jpg  IMG2345.jpg  IMG3456.jpg  IMG4567.jpg
[jesse@hcqserv:oahio/test]$ ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'
[jesse@hcqserv:oahio/test]$ ls                                    (11-08 19:24)
IMG1234.jpg  IMG2345.jpg  IMG3456.jpg  IMG4567.jpg
[jesse@hcqserv:oahio/test]$                                       (11-08 19:24)

```No output. My mind is boggled.

---

### Post by stylishpants on 2007-11-08
OK, this is bizarre alright.

The problem is that the filename comes in with a trailing newline.

```

# print the input filename with delimiters
fhanson@fhanson:/tmp/punk$ \ls IMG* | sort -n | perl -ne 'print "($_)\n";'
(IMG1234.jpg
)
(IMG2345.jpg
)
(IMG3456.jpg
)
(IMG4567.jpg
)

# Fixed by using perl's "-l" flag, which chops line delimiters automatically from input lines
fhanson@fhanson:/tmp/punk$ \ls IMG* | sort -n | perl -nle 'print "($_)";'
(IMG1234.jpg)
(IMG2345.jpg)
(IMG3456.jpg)
(IMG4567.jpg)

# Now that 'rename' is renaming a filename that actually exists, it works:
fhanson@fhanson:/tmp/punk$ ls IMG* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'

fhanson@fhanson:/tmp/punk$ ls
000.jpg  001.jpg  002.jpg  003.jpg

# Note the perl version, FYI
fhanson@fhanson:/tmp/punk$ perl -v | head -2

This is perl, v5.8.8 built for i486-linux-gnu-thread-multi

fhanson@fhanson:/tmp/punk$ dpkg -l perl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                Version                             Description
+++-===================================-===================================-======================================================================================
ii  perl                                5.8.8-7ubuntu3         

```

I can't explain what has changed since your original post.  The above code was run on Gutsy, but Perl 5.8.8 was also used in Feisty.  The bash shell has had a patch applied since Feisty related to word splitting, but you are also seeing this problem in zsh (and I can reproduce it there too.)  That's just weird.

---

### Post by motoperpetuo on 2007-11-09
would anyone be able to post the linux 'rename' equivalent of this command in DOS:

ren *.jpg *.jpx

i'm too damn stupid to figure out the perl expression (or perhaps the other parameters) needed for 'rename'. all i get are oodles and boodles of syntax errors and urecognized character errors. i tried using 'mv' too, but it doesn't support wildcards (as near as this noob can tell).

thanks!

---

### Post by stylishpants on 2007-11-10
> **motoperpetuo said:**
> would anyone be able to post the linux 'rename' equivalent of this command in DOS:

ren *.jpg *.jpx

i'm too damn stupid to figure out the perl expression (or perhaps the other parameters) needed for 'rename'. all i get are oodles and boodles of syntax errors and urecognized character errors. i tried using 'mv' too, but it doesn't support wildcards (as near as this noob can tell).

thanks!


It's been a while since I used dos, but think it means this:
```

rename 's/\.jpg$/.jpx/' *

```

---

### Post by Matt Yun on 2007-11-10
> **motoperpetuo said:**
> would anyone be able to post the linux 'rename' equivalent of this command in DOS:

ren *.jpg *.jpx



do:  

rename s/jpg/jpx/g *.jpg

**rename** is a very, very powerful command; do 'man rename' for a full description.  It uses regexp.

Also, if you want a pretty GUI batch renaming tool, try [metamorphose]("http://file-folder-ren.sourceforge.net/").  You can download an [Ubuntu-ready deb]("http://www.getdeb.net/app.php?name=Metamorphose") at getdeb.net.  Metamorphose can even rename *.mp3 files according to ID3 tags.

---

### Post by motoperpetuo on 2007-11-10
awesome, thanks very much for the replies. i tried matt's and it worked like a charm.

does anyone know if 'rename' works differently in ubuntu than in other distros? i was working off info that wasn't distro-specific and having no luck whatsoever.

---

### Post by mali2297 on 2007-11-10
> **motoperpetuo said:**
> 
does anyone know if 'rename' works differently in ubuntu than in other distros? i was working off info that wasn't distro-specific and having no luck whatsoever.

The tool **rename** in Ubuntu uses Perl and is different from the more basic rename tool in other distros. It confused me some before I realised that they were two different programs but with the same name.

This link includes brief descriptions of both programs:
[http://wiki.linuxquestions.org/wiki/Rename](http://wiki.linuxquestions.org/wiki/Rename)

---

### Post by boweeb on 2007-11-16
A HA!!!

The culprit has been the l flag. Notice it was in the debug code "... perl -nle ..." but not the original "... perl -ne ...". You'll see the l in every debug post but not command posts.

Your comments in post #21 are what brought it to my attention.
```
# Fixed by using perl's "-l" flag, which chops line delimiters automatically from input lines.
...
# Now that 'rename' is renaming a filename that actually exists, it works:
fhanson@fhanson:/tmp/punk$ ls IMG* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); rename($_,$new);'
```
Notice my zsh log:
```
[jesse@hcqserv:oahio/test]$ ls IMG* | sort -n | perl -nle '$new = sprintf("%03d.jpg",$i++); print "($_) => ($new)";'
(IMG1234.jpg) => (000.jpg)
(IMG2345.jpg) => (001.jpg)
(IMG3456.jpg) => (002.jpg)
(IMG4567.jpg) => (003.jpg)
[jesse@hcqserv:oahio/test]$ ls IMG* | sort -n | perl -ne '$new = sprintf("%03d.jpg",$i++); print "($_) => ($new)";'
(IMG1234.jpg
) => (000.jpg)(IMG2345.jpg
) => (001.jpg)(IMG3456.jpg
) => (002.jpg)(IMG4567.jpg
) => (003.jpg)%
```
So, adding the l in the actual command worked! Man, that was a work-out. This was a good thread. I'm glad that these things got posted here and that other peoples questions were answered as well.

---

