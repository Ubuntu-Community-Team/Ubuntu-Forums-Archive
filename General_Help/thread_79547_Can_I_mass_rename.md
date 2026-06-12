---
title: "Can I mass rename?"
date: 2005-10-20
forum: General Help
---

### Post by ymmotrojam on 2005-10-20
Is there a way to mass rename files? I know in Windows, it's as simple as selecting them all and just renaming them, and then each one is given the name you chose along with a sequential number... is there something similar for Ubuntu?

EDIT: Those that may be wondering why it is beneficial to have a feature like this...
Say you're organizing two groups pictures off your camera and you want to put them all in a single folder, but the camera gave each group the same arbitrary names (Picture1, Picture2, etc). You can mass rename those pictures with a new arbitrary name so that they can easily be put in that one folder without having conflicts...

---

### Post by KingBahamut on 2005-10-20
I dont believe so, not without writing a shell script to do it. 

Try writing one, it could be fun.

---

### Post by KnottyMan on 2005-10-20
Bash is your friend

To get: file1, file2, file3, file4 => newfilename10, newfilename20, newfilename30, newfilename40

Open terminal, cd to dir, for i in file* do ; mv $i newfilename`seq 10 40 10` ; done

seq syntax "seq startnumber endnumber [increment]"

---

### Post by auburn on 2005-10-20
wow. I didn't know you could do that in windows... 

With linux I've been renaming *.JPG to *.jpg with this:

```
for i in $(find . -name '*.JPG'); do mv $i ${i//.JPG/.jpg}
```

so maybe:

...well, I'll have to work on this a bit more later.

You know, this would be a good nautilus script. & there might already be one...

[http://ubuntu.wordpress.com/2005/09/25/scripts-lots-of-nautilus-scripts/](http://ubuntu.wordpress.com/2005/09/25/scripts-lots-of-nautilus-scripts/)

-peter

---

### Post by auburn on 2005-10-20
nice knottyman. I was wondering how to make seq work with this script.

---

### Post by KingBahamut on 2005-10-20
Thats pretty swank Knotty, I shall add that to my list of "how the heck do I do this".

---

### Post by auburn on 2005-10-20
Okay. I found a gui file renamer created by Maciej Katafiasz which incorporates into nautilus as a script. It's called Purrr. It looks really good, but I think it's still unstable.

Here's the homepage for version 0.5:
[http://mathrick.org/software/purrr.html](http://mathrick.org/software/purrr.html)

& more recently (v 0.8 pre-release):
[http://mathrick.org/software/0.8/purrr.html](http://mathrick.org/software/0.8/purrr.html)

here's how to install 0.5:
```
 wget http://mathrick.org/software/purrr-0.5.1.tgz
tar xvfz purrr-0.5.1.tgz
cd purrr-0.5.1
sudo ./setup.py install
```

Simply right-click in nautilus, choose scripts, and choose "mass rename"

syntax on how to use it:
[http://mathrick.org/software/purrr.html#syntax](http://mathrick.org/software/purrr.html#syntax)

It *does* take a few minutes to understand. But it also really compliments nautilus. Hopefully, Maciej will release a final version or someone else will take it on.


After writing all this I think the easiest solution is knottyman's or batren. Batren is a command line app available on sourceforge.
Example:
```
batren -v -f 15 -p "pic-" -s "-sea" -t "00000" -d "_renamed_" *.jpg
```
This will copy *.jpg files to directory _renamed_, naming them like: pic-00015-sea.jpg

batren can be downloaded from:
[http://sourceforge.net/projects/batren/](http://sourceforge.net/projects/batren/)

---

### Post by KnottyMan on 2005-10-20
I you know how the Bash way, you are not dependent on other people's tools.  I would much rather use k3b or qdvdauthor than use the command line, but it is good to know an alternative.

Knowing how to use Bash is a GoodThing(tm)

---

### Post by egon spengler on 2005-10-20
Another alternative is [B]for i in *.jpg ; do mv $i newname$((++n)).jpg; done
[/B]

This will rename every jpg in the diretory newname1.jpg, newname2.jpg -> newname100.jpg

---

### Post by stoeptegel on 2005-10-20
If you prefer a gui: [http://www.krename.net/](http://www.krename.net/) (it's in universe)

---

### Post by johnnymac on 2005-10-20
Yes...through regular expression and perl

rename 's/_/ /g' *

This would rename all your files in a given directory that have and '_' and replace the underscore with a space....just an example.

Look up more on regexp w/perl

gl

---

### Post by 3david on 2005-10-21
try these 2:

sudo apt-get install mrename

and

sudo apt-get install renameutils


and also, there seems to be a 'rename' utility (/usr/bin/rename) on my system, try running "rename" in a terminal, see if you get something like this: 
     
    Usage: rename [-v] [-n] [-f] perlexpr [filenames]

it's a very nice tool, I can't remember if I installed it or if it came with the system (i'd be grateful if someone could tell if it comes built-in or if it comes with any package)

hope these help.

---

### Post by stoeptegel on 2005-10-21
cool, is there something ubuntu doens't have? :cool:

---

### Post by jonesy on 2005-10-21
I'd like to take this opportunity to say that I think the "rename" utility /usr/bin/rename that comes with Ubuntu is crap.  Maybe it is more powerful than it's competitors because it uses Perl terminology, but the rename utility provided with Gentoo, RedHat, etc is very simple:

rename "search string" "substitution string" "list of files"

It doesn't get much easier to convert .JPG to .jpg than typing:

rename "JPG" "jpg" *

Why can't Ubuntu offer that version for download?  Where can you get it?

---

### Post by 3david on 2005-10-21
what's wrong with running: 

rename 's/JPG/jpg/' *

if you want, you can create a script like this:

alt_rename:
 
```

  rename "s/$1/$2/" $3

```

then you can run:
  alt_rename "JPG" "jpg" *

---

### Post by jonesy on 2005-10-24
actually, that doesn't work in bash because the "*" for filename expansion expands each matching file as it's own entry on the command line, so $3 will only grab the first matching file.  I haven't found a way around this yet :-(  I just don't understand why a perl matching algorithm is advantageous to the simple expression matching program that comes with other distros.  Surely the simple one would be easier for people to figure out.

---

### Post by denisesballs on 2005-10-24
This is so funny cuz I was just trying to do this week. I wound up using the rename CLI, but this also works:

```
jesse@jesseubuntu:~/invitationpics$ for FILE in *.jpg
> do
> mv $FILE ${FILE%.jpg}.jpeg
> done
```

---

