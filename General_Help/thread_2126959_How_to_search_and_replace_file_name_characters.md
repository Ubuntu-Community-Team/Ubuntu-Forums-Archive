---
title: "How to search and replace file name characters"
date: 2013-03-18
forum: General Help
---

### Post by meanmrmustard on 2013-03-18
I have 2 TB of mp3 files in which I need to replace all instances of : and / in the file names within directories three or four levels deep with a dash (-).

I have no knowledge of any programming language and I'm not sure which tool would be the quickest/easiest to use.

Is there a simple way to do this?

---

### Post by papibe on 2013-03-18
Hi meanmrmustard.

There are basically 2 options: use a GUI tool, or a write a custom script. For GUI solutions take a look at pyRenamer and KRename.

Here's a few tips for scripting:
[LIST]
[*]There are 2 main steps:
[LIST]
[*][*]building a regular expression to find the files.
[*][*]creating the command to actually rename the files.
[*]
[/LIST]
[*]Take a look at the command 'find', with the option -exec and the command 'rename' to do the actual renaming
[*]
[/LIST]
I would gladly give you more tips, if you post some examples of files you need to rename, and the final result you want.

Regards.

---

### Post by cortman on 2013-03-18
A forward slash (/) isn't legal in a filename in Linux or Windows. May want to check again what character you're needing replaced.

---

### Post by schragge on 2013-03-18
As you're running Xubuntu, you probably can use the [Bulk Rename]("http://docs.xfce.org/xfce/thunar/bulk-renamer/start") feature of Thunar (Xubuntu's default file manager). There's also the [thunar-media-tags-plugin]("http://goodies.xfce.org/projects/thunar-plugins/thunar-media-tags-plugin") that works hand in hand with Bulk Renamer.

But the command line solution with [find]("http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html") and [rename]("http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html") is the most versatile.

---

### Post by meanmrmustard on 2013-03-18
> **papibe said:**
> Hi meanmrmustard.

There are basically 2 options: use a GUI tool, or a write a custom script. For GUI solutions take a look at pyRenamer and KRename.

Here's a few tips for scripting:
[LIST]
[*]There are 2 main steps:
[LIST]
[*][*]building a regular expression to find the files.
[*][*]creating the command to actually rename the files.
[*]
[/LIST]
[*]Take a look at the command 'find', with the option -exec and the command 'rename' to do the actual renaming
[*]
[/LIST]
I would gladly give you more tips, if you post some examples of files you need to rename, and the final result you want.

Regards.

Hello papibe!
Thanks for the reply.

I'm looking over pyrenamer now.

Here is one example:

KIN: Songs by Mary Karr & Rodney Crowell (2012) FLAC

This could pass muster if it was KIN - Songs by Mary Karr & Rodney Crowell (2012) FLAC

Even a white space rather than the ":" would work and it doesn't really matter to me.

I'm trying to populate my new NAS with my audio but every time it finds a filename like this or the one below it stops, followed by my renaming it manually and then re-starting the transfer.

Another example:

Kippington Lodge - Shy Boy/The Complete Recordings 1967-69
Again either "-" or white space replacing the "/" would resolve the issue.

I've only begun to learn bash scripting and my progress is slow at best.

I have a 3 TB disk dedicated to audio files. Some of the top dirs have another directory inside,  <album title> inside <Band/Artist name> for instance, so it's two levels deep. 
There may be instances of song names which have colons or slashes in them - not sure about that but they would probably also need to be modified.
Each colon or slash needs to be changed to another character in order for the NAS software to successfully transfer them to the NAS hard disks.

---

### Post by schragge on 2013-03-18
I guess the slash in the second example is actually [DIVISION SLASH (U+2215)]("http://www.fileformat.info/info/unicode/char/2215/index.htm"). Let's try with this code
```

find [COLOR=blue]Music[/COLOR] -type f -exec rename -v[COLOR=red]n[/COLOR] 's/:|&#8725;/-/g' {} +

``` The [COLOR=red]n[/COLOR] is there for testing purposes. When you're positive this command works as expected, run it without [COLOR=red]n[/COLOR] to do the actual job. Also, replace [COLOR=blue]Music[/COLOR] with the mount point of your 3TB disk.

---

### Post by meanmrmustard on 2013-03-18
> **schragge said:**
> I guess the slash in the second example is actually [DIVISION SLASH (U+2215)]("http://www.fileformat.info/info/unicode/char/2215/index.htm"). Let's try with this code
```

find [COLOR=blue]Music[/COLOR] -type f -exec rename -v[COLOR=red]n[/COLOR] 's/:|&#8725;/-/g' '{}' +

``` The [COLOR=red]n[/COLOR] is there for testing purposes. When you're positive it works as expected, run it without [COLOR=red]n[/COLOR] to do the actual job. Also, replace [COLOR=blue]Music[/COLOR] with the mount point of your 3TB disk.

So if I'm understanding this code it should replace colons and forward slashes with a dash?

The problem I see is without manually looking at each top level directory after the operation I wouldn't know if it worked or not, not to mention song titles that may or may not contain one or both of the characters.
Will it also output the result of the operation?

---

### Post by meanmrmustard on 2013-03-18
> **cortman said:**
> A forward slash (/) isn't legal in a filename in Linux or Windows. May want to check again what character you're needing replaced.

I do understand that but isn't there a distinction between a filename and the name of a directory?

I've posted two examples to papibe's reply of directory names that are causing the problem.

---

### Post by schragge on 2013-03-18
> **meanmrmustard said:**
> Will it also output the result of the operation?Yes. The -v in *rename -v* is a short form of  *--verbose*. This option will print the name of each file being renamed. Similarly, -n is a short form of *--no-act*. Have a look at the manual page for rename I [post=12563675]linked above[/post].

---

### Post by papibe on 2013-03-18
> **meanmrmustard said:**
> I've posted two examples to papibe's reply of directory names that are causing the problem.
Those help, but it would be very useful some actual names, for instance if you could paste the result of a 'ls' command.

Regards.

---

### Post by meanmrmustard on 2013-03-18
> **schragge said:**
> Yes. The -v in *rename -v* is a short form of  *--verbose*. This option will print the name of each file being renamed. Similarly, -n is a short form of *--no-act*. Have a look at the manual page for rename I [post=12563675]linked above[/post].

Ok... It seem to work but it appears there's another problem character. Any name that starts with a "." will also stop the transfer.
So would the correct syntax for taking care of that be:

```
-type f -exec rename -vn 's/:|&#8725;|./-/g' '{}' +
```

adding "|." in order to also change the "." to a dash?

---

### Post by meanmrmustard on 2013-03-18
> **papibe said:**
> Those help, but it would be very useful some actual names, for instance if you could paste the result of a 'ls' command.

Regards.

Sorry?
The first example is the exact name that actually caused the transfer to stop.

I manually renamed it with the dash and it was no longer a problem.

---

### Post by Impavidus on 2013-03-18
I think it would require a \. as . itself is a wildcard character.

---

### Post by meanmrmustard on 2013-03-18
As a pipe separates the two problem characters in schragge's example, I'd thought another pipe would be necessary before a third character.

---

### Post by schragge on 2013-03-18
Yes the pipe is needed, but the backslash is needed, too, to escape the special meaning of dot in regular expression:
```
find -type f -exec rename -vn 's/:|&#8725;|\./-/g' '{}' +
``` Beware that this will convert _all_ dots to dashes. Are you sure this is what you want? I'd rather ```
find -type f -exec rename -vn 's/:|&#8725;|^\./-/g' '{}' +
``` to only convert the dot if it's the first character of file name.

---

### Post by Impavidus on 2013-03-18
Yes, I meant s/:|&#8725;|\./g

It's a regular expression, so, although I don't know much about the rename command, I do know that . is a wildcard character that has to be escaped, or it will mach anything. But with the n option it will show what will happen before you actually do the rename.

---

### Post by meanmrmustard on 2013-03-18
> **schragge said:**
> Yes the pipe is needed, but the backslash is needed, too, to escape the special meaning of dot in regular expression:
```
find -type f -exec rename -vn 's/:|&#8725;|\./-/g' '{}' +
``` Beware that this will convert _all_ dots to dashes. Are you sure this is what you want? I'd rather ```
find -type f -exec rename -vn 's/:|&#8725;|^\./-/g' '{}' +
``` to only convert the dot if it's the first character of file name.

Yes it is for files beginning with "." 
Thanks.

---

### Post by meanmrmustard on 2013-03-18
> **schragge said:**
> Yes the pipe is needed, but the backslash is needed, too, to escape the special meaning of dot in regular expression:
```
find -type f -exec rename -vn 's/:|&#8725;|\./-/g' '{}' +
``` Beware that this will convert _all_ dots to dashes. Are you sure this is what you want? I'd rather ```
find -type f -exec rename -vn 's/:|&#8725;|^\./-/g' '{}' +
``` to only convert the dot if it's the first character of file name.

After determining that the command worked with the -n switch, I've now run it without and the output is claiming:

"Can't rename /<pathtodirectory>/<Band/Artist Name>/<Album Title>: <subtitle>/<specific track.mp3>: No such file or directory"

I've randomly verified that several of the claimed non-existent directories/files are there and named just as the output shows them.

This is the actual command I ran:
```
$ find /media/newest3TB/ -type f -exec rename -v 's/:|&#8725;|^\./-/g' '{}' +
```

I run it again this time including the -n switch and it says everything was renamed properly.
:confused:

---

### Post by Vaphell on 2013-03-18
wouldn't ```
s/^[.]|[&#8725;:]/-/g
``` be cleaner? square brackets are just for that :)


> /<pathtodirectory>/**<Band[COLOR="#0000CD"]/[/COLOR]Artist Name>/<Album Title>[COLOR="#0000FF"]: [/COLOR]<subtitle>**/<specific track.mp3>
don't you need to only rename directories? If the file names are peachy then it's all that's required. Furthermore that might be source of the problem with your current code. It tries to change the whole path of the file, which means moving files to a destination that doesn't exist yet.

---

### Post by meanmrmustard on 2013-03-18
> **Vaphell said:**
> wouldn't **s/[&#8725;.]/-/g** be cleaner? square brackets are just for that :)

Frankly I have no idea.
All of this is somewhat beyond my knowledge.
I'm trying to rename files to change all instances of these three characters "/", ":" and "." where the filename begins with "." to "-".
As a test, the code's output looks fine.
Not sure what happened when the -n switch was removed.

---

### Post by meanmrmustard on 2013-03-18
> **Vaphell said:**
> wouldn't ```
s/[&#8725;:.]/-/g
``` be cleaner? square brackets are just for that :)

i think you need to perform the operation on directories first. When you try to rename files but also change the directory part of its path you are effectively trying to move the file to a place that doesn't exist yet.
When you rename dirs first, files don't care and then when you rename files, dir part is already set so no problem.

I see what you're saying.
So this code only operates on directories?... or how do I exclude the files in the next levels?
How do I test this and see the output before actually executing?

---

### Post by Vaphell on 2013-03-18
instead of find -type f try find -type d
i'll update my post soon with more substance when i whip up some working example.

can you give an example path broken down to pieces, eg /some/dir/with:troublesome/characters/file.mp3 =
some
dir
with:troublesome
characters
file.mp3

It would be much easier to recreate the situation because trying to figure out which slash is what is not exactly easy on the eyes ;-)



in the charmap there are 2 fancy slashes and i used both in my example. I went with pure bash because i had a regex problem with unexpected char in rename (maybe my version is old or something)
my test:
some[COLOR="#FF0000"]&#8260;[/COLOR]band[COLOR="#FF0000"]&#8725;[/COLOR]artist (2 different slashes)
some[COLOR="#FF0000"]:[/COLOR]album
file.mp3

```
$ find -type d
.
./some&#8260;band&#8725;artist
./some&#8260;band&#8725;artist/some:album
$ **while read -rd $'\0' d; do p=${d%/*}; n=${d##*/}; mv -- "$d" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -type d -iname '*[&#8260;&#8725;:]*' -print0 ) **
$ find -type d
.
./some-band-artist
./some-band-artist/some-album
```
this should get rid of : and weird slashes in directory names. Try on some disposable data first to see if it works.

---

### Post by meanmrmustard on 2013-03-18
> **Vaphell said:**
> instead of find -type f try find -type d
i'll update my post soon with more substance when i whip up some working example.

can you give an example path broken down to pieces, eg /some/dir/with:troublesome/characters/file.mp3 =
some
dir
with:troublesome
characters
file.mp3

It would be much easier to recreate the situation because trying to figure out which slash is what is not exactly easy on the eyes ;-)

Are you saying I should execute ```
/<media/pathtodirectories>/ find -type d -exec rename -vn s/[&#8725;:.]/-/g
```

Here is a 

path/dir/dir/file 

which is causing problems:

media
newest3TB
Sun Ra
Sun Ra - God:Love
God Is More Than Love Can Ever Be
01 Days of Happiness.mp3

Although in this example the track name has no offending characters.
Here only the colon needs to be changed.

---

### Post by Vaphell on 2013-03-19
i updated my post even more, either way try running this (but on trash data first so there are no surprises):
```
while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -iname '*[&#8260;&#8725;:]*' -print0 ) 
```

this will replace all troublesome chars, from both files and dirs (my earlier post dealt only with dirs but less specific solution should work too). 

```
$ find
.
./some&#8260;band&#8725;artist
./some&#8260;band&#8725;artist/some:album
./some&#8260;band&#8725;artist/some:album/track:1.mp3
$ while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -iname '*[&#8260;&#8725;:]*' -print0 ) 
$ find
.
./some-band-artist
./some-band-artist/some-album
./some-band-artist/some-album/track-1.mp3
```


i see that you didn't have a problem with slashes at all, i somewhat expected that.
. at the beginning of the name can be dealt with in similar manner: *find ... -name '.*' ...* and instead of "$p/${n//.../-}" we can use "$p/-${n#.}"

---

### Post by meanmrmustard on 2013-03-19
> **Vaphell said:**
> i updated my post even more, either way try running this (but on trash data first so there are no surprises):
```
while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -iname '*[&#8260;&#8725;:]*' -print0 ) 
```


I fee like I'm trying to read Greek here.
This should be preceded by the path? In my case "/media/newest3TB" ? 
I have no other data to run it on but the actual files.

I don't understand how you see no problem with slashes.

I'm sure there are some slashes within directory and/or file and/or song names that will stop the transfer.


I'm not even sure what question to as about the code below.
Is this literally what precedes the "$ while...." line?... and so it will be looking for exactly that format, colons and slashes in only those positions?

```
$ find
.
./some&#8260;band&#8725;artist
./some&#8260;band&#8725;artist/some:album
./some&#8260;band&#8725;artist/some:album/track:1.mp3
$ while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -iname '*[&#8260;&#8725;:]*' -print0 ) 
$ find
.
./some-band-artist
./some-band-artist/some-album
./some-band-artist/some-album/track-1.mp3
```


Not sure if it matters but mp3 is not the only format, there's also .flac, .m4a, .shn, etc.

---

### Post by meanmrmustard on 2013-03-19
> **Vaphell said:**
> 



in the charmap there are 2 fancy slashes and i used both in my example. I went with pure bash because i had a regex problem with unexpected char in rename (maybe my version is old or something)
my test:
some[COLOR="#FF0000"]&#8260;[/COLOR]band[COLOR="#FF0000"]&#8725;[/COLOR]artist (2 different slashes)
some[COLOR="#FF0000"]:[/COLOR]album
file.mp3

```
$ find -type d
.
./some&#8260;band&#8725;artist
./some&#8260;band&#8725;artist/some:album
$ **while read -rd $'\0' d; do p=${d%/*}; n=${d##*/}; mv -- "$d" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find -depth -type d -iname '*[&#8260;&#8725;:]*' -print0 ) **
$ find -type d
.
./some-band-artist
./some-band-artist/some-album
```
this should get rid of : and weird slashes in directory names. Try on some disposable data first to see if it works.

Doesn't this tell find to search from the root directory?
I'm also confused about:

./some&#8260;band&#8725;artist
./some&#8260;band&#8725;artist/some:album

As an example with both characters, and separating dirs in new lines to avoid slash confusion, what I'd expect to find would be more like:

/Band
/Artist
/album Name/Title: susbtitle/yet somemore text

where slashes behind Title are not the problem ones.

If I understood exactly what your code is saying I probably wouldn't be so confused.

Since I have no other data to test this, is there no way to run it non-destructively?

---

### Post by Vaphell on 2013-03-19
find by default works with current directory (.) and i worked on my example from its root dir, hence ./<things> format. I created just 1 file for test purposes and the code doesn't care about that either way.

in your case you either need to cd to the proper directory first
```
cd /media/newest3TB
find .
```
```
cd /media/newest3TB
while read ...; do ....; done < <( find .  .... )
```
or give path directly to find
```
find /media/newest3TB
```

```
while read ...; do ....; done < <( find /media/newest3TB  .... )

```
if you run these *find .* / *find <dir>* you will see what is the difference (*find* prepends everything with the path supplied, so *find .* returns ./<things> but *find /media/newest3TB *will return a bunch of /media/newest3TB/<things> - both are equally good for the code below assuming you are in the right directory where . and /media/newest3TB are the same location



```
while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find "/media/newest3TB" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
```

splitting that oneliner to a tidier multiline, script ready form looks like this:
```
while read -rd $'\0' fd             # read paths listed by find one by one
do
  p=${fd%/*}                        # dir that owns $fd (everything but the last part of path)
  n=${fd##*/}                       # name of $fd (the last part of path)
  mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"    # rename (change $n)
done < <( find "/media/newest3TB" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
```

this thing catches the *find* output (list of everything that has slashes or : in its name, starting from the deepest levels)
*while read* combo reads the list one path by one, puts current item in fd variable, fd path gets cut to p (path/dir where fd is located) and n (name) and then it's renamed with *mv* to p/(n with chars replaced by -). Doing it only on the last parts of the whole paths depth first avoids the problem of moving objects to places that don't exist.

as i said, make some dir with trash data and check if it works there first (tweak the line by setting proper dir in find)
you can also put *echo* before *mv* so you get a printout of "mv --- oldpath oldpathwithnewname" that would have been executed (no renaming taking place, last part of the path should change to -'s in place of /: )

---

### Post by meanmrmustard on 2013-03-19
Ahhh! I think I see.
I appreciate the explanation for how the code works.

So what I've done is mkdir "0 test" inside newest3TB and place one album whose title needs fixing in it... 

JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]

After cding to that dir I ran:
```
while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find "/media/newest3TB/0 test" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
```

the result:
```
/media/newest3TB/0 test$ while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; mv -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find "/media/newest3TB[COLOR="#FF0000"]/0 test[/COLOR]" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
mv: cannot move `/media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]' to a subdirectory of itself, `/media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
```

I think I didn't need to add "/0 test" to the code?


BTW, is this Perl, Python, something else or simply bash scripting?

---

### Post by Vaphell on 2013-03-19
interesting,  somehow part of the path gets duplicated. I'll investigate that.

find is recursive so if you didn't add '0 test' to the /media/newest3TB path everything under /media/newest3TB would get tested (all of your stuff).
if your test data is in some specific dir and that's all that is meant to be tested you have to point exactly there. Being too broad might have disastrous effects if there is some bug, especially with commands like *rm*, which are irreversible and require recovery software.

the loop itself is pure bash

generally you can use while read like this:
```
while read ...; do ...; done < file
while read ...; do ...; done < <( command )
while read ...; do ...; done <<< "string"
```
what the 'line' is is decided by *read -d*. By default delimiter is set to newline but in my code null-char is used to separate the results (both in *find -print0* and *read -d $'\0'*) because newline is a legit character that can be used in names in linux filesystems, using \n to delimit results would butcher such weirdo paths.



edit:
what happens when you add -T parameter to mv?
```
mv -T -- ....
```

to get more info about the variables you can add debugging stuff, eg *echo*
```
while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; **echo "p: '$p'"; echo "n: '$n'"; echo "n2: '${n//[&#8260;&#8725;:]/-}'";** mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find "/media/newest3TB/0 test" -depth -iname '*[&#8260;&#8725;:]*' -print0 )

```
this will print the values of temporary p, n variables which are used to determine new path. If something goes wrong there, printing these out should indicate if the problem is with them or with the mv itself.

the code became somewhat unwieldy, you can think about putting it in script, tidily cut to separate lines as shown earlier. Editing it and/or commenting things out with # (eg mv to only see the temporary values to check if they calculate properly) would become much easier.

```
#!/bin/bash

while read -rd $'\0' fd
do
  p=${fd%/*}
  n=${fd##*/}
  echo "p: '$p'"
  echo "n: '$n'"
  echo "n2: '${n//[&#8260;&#8725;:]/-}'"
  mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
done < <( find "/media/newest3TB/0 test" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
```

```
chmod +x myscript.sh     # make the file executable
./myscript.sh   # run the script
```

---

### Post by meanmrmustard on 2013-03-19
> **Vaphell said:**
> 
edit:
what happens when you add -T parameter to mv?
```
mv -T -- ....
```


Here's the command and result:
 ```
/media/newest3TB/0 test$ while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; echo mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"; done < <( find "/media/newest3TB/0 test" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
mv -T -- /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD] /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]
curt@Cocobolo:/media/newest3TB/0 test$
```


Looking in the 0 test dir, the colon is still there.

I'm still digesting the rest of you post.

---

### Post by Vaphell on 2013-03-19
wth? o.O

inside the loop what happens can be reduced to this:

```
$ fd='/media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
$ p=${fd%/*}
$ n=${fd##*/}
$ echo "p: '$p'"
p: '/media/newest3TB/0 test'
$ echo "n: '$n'"
n: 'JON ANDERSON -Lord Of The Rings[COLOR="#FF0000"]:[/COLOR] The Unreleased Yes Songs -[no label 1CD]'
$ echo "n2: '${n//[&#8260;&#8725;:]/-}'"
n2: 'JON ANDERSON -Lord Of The Rings[COLOR="#0000FF"]-[/COLOR] The Unreleased Yes Songs -[no label 1CD]'
$ echo mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
mv -T -- /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings[COLOR="#FF0000"]:[/COLOR] The Unreleased Yes Songs -[no label 1CD] /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings[COLOR="#0000FF"]-[/COLOR] The Unreleased Yes Songs -[no label 1CD]
```
this is what i get in terminal when i paste fd='...' and then the code line by line - ':' clearly becomes '-'  o.O
can you repeat that sequence on your machine and paste the output?

---

### Post by meanmrmustard on 2013-03-19
strange, doesn't seem to be working here.
:confused:

/media/newest3TB/0 test$ fd='/media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ p=${fd%/*}
/media/newest3TB/0 test$ n=${fd##*/}
/media/newest3TB/0 test$ echo "p: '$p'"
p: '/media/newest3TB/0 test'
/media/newest3TB/0 test$ echo "n: '$n'"
n: 'JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ echo "n2: '${n//[&#8260;&#8725;:]/-}'"
n2: 'JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ echo mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
mv -T -- /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD] /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]

---

### Post by Vaphell on 2013-03-19
o.O
somehow *${variable//pattern/replacement}* doesn't work on your end
what is your system/bash version?
```
lsb_release -a
bash --version
```

---

### Post by meanmrmustard on 2013-03-19
GNU bash, version 4.2.8(1)-release (i686-pc-linux-gnu)
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is Ubuntu 11.04 running xfce desktop

---

### Post by papibe on 2013-03-19
Maybe it's not a colon after all, but a [Unicode Character 'FULLWIDTH COLON']("http://www.fileformat.info/info/unicode/char/ff1a/index.htm").

---

### Post by Vaphell on 2013-03-19
crap, i deleted virtualbox image of 11.04 not long ago, only have 11.10+ and don't feel like installing.

you say that even simple
```
$ x='a:b:c'
$ echo ${x//[&#8260;&#8725;:]/-}
a-b-c
```
fails?

tell me, does something like this return the correct result?
```
$ n='JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
$ echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g'
JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD]
```
if so, you can plug it in in place of ${n//.....}
```
mv -- "$fd" "$p"/"$(echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g' )";
```

edit:
as papibe mentioned and i started suspecting this might be an issue with the colon not being the one we think it is, just like there are these other slashes.

---

### Post by papibe on 2013-03-19
> **papibe said:**
> Maybe it's not a colon after all, but a [Unicode Character 'FULLWIDTH COLON']("http://www.fileformat.info/info/unicode/char/ff1a/index.htm").

For example:
```
$ touch "$(python -c 'print "file", u"\uFF1A".encode("utf-8"), "one"')"
$ touch "file : one"
$ ls -1 fi*
file : one
file &#65306; one

$ ls -1 file* | od -a
0000000   f   i   l   e  sp   **[COLOR="#FF0000"]:[/COLOR]**  sp   o   n   e  nl   f   i   l   e  sp
0000020   [COLOR="#FF0000"]**o   < sub**[/COLOR]  sp   o   n   e  nl
0000030

```

---

### Post by meanmrmustard on 2013-03-19
I'm really out of my depth now.
As if I wasn't already!

---

### Post by Vaphell on 2013-03-19
OP, can you copy paste that troublesome colon verbatim into this

```
$ printf "\\\x%s\n" $(printf '[COLOR="#00FF00"]:[/COLOR]'|xxd -p -c1 -u)    # standard ascii
\x3A
$ printf "\\\x%s\n" $(printf '[COLOR="#00FF00"]&#65306;[/COLOR]'|xxd -p -c1 -u)  # fullwidth colon
\xEF
\xBC
\x9A
```
sadly in charmap program searching for 'colon' yields many vertically aligned double dots :/



edit: you might understand now why IT people consider remote helpdesking one of the worst jobs imaginable. Without hands on the problem they are limited to guesswork and asking weird questions that don't make any sense to common folk in hope of pinpointing the source of issues ;-)

---

### Post by meanmrmustard on 2013-03-19
> **Vaphell said:**
> crap, i deleted virtualbox image of 11.04 not long ago, only have 11.10+ and don't feel like installing.

you say that even simple
```
$ x='a:b:c'
$ echo ${x//[&#8260;&#8725;:]/-}
a-b-c
```
fails?

/media/newest3TB/0 test$ x='a:b:c'
/media/newest3TB/0 test$ echo ${x//[&#8260;&#8725;:]/-}
a:b:c


> 
tell me, does something like this return the correct result?
```
$ n='JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
$ echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g'
JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD]
```




/media/newest3TB/0 test$ n='JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g'
JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD]

Yay!

> 
if so, you can plug it in in place of ${n//.....}
```
mv -- "$fd" "$p"/"$(echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g' )";
```


I'll have to check that when I return in a couple hours.

BTW, I sure appreciate all your help

> 
edit:
as papibe mentioned and i started suspecting this might be an issue with the colon not being the one we think it is, just like there are these other slashes.

---

### Post by meanmrmustard on 2013-03-19
> **Vaphell said:**
> 

tell me, does something like this return the correct result?
```
$ n='JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
$ echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g'
JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD]
```
if so, you can plug it in in place of ${n//.....}
```
mv -- "$fd" "$p"/"$(echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g' )";
```

edit:
as papibe mentioned and i started suspecting this might be an issue with the colon not being the one we think it is, just like there are these other slashes.

I'm not sure I have this right but here's what I tried and the result:
```

/media/newest3TB/0 test$ while read -rd $'\0' fd; do p=${fd%/*}; n=${fd##*/}; echo mv -- "$fd" "$p"/$(echo "$n" | sed -r 's/[//:]/-g' )"; done < <( find "/media/newest3TB/0 test" -depth -iname '*[&#8260;&#8725;:]*' -print0 )
>
```

I think I've got something wrong.

You placed a quotation mark here:
mv -- "$fd" "$p"/[COLOR="#FF0000"]"[/COLOR]$(echo "$n" | sed -r 's/[&#8260;&#8725;:]/-/g' )";

That wasn't in your first example. Also... the space between the g' and the ).. was intentional?

---

### Post by Vaphell on 2013-03-19
wth, your bash version seems borked for whatever reason o.O This simply should work, it's a pretty basic bash feature (one of builtin parameter expansion operations)
[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)

quotes are used to make sure the text inside them stays as a single chunk (unshielded spaces cut strings to pieces by default and command sees greater number of bad parameters

'levels' are as follows
```
echo "$n" | sed -r 's/[//:]/-g'  <- we need to capture the output of this and embed it in mv command
[COLOR="#0000FF"]$([/COLOR] echo "$n" | sed -r 's/[//:]/-g' [COLOR="#0000FF"])[/COLOR]    <- name can contain spaces, so we need to quote it
[COLOR="#0000FF"]"[/COLOR]$( echo "$n" | sed -r 's/[//:]/-g' )[COLOR="#0000FF"]"[/COLOR]
```
put together with the rest
```
mv ... "fd" "$p"/"$( ... )"  <- two quoted strings glued together with /
```
you can also make it a single "..."
```
mv ... "fd" "$p/$( ... )"    <- single string with / inside
```



space in $([COLOR="#0000FF"]_[/COLOR]...[COLOR="#0000FF"]_[/COLOR]) don't matter, i simply find them more readable, it appears i didn't type the other one :-)

---

### Post by meanmrmustard on 2013-03-20
Here's an update...
Weirdness.
I've booted into my Precise install (12.04.2) with bash version 4.2.24(1). I cd'd to the 0 test dir and tried the command, it tells me that the 0 test directory doesn't exist in /media/newest3TB!
I renamed it 0test, but it is also not recognized.

On booting it reported an "internal error" - sent the report and proceded.

Before I ran the command I tried updating via the GUI but it reported it couldn't download the packages and to check the internet connection. No problem accessing web pages <sigh>.
Then ran update from the CLI and it updated with no problem.

I haven't tried an upgrade for several years but tried with this install and it tells me there is no new version. I'm guessing since it's the latest LTS version it won't upgrade to a non-LTS version?
I'm presently downloading and am going to install the Ubuntu-gnome-12.10.1-amd64 (I'm not particularly fond of Unity) version and try again to change those pesky characters.

---

### Post by schragge on 2013-03-20
TBH, I think we all got misled into thinking there _are_ some weird Unicode characters in the file names. I feel my share of guilt as I was the first who suggested this. Now, I'm inclined to agree with
> **Vaphell said:**
> i see that you didn't have a problem with slashes at all, i somewhat expected that.
I guess the NAS is NTFS-formatted and mounted with the option *windows_names* that prevents creating files with colon and some other characters in file names.

I further guess the part of the problem now is that the OP somehow manages to put normal slashes in the sed expression:
> **meanmrmustard said:**
> ```
sed -r 's/[//:]/-/g'
``` No wonder it doesn't work.

Try only replacing colons instead: ```
sed 's/:/-/g'
``` This should be enough.

---

### Post by meanmrmustard on 2013-03-20
> **schragge said:**
> 
I guess the NAS is NTFS-formatted and mounted with the option *windows_names* that prevents creating files with colon and some other characters in file names.
.

Actually the NAS is formatted as ext4.
> Now, I'm inclined to agree with
 Originally Posted by Vaphell  
i see that you didn't have a problem with slashes at all, i somewhat expected that.

I'm not understanding why it seems there's no problem with the slashes.
I've had to rename some of the files that caused the transfer to choke and there were no colons in the names, only a slash.
Changing it to a dash allowed the transfer to continue.

---

### Post by schragge on 2013-03-20
Sorry, then I must have been wrong and stand corrected. Hmm, how does your NAS get mounted? As a Samba share? Check the options *mapchars* and *iocharset* of [smbmount]("http://manpages.ubuntu.com/manpages/precise/en/man8/smbmount.8.html").

---

### Post by Vaphell on 2013-03-20
> I'm not understanding why it seems there's no problem with the slashes.

your few examples seem to have only : but none of "the other slashes" so it's somewhat understandable to suspect that slashes were not the problem. If you say you have / in names and have to change them manually then the suspicion is false.
You should give the most broken example possible that covers all corner cases or compile a sample that covers them all.

---

### Post by steeldriver on 2013-03-20
I've been having a bit of a play with this as well

Rather than having to guess / copy-paste the troublesome UTF-8 characters, I wonder if it might work to replace essentially the whole non-ASCII unicode range? it seems to work in 'sed' 

```

$ > a$'\u2215'funny$'\u2215'file
$ > another$'\u2215'funny$'\u2215'file
$
$ ls
a&#8725;funny&#8725;file  another&#8725;funny&#8725;file
$
$ for file in *; do echo mv "$file" "$(sed s/[^U+0000-U+007f]/-/g <<< "$file")"; done
mv a&#8725;funny&#8725;file a-funny-file
mv another&#8725;funny&#8725;file another-funny-file
$

```
I can't  make it work in 'rename' though - maybe one of the perl folks on here can figure it out?
```

$ rename -nv 's/[^U+0000-U+007f]/-/g' *
a&#8725;funny&#8725;file renamed as ----f-------f---
another&#8725;funny&#8725;file renamed as ----------f-------f---
$ 
```

---

### Post by Vaphell on 2013-03-20
reportedly ^\x{0000}-\x{007f} should match non-ascii but i think it's too broad and will destroy non-english names/titles.

---

### Post by steeldriver on 2013-03-21
^^^ that's a good point - perhaps adjusting the range like [U+0020-U+024f] (printable ASCII through Latin Extended-B) or [U+0020-U+1fff] (printable ASCII through 'Greek Extended' - stops short of 'General Punctuation')

```
for file in *; do echo mv "$file" "$(sed s/[^U+0020-U+024f]/-/g <<< "$file")"; done
```
```
for file in *; do echo mv "$file" "$(sed s/[^U+0020-U+1fff]/-/g <<< "$file")"; done
```

---

### Post by meanmrmustard on 2013-03-21
> **Vaphell said:**
> your few examples seem to have only : but none of "the other slashes" so it's somewhat understandable to suspect that slashes were not the problem. If you say you have / in names and have to change them manually then the suspicion is false.
You should give the most broken example possible that covers all corner cases or compile a sample that covers them all.

I don't recall any of them at the moment. I only found them because the Disk Station software reported the problem as it found one file at a time with one error or the other.
There have definitely been more trouble with colons than slashes.

This is the one I posted near the beginning of the thread:

Kippington Lodge - Shy Boy/The Complete Recordings 1967-69

---

### Post by meanmrmustard on 2013-03-21
> **schragge said:**
> Sorry, then I must have been wrong and stand corrected. Hmm, how does your NAS get mounted? As a Samba share? Check the options *mapchars* and *iocharset* of [smbmount]("http://manpages.ubuntu.com/manpages/precise/en/man8/smbmount.8.html").

I'm at a complete loss as to how to determine this. It does use NFS to access files on my computer.
The NAS software is far less intuitive than I had originally thought.

Incidently, I've installed and am working from Ubuntu 12.10 modified to be ubuntu-gnome (gnome classic) but have not tried any of the previous suggestions from this install yet.

---

### Post by schragge on 2013-03-21
> **meanmrmustard said:**
> Kippington Lodge - Shy Boy/The Complete Recordings 1967-69Could you please post the output of
```
find /media/newest3TB -path '*Kippington Lodge - Shy Boy?The Complete Recordings 1967-69*' -exec sh -c 'echo "${0%/*} | ${0##*/}"' '{}' \;
```

---

### Post by schragge on 2013-03-21
> **meanmrmustard said:**
> It does use NFS to access files on my computer.Hmm, then it probably doesn't use Samba. NFSv4 supports UTF-8 out of the box, but I'm not sure about NFS v2/3.

---

### Post by meanmrmustard on 2013-03-21
> **schragge said:**
> Could you please post the output of
```
find /media/newest3TB -path '*Kippington Lodge - Shy Boy?The Complete Recordings 1967-69*' -exec sh -c 'echo "${0%/*} | ${0##*/}"' '{}' \;
```

It returned me to the prompt.

I guess it's no help but since I've edited it manually,  the file now reads

Kippington Lodge - Shy Boy-The Complete Recordings 1967-69

---

### Post by meanmrmustard on 2013-03-21
> **schragge said:**
> Hmm, then it probably doesn't use Samba. NFSv4 supports UTF-8 out of the box, but I'm not sure about NFS v2/3.

BTW I see SMB is allowed but I do not have it enabled.

---

### Post by meanmrmustard on 2013-03-21
> **meanmrmustard said:**
> strange, doesn't seem to be working here.
:confused:

/media/newest3TB/0 test$ fd='/media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ p=${fd%/*}
/media/newest3TB/0 test$ n=${fd##*/}
/media/newest3TB/0 test$ echo "p: '$p'"
p: '/media/newest3TB/0 test'
/media/newest3TB/0 test$ echo "n: '$n'"
n: 'JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ echo "n2: '${n//[&#8260;&#8725;:]/-}'"
n2: 'JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
/media/newest3TB/0 test$ echo mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
mv -T -- /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD] /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]

I've just gone back to this post and ran each line as above.
The output of the last three commands:

$ echo "n: '$n'"
n: 'JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD]'
$ echo "n2: '${n//[&#8260;&#8725;:]/-}'"
n2: 'JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD]'
$ echo mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
mv -T -- /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings: The Unreleased Yes Songs -[no label 1CD] /media/newest3TB/0 test/JON ANDERSON -Lord Of The Rings- The Unreleased Yes Songs -[no label 1CD

...but I look in the 0test dir and see the colon is still there.

---

### Post by schragge on 2013-03-21
Yes, because the last command doesn't actually rename anything, notice *echo* at the beginning. To do the real job, it should be executed without *echo*:
```
mv -T -- "$fd" "$p/${n//[&#8260;&#8725;:]/-}"
``` But it's relieving to see that colon gets converted to dash after all: this means it's a regular colon, not some fancy Unicode character.

---

### Post by meanmrmustard on 2013-03-23
It seems all of your help has resolved the issue.
I ran the command on the 3 TB disk and am proceeding with the transfer to the NAS with no issues so far.

I've installed Ubuntu 12.10 which has a newer version of bash, so maybe that was the key.

Thanks for all the input.

---

