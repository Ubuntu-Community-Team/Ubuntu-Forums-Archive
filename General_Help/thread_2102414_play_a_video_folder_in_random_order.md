---
title: "play a video folder in random order"
date: 2013-01-07
forum: General Help
---

### Post by CaptainMark on 2013-01-07
I need to put a collection of videos on repeat play on my raspberry pi, (not ubuntu i know but debian none the less), I currently just have to punch this in from the console and this will play all videos in the Videos directory, and any new videos that appear during the while loop will just be added on the next cycle```
 while true; do for v in ./Videos/*; do omxplayer -o hdmi $v; done; done

```
Now is there a way to randomise the order of the videos being played, I'm trying to keep it nice and simple I don't want anything fancy but is it simple enough to just shuffle the order of the videos before the 'for' sequence starts, I tried to piping with sort and fiddling with xargs but I couldn't get it right,

Any ideas?
Regards 
Mark

---

### Post by CaptainMark on 2013-01-07
If installed randomize-lines and can kinda get it to work but unless I redefine IFS I cant get it to work (otherwise it will treat a file with a space as two files and fail) this is the best i've got ```
IFS="\n";  while true; do for v in $(ls ./Videos/* |rl); do omxplayer -o hdmi $v; done; done;

```

---

### Post by sudodus on 2013-01-07
> **CaptainMark said:**
> If installed randomize-lines and can kinda get it to work but unless I redefine IFS I cant get it to work (otherwise it will treat a file with a space as two files and fail) this is the best i've got ```
IFS="\n";  while true; do for v in $(ls ./Videos/* |rl); do omxplayer -o hdmi $v; done; done;

```
You can sort the file names in a random way with```

sort -R
``` inserted in the right place in your command line, script or alias. See ```
man sort
```. There is also [FONT="Courier New"][SIZE="3"]--random-source=FILE[/SIZE][/FONT]

---

### Post by CaptainMark on 2013-01-07
I've already tried piping to sort, if I use a pipe in this part "for v in ./Videos/*" I get an error "bash: syntax error near unexpected token `|'"
If I try to use quote marks it passes the whole output to omxplayer in one big lump which fails and if i try to use results brackets for v in $(./Videos/* |sort -R) then I get a permission denied error, I assume its trying to pass the video contents onto omxplayer rather than the file name,

---

### Post by sudodus on 2013-01-07
> **CaptainMark said:**
> I've already tried piping to sort, if I use a pipe in this part "for v in ./Videos/*" I get an error "bash: syntax error near unexpected token `|'"
If I try to use quote marks it passes the whole output to omxplayer in one big lump which fails and if i try to use results brackets for v in $(./Videos/* |sort -R) then I get a permission denied error, I assume its trying to pass the video contents onto omxplayer rather than the file name,
I think it will be much easier to manage if you put your command line into an editor and take it apart into several lines. Then you can even create a file containing all video-file-names, sort that as you like, and then read from it to obtain the command parameter for the video player, or if the player can use a ***play-list***, use that file containing all video-file-names as play-list.

---

### Post by steeldriver on 2013-01-07
there's also 'shuf'

```
NAME
       shuf - generate random permutations

SYNOPSIS
       shuf [OPTION]... [FILE]
       shuf -e [OPTION]... [ARG]...
       shuf -i LO-HI [OPTION]...

DESCRIPTION
       Write a random permutation of the input lines to standard output.

``````
while read -r -d $'\0' file; do echo play "$file"; done < <(shuf -ze *.mp3)
```

---

### Post by Vaphell on 2013-01-07
I see steeldriver already responded with more or less correct answer.


This was meant to be sent in PM, but i post here so more people can read it:

If you can use globs, use them, they just work. You can enable globstar ** too if you need any depth, eg **/*.mp3
If for whatever reason you can't use builtin globs, go straight to **while read** approach and use commands that support null delimiter, eg **find -print0**, **grep -Z**, **sort -z**, **shuf -z**, etc.

```
while IFS= read -rd '\0' f
do
  echo "$f"
done < <( find -print0 | sort -z ... | ... | whatever -with -null -delimiter )
```
this is a boilerplate code that should be the default when processing file lists, forget anything else

ls is wrong because it's for human eyes. It doesn't necessarily produce faithful representation of the object name. You simply can't write a rock solid script with ls and IFS. *While read* approach based on the null delimiter is rock solid because you are 100% safe against weird characters (null is considered illegal by filesystems so no collision can ever occur).
Redefining IFS also can introduce bugs down the road should you ever forget to restore it and if anything it should be overriden locally only for the command that requires it, eg
```
LANG=C time
IFS=$'\n' some_command
```
Overall it's a bad practice and if it can be avoided, it should be avoided (and it can be avoided so ... ;-) )

If you really want tidy for-loop you can create an array first
```
files=()
while IFS= read -rd '\0' f; do
  files+=( "$f" )
done < <( find -print0 )

for f in "${files[@]}"
do
  echo "$f"
done
```
Arrays are nice because once you have them populated, they are as reliable as globs and you don't have to think about delimiters at all.

As you can see the array creation uses *while read -d <NULL>* either way.
*Read* command has a tidy syntax that could be used with delimiter to automatically create a pretty array (IFS=<delim> read -a arrayname) but unfortunately it can't be made to work reliably with NULL in this context (which is a shame really because that would rock), so slightly more verbose method (while read ...) is required.

---

### Post by CaptainMark on 2013-01-10
Okay thanks thats a lot to digest but I'll go over this a few times and make sure it all sinks in

Many thanks

---

### Post by Vaphell on 2013-01-10
i'll explain how that *while read -d $'\0'* business works so it doesn't look too much like magic ;-)

assume that lines are 'records' and words in them are 'fields'
*read* consumes 'records' marked by its delimiter (\n by default) and fields are decided by characters of IFS, eg
```
$ while IFS='[COLOR="Red"],:[/COLOR]' read -d '[COLOR="Blue"]:[/COLOR]' -a arr; do printf "%s/" "${arr[@]}"; echo; done <<< "a[COLOR="Red"],[/COLOR]b[COLOR="Red"],[/COLOR]c[COLOR="Blue"]:[/COLOR]d[COLOR="Red"],[/COLOR]e[COLOR="Red"],[/COLOR]f[COLOR="Blue"]:[/COLOR]"
a/b/c/     [COLOR="Silver"]<- $ARR_SIZE fields[/COLOR]
d/e/f/
```

as you can see the input is cut to big pieces using **-d** and to individual fields using IFS that can be locally defined. I used -a arrayname to store the fields of the record, but you can also use variables ( read ... f1 f2 f3). Read will pack data in those variables. If the number of variables is too small to fit individual fields, the last one will hold all leftovers. Obviously in case of a single var, the whole 'record' is stored (and that's what we use in our *while read* efforts related to files).
```
$ while IFS=',:' read -d ':' f1 f2; do printf "%s/" "$f1" "$f2"; echo; done <<< "a,b,c:d,e,f:"
a/b,c/   [COLOR="Silver"]<- 2 fields[/COLOR]
d/e,f/
$ while IFS=',:' read -d ':' f; do printf "%s/" "$f"; echo; done <<< "a,b,c:d,e,f:"
a,b,c/  [COLOR="Silver"]<- 1 field[/COLOR]
d,e,f/
```

obviously when you use *read -d $'\0'* you set null delimiter and can work with data where paths are separated by that character (which can be produced and processed by all these null enabled commands like find, grep, sort, ...)

---

### Post by CaptainMark on 2013-02-09
I thought I understood your explanation of your code until this didn't bring back any results, now I'm just confused ```
mark@desktop ~/Music/ $ while read -rd '\0' dir; do echo $dir; done < <(find -type d)
```

---

### Post by Vaphell on 2013-02-09
find ... **-print0**
by default find produces \n-delimited list, you need \0 to match read -d $'\0'

```
$ find -type d
.
./test
$ while read -d $'\0' d; do echo "[$d]"; done < <( find -type d )
$ while read -d $'\0' d; do echo "[$d]"; done < <( find -type d -print0 )
[.]
[./test]

```

---

### Post by CaptainMark on 2013-02-10
I did try adding the print0 option but I must have incorrectly declared the delimiter when I used print0, thanks for clearing that up, I'll have to become more familiar with this tip

---

