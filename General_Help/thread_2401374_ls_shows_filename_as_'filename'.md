---
title: "ls shows filename as 'filename'"
date: 2018-09-17
forum: General Help
---

### Post by tomhsiung on 2018-09-17
Run this:
```
ubuntu[COLOR=#39C026][FONT=Menlo]**@Server**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**/Data/movies**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$ ls -lia[/FONT][/COLOR]
```

resulted in this:
```
[COLOR=#000000][FONT=Menlo]203423892 drwxr-xr-x  3 ubuntu ubuntu   4096 Sep 17 15:53 [/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**'Zootopia.2016.BD1080P.X264.AAC.English&Mandarin.CHS-ENG.Mp4Ba'**[/FONT][/COLOR]
```

Note the double marks of ' ' around the filename.

And run this:
```
ubuntu[COLOR=#39C026][FONT=Menlo]**@Server**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**/Data/movies**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$ cd Zootopia.2016.BD1080P.X264.AAC.English\&Mandarin.CHS-ENG.Mp4Ba/[/FONT][/COLOR]
```

resulted in this:
```
ubuntu[COLOR=#39C026][FONT=Menlo]**@Server**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**/Data/movies/Zootopia.2016.BD1080P.X264.AAC.English&Mandarin.CHS-ENG.Mp4Ba**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$[/FONT][/COLOR]
```

The actual filename is without the marks of ' '

and what does they mean?

---

### Post by deadflowr on 2018-09-17
There's a slash between the h in English and the & symbol.
This is because without it the file would run only as Zootopia.2016.BD1080P.X264.AAC.English.
The & symbol in console denotes a break and the start of a new command so everything after it would be considered a new command.
The slash and quotes are how  it gets around this for odd filenames like that.
It only shows like that for the output and not the working directory path, as shown.
Case in point I have Virtualbox installed, so when I run ls it shows as 'Virtualbox VMs' with quotes.
But if I move into that directory it shows in the working directory line as ~/Virtualbox VMs without quotes.
Does any of that make sense?

---

### Post by Impavidus on 2018-09-18
When a filename written by ls can't be used directly on the command line, it's automatically quoted. There are some options to tune the way the quotes work. Some fun with file names with embedded quote characters, spaces and backslashes:```
# Just the bare filename
$ ls -N1
file1
file 2
'file 3'
"file 4"
file\ 5
'file' "6"
# Default: single quotes. The one with single quotes in the filename gets double quotes, the one with both
# single and double quotes has the single quotes escaped and outside the quotes.
$ ls -1
file1
'file 2'
"'file 3'"
'"file 4"'
'file\ 5'
''\''file'\'' "6"'
# Escape with backslash; doesn't escape the quotes though
$ ls -b1
file1
file\ 2
'file\ 3'
"file\ 4"
file\\\ 5
'file'\ "6"
# Use double quotes, escaping double quotes in the file name
$ ls -Q1
"file1"
"file 2"
"'file 3'"
"\"file 4\""
"file\\ 5"
"'file' \"6\""

```Also read the man page for ls and try the option --quoting-style=... There's even more fun when using filenames with embedded newlines or non-printing characters. Of course, one normally avoids filenames with these funny chracters, but in some locales some of the default directories have such names. With dutch settings, videos are stored in the "Video's" directory (with the apostrophe, not with the double quotes).

---

### Post by tomhsiung on 2018-09-20
Thanks, that helps.

---

