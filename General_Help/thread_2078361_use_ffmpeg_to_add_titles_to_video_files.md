---
title: "use ffmpeg to add titles to video files"
date: 2012-10-30
forum: General Help
---

### Post by HiImTye on 2012-10-30
I wrote a bash script to be used by nautilus to add '*[COLOR=Plum]Title[/COLOR]*' metadata to video files.

[SIZE=2]**[COLOR=DarkGreen]what it does[/COLOR]**[/SIZE]

[LIST]
[*]filters the input list to exclude any file that doesn't end in either '[COLOR=Plum].*avi*[/COLOR]' '[COLOR=Plum].*mkv*[/COLOR]' or '[COLOR=Plum].*mp4*[/COLOR]'   - these are the formats I have included, but you can easily edit it to   include any other file format that ffmpeg can handle (including audio   files)
[*]if the filename is in the format of '*[COLOR=Plum]Show Name.S##E##.Episode Name.extension[/COLOR]*' it will automagically fill the title popup to '*[COLOR=Plum]Show Name S##E##: Episode Name[/COLOR]*' allowing for you to just add the episode name at the end. this works so long as '*[COLOR=Plum]Show Name[/COLOR]*' and '*[COLOR=Plum]S##E##[/COLOR]*' are separated by either a period or a space. works even if there is no episode name following the '*[COLOR=Plum]S##E##[/COLOR]*' it will just end in '*[COLOR=Plum]S##E##: [/COLOR]*'. note: there is no filtering of either the show name or the episode name, so you will need to have those done in advance.
[*]if the filename is not in that format, it automagically fills the title popup with the filename, minus the file extension.
[*]if the user hits '*close*' or '*cancel*' then it skips the file
[*]re-encodes (using '*copy*' for both video and audio) with the new metadata, using a temporary file at '*[COLOR=Plum]/path/to/.file[/COLOR]*' (this is very fast since it is just copying, not transcoding)
[*]deletes the old file, replacing it with the new one
[*]works on networked files, too! (assuming you have write permissions to those paths)
[/LIST]
**[COLOR=DarkGreen]how to use[/COLOR]**

[LIST=1]
[*] save the script to '*[COLOR=Plum]~/.gnome2/nautilus-scripts/Tag Videos[/COLOR]*'
[*]  give it execute permissions (i.e. by right clicking on it, going to  'properties,' the 'permissions' tab, and placing a check mark beside  'allow executing file as program')
[*]right click on a file, or selection of files, then go to Scripts > Tag Videos
[*]enter the title you want in the popup.
[/LIST]
 **Tag Videos**:
```
#!/bin/bash

while read -r f
do
 # the file path of our hidden temporary file.
 nF=$(echo "$f" | sed 's|\(.*/\).*$|\1|').$(echo "$f" | sed 's|.*/\(.*\)$|\1|')
 # create title suggestion for this file.
 # strip the file extension and folder path
 Title=$(echo "${f%.*}" | sed 's|.*/\(.*\)|\1|')
 # auto populate 'Show Title S##E##: Episode Title' for filenames using that
  # structure. the episode title will be missing if it is not present in the file
  # name. also, there is no filtering of either the show title or the episode title
  # so that will need to be done in advance.
 if [[ "$Title" =~ [sS][0-9]{1,2}[eE][0-9]{2} ]]; then
 Title=$(echo "$Title" | sed 's|\(.*\)[ .]\([sS][0-9]\{2\}[eE][0-9]\{2\}\)|\1 \U\2: |')
  # check if there is an episode name following the episode number.
  if [[ ! "$Title" =~ [eE][0-9]{2}$ ]]; then
   # if there is, filter out a separating '.' if one exists.
   Title=$(echo "$Title" | sed 's|\([eE][0-9]\{2\}: \)\.|\1|')
  fi
 fi
 # prompt user for new title.
 Title=$(zenity --entry --title="Video Title" --text="Enter a new title for the video  file $Title." --entry-text="$Title")
 # if no title (i.e. user hit 'Cancel' during the Zenity popup), skip.
 if [ ! -n "$Title" ]; then
  continue
 fi
 # use ffmpeg to re-encode with new tag.
 gnome-terminal -x ffmpeg -i "$f" -metadata title="$Title" -acodec copy -vcodec copy -scodec copy "$nF" &

 # pretend that the old file didnt exist.
 rm -f \"$Filename\"
 mv \".$Filename\" \"$Filename\"
done < <( echo "$NAUTILUS_SCRIPT_SELECTED_URIS" | grep -iE '.avi$|.mp4$|.mkv$' | sed 's|%20| |g')

exit
```

---

### Post by FakeOutdoorsman on 2012-10-30
Newer ffmpeg syntax for your script is:
```
ffmpeg -i "$f" -metadata title="$Title" -c copy -map 0 "$nF"
```

This will copy all streams: including subtitle, data, and attachments (not that you see many of those), from the input to the output.  Otherwise I believe only the first video video and audio streams are copied using only "-vcodec copy -acodec copy".

---

### Post by Vaphell on 2012-10-30
that whole *SAVEIFS=$IFS; IFS=$'\n'; for ... done; IFS=$SAVEIFS* hack stinks.

if you have a string that needs to be dealt with on a per line basis, you should use ```
while read -r f
do
  ...
done <<< "$string" 
``` for that

grepping files names one by one doesn't have much sense when you can filter whole $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS at once and work only with valid files
```
while read -r f
do
  ...
done < <( echo "NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | grep -iE '.avi$|.mp4$|.mkv$' )
```

you can separate sed expressions with any char you want, you are not limited to / and |. Sed will cut with the first char after s. Also -r makes for a tidy expression without \'s
```
$ echo abc.mp4 | sed -r 's![.](avi|mp4|mkv)$!!'
abc
```
besides you don't need avi|mp4|mkv, you have tested for extensions already, so you can simply chop off whatever extension you get, eg [.][^.]+
Also you can go with native bash:
```
Title=${f%.*}
```

testing for S##E## format can be easily done with [[ $f =~ regex ]]
```

$ x='abc.s01e12.avi'
$ [[ $x =~ [sS][0-9]{1,2}[eE][0-9]{2} ]] && echo true || echo false
true
$ x='abc.se.avi'
$ [[ $x =~ [sS][0-9]{1,2}[eE][0-9]{2} ]] && echo true || echo false
false
```

---

### Post by HiImTye on 2012-10-30
> **FakeOutdoorsman said:**
> Newer ffmpeg syntax for your script is:
```
ffmpeg -i "$f" -metadata title="$Title" -c copy -map 0 "$nF"
```This will copy all streams: including subtitle, data, and attachments (not that you see many of those), from the input to the output.  Otherwise I believe only the first video video and audio streams are copied using only "-vcodec copy -acodec copy".

that gives ```
Unrecognized option 'c'
Failed to set value 'copy' for option 'c'
```

---

### Post by HiImTye on 2012-10-30
> **Vaphell said:**
> that whole *SAVEIFS=$IFS; IFS=$'\n'; for ... done; IFS=$SAVEIFS* hack stinks.
why?

> grepping files names one by one doesn't have much sense when you can filter whole $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS at once and work only with valid filesI know, I just wanted to get a working copy done first. I'm still working on it. for instance, I just made it work with networked files, but I wanted to get it working and posted before I did dishes/ate dinner.

> you can separate sed expressions with any char you want, you are not limited to / and |.I know, but I wanted to get the actual work done before I left to do dishes/eat dinner ;)
> besides you don't need avi|mp4|mkv, you have tested for extensions already, so you can simply chop off whatever extension you get, eg [.][^.]+ I know, I'm going to be using ```
\.[^.]*$
``` to account for if there are periods in the filename
> testing for S##E## format can be easily done with [[ $f =~ regex ]]
```

$ x='abc.s01e12.avi'
$ [[ $x =~ [sS][0-9]{1,2}[eE][0-9]{2} ]] && echo true || echo false
true
$ x='abc.se.avi'
$ [[ $x =~ [sS][0-9]{1,2}[eE][0-9]{2} ]] && echo true || echo false
false
```that's good to know. I'll try out some version of this

---

### Post by Vaphell on 2012-10-30
> that whole SAVEIFS=$IFS; IFS=$'\n'; for ... done; IFS=$SAVEIFS hack stinks.
[QUOTE]why?[/QUOTE]
while read works on per-line basis right off the bat and $f inside the *do done* block behaves the same, so why bother with all that boilerplate code to avoid the issue with delimiters? while read solves it for free.
While in this case it doesn't really make much difference, there are things the for loop can't do easily, like reading a file and preserving empty lines (IFS hack will preserve non-empty lines but will kill empty ones)

my take on the for vs while thing is:
- tidy explicitly listed data and arrays go to for loops
- random strings, command outputs and other rather unpredictable crap go to while read loops

assuming that one is hellbent on using for loop - one can create a pretty array and use it with for
```
IFS=$'\n' read -rd '' -a files < <( echo "$NAUTILUS_WHATEVER" | grep -Ei '...' )

for f in "${files[@]}"
do
  ...
done
```
this way IFS change is localized only to read command and there is nothing to save and restore.


> I know, I'm going to be using 
\(.*\)\.[a-zA-Z0-9]+$
imo you should go with native bash ${f%.*}, it's good enough for this case and it doesn't spawn a separate sed process to do a trivial job

---

### Post by HiImTye on 2012-10-30
> **Vaphell said:**
> while read works on per-line basis right off the bat and $f inside the *do done* block behaves the same, so why bother with all that boilerplate code to avoid the issue with delimiters? while read solves it for free.
I'll give it a try and see how it ends up, I've never considered using while for anything other than infinite loops
> While in this case it doesn't really make much difference, there are things the for loop can't do easily, like reading a file and preserving empty lines (IFS hack will preserve non-empty lines but will kill empty ones)I had that issue earlier, I normally like to separate my sed lines after every ; and space indent the next one, but it won't work while space isn't excluded, unless the next sed job is at the start of the next line

> imo you should go with native bash ${f%.*}, it's good enough for this case and it doesn't spawn a separate sed process to do a trivial jobdo you have any documentation for this? I don't understand the function, and google is an a-hole when you search for anything other than words

---

### Post by Vaphell on 2012-10-30
> I'll give it a try and see how it ends up, I've never considered using while for anything other than infinite loops

**while read** is perfect for
- reading files: *...; done < file*
- command outputs:  *...; done < <( command )*
- strings of unknown size: *...; done <<< "$string"*
It stops automatically when there is nothing else to read, it can read data into multiple variables (eg *while read -r col1 col2 col3; do ...*). You can modify local IFS and *read -d* to fine tune how input data is processed.

There are some caveats though - data is put in stdin queue for *read* to eat it, so in case you put something interactive inside the loop, something that reads from stdin as well, it will get the data instead of *read*.
There is workaround to that though, so no problem (separate file descriptor for the loop so nothing interferes with the buffer)

approach with read into array (IFS=$'\n' read -rd '' -a array <... ) i mentioned earlier might be the best solution here
Preprocessed data is clean and ready to use, no caveats with stdin

> do you have any documentation for this? I don't understand the function, and google is an a-hole when you search for anything other than words

to get the list of available expansion operations
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

${variable**%**.*} = chop of the **shortest** possible dot+anything from the right
${variable**%%**.*} = chop of the **longest** possible dot+anything from the right

```
$ x=aaa.bbb.ccc.ddd
$ echo ${x%.*}
aaa.bbb.ccc
$ echo ${x%%.*}
aaa
```
these patterns work the same as globs for files/dirs, you have *, ?, [] - more limited than fullblown regexes, but good enough for most cases.


there are also # and ## which do the same with provided pattern on the left side.

---

### Post by FakeOutdoorsman on 2012-10-31
> **HiImTye said:**
> that gives ```
Unrecognized option 'c'
Failed to set value 'copy' for option 'c'
```

That just means you're using something that only supports the older syntax and it probably works just fine; although consider adding "-scodec copy" if you want to keep any subtitle streams, if any.

---

### Post by HiImTye on 2012-10-31
> **Vaphell said:**
> **while read** is perfect for
- reading files: *...; done < file*
- command outputs:  *...; done < <( command )*
- strings of unknown size: *...; done <<< "$string"*
It stops automatically when there is nothing else to read, it can read data into multiple variables (eg *while read -r col1 col2 col3; do ...*).
sounds just like a for loop, except I can see some situations where it would save on typing
> and *read -d* to fine tune how input data is processed.
I'm not sure what 'read -d' does, the man page doesn't list any switches
> There are some caveats though - data is put in stdin queue for *read* to eat it, so in case you put something interactive inside the loop, something that reads from stdin as well, it will get the data instead of *read*.
There is workaround to that though, so no problem (separate file descriptor for the loop so nothing interferes with the buffer)
what's an example of this workaround?
> approach with read into array (IFS=$'\n' read -rd '' -a array <... ) i mentioned earlier might be the best solution here
Preprocessed data is clean and ready to use, no caveats with stdin
that sounds great
> to get the list of available expansion operations
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

${variable**%**.*} = chop of the **shortest** possible dot+anything from the right
${variable**%%**.*} = chop of the **longest** possible dot+anything from the right

```
$ x=aaa.bbb.ccc.ddd
$ echo ${x%.*}
aaa.bbb.ccc
$ echo ${x%%.*}
aaa
```these patterns work the same as globs for files/dirs, you have *, ?, [] - more limited than fullblown regexes, but good enough for most cases.
thank you :D

> **FakeOutdoorsman said:**
> That just means you're using something that only supports the older syntax and it probably works just fine; although consider adding "-scodec copy" if you want to keep any subtitle streams, if any.
I'm using the ffmpeg in the 12.10 repos

---

### Post by Vaphell on 2012-10-31
> sounds just like a for loop, except I can see some situations where it would save on typing

well, loop body is the same in both cases, but really *for* is less flexible when it comes to data parsing. *While read* saves not only typing, but also worrying about unexpected effects of IFS modifications.
*read -d <char>* defines what symbol should be used as a record/line delimiter (default \n)
IFS before *read* defines field separator, in other words how to cut contents of the record into separate fields so they can be packed into listed variables

```
$ while IFS=[COLOR="Blue"],[/COLOR] read -d[COLOR="Red"].[/COLOR] x y z; do echo "->($x)($y)($z)"; done <<< "a[COLOR="Blue"],[/COLOR]b[COLOR="Blue"],[/COLOR]c[COLOR="Red"].[/COLOR]d[COLOR="Blue"],[/COLOR]e[COLOR="Blue"],[/COLOR]f[COLOR="Red"].[/COLOR]g[COLOR="Blue"],[/COLOR]h[COLOR="Blue"],[/COLOR]i[COLOR="Red"].[/COLOR]"
->(a)(b)(c)
->(d)(e)(f)
->(g)(h)(i)
```

> what's an example of this workaround?

[http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

```
while read -r **-u9** line
do
  cat > ignoredfile
  echo "$line"
done **9<** "$file"
```
standard file descriptors are 0, 1, 2 (stdin/stdout/stderr). Using some other number makes the loop go out of the way of other programs that might want to use these.

---

### Post by HiImTye on 2012-10-31
> **Vaphell said:**
> well, loop body is the same in both cases, but really *for* is less flexible when it comes to data parsing. *While read* saves not only typing, but also worrying about unexpected effects of IFS modifications.
*read -d <char>* defines what symbol should be used as a record/line delimiter (default \n)
IFS before *read* defines field separator, in other words how to  cut contents of the record into separate fields so they can be packed  into listed variables

```
$ while IFS=[COLOR=Blue],[/COLOR] read -d[COLOR=Red].[/COLOR] x y z; do echo "->($x)($y)($z)"; done <<< "a[COLOR=Blue],[/COLOR]b[COLOR=Blue],[/COLOR]c[COLOR=Red].[/COLOR]d[COLOR=Blue],[/COLOR]e[COLOR=Blue],[/COLOR]f[COLOR=Red].[/COLOR]g[COLOR=Blue],[/COLOR]h[COLOR=Blue],[/COLOR]i[COLOR=Red].[/COLOR]"
->(a)(b)(c)
->(d)(e)(f)
->(g)(h)(i)
```
when you use an example like that, *for* certainly seems much less powerful
> [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

```
while read -r **-u9** line
do
  cat > ignoredfile
  echo "$line"
done **9<** "$file"
```standard file descriptors are 0, 1, 2  (stdin/stdout/stderr). Using some other number makes the loop go out of  the way of other programs that might want to use these.I'll have to remember that trick

I changed the script to a new version. I had some issues with how I was handling titles that weren't apparent because of my file structure, but I got it all sorted now

edit: I did notice that $f{##/*} doesn't work for some reason

---

### Post by Vaphell on 2012-11-01
> edit: I did notice that $f{##/*} doesn't work for some reason

it, as you've written it here, has 2 things wrong:
- f is outside {} (probably a typo)
- ##/* is a bad expression, because there are only 2 scenarios for it and both don't make any sense.
- value starts with / -> expression will delete everything
```
$ f=[COLOR="Blue"]/abc.def[/COLOR]
$ echo ${f##[COLOR="Blue"]/*[/COLOR]}

$
```
- value doesn't start with / -> nothing happens
```
$ f=abc.def
$ echo ${f##/*}
abc.def
$
```


what did you expect to achieve here?

---

### Post by HiImTye on 2012-11-07
no, it just doesn't work, when I was testing it it did nothing
```
tye@T:~$ a=aaa.bbb.ccc.ddd
tye@T:~$ echo ${a##.*}
aaa.bbb.ccc.ddd
tye@T:~$ echo ${a#.*}
aaa.bbb.ccc.ddd
```

---

### Post by HiImTye on 2012-11-07
new version with file size checking, in case ffmpeg has an error:
(since I can no longer edit the original post)
I also split the ffmpeg job into a separate script, so the location of that needs to be specified in the first script

tagVideos.sh
```
#!/bin/bash

tagVideosCore=$HOME/Launchers/tagVideosCore.sh

while read -r f
do
 # the file path of our hidden temporary file.
 nF=${f%/*}/.${f##*/}
 # create title suggestion for this file.
 # strip the file extension and folder path
 Title=${f%.*}; Title=${Title##*/}
 # auto populate 'Show Title S##E##: Episode Title' for filenames using that
  # structure. the episode title will be missing if it is not present in the file
  # name. also, there is no filtering of either the show title or the episode title
  # so that will need to be done in advance.
 if [[ "$Title" =~ [sS][0-9]{1,2}[eE][0-9]{2} ]]; then
 Title=$(echo "$Title" | sed 's|\(.*\)[ .]\([sS][0-9]\{2\}[eE][0-9]\{2\}\)|\1 \U\2: |')
  # check if there is an episode name following the episode number.
  if [[ ! "$Title" =~ [eE][0-9]{2}$ ]]; then
   # if there is, filter out a separating '.' if one exists.
   Title=$(echo "$Title" | sed 's|\([eE][0-9]\{2\}: \)\.|\1|')
  fi
 fi
 # prompt user for new title.
 Title=$(zenity --entry --title="Video Title" --text="Enter a new title for the video  file $Title." --entry-text="$Title")
 # if no title (i.e. user hit 'Cancel' during the Zenity popup), skip.
 if [ ! -n "$Title" ]; then
  continue
 fi
 # use ffmpeg to re-encode with new tag.
 gnome-terminal -x $tagVideosCore "$f" "$nF" "$Title"
 echo tagging video file with ffmpeg, refer to fout.txt to see results >> out.txt
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_URIS" | grep -iE '.avi$|.mp4$|.mkv$' | sed 's|%20| |g')

exit
```tagVideosCore.sh
```
#!/bin/bash
echo tagging video file "$1" >> fout.txt
echo ffmpeg -i "$1" -metadata title="$3" -acodec copy -vcodec copy -scodec copy "$2"
ffmpeg -i "$1" -metadata title="$3" \
 -acodec copy -vcodec copy -scodec copy "$2"
file_f=$(stat -c %s "$1")
file_nF=$(stat -c %s "$2")
if [ "$file_nF" -gt "$file_f" ]; then
 echo new file "$2" larger than old file, deleting old file >> fout.txt
 rm -f "$1"
else
 echo new file "$2" not larger than old file, skipping >> fout.txt
 rm -f "$2"
fi

exit
```

---

### Post by Vaphell on 2012-11-07
```
$ a=aaa.bbb.ccc.ddd
$ echo ${a##.*} [COLOR="Blue"]${a##*.}[/COLOR]
aaa.bbb.ccc.ddd [COLOR="Blue"]ddd[/COLOR]
$ echo ${a#.*} [COLOR="Blue"]${a#*.}[/COLOR]
aaa.bbb.ccc.ddd [COLOR="Blue"]bbb.ccc.ddd[/COLOR]
```

you are doing it wrong ;-) Of course nothing happens, your example string doesn't start with . and your pattern .* says 'dot+anything'. There is no dot on the left, iiight? ;-) But even if there was, the expression would simply consume dot (#) or everything (##): . at 1st position would satisfy . in the pattern, * would match (## - the rest of string, # - nothing). Result = (## everything is axed, # dot is trimmed)

```
$ a=[COLOR="Red"].[/COLOR][COLOR="Blue"]aaa.bbb.ccc.ddd[/COLOR]
$ echo "(${a#[COLOR="Red"].[/COLOR]*})(${a##[COLOR="Red"].[/COLOR][COLOR="Blue"]*[/COLOR]})"
(aaa.bbb.ccc.ddd)()
```



> ```
nF=$(echo "$f" | sed 's|\(.*/\).*$|\1|').$(echo "$f" | sed 's|.*/\(.*\)$|\1|')
```

```
nF=${f%/*}/.${f##*/}
```
example:```
$ f=/abc/def/ghi.avi
$ echo "$f -> ${f%/*}/.${f##*/}"
/abc/def/ghi.avi -> /abc/def/.ghi.avi
```

> ```
Title=$(echo "${f%.*}" | sed 's|.*/\(.*\)|\1|' )
```
```
Title=${f%.*}; Title=${Title##*/}
```
example
```
$ f=/abc/def/ghi.avi
$ Title=${f%.*}; Title=${Title##*/}
$ echo "$Title"
ghi
```

---

### Post by HiImTye on 2012-11-07
ok, I understand it now. for some reason my brain wasn't wrapping around it. but I see it now

---

### Post by Vaphell on 2012-11-07
i think it might be useful to use sed only to parse the name into pieces and use bash on those pieces. Greater flexibility and conditions easier to write

```
$ f=Some.Series.s01e12.Some.Ep.Title.avi
$ IFS=$'\t' read -r main epn ept < <( echo "${f%.*}" | sed -r 's/(.*[^. ])[. ]*([sS][0-9]{1,2}[eE][0-9]{2})[. ]*(.*)/\1\t\2\t\3/' )
$ echo ${main//./ } = ${epn^^} = ${ept//./ }
Some Series = S01E12 = Some Ep Title
```
sed spits out tab delimited chunks, read with IFS set to \t puts chunks into variables.

---

