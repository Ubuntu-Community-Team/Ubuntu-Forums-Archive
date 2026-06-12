---
title: "Can't get sed commands to work"
date: 2017-03-30
forum: General Help
---

### Post by raysa on 2017-03-30
I have a folder with several text tiles that I'd like to edit as a batch, but I can't get sed to work.
All the files have several unwanted blank lines in them which I'd like to remove.
Also, the start of each file is identical and I'd like to remove line 17 from them all as it has unwanted content.
So, in a terminal opened in the folder containing the files, I typed commands (separately, one command at a time) that I've seen on sed guide pages.
To remove the blank lines I've tried:
```
sed -i '/./!d' *txt
sed -i '/^$/d' *txt
```
To remove line 17 I've tried:
```
sed -i '17d' *txt
```
In each case, the folder and all the files in it have remained completely unchanged.
My system is Ubuntu 16.04.2 with GNU sed 4.2.2
I'd love to get sed working for this task (it's as job which will often recur), but I can't see what I'm doing wrong.
Thanks for any help.

---

### Post by SeijiSensei on 2017-03-30
Rather than sed, you can use head/tail to remove that line:
```

head -n 16 < file > newfile && tail -n 18 < file >> newfile

```
That puts the first 16 lines into newfile, then appends everything from line 18 to the end.

---

### Post by raysa on 2017-03-30
Thanks, but can this be done as a batch operation on the whole folder of many files, rather than file by file?

---

### Post by SeijiSensei on 2017-03-31
```

#!/bin/bash
mkdir newfiles
for f in *
do
     head -n 16 < $f > newfiles/$f && tail -n 18 < $f >> newfiles/$f
done
exit 0

```
This creates a subdirectory called "newfiles" below the current directory, then iterates over all the files in the current directory and saves the edited files in the newfiles directory.

Put those commands into a text file, then mark the file executable with "chmod a+x filename".  You can then run it from the command prompt with "./filename".

You can replace "*" with any file specification like "*.html" to limit the script to HTML files.

---

### Post by sudodus on 2017-03-31
There should be a space before the d (for delete). Try these commands [COLOR="#0000FF"](blue)[/COLOR] and you should get the same output (black)

```
[COLOR="#0000FF"]$ echo 'line 1

line 3
line 4

line 6'[/COLOR]
line 1

line 3
line 4

line 6
```


```
[COLOR="#0000FF"]$ echo 'line 1

line 3
line 4

line 6'|sed '/^$/ d'[/COLOR]
line 1
line 3
line 4
line 6
```

You can also use the tr command to remove blank lines, identified by adjacent \n (newline) characters:

```
[COLOR="#0000FF"]$ echo 'line 1

line 3
line 4

line 6'| tr -s '\n' '\n'[/COLOR]
line 1
line 3
line 4
line 6
```

---

### Post by raysa on 2017-03-31
Thank you SeijiSenei.  This looks promising, but I get this line 10 times in the terminal:
./abcbatchedit: line 17: $f: ambiguous redirect
abcbatchedit is the name I gave the file with the commands.
The new subdirectory 'newfiles' appeared but contained only one of the txt files (the third one in the folder) and it still had line 17 present.

---

### Post by raysa on 2017-03-31
Thank you sudodus.  I tried my commands from the first post above again, but with a space before the d, but it made no difference - they still didn't work.

In the terminal your line suggestions work perfectly - both approaches remove the blank lines. Indeed the one using d for delete works whether or not there's a space before the d.
So sed is working fine on my computer ... I must be doing something wrong when trying to apply it to edit the text files rather than just writing to the terminal. Is there anything else I need to do apart from what I describe in my first post above?
Thanks

---

### Post by sudodus on 2017-03-31
- Are there 'special characters' in the file names? Then you should use double quotes, "$f" instead of $f.

- Maybe replace the head and tail commands with sed '17 d' in the for loop.

```
< "$f" sed '17 d' > "newfiles/$f"
```

---

### Post by sudodus on 2017-03-31
> **raysa said:**
> Thank you sudodus.  I tried my commands from the first post above again, but with a space before the d, but it made no difference - they still didn't work.

In the terminal your line suggestions work perfectly - both approaches remove the blank lines. Indeed the one using d for delete works whether or not there's a space before the d.
So sed is working fine on my computer ... I must be doing something wrong when trying to apply it to edit the text files rather than just writing to the terminal. Is there anything else I need to do apart from what I describe in my first post above?
Thanks

I checked, and you are right, it works without the space too :-) So the problem is how to fix it in the shellscript.

---

### Post by raysa on 2017-03-31
There are no special characters in any of the filenames (brackets ( ) aren't "special" are they?)  But I've added the double quotes anyway because the single ones, or none, gave me an "ambiguous redirect" error.
With the double quotes and the 'd' delete approach, the new subdirectory is duly created and copies of all the files appear in it - but alas with no editing ... all the blank lines still there.

---

### Post by raysa on 2017-03-31
And just tried it with a specific line to delete rather than all blanks - eg '4 d' - but still no result.

---

### Post by sisco311 on 2017-03-31
You have to use the -s flag. sed is a stream editor  after all.. ;) (check the man page) 

```
sed -si -e '17d' -e '/^$/d' *.txt
```

---

### Post by sudodus on 2017-03-31
Try this approach with ***find***. It is better at treating file names with special characters, and yes, () are special characters in linux.

```

#!/bin/bash

mkdir -p newfiles

find . -maxdepth 1 -type f -name "*.txt" \
 -exec echo "-----------------------------------------------------------" \; \
 -exec cp -pv {} newfiles/{} \; \
 -exec sed -i -e '17 d' -e '/^ *$/ d' newfiles/{} \; \
 -exec diff {} newfiles \;

```

The \ at the line ends makes the shell read the next line as if it were continuing on the previous line 'a line break for the programmer, but not for the program'.

The \; is finishing the -exec 'action'.

The {} is a placeholder for the argument (the file name), and it works with special characters too.

The final line is only checking that the blank lines and line #17 are removed. You can skip the final \ on the previous line and that last line in your final script.

If you want the script silent, you can remove the exec echo line and the option **v** from cp -pv in the next line.

---

### Post by raysa on 2017-03-31
Thank you for this, sisco311.  I've looked at so many sed guide pages and tried so many of the apparently relevant examples etc, and I'm really grateful to the several people who have tried to help.
But I'm still not there ... typed your command exactly in a terminal in the folder where the files are, and the files remain stubbornly unchanged.
Double-checked to ensure no typos and tried again. No result. And no clues in the terminal - it just moves to the next $ line.

---

### Post by raysa on 2017-03-31
Many thanks sudodus.  This produces the newfiles directory and all the file copies are in there ... but alas without anything changed.
The terminal also shows a list of the files and the redirect, eg: './1814.txt' -> 'newfiles/./1814.txt'

---

### Post by sudodus on 2017-03-31
Both sisco's and my scripts work with my test files. If they don't work with your files, your files must be strange somehow, or maybe they have less than 17 lines and there are no blank lines.

Please show a file: if fairly small put it within code tags:

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

-o-

If the file is too big for that, please upload it to somewhere and give us a link to it. Or you can cut part of a file (with more than 17 lines and at least one blank line) and put it within code tags.

---

### Post by raysa on 2017-03-31
Here's a typical file. These are files which are for the abc music notation system, and would be switched to an .abc extension before use by abc music software.
These files have been exported from a music notation graphical package which renders normal music notation but which can export these ascii text files for transporting to abc.
I wonder if the % characters are part of the problem?  These are actually quite unnecessary and I would happily lose all the % symbols and the rest of the lines to the right of them if that helps.

```

X:1     %Music
T:     %Tune name
 
 
V:1     %
     %!STAVE 0 '' @
     %!INSTR 'Staff 1' 0 0 @
|:
M:3/4     %Meter
L:1/8     %
K:G
\"G"dc B2 G2 |
\"D"c3/2B/ A2 D2 |
\"G"G3/2F/ GA Bc |
dd/e/ dc Bc |

\dc B2 G2 |
\"D"c3/2B/ A2 D2 |
\"G"G3/2F/ GA Bc |
"D"AF "G"G4 ::

\"G"B,[D-B,-][DB,][D-B,-][DB,][DB,] |
\"C"C[E-C-][EC][E-C-][EC]F |
\"G"G3/2A/ BA "D"GF |
"G"G2 D/E/D/C/ "D"B,A, |

\"G"B,[D-B,-][DB,][D-B,-][DB,][DB,] |
\"C"C[E-C-][EC][E-C-][EC]F |
\[G3/2"G"G,3/2]A/ BA "D"GF |
\"G"G2 G4 :|
\
V:2     %
     %!STAVE 0 '' @
     %!INSTR 'Staff 2' 0 0 @
|:
M:3/4     %Meter
L:1/8     %
K:G
\BA G2 D2 |
\A3/2G/ F2 A,2 |
\D3 F GA |
BB/c/ BA GA |

\BA G2 D2 |
\A3/2G/ F2 A,2 |
\D3 F GA |
FD [D4B,4] ::

\B,[D-G,-][DG,][D-G,-][DG,][DG,] |
\C[E-G,-][EG,][E-G,-][EG,]A, |
\B,3/2F/ GF DA, |
B,2 B,/C/B,/A,/ G,A, |

\B,[D-G,-][DG,][D-G,-][DG,][DG,] |
\C[E-G,-][EG,][E-G,-][EG,]A, |
\B,3/2F/ GF DA, |
\[D2B,2] [D4B,4] :|
\

```

---

### Post by sudodus on 2017-03-31
My script produces the following output:

```

-----------------------------------------------------------
'./abc.txt' -> 'newfiles/./abc.txt'
16,17d15
< 
< \dc B2 G2 |
21d18
< 
26d22
< 
43d38
< 
48d42
< 
53d46
< 

```

and I think it is correct. Line #17 and the blank lines are removed. There are some lines, for example line #3,4 that look blank, but there is a space character. Do you want to remove such lines too?

---

### Post by raysa on 2017-03-31
OK, it is clearly the nature of these files with their strange characters etc that's the problem.
I've just tried (why didn't I try it before? duh!) a new test text file with ordinary non-special characters, and your suggestions work perfectly, sisco and sudodus.
Is there any way I can bulk-edit these abcmusic files using sed or another approach?

---

### Post by raysa on 2017-03-31
Thanks again sudodus - we cross-posted.  Yes, lines with nothing but blank spaces should also be removed if poss.

---

### Post by raysa on 2017-03-31
I might be getting tired, but I've just tried your script again and the terminal output is as follows, showing the names of the files. And the files themselves remain unchanged.
```

ray@ray-desktop:~/Documents/Myriad Documents/Export/Music Export/Test$ ./abcbatchedit
-----------------------------------------------------------
'./A Bruxa (Am).txt' -> 'newfiles/./A Bruxa (Am).txt'
-----------------------------------------------------------
'./A Certain Smile.txt' -> 'newfiles/./A Certain Smile.txt'
-----------------------------------------------------------
'./A M Shinnie.txt' -> 'newfiles/./A M Shinnie.txt'
-----------------------------------------------------------
'./1814.txt' -> 'newfiles/./1814.txt'
-----------------------------------------------------------
'./72nds Farewell to Aberdeen, The.txt' -> 'newfiles/./72nds Farewell to Aberdeen, The.txt'
-----------------------------------------------------------
'./Albert Farmer'\''s Bonfire Tune.txt' -> 'newfiles/./Albert Farmer'\''s Bonfire Tune.txt'
-----------------------------------------------------------
'./A Jigg Ashling v2.txt' -> 'newfiles/./A Jigg Ashling v2.txt'
-----------------------------------------------------------
'./Accustomed to your face.txt' -> 'newfiles/./Accustomed to your face.txt'
-----------------------------------------------------------
'./30-ars Jiggen.txt' -> 'newfiles/./30-ars Jiggen.txt'
-----------------------------------------------------------
'./A Bruxa (Bm).txt' -> 'newfiles/./A Bruxa (Bm).txt'
-----------------------------------------------------------
'./Abbess, The.txt' -> 'newfiles/./Abbess, The.txt'
ray@ray-desktop:~/Documents/Myriad Documents/Export/Music Export/Test$ 


```

---

### Post by sudodus on 2017-03-31
The file that you gave us works. You need not remove any characters from it, and it would be easy to remove also lines with only blank characters.

If the other files are similar, there is some other problem. Either your shellscript is faulty, or your files are not linux text files, but maybe coded for Windows or MacOS. (It is possible to convert from from Windows or MacOS to linux.)

Try to copy my script from Post #13 to your editor. You can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from the code box in post #13 to your editor. In some browsers you might need ctrl+c to copy and after that ctrl+v to paste into the editor.

That way there should be no typing error. Make sure that there is a newline at the end (press the Enter key to create a new line). Save it with a suitable name.

---

### Post by sudodus on 2017-03-31
I edited the script in post #13 to remove lines with only blanks (actually with zero or more blanks /^ *$/

---

### Post by raysa on 2017-03-31
I've done exactly as you said (which is actually what I'd done before - copying your script rather than typing it) and tried again.
Again it works on a test file with no special characters in but does not change my abc music text files including the one I gave you.
So if these files are edited by the script on your system but not on mine, there must be something about them that my system doesn't like?
Mine is an all-linux system (haven't used Windows for many years, and never Mac) so I really don't know where to look to crack this mystery.
Thank you so much for the time you've been spending on this, sudodus, but I have to close down now. I'll revisit it again tomorrow when hopefully I'll be fresher, and go over all your advice again.
Thanks again.

---

### Post by sudodus on 2017-03-31
It is a good idea to rest. *After a good night's sleep you will probably see what to change to fix it.* If not, please come back here :-)

I'm running Lubuntu 16.04, which is up to date. I'm using the xenial 32-bit kernel

```
$ uname -a
Linux xenial32 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:27:09 UTC 2017 i686 i686 i686 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

```

It says 16.04.2 LTS, but It is still the kernel series 4.4, xenial. But that *should* not make any difference to your system, even if your system has a 64-bit yakkety kernel.

*It is possible that the transfer via the Ubuntu Forum post window made the difference (converted something)*. Test to copy and paste from the code window in post #17 into your favourite editor, and save it as a new file name. After that, run your copy of my script and test if it works.

---

### Post by sudodus on 2017-03-31
I found '1814' via [http://abcnotation.com](http://abcnotation.com) and in that version there are two blank lines, the first one and the last one (#1 and #17)

```

(blank)
X: 1
T: 1814
N: Nedtecknad efter en inspelning av [[Grupper/Bordunverkstan]]. Utlärd till nyckelharpsspelaren [[Personer/Magnus Holmström]] av [[Personer/Edward Anderzon]] på Eric Sahlströminstitutets nyckelharpskurs 2001.
N: Låten kommer från en notsamling som är märkt med årtalet 1814. Därav namnet. Se även +
N: -
N: Ytterligare en variant av "1814" finns i länken nedan, denna gång efter Seth Carlsson J:r, f. 1884, Strångsjö, Södermanland. Polskan överst på sidan 10 (nr. 19) i Carlssons häfte här: http://www.samlingarna.sormlandsspel.se/wp-content/uploads/2013/04/carlsson_seth_-f1.9_small.pdf . 
Z: Nils L, 2008-06-06
R: Slängpolska
M: 3/4
L: 1/16
K: G
d2c2 B4 G4 | c2B2 A4 D4 | G2>F2 G2A2 B2c2 | d2de d2c2 B2c2 |
d2c2 B4 G4 | c2B2 A4 D4 | G2>F2 G2A2 B2c2 | A2F2 G8 ::
D2D2 D2D2 D2D2 | (D2E2) E2E2 E2F2 | G2>A2 B2A2 G2F2 | G4 (DE)DC B,2C2 |
D2D2 D2D2 D2D2 | (D2E2) E2E2 E2F2 | G2>A2 B2A2 G2F2 | G4 G8 :|
(blank) 

```

and the output of my script is

```
'./1814.abc.txt' -> 'newfiles/./1814.abc.txt'
1d0
< 
17d15
< 

```

Please tell us what you intend to do with this music :-)

---

### Post by steeldriver on 2017-03-31
The most likely explanation I can think of - at least some of - your issues is that the files have DOS-style line endings (CR-LF)

They therefore don't appear empty (the apparently "empty" lines actually include a CR character)

The output of

```

file one-of-your-files.txt

```

might be enlightening

---

### Post by sudodus on 2017-04-01
I think the biggest problems would arise, if you have Mac OS (OS X) text files, because they contain no LF (line feed character), but instead a CR (carriage return character) to indicate a line break. This causes linux tools to consider it to be one single line.

See this link, [https://www.editpadpro.com/tricklinebreak.html](https://www.editpadpro.com/tricklinebreak.html)

> Windows, and DOS before it, uses a pair of CR and LF characters to terminate lines. UNIX (Including Linux and FreeBSD) uses an LF character only. OS X also uses a single LF character, but the classic Mac operating system used a single CR character for line breaks. In other words: a complete mess.

You can convert such mac os files with a linux tool, or with the following command line using ***tr***

```
< mac.txt tr '\015' '\n' > linux-from-mac.txt
```

where  **'\015'** is octal (8+5) octal = 13 decimal, alias ctrl M, alias carriage return, and **'\n'** is line feed.

But use another tool or command line to convert Windows text files, for example

```
< win.txt sed 's/\r$//' > linux-from-win.txt
```

where **'\r'** is carriage return.

-o-

Another question: ***Are you sure that line #17 should always be deleted?*** Some abc files that I have looked at via the internet seem to have useful information at that position.

---

### Post by raysa on 2017-04-01
Thank you all for your help ... problem now solved (well, almost). After looking at the files in more detail, and doing some experimenting, I discovered what the problem was: The text files I was trying to edit had CR line-end characters. When I changed this to LF the script and the sed commands worked fine. 

I then came back here and saw steeldriver's post - spot on! These files were exported from a music notation programme and I can't control the export parameters, so I guess that's how the unhelpful line-endings were generated (I didn't know they were DOS-type, steeldriver - thanks).

_So the next question is_: Is there a way of converting a whole load of text files from CR to LF line-endings in one go?  I have a project to convert some 2,500 musical scores and I haven't got enough years left in me to do 'em individually!

PS: thanks for interest in my purpose, sudodus.  I play in a band and we have accumulated a huge number of tunes over the years which we have notated, many of them with original arrangements. We've made pdfs of them available on our website [http://www.rudemex.co.uk]("http://www.rudemex.co.uk"), but the abc music notation is very popular and we have been asked if we can make the collection available in that format.

---

### Post by raysa on 2017-04-01
Oh - cross-posted, sudodus.  Thanks.  I converted a couple of test files with the Skite text editor which has a facility for changing line-endings, but doesn't seem to have a bulk-editing facility.

---

### Post by sudodus on 2017-04-01
You can use command lines like in post #28 to fix it in a shellscript file for the whole batch of files. I think it is a good idea to create copies and do it with the copies. Do not take the risk of damaging the original files.

Good luck with your band and your music website :-)

(I used to dance folk dances, so I recognize the background information about 1814.)

Edit: You can also use mac2unix, which converts inline with

```
$ mac2unix mac.txt
```

and creates a new file with the -n option

```
$ [COLOR="#0000FF"]mac2unix -n mac.txt linux-from-mac.txt[/COLOR]
mac2unix: converting file mac.txt to file linux-from-mac.txt in Unix format ...
```

Install ```
sudo apt-get install dos2unix
``` to use mac2unix or dos2unix

---

### Post by raysa on 2017-04-01
Just seen your edit to #28, sudodus, thanks.  The mac one worked, although I had to take all spaces out of the filenames of the couple I tried.  Is there a way of applying this code to a whole load of files to convert them to CR to LR, and without having the change filenames where they include spaces?

I'm conscious of, and feeling a rather guilty about, the amount of time you're giving me on this ... I'll quite understand if you decide I've had enough of your attention.

Re line 17 ... this was just an example for testing purposes, but there are lines which do need removing across the whole collection of files. They are produced - same in every file - by the exporting process from the notation package. They are unnecessary for the tunes and might be problematic in some abc printing processes.

---

### Post by raysa on 2017-04-01
Oh - cross-posted again.  Thanks.

---

### Post by sudodus on 2017-04-01
I think you are doing something good, and I am happy to help you :-)

If you use **mac2unix**, you can use a command line with **find ... -exec** and it will work with special characters (spaces etc) in the file names. Do you need detailed help?

-o-

By the way, there is a folk music festival, 'spelmansstämma' in my home village, the Church Town of Gammelstad, in June. See these links

[Gammelstads Spelmansstämma 16 - 18 juni 2017](http://www.spelmansstamman.se/spelmansstamman_2017/index.html)

[This will be played together (a pdf-file)](http://www.spelmansstamman.se/spelmansstamman_2017/bilder/allspel2016.pdf)

---

### Post by raysa on 2017-04-01
Many thanks again, sudodus.  What a lovely set of tunes in your post!  We are very fond of Swedish music - indeed the vast majority of the tunes in the "Scandinavian" section of our website are Swedish. Whenever we perform we always include a few Swedish tunes. One of the band members plays the nyckelharpa and we find that his harpa and my English concertina work together very well. In fact the harpa player is currently in Sweden visiting his daughter - in Gothenburg, opposite ends of the country from your village.  When he returns next week I am sure we'll be running through the tunes you sent and maybe adding some to our repertoire.

Thanks for saying my project is good. Many people find our website tune library very helpful - a lot of traditional players here in Sussex, UK, and some a good deal further afield, use it as resource, but making it available for abc users would certainly extend its usefulness.

But back to the conversion issue ... I've installed dos2unix as suggested, and I'm very attracted to the idea of a script that would achieve the necessary edits for the whole batch in a folder. If the three ingredients could be included in the script: removing any blank lines; removing particular lines that I can specify before running; and ensuring the LF character is right throughout - this would be brilliant.

You very kindly asked if I needed further detailed help ... my experience of shellscript writing is nil, so if you could add the line-feed thing to the script you've already done for removing lines, that would be wonderful.  

And there's one other task needed in all this, although I don't know if it's at all achievable within this script solution.  The music notation application that exports the abc text files does not capture the tune title from the separate notation package in which the tunes were originally notated - so the titles don't get exported in the abc text. The filenames are always the tune title, so the task is to read the filename and then insert it - After "T:" - as the second line of the abc file, if possible losing the filename extension. I have reason to believe that a contact of ours in America can probably achieve this with a quite separate process, so if it's not possible (or too time-consuming), to include it in the current scripting, please don't worry.  But it would obviously be much neater to do it all in the one sweep.

Many thanks again for your kind interest and help.

---

### Post by sudodus on 2017-04-01
I'm glad you like the 'allspels' tunes from our spelmansstämma :-)

I will look into this and try to make a good shellscript for you.

---

### Post by raysa on 2017-04-01
Brilliant - thank you!  In the meantime I shall now run through some of your 'allspels' tune on the concertina or flute.

---

### Post by sudodus on 2017-04-01
I hope that this script will work for you. Please try it and report the result. It will process the files in the current directory and write the converted files in the subdirectory 'newfiles'.

Main script 'fix-abc':

```

#!/bin/bash

if [ $# -lt 2 ]
then
 echo "Usage:    $0 \"target file pattern\" <line number to delete> <debug>"
 echo "Example:  $0  \"*.abc\" 17 debug"
 echo "See the log file '${0##*/}.log'"
 exit
fi

mkdir -p newfiles

if [ "$3" == "debug" ]
then
 find . -maxdepth 1 -type f -name "$1" \
 -exec echo "-----------------------------------------------------------" \; \
 -exec cp -pv {} newfiles/{} \; \
 -exec dos2unix -q newfiles/{} \; \
 -exec mac2unix -q newfiles/{} \; \
 -exec ./enter-name {} \; \
 -exec sed -i -e "$2 d" -e '/^ *$/ d' newfiles/{} \; \
 -exec diff {} newfiles \; | tee "${0##*/}.log"
else
 find . -maxdepth 1 -type f -name "$1" \
 -exec cp -pv {} newfiles/{} \; \
 -exec dos2unix -q newfiles/{} \; \
 -exec mac2unix -q newfiles/{} \; \
 -exec ./enter-name {} \; \
 -exec sed -i -e "$2 d" -e '/^ *$/ d' newfiles/{} \; \
 | tee "${0##*/}.log"
fi

```

Subscript 'enter-name':

```

#!/bin/bash

#echo "start $0 $1"

mkdir -p newfiles
if ! test -s "newfiles/$1"
then
 cp -pi "$1" newfiles
fi

if test -s "$1"
then
 name="${1/.abc}"
 name="${name/.txt}"
 name="${name/.\/}"
 if [ "$name" == "" ]
 then
  name="$1"
 fi
 sed -si "s#^T:.*#T: $name#" "newfiles/$1"
else
 echo "No such file"
fi

#echo "finish $0 $1"

```

***Edit:*** I fixed a bug in the main script (second edit), moved call of ./enter-name to after call of dos2unix and mac2unix.

---

### Post by sudodus on 2017-04-01
Fixed :-)

I think that it will work now, including adding the name to the line starting with **T:**

---

### Post by raysa on 2017-04-01
Many thanks sudosu.  I copied the script into a file called abcbatchedit and made it executable, then ran it in a directory containing several of the abc files. In the terminal I got the three echo lines:
```

Test$ ./abcbatchedit
Usage:    ./abcbatchedit "target file pattern" <line number to delete> <debug>
Example:  ./abcbatchedit  "*.abc" 17 debug
See the log file 'abcbatchedit.log'

```
But nothing else happened and the new directory didn't appear.  Should I have done something else? (I told you my experience with scripts is nil!)

---

### Post by raysa on 2017-04-01
Oh - cross-posting again.  How do I add the sub-script - just tag it on after the main bit in the script file?

---

### Post by The Cog on 2017-04-01
I think this one-liner should convert all your *.txt files with mac line endings to *nix line endings and remove blank lines at the same time:
```
sed -i 's/\x0d\x0d*/\n/g' *txt
```

---

### Post by raysa on 2017-04-01
Yes, it achieves both those things successfully, Cog, thank you. Can you extend that to also remove lines which are empty except for blank spaces?

Sudodu: does this simplify the first part of what you've suggested?

Thanks both.

---

### Post by sudodus on 2017-04-01
> **raysa said:**
> Many thanks sudosu.  I copied the script into a file called abcbatchedit and made it executable, then ran it in a directory containing several of the abc files. In the terminal I got the three echo lines:
```

Test$ ./abcbatchedit
Usage:    ./abcbatchedit "target file pattern" <line number to delete> [debug (optional parameter)]
Example:  ./abcbatchedit  "*.abc" 17 debug
See the log file 'abcbatchedit.log'

```
But nothing else happened and the new directory didn't appear.  Should I have done something else? (I told you my experience with scripts is nil!)

You need the other script file 'enter-name' in the same directory and it should also have execute permissions. That script fixes the name (and strips the .abc or .txt extension).

Read the output: You need parameters now:

```
./abcbatchedit "*.txt" 17
```

if you want to convert files with the extension .txt and delete line #17.

---

### Post by The Cog on 2017-04-01
> **raysa said:**
> Yes, it achieves both those things successfully, Cog, thank you. Can you extend that to also remove lines which are empty except for blank spaces?

Sudodu: does this simplify the first part of what you've suggested?

Thanks both.
try this:
```
sed -i 's/\x0d[\x0d ]*/\n/g' *txt
```
Replace CR followed by any number of CR or space characters with a single newline.

---

### Post by raysa on 2017-04-01
Sudodus, the filename bit doesn't seem to be working here. It creates the newfiles directory but without files in it.

---

### Post by raysa on 2017-04-01
The Cog: Yes the line in #45 combines the three tasks of removing blank lines, removing lines with spaces, and converting CR to LF.  Great - thanks.

---

### Post by sudodus on 2017-04-01
> **raysa said:**
> Sudodus, the filename bit doesn't seem to be working here. It creates the newfiles directory but without files in it.

The filename bit is supposed to be called by the main script, with the name **abcbatchedit**, so if you give the name **enter-name** to the filename bit, and keep it in the same directory as the files you want to convert and **abcbatchedit**, it will be found and used when you run for example

```
./abcbatchedit "*.txt" 17
```

or

```
./abcbatchedit "*.abc" 12
```

if your files have the files have the extension .abc and you want to delete line #12. If you don't want to delete any line, you can enter a high number, higher than the number of lines you would find in any file, for example 9999.

***Edit:*** the filename bit is not intended to run separately, but run as a help program when you run the main script, **abcbatchedit**

---

### Post by raysa on 2017-04-01
Great, we're so nearly there, sudodus. All works now except the new files don't have the title in the T: line. Everything else achieved - blank lines gone, LF as they should be, etc.

---

### Post by sudodus on 2017-04-01
When you get enter-name working correctly, the name will be there. It works for me.

***I have attached a small tarball that you can download and extract somewhere.*** It will create the directory abc-testdir with six files. You can use it for testing purposes, to find how things should work.

```

$ [COLOR="#0000FF"]tar -xvzf abc-test.tar.gz[/COLOR] 
abc-testdir/
abc-testdir/script
abc-testdir/1814.abc.txt
abc-testdir/abc.txt
abc-testdir/mac-abc.txt
abc-testdir/Artonhundrafjorton.abc
abc-testdir/enter-name
$ [COLOR="#0000FF"]cd abc-testdir/[/COLOR]
$ [COLOR="#0000FF"]ls[/COLOR]
1814.abc.txt  abc.txt  mac-abc.txt Artonhundrafjorton.abc  [COLOR="#00bb00"]enter-name  script[/COLOR]
$ [COLOR="#0000FF"]./script "*abc*" 17[/COLOR]
'./1814.abc.txt' -> 'newfiles/./1814.abc.txt'
'./abc.txt' -> 'newfiles/./abc.txt'
'./mac-abc.txt' -> 'newfiles/./mac-abc.txt'
'./Artonhundrafjorton.abc' -> 'newfiles/./Artonhundrafjorton.abc'
$ [COLOR="#0000FF"]./script "*abc*" 17 debug[/COLOR]
-----------------------------------------------------------
'./1814.abc.txt' -> 'newfiles/./1814.abc.txt'
1d0
< 
17d15
< 
-----------------------------------------------------------
'./abc.txt' -> 'newfiles/./abc.txt'
2,4c2
< T:     %Tune name
<  
<  
---
> **[COLOR="#cc0000"]T: abc[/COLOR]**
16,17d13
< 
< \dc B2 G2 |
21d16
< 
26d20
< 
43d36
< 
48d40
< 
53d44
< 
-----------------------------------------------------------
'./mac-abc.txt' -> 'newfiles/./mac-abc.txt'
1c1,49
\[D2B,2] [D4B,4] :|-][EG,]A, |,] |] |
\ Ingen nyrad vid filslut
---
> X:1     %Music
> **[COLOR="#cc0000"]T: mac-abc[/COLOR]**
> V:1     %
>      %!STAVE 0 '' @
>      %!INSTR 'Staff 1' 0 0 @
> |:
> M:3/4     %Meter
> L:1/8     %
> K:G
> \"G"dc B2 G2 |
> \"D"c3/2B/ A2 D2 |
> \"G"G3/2F/ GA Bc |
> dd/e/ dc Bc |
> \"D"c3/2B/ A2 D2 |
> \"G"G3/2F/ GA Bc |
> "D"AF "G"G4 ::
> \"G"B,[D-B,-][DB,][D-B,-][DB,][DB,] |
> \"C"C[E-C-][EC][E-C-][EC]F |
> \"G"G3/2A/ BA "D"GF |
> "G"G2 D/E/D/C/ "D"B,A, |
> \"G"B,[D-B,-][DB,][D-B,-][DB,][DB,] |
> \"C"C[E-C-][EC][E-C-][EC]F |
> \[G3/2"G"G,3/2]A/ BA "D"GF |
> \"G"G2 G4 :|
> \
> V:2     %
>      %!STAVE 0 '' @
>      %!INSTR 'Staff 2' 0 0 @
> |:
> M:3/4     %Meter
> L:1/8     %
> K:G
> \BA G2 D2 |
> \A3/2G/ F2 A,2 |
> \D3 F GA |
> BB/c/ BA GA |
> \BA G2 D2 |
> \A3/2G/ F2 A,2 |
> \D3 F GA |
> FD [D4B,4] ::
> \B,[D-G,-][DG,][D-G,-][DG,][DG,] |
> \C[E-G,-][EG,][E-G,-][EG,]A, |
> \B,3/2F/ GF DA, |
> B,2 B,/C/B,/A,/ G,A, |
> \B,[D-G,-][DG,][D-G,-][DG,][DG,] |
> \C[E-G,-][EG,][E-G,-][EG,]A, |
> \B,3/2F/ GF DA, |
> \[D2B,2] [D4B,4] :|
> \
-----------------------------------------------------------
'./Artonhundrafjorton.abc' -> 'newfiles/./Artonhundrafjorton.abc'
1d0
< 
3c2
< T: 1814
---
> **[COLOR="#cc0000"]T: Artonhundrafjorton[/COLOR]**
17d15
< 
$ [COLOR="#0000FF"]diff newfiles/abc.txt newfiles/mac-abc.txt[/COLOR] 
2c2
< T: abc
---
> **[COLOR="#cc0000"]T: mac-abc[/COLOR]**

```

Please scroll the code window to see that the title is modified (**[COLOR="#cc0000"]bold red[/COLOR]**) except for 1814, where the title was already there in the original file. 'Artonhundrafjorton' is 1814 in Swedish.

***Edit:*** I fixed a bug and uploaded a modified tarball. Please try the current tarball.

---

### Post by sudodus on 2017-04-02
I fixed a bug and uploaded a modfied tarball. I moved the call of ./enter-name to after the calls of dos2unix and mac2unix.

You should also modify your main shellscript file. Use the version in the tarball, or copy it from post #38.

---

### Post by raysa on 2017-04-02
Sudodus - you're a star!  Everything is working well here now - thank you so much for all the time and effort you've put it.  Thanks to the other contributors, too - the sed one-liners will certainly be very useful on some occasions. I've learnt a great deal and not only achieved solutions but also gained some lovely Swedish tunes!

My next task - the one that prompted this endeavour - is to convert some 2,500 tunes from the notation software they were originally written in to the popular abc music format, and make them available publicly from the tune library (currently just pdf) of my band's website [http://www.rudemex.co.uk]("http://www.rudemex.co.uk"). This won't be immediate because there's a bug in the intermediate commercial application which does the initial music notation transfer, but I'm assured this will be fixed in a new version due out shortly.  Then I'll be expanding our tune library with the abc versions - and a lot of musicians will be very grateful for the help I've received on this forum.

Thanks again all, and best wishes. :D:D

---

### Post by sudodus on 2017-04-02
I'm glad that I could help, and good luck :-({|=

Please remember to come back to this thread, when you have uploaded the converted files, and tell us about it!

---

