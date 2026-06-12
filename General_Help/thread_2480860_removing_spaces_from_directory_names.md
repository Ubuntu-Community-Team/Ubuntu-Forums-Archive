---
title: "removing spaces from directory names"
date: 2022-11-12
forum: General Help
---

### Post by Old Jimma on 2022-11-12
Hello Ubuntuers:

For a specified directory, I need to build bash code to 
[LIST]
[*]remove the spaces from the names of each directory one level down in the specified directory... but no lower... replacing spaces with an underline that would turn "FUNNY DIRECTORY NAME" into FUNNY_DIRECTORY_NAME" as an example
[*]
[/LIST]

I was a bash coder 50 years ago, but don't know anymore.

However, I decided to try anyway... taking it one step at a time.

I tried this and it didn't work.

> 
dir="/home/computer/Music/CDs/"
for a in "$dir"/*; do
    mv -R $a/ ${a// /_}
done


I'd be grateful if somebody could tell me how to fix this code!

After I get that done,  I'll "recycle" it compressing each of the renamed directories using 7z

Many thanks,
Old White Haired Jimma

---

### Post by #&amp;thj^% on 2022-11-12
Just so **"I'm"** clear here>>> you want to  remove the whitespace from all the names in the parent directory and all sub directories at once? Correct?
see if this first guess is workable:
```
find /tmp/ -depth -name "* *" -execdir rename 's/ /_/g' "{}" \;
```
or Replace s/ //g by s/ /_/g to replaces spaces by underscores rather than remove them outright, or s/ +/_/g to replace sequences of spaces by a single underscore.
EDIT: Here's what that would look like run with correct syntax:
```
find /tmp/ -depth -name "* *" -execdir rename 's/ /_/g' "{}" \;
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-systemd-logind.service-Y0dYWv&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-colord.service-UJz3wS&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-bluetooth.service-6h4mAO&#8217;: Permission denied
find: &#8216;rename&#8217;: No such file or directory
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-ModemManager.service-13G72a&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-systemd-resolved.service-nFLJIy&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-systemd-timesyncd.service-lBS4MO&#8217;: Permission denied
find: &#8216;/tmp/tmplgp_baxh&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-apache2.service-xYiDtl&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-ubuntu-advantage-desktop-daemon.service-QuPls9&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-1f33fe2bd08d493497ca74a4a10c97eb-upower.service-69esUZ&#8217;: Permission denied

```

---

### Post by Old Jimma on 2022-11-12
Hi 1fallen:

Thanks for your reply. I'm not sure exactly what Parent directory and all subdirectories means exactly and will give an example of what I mean.


I have a directory named "CDs" that has a sub-directory that contains many folders.... and each of those folders is the name of an artist, e.g., "George Benson"

The directory "George Benson" has many subdirectories that have the names of his albums. Those names contain spaces between words.... that I not want changed.

However, I want the directory "George Benson" to be changed to "George_Benson"

that's the first thing I want to do.

Then, the second thing I want to do is to compress "GEORGE_BENSON" using 7z:

7z a GEORGE_BENSON.7z GEORGE_BENSON


.... I want to do this for all directories in the CDs directory... but not in sub directories that are named after artists.

Thanks,
Old

---

### Post by #&amp;thj^% on 2022-11-12
First Check my EDIT to post#2
If you want bash, edit this to your desire:
```
find /path/to/directory -depth -name '* *' -exec sh -c '
    for file do
      dir=${file%/*};
      file=${x##*/};
      without_spaces=$(printf %s "$file." | sed "s/ //g")
      mv "$dir/$file" "$dir/${without_spaces%.}";
    done
' _ {} +
```

---

### Post by Old Jimma on 2022-11-12
Hi 1fallen:
[B]
You wrote: [/B]"just so "I'm" clear here>>> you want to remove the whitespace from all the names in the parent directory and all sub directories at once? Correct?
see if this first guess is workable:"

**My reply:** No. I want to do something a little different. I wanto remove the white speace names in the parent directory.... but not in any sub directories. THANKS!

OLD

---

### Post by #&amp;thj^% on 2022-11-12
> **Old Jimma said:**
> However, I want the directory "George Benson" to be changed to "George_Benson"
Doesn't my script do that?
I'm old too so let me think about the rest of the sub folders/Directory's un-touched

---

### Post by Old Jimma on 2022-11-12
Yeah. "Old" is going around just like COVID did... but, more lethal.

I'm very greatful for your effort... didn't work... or perhaps I screwed it up.

---

### Post by #&amp;thj^% on 2022-11-12
Ok I simplify a bit, you may still need to change, add to it:
```
 me on Sat Nov 12 at 03:35 PM in ~ branch: (HEAD) 
>> cd Music 


me on Sat Nov 12 at 03:39 PM in ~/Music branch: (HEAD) 
>> for f in *; do mv "$f" `echo $f | tr ' ' '_'`; done


```
Notice where I run the command^^^^
Result"/home/me/Music/**One_to_One_-_Forward_Your_Emotions_[1985]**"
EDIT: Inside the folder remains intact>>>"01. Don't Call It Love.mp3"
Us Old farts have to stick together right???? :)

---

### Post by Old Jimma on 2022-11-12
Yes. Thanks, 1fallen:
I'm very grateful... and have been very grateful for your help.
Hope you are doing well, and enjoying life.
Best,
Old Jimma from the Old Country

---

### Post by HermanAB on 2022-11-13
Just a general tip:  The find utility with the exec option, is usually the best way to iterate over files and folders.

We used to be young and handsome.  Now we are just handsome :)

---

### Post by The Cog on 2022-11-13
How about:
```
cd Music
rename -n 'y/ /_/' *
```
Remove the -n (or change it to -v) and it will do it rather than just tell you what it would have done.

---

### Post by Old Jimma on 2022-11-13
About that being only handsome now thing:

My wife says:
[LIST]
[*]I put the "UGH" in ugly, and
[*]am so ugly that I'd make a freight train take a dirt road.
[*]
[/LIST]

Is there a bash command that can fix that?

---

### Post by Old Jimma on 2022-11-13
That's very cool, The Cog. Thanks!

---

### Post by HermanAB on 2022-11-13
That rename example is brilliant, but I’m wondering why nobody else in the wide wide world knows that Bash substitute syntax can be used like that with a wildcard.

---

### Post by Old Jimma on 2022-11-13
I can only speak for myself: I knew bash pretty well 45 years ago. 

However, time went by, I changed my professional focus, forgot bash over the past 45 years (except for arround 25 commonly used commands like mkdir, mv, etc).... to say nothing about inevitable cognitive decline in old age.

However, in my old age I still use linux and will be glad to ride it into the sunset.

Thank you for your very superb help over many, many years now.

Old Jimma

---

### Post by TheFu on 2022-11-13
> **Old Jimma said:**
> I can only speak for myself: I knew bash pretty well 45 years ago. 

Doubtful, since bash isn't that old. Bash was released in 1989 ... so 33 yrs old. I don't remember seeing it until 2000, not in the 1990s, but I was mainly doing MVS, Unix & OS/2 then. Linux was a hobby or setup and forgotten for years.

```
$ find . -type d -exec rename 's/ /_/g' "{}" \;
```
Obviously, test it somewhere safe first.  Come to think of it, that seems a bit dangerous to do over a huge directory tree.  I foresee issues with parent directories names being changed, so it may been to be run as many times as the deepness in the directory tree from the starting location.  Just to be clear, I have a similar issue and have decided against running that command, but feel free to try it!  Maybe reverse sorting the found directories would be good?  Thankfully, we have the 'tac' command. ;)

Music directories and song titles often have really odd characters.  I'd probably use 'find' to get a list of directories with spaces, save that to a file, then use 'qmv -fdo' on that list with the power of my editor to change the filenames. A little caution is needed. Definitely want excellent backups and a way to validate no harm was caused.

To see how large my problem is:
```
$ find . -type d |wc -l   # find the number of directories
9455

$ find . -type d -name "* *" |wc -l
3468
```
So, 3400 of my directories have spaces in the names out of 9400 total directories.
BTW, 
```
$ sudo du -sh .
451G    .
```
So, 450GB if data would be at risk.  Nope.  Think I'll be more cautious and only fix 1 Artist's directory at a time, when it makes sense.

---

### Post by Old Jimma on 2022-11-13
.,.. Well, what ever they called the OS for Cray computers back then. I learned it out of a Unix book.

The problem with young fold like Fu is that they always do the math. Later in life, older folk only hope to be somewhat logical and to have friends who are indulgent.

---

### Post by Old Jimma on 2022-11-13
Thanks for your advice, The Fu.

---

### Post by TheFu on 2022-11-14
> **Old Jimma said:**
> .,.. Well, what ever they called the OS for Cray computers back then. I learned it out of a Unix book.

The problem with young fold like Fu is that they always do the math. Later in life, older folk only hope to be somewhat logical and to have friends who are indulgent.

I used that "new math" and wikipedia  ... you know, counting by tens.

BTW, here's my non-recursive rename script.  Not bash.
```
#!/bin/sh

IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/[_]+/_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*
rename 's/_2022/-2022/g' $IN*

```

I tend to use it like:
```
script  [A-Z]
```
to rename any directory or file that begins with capital letters.  It leverages the perl rename script and globbing.

---

### Post by #&amp;thj^% on 2022-11-14
> **TheFu said:**
> Thankfully, we have the 'tac' command. ;)

Music directories and song titles often have really odd characters.  I'd probably use 'find' to get a list of directories with spaces, save that to a file, then use 'qmv -fdo' on that list with the power of my editor to change the filenames. A little caution is needed. Definitely want excellent backups and a way to validate no harm was caused.

To see how large my problem is:
```
$ find . -type d |wc -l   # find the number of directories
9455

$ find . -type d -name "* *" |wc -l
3468
```
So, 3400 of my directories have spaces in the names out of 9400 total directories.
BTW, 
```
$ sudo du -sh .
451G    .
```
So, 450GB if data would be at risk. **_ Nope.  Think I'll be more cautious and only fix 1 Artist's directory at a time, when it makes sense._**

+1 makes perfect sense with a perfect approach.
That's why I left the script part unfinished>>>That's up to a user's choice....I like your sound thinking. ;)

---

### Post by ajgreeny on 2022-11-14
Using Xubuntu, I make use of the custom actions utility in thunar file manager.
It uses the simple command ```
rename 's/\ /_/g' %F
``` which I use by highlighting all the files in a directory (Ctrl+A) then I right click and point to the ***Remove Spaces*** command in the context menu.

This changes all white spaces in file or directory names into underscores, making life many times easier for me.

---

### Post by The Cog on 2022-11-15
> **ajgreeny said:**
> Using Xubuntu, I make use of the custom actions utility in thunar file manager.
Now, there's a good idea!

---

### Post by ajgreeny on 2022-11-15
> **The Cog said:**
> Now, there's a good idea!

Do the other DE file managers not have anything similar to the "custom actions" of thunar?

I have lots of them set up and would be a bit lost if I didn't have them. Eg, i can right click on any video and choose to get an mp3 or flac file from it with just the couple of mouse clicks, or I can resize an image, or even ask to either move a file or copy it to another folder.

These are things I use daily and can't imagine not having them.

---

### Post by dragonfly41 on 2022-11-15
> [COLOR=#000000]Do the other DE file managers not have anything similar to the "custom actions" of thunar?[/COLOR]

Krusader > either right click > or Useractions for custom scripts

---

### Post by Old Jimma on 2022-11-16
Thanks the Fu. You are a great guy!

---

### Post by cmcanulty on 2022-11-16
Another GUI option is install a renamer like Bulk renamer and tell it to replace all spaces with _

---

### Post by TheFu on 2022-11-16
> **Old Jimma said:**
> Thanks the Fu. You are a great guy!

Is your location correct?  ALE [https://ale.org/](https://ale.org/) does weekly meetings, in person and virtual, where things like this get a 20 min discussion.

---

