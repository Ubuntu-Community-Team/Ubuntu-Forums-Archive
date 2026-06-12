---
title: "grep sed (find and replace) bash script?"
date: 2008-01-21
forum: General Help
---

### Post by dbrooke on 2008-01-21
Hello,

I am trying (simply) to do a recursive find and replace on a basic pattern.

I have some of the parts, but I need help to put it together.

My logic has gotten me thus far:

First, find all the files in which [pattern] exists:

grep -lr -e <pattern> *

returns <path>/<filename> of all the instances of files that contain at least one match

Then:

I believe this sed command will replace all instances of a pattern within the file:

sed  -i 's/<from>/<to>/g' <$path/filename>

Now for scripting...

Logically, I know that I need to set the grep results to a variable (perhaps separated by a delimiter). Then I need to loop through those separated values within that variable, setting the value in the "<$path/filename>" holder within the sed line.  However, my noobness is showing.  can someone help me complete the script?  

Thanks,
Donovan

---

### Post by geirha on 2008-01-21
Something like this maybe?

```
grep -lr -e '<pattern>' . | xargs sed -i 's/<from>/<to>/g'
```

EDIT: The above won't handle paths with spaces though, so a little fix here:
```
grep -lre 'pattern' . | xargs -d'\n' sed -i 's/from/to/g'
```

---

### Post by dbrooke on 2008-01-21
> **geirha said:**
> Something like this maybe?

[snip]
```
grep -lre 'pattern' . | xargs -d'\n' sed -i 's/from/to/g'
```


Excellent geirha!.. but a couple questions before I test...

First, I was testing just the sed part (ie. 's/from/to/g')  and it
is not working for lines that contain "/"  ([http://.](http://.).) etc...  how do I tell
sed to match those type of things?  I tried:

sed -i s/"<from>"/to/g' <file>

but that didn't work.

thx,
Donovan

---

### Post by gangrelsurf on 2008-01-21
check man sed, but I think you can define a diferent (arbitrary) seperator in your regex, something like:
's*from*to*g'

It sounds like sed is confusing the '/' s in your string with seperators

---

### Post by geirha on 2008-01-21
Yes, use | or , as seperator. Don't think you can use * since it's a special regex character.
's|http://foo.domain.com/bar|replacement|g'

---

### Post by dbrooke on 2008-01-21
Thanks!  Just was trying to escape the regexp offending character/s... worked, but then I read that it takes more processing power to do multiple escapes than to assign a different delimiter!

I'm doing a global change on a large website directory, which is freaking me out... ;-) so I'll bet that little difference will help when I (finally) initiate the command!

thanks for the help! (great forum)

Donovan

---

### Post by dbrooke on 2008-01-21
The -d option is not a valid option in 3 of my xargs versions... can you tell me what the verbose syntax is?

thx,
Donovan

---

### Post by dbrooke on 2008-01-21
I'm guessing the -d option is for delimiter...  so the issue is that the version of xargs I have (GNU v. 4.1.7)  on the machine that I need to make the change does not include a delimiter option.

Is there a standard (assumed) delimiter.... for example "new line"?

Thx,
Donovan

---

### Post by dbrooke on 2008-01-21
hmmm, it appears that the default xargs (w/o options) may work.  thx.

D

---

### Post by geirha on 2008-01-21
```
$ xargs --version
GNU xargs version 4.2.27
$ xargs --help
Usage: xargs [-0prtx] [--interactive] [--null] [-d|--delimiter=delim]
       [-E eof-str] [-e[eof-str]]  [--eof[=eof-str]]
       [-L max-lines] [-l[max-lines]] [--max-lines[=max-lines]]
       [-I replace-str] [-i[replace-str]] [--replace[=replace-str]]
       [-n max-args] [--max-args=max-args]
       [-s max-chars] [--max-chars=max-chars]
       [-P max-procs]  [--max-procs=max-procs]
       [--verbose] [--exit] [--no-run-if-empty] [--arg-file=file]
       [--version] [--help] [command [initial-arguments]]

```

The -d must be a newer feature then. The man-page doesn't specify any way to choose a delimiter?

And yes, without -d/--delimiter will still work as long as there are no spaces in the paths (which is fairly uncommon to use on websites anyway). You could loop through the output of grep line by line though, in case you happen upon files with spaces.
```
grep -lre 'pattern' . | while read path; do
  sed -ir 'expression' "$path"
done

```

---

### Post by dbrooke on 2008-01-21
n1, thanks for the help.  I have a lot to learn!

Donovan

---

### Post by gangrelsurf on 2008-01-21
I was looking through scripts i use on solaris at work and saw that i had one that does what you want, and then some. The file parsing thing is a bit tricky, which is the reason for the -t option, but that's not what you're trying to do anyway. Note that this only does it's thing in php files, so you probably want to change that. Course it's been a few hours so you've probably written your own by now.

The function 'search' in there is what you were talking about. You could just chop that out and make a short and sweet single purpose script.  $1 is the directory to start in, $2 is the search $3 is the replace. Note that I'm using a temp file. I wrote this a while back and it's evolved a bunch, but I recall fumbling around a lot before doing the temp file thing.

Any way, for what it's worth:

```
#!/bin/bash

function search {
        find $1 -type f \( -name '*php' \) -print | while read file
        do
        echo replacing \"$2\" with \"$3\" in $file
                sed "s,$2,$3,g" < "$file" > "$file".tmp
                mv "$file".tmp "$file"
        done
}

function nothing {
    echo "dir: $1 search string: $2 replace string:  $3"
}

# A directory has been given.  Search for files containing the term, and replace it
if [ -d "$1" ]; then
    search $1 $2 $3

# A file has been given. Search the file for the term and replace it
elif [ -f "$1" ]; then 
        sed "s,$2,$3,g;" < "$1" > "$1".tmp
        mv  "$1".tmp "$1"

# A file to parse or test has been given.  If parse, set the directory,
# then step though every file in the directory replacing search / rplace pairs.
# Keep going until there are no more pairs.
elif [ "$1" == '-f' ] || [ "$1" == '-t' ] && [ -f "$2" ]; then
    index=0
    cat $2 | while read line
        do
            if [ $index -eq 0 ] && [ -d "$line" ]; then
                dir=$line
            elif [ $index -eq 0 ] && [ ! -d "$line" ]; then
                exit
            elif [ $index -gt 0 ]; then
                findSt=`echo ${line%% *}` 
                repSt=`echo ${line##* }`
            fi
            if [ "$1" == '-f' ] && [ ! "$repSt" == '' ] && [ ! "$findSt" == '' ]; then
                search $dir $findSt $repSt
            elif [ "$1" == '-t' ] && [ ! "$repSt" == '' ] && [ ! "$findSt" == '' ]; then
                nothing $dir $findSt $repSt
            fi
            let "index += 1"
        done
else
    echo "Jim's handy dandy searcher and replacer:"
    echo "useage:"
    echo "$0 [directory to search] [phrase to search for] [replacement phrase]"
    echo "$0 [file to search] [phrase to search for] [replacement phrase]"
    echo "$0 [-f|-t] [file to parse]"
    echo "To parse a file the first line should be the directory, then each line after is a pair of terms"
    echo "and replacements seperated by white space.  If the -f os given, the file will be parsed.  If -t "
    echo "is given then the file will be read and the terms that would be replaced are output."
    echo 
fi

```

---

