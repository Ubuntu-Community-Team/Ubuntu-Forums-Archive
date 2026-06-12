---
title: "cat Japanese text file"
date: 2012-11-18
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]When I ls the contents of a directory with Japanese filenames it works perfectly fine,
```

ls
$read            oto.ini      &#12354;_wav.frq    &#12360;.wav
Mattithyahu.bmp  readme.txt   &#12356;.wav        &#12360;_wav.frq
New Project.ust  &#12354;.wav        &#12356;.wav.uspec  &#12422;.wav
character.txt    &#12354;.wav.uspec  &#12356;_wav.frq    &#12422;_wav.frq

```but when I cat a text file with Japanese characters (the very same ones) it gives me these replacement characters.
```

cat oto.ini
&#65533;&#65533;.wav=a,0,0,0,0,0
&#65533;&#65533;.wav=i,0,0,0,0,0
&#65533;&#65533;.wav=e,0,0,0,0,0
&#65533;&#65533;.wav=yu,0,0,0,0,0

```I tried setting the language to Japanese (have to do this with a few of my programs) but it still gives me the same results.
```

LANG=ja_JP.utf8 cat oto.ini
&#65533;&#65533;.wav=a,0,0,0,0,0
&#65533;&#65533;.wav=i,0,0,0,0,0
&#65533;&#65533;.wav=e,0,0,0,0,0
&#65533;&#65533;.wav=yu,0,0,0,0,0

```It *should* read as
```

&#12354;.wav=a,0,0,0,0,0
&#12356;.wav=i,0,0,0,0,0
&#12360;.wav=e,0,0,0,0,0
&#12422;.wav=yu,0,0,0,0,0
```Does anyone know how to fix this issue?[/FONT] [FONT=Courier New]
[/FONT]

---

### Post by The Cog on 2012-11-18
Do you know what character encoding the text files are using? 

It might help to see the actual file contents, just a snippet with this command would help:
```
cat oto.ini | hd | head
```

P.S.
That character is apparently HIRAGANA LETTER A, unicode value 0x3042 which in UTF8 encoding would be three bytes 0xE3 0x81 0x82.

---

### Post by Vaphell on 2012-11-18
the question is does the .ini file have utf8 encoding?

```
$ echo "&#12356;"  | od -x
0000000 81e3 0a84
0000004
$ echo "&#12356;" > jp.txt
$ cat jp.txt
&#12356;
$ cat jp.txt | od -x
0000000 81e3 0a84
0000004
```

---

### Post by ntzrmtthihu777 on 2012-11-18
> **The Cog said:**
> Do you know what character encoding the text files are using? 

It might help to see the actual file contents, just a snippet with this command would help:
cat oto.ini | hd | head
[FONT=Courier New]First off, thank you for this interesting new trick you taught me! Hehe, it would be very useful to a project I had on the back burner.

Second, the encoding is Japanese (SHIFT_JIS), can I set it to this with LANG=? or something similar?

[/FONT]
[FONT=Courier New]```
cat oto.ini | hd | head
00000000  82 a0 2e 77 61 76 3d 61  2c 30 2c 30 2c 30 2c 30  |...wav=a,0,0,0,0|
00000010  2c 30 0d 0a 82 a2 2e 77  61 76 3d 69 2c 30 2c 30  |,0.....wav=i,0,0|
00000020  2c 30 2c 30 2c 30 0d 0a  82 a6 2e 77 61 76 3d 65  |,0,0,0.....wav=e|
00000030  2c 30 2c 30 2c 30 2c 30  2c 30 0d 0a 82 e4 2e 77  |,0,0,0,0,0.....w|
00000040  61 76 3d 79 75 2c 30 2c  30 2c 30 2c 30 2c 30 0d  |av=yu,0,0,0,0,0.|
00000050  0a                                                |.|
00000051

```[/FONT]

---

### Post by ntzrmtthihu777 on 2012-11-18
> **The Cog said:**
> P.S.
That character is apparently HIRAGANA LETTER A, unicode value 0x3042 which in UTF8 encoding would be three bytes 0xE3 0x81 0x82.
Yes that is a hiragana 'a', how did you tell? By searching for &#12354; or did you figure it out from the apparently useless &#65533;&#65533; character? And can I still use this info in a shell script? What I am actually trying to achieve is create a "Voicebank Aliaser" for Ubuntu/linux UTAU users.
Basically oto.ini contains info on all the wav files for a certain voicebank, and also any "aliases" they may have, in my example &#12354;.wav is aliased to a.wav.
What I eventually want to achieve is a simple script that will look at
a.wav=,#,#,#,#,# and recognize that a = &#12354;, and alias it to that, like
a.wav=&#12354;,#,#,#,#,# and also the reverse.
&#12354;.wav=,#,#,#,#,# &#12354; = a
&#12354;.wav=a,#,#,#,#,#

---

### Post by Vaphell on 2012-11-18
you can use **iconv -f SHIFT_JIS -t UTF-8** to convert the file.

---

### Post by ntzrmtthihu777 on 2012-11-18
> **Vaphell said:**
> you can use **iconv -f SHIFT_JIS -t UTF-8** to convert the file.
Very interesting! Does this actually change the file itself or just allows its contents to be displayed properly in terminal? Because the program that uses the oto.ini file may require the SHIFT_JIS encoding.

---

### Post by The Cog on 2012-11-18
> **ntzrmtthihu777 said:**
> Yes that is a hiragana 'a', how did you tell? 
I did this command:
```
echo &#12354; | hd
```
(copy/paste the character from the browser to the command prompt). That tells me the character is encoded as e3 81 82.
Equally, I could start python and paste the quoted character there (my typing is in bold):
```
$ **python**
Python 2.7.3 (default, Sep 26 2012, 21:53:58) 
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> **'&#12354;'**
'\xe3\x81\x82'

```
To get the unicode value from that, I tell python to decode the utf8 bytes (2 ways shown):
```
>>> '&#12354;'.decode("utf8")
u'\u3042'
>>> "\xe3\x81\x82".decode("utf8")
u'\u3042'

```
then I used the Character Map program supplied with Ubuntu. It's under Accesories in the Xubuntu start menu. Just looked it up in there.

I don't know how to convert easily, so I will bow to Vaphell on that subject.

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]Very nice trick, that. For the most part I don't need it for what I do, have a very nice Japanese input method set up (anthy and iBus), but still a very cool trick.[/FONT]

---

### Post by Vaphell on 2012-11-18
> Very interesting! Does this actually change the file itself or just allows its contents to be displayed properly in terminal? Because the program that uses the oto.ini file may require the SHIFT_JIS encoding.

not that i converted anything in my life using that tool, but short test shows that it merely prints out the converted content and the original file stays intact.

so what do you want to achieve exactly with these synonyms? you want to create symlinks pointing to real .wav files or what?

---

### Post by ntzrmtthihu777 on 2012-11-18
> **Vaphell said:**
> not that i converted anything in my life using that tool, but short test shows that it merely prints out the converted content and the original file stays intact.

so what do you want to achieve exactly with these synonyms? you want to create symlinks pointing to real .wav files or what?
[FONT=Courier New]Basically the way it works is you place notes, either hiragana or romaji (Roman letters) on the screen, and tell it what voicebank (collection of *.wav files and oto.ini) to use. If you place hiragana notes but use a voicebank with romaji *.wav files, a properly aliased oto.ini should point &#12354; to a.wav (and same for romaji notes and a hiragana voicebank, points a to &#12354;.wav), no need to create Linux symlinks.

The reason I needed to figure this out proper is I want to create a automatic aliaser script, probably using sed. See, a good voicebank can have an upwards of 300 lines, and manually aliasing them all is quite tedious. There are already windows batch files that do this, but I am developing tools for UTAU users on ubuntu. Wrote a tutorial on how to install UTAU (a Japanese windows .exe) on a non-Japanese ubuntu install, and how to properly unzip voicebanks with Japanese folder and/or file names (using the default file-roller or archive mounter gives gibberish names).
[/FONT]

---

### Post by Vaphell on 2012-11-18
so what's the input for that automatic aliaser script and what's the expected output?

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]Input 1 (going to have 2, I think. One to do this)
```

&#12354;.wav=,0,0,0,0,0
&#12356;.wav=,0,0,0,0,0
&#12358;.wav=,0,0,0,0,0
&#12360;.wav=,0,0,0,0,0
&#12362;.wav=,0,0,0,0,0
```Output 1
```

&#12354;.wav=a,0,0,0,0,0
&#12356;.wav=i,0,0,0,0,0
&#12358;.wav=u,0,0,0,0,0
&#12360;.wav=e,0,0,0,0,0
&#12362;.wav=o,0,0,0,0,0
```Input 2 (and one to do this)
```

a.wav=,0,0,0,0,0
i.wav=,0,0,0,0,0
u.wav=,0,0,0,0,0
e.wav=,0,0,0,0,0
o.wav=,0,0,0,0,0

```Output 2[/FONT]        [FONT=Courier New]
```

a.wav=&#12354;,0,0,0,0,0
i.wav=&#12356;,0,0,0,0,0
u.wav=&#12358;,0,0,0,0,0
e.wav=&#12360;,0,0,0,0,0
o.wav=&#12362;,0,0,0,0,0

```I think
```
sed 's/a.wav=/a.wav=&#12354;/'
```and so on would do the trick, make a sedscript with all the equivalents and run 
```
sed -f sedscript oto.ini
```would be what is called for, yes?

This may not seem to be too much work to do manually, but I am only showing a small portion of what a full oto.ini file would contain. As I said, a good bank would have at least 120-ish just to cover Japanese syllables, and a few are multilingual, so lists of over 300 are not uncommon.
[/FONT]

---

### Post by Vaphell on 2012-11-18
but i don't see from where the script should get the info that a=&#12354;, i=&#12356;, etc
if you had a tidy list of synonyms, it would be rather easy to generate these files.

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]> **Vaphell said:**
> but i don't see from where the script should get the info that a=&#12354;, i=&#12356;, etc
if you had a tidy list of synonyms, it would be rather easy to generate these files.
I was thinking along [these](http://www.grymoire.com/Unix/Sed.html#uh-16) lines, have 2 files: 

hira_roma containing:
```

s/&#12354;.wav=/&#12354;.wav=a/g
s/&#12356;.wav=/&#12356;.wav=i/g
s/&#12358;.wav=/&#12358;.wav=u/g
s/&#12360;.wav=/&#12360;.wav=e/g
s/&#12362;.wav=/&#12362;.wav=o/g
...
```

roma_hira containing:
```

s/a.wav=/a.wav=&#12354;/g
s/i.wav=/i.wav=&#12356;/g
s/u.wav=/u.wav=&#12358;/g
s/e.wav=/e.wav=&#12360;/g
s/o.wav=/o.wav=&#12362;/g
...
```

And running
[/FONT][FONT=Courier New]```
sed -f roma_hira oto.ini

```or
```
sed -f hira_roma oto.ini

```[/FONT][FONT=Courier New]as needed, assuming oto.ini is in the same dir.
[/FONT]

---

### Post by Vaphell on 2012-11-18
awk would be much better

consider this example:
```
$ cat syn.txt 
a &#12354;
i &#12356;
u &#12358;
e &#12360;
o &#12362;
$ awk '{ printf("%s.wav=%s,0,0,0,0,0\n", $1, $2); }' syn.txt
a.wav=&#12354;,0,0,0,0,0
i.wav=&#12356;,0,0,0,0,0
u.wav=&#12358;,0,0,0,0,0
e.wav=&#12360;,0,0,0,0,0
o.wav=&#12362;,0,0,0,0,0
$ awk '{ printf("%s.wav=%s,0,0,0,0,0\n", $2, $1); }' syn.txt
&#12354;.wav=a,0,0,0,0,0
&#12356;.wav=i,0,0,0,0,0
&#12358;.wav=u,0,0,0,0,0
&#12360;.wav=e,0,0,0,0,0
&#12362;.wav=o,0,0,0,0,0
```
pipe to iconv to convert to SHIFT_JIS, dump the result to a file and it's done

even pure bash can do it:
```
$ while read -r a b; do echo "$a.wav=$b,0,0,0,0,0"; done < syn.txt
a.wav=&#12354;,0,0,0,0,0
i.wav=&#12356;,0,0,0,0,0
u.wav=&#12358;,0,0,0,0,0
e.wav=&#12360;,0,0,0,0,0
o.wav=&#12362;,0,0,0,0,0
$ while read -r a b; do echo "$b.wav=$a,0,0,0,0,0"; done < syn.txt
&#12354;.wav=a,0,0,0,0,0
&#12356;.wav=i,0,0,0,0,0
&#12358;.wav=u,0,0,0,0,0
&#12360;.wav=e,0,0,0,0,0
&#12362;.wav=o,0,0,0,0,0
```

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]Very interesting... I have used awk for a few personal projects, very nice use here. But, I have just considered what may be a hitch using my old scheme and was about to post it, but then I saw yours and it may have a similar problem...

Suppose this oto.ini is already partially aliased, say:[/FONT] [FONT=Courier New]        

```
[/FONT] [FONT=Courier New]
a.wav=&#12354;,0,0,0,0,0
i.wav=,0,0,0,0,0
u.wav=&#12358;,0,0,0,0,0
e.wav=,0,0,0,0,0
o.wav=&#12362;,0,0,0,0,0
```Wouldn't using either of our scripts give us   

```
[/FONT] [FONT=Courier New]
a.wav=&#12354;&#12354;,0,0,0,0,0
i.wav= &#12356;,0,0,0,0,0
u.wav=&#12358;&#12358; ,0,0,0,0,0
e.wav= &#12360;,0,0,0,0,0
o.wav= &#12362;&#12362;,0,0,0,0,0
```
?  
I was thinking extending the sed to: 
```
s/a.wav=*,/a.wav=&#12354;,/g
```unless your know of a better solution.

Also, an actual oto.ini would have numbers other than 0 depending on the frequency of the sound, length of the consonant or vowel, and other info, so merely creating them out of thin air with the awk example would only be useful when creating a brand new bank which default to ,0,0,0,0,0 or ,,,,, anyway. And each bank has its own more or less unique oto.ini. Creating the initial one is done by the program itself, its just aliasing that takes a bit. I am looking to modify an existing oto.ini, sorry if I was not 100% clear on that from the start. [/FONT] [FONT=Courier New]
[/FONT]

---

### Post by Vaphell on 2012-11-18
my code created the output from scratch using template line
PUT_STUFF_HERE.wav=PUT_STUFF_HERE,0,0,0,0,0
but those changing numbers you speak of make that approach go out the window

duplicated symbols you mentioned are easy to fix - simply strip anything between = and , before doing substitutions.

can you give few example lines of real data (or even full oto.ini) so i can get full picture

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]```

a.wav=‚ ,54,105,348,36,17 
ad.wav=,8,133,155,79,39 
ah.wav=,80,97,318,39,14 
ai.wav=,64,132,284,57,31 
al.wav=,303,109,152,33,10 
all.wav=,270,118,168,32,18 
am.wav=,27,74,19,23,11 
an.wav=,63,75,307,26,10 
and.wav=,209,80,297,33,13 
ang.wav=,110,74,352,24,11 

```A few of these will not have a hiragana equivalent, but again some of these banks are designed to be multilingual.
[/FONT]

---

### Post by Vaphell on 2012-11-18
i think sed -f is a good approach but i'd generate these sed files too, based on the clean list to make it easier to introduce changes, should the need arise.
 
```
#!/bin/bash

while read -r a b
do
  echo "s/^$a[.]wav=[^,]*,/$a.wav=$b,/"
done < syn.txt > sed1.txt

while read -r a b
do
  echo "s/^$a[.]wav=[^,]*,/$b.wav=$a,/"
done < syn.txt > sed2.txt

echo
echo "Sed #1"
sed -f sed1.txt oto.txt # | iconv -f UTF-8 -t SHIFT_JIS > output1.txt
echo "Sed #2"
sed -f sed2.txt oto.txt # | iconv -f UTF-8 -t SHIFT_JIS > output2.txt
```

example, using trash data ;-)
```
**$ cat syn.txt**
a XoXo
ad !!!
ah ###
ai ===
al ---
all @@@
am FFUU-
an -_-
and o.O
ang >_<
**$ ./jp.sh **
Sed #1
a.wav=XoXo,54,105,348,36,17 
ad.wav=!!!,8,133,155,79,39 
ah.wav=###,80,97,318,39,14 
ai.wav====,64,132,284,57,31 
al.wav=---,303,109,152,33,10 
all.wav=@@@,270,118,168,32,18 
am.wav=FFUU-,27,74,19,23,11 
an.wav=-_-,63,75,307,26,10 
and.wav=o.O,209,80,297,33,13 
ang.wav=>_<,110,74,352,24,11
Sed #2
XoXo.wav=a,54,105,348,36,17 
!!!.wav=ad,8,133,155,79,39 
###.wav=ah,80,97,318,39,14 
===.wav=ai,64,132,284,57,31 
---.wav=al,303,109,152,33,10 
@@@.wav=all,270,118,168,32,18 
FFUU-.wav=am,27,74,19,23,11 
-_-.wav=an,63,75,307,26,10 
o.O.wav=and,209,80,297,33,13 
>_<.wav=ang,110,74,352,24,11

```

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]Hmm... yes I just ran my example on a dupe oto.ini so as not to ruin the real thing if it goes horridly wrong >.< and it would have, lol.
There are a number of Japanese characters whose romaji equivalent would match a few search strings, such as
[/FONT]```
sha.wav=,0,0,0,0,0

```[FONT=Courier New] matches all three of these search strings:
[/FONT]```

s/a.wav=,/a.wav=&#12354;,/g
s/ha.wav=,/ha.wav=&#12399;,/g
s/sha.wav=,/sha.wav=&#12375;&#12419;,/g

```[FONT=Courier New]So how could confusion be prevented in this matter?

[NOTE]
The reverse is not totally true, the same example (but instead from hiragana to romaji) would not have many issues:
[/FONT]```
&#12375;&#12419;.wav=,0,0,0,0,0
```[FONT=Courier New]
does not match
[/FONT]```
s/&#12354;.wav=,/&#12354;.wav=a,/g
s/&#12399;.wav=,/&#12399;.wav=ha,/g
s/&#12375;&#12419;.wav=,/&#12375;&#12419;.wav=sha,/g

```

[FONT=Courier New]Though they are the same in reverse.[/FONT]

---

### Post by Vaphell on 2012-11-18
add ^ to your regex to signal you want to match from start, not anywhere

did you try my script? finetuning s/// expressions by hand for few hundred pairs would be ungodly tedious.

---

### Post by ntzrmtthihu777 on 2012-11-18
[FONT=Courier New]
[/FONT][LEFT][FONT=Courier New]No, I have not tried it yet, in the middle of a couple of things, >.<
I actually intend to use your original awk script to generate the s/// expressions for me, as it can easily be done with:```
[/FONT][LEFT][FONT=Courier New]$ cat syn.txt
a &#12354;
i &#12356;
u &#12358;
e &#12360;
o &#12362;
$ awk '{ printf("s/%s.wav=,/%s.wav=%s,/g\n", $1, $1, $2); }' syn.txt
$ awk '{ printf("s/%s.wav=,/%s.wav=%s,/g\n", $2, $2, $1); }' syn.txt 
[/FONT][/LEFT]
[FONT=Courier New]
```

If my grasp of awk is correct this should give me the expressions I need, correct?
Also, where exactly would the ^ go? still a bit of a linux n00b, but loving every thing I learn, lol.
[/FONT][/LEFT]

---

### Post by Vaphell on 2012-11-18
oh ok, my script uses pure bash to generate but the result will be pretty much identical.

```
printf("s/[COLOR="Blue"]^[/COLOR]%s.wav=,/%s.wav=%s,/g\n", $1, $1, $2);
```

---

### Post by ntzrmtthihu777 on 2012-11-18
> **Vaphell said:**
> oh ok, my script uses pure bash to generate but the result will be pretty much identical.

```
printf("s/[COLOR=Blue]^[/COLOR]%s.wav=,/%s.wav=%s,/g\n", $1, $1, $2);
```[FONT=Courier New]
Ah, thank you so much! I basically want it the way I was describing (two files you use for sed) to mirror an existing Windows alias tool in order to be more familiar to UTAU users. Many thanks, my friend.[/FONT]

---

### Post by ntzrmtthihu777 on 2012-11-19
[FONT=Courier New]Having an issue with my script and yours, Vaphell.
The iconv is returning an error message, yours at position 6 and mine at 78** or some such number. Any tips?
[/FONT]

---

### Post by Vaphell on 2012-11-19
i guess the problem is that the original file is in SHIFT_JIS and the script doesn't take that into account

try this:
```
iconv -f SHIFT_JIS -t UTF-8 oto.txt | sed -f sed1.txt | iconv -f UTF-8 -t SHIFT_JIS > output1.txt
```

---

### Post by ntzrmtthihu777 on 2012-11-19
> **Vaphell said:**
> i guess the problem is that the original file is in SHIFT_JIS and the script doesn't take that into account

try this:
```
iconv -f SHIFT_JIS -t UTF-8 oto.txt | sed -f sed1.txt | iconv -f UTF-8 -t SHIFT_JIS > output1.txt
```[FONT=Courier New]
Ah, just figured part of it out, lol. Mine stopped later because I was running it against "test", an oto.ini I removed all (or so I thought) the aliases from (apparently I missed one or two) but yours was targeting the raw oto.ini which still had aliases and stopped short on the first one due to its &#12354; alias. Also the $a and $b orders were wrong, so even when I cleaned out all the aliases it did nothing, lol. Should have been:[/FONT] [FONT=Courier New]
```

while read -r a b
do
  echo "s/^$b[.]wav=[^,]*,/$b.wav=$a,/"
done < syn.txt > hira_roma

while read -r a b
do
  echo "s/^$a[.]wav=[^,]*,/$a.wav=$b,/"
done < syn.txt > roma_hira
```[/FONT]

---

### Post by ntzrmtthihu777 on 2012-11-19
Aha, absolutely done! I can now do as needed, thank you so much for your help Vaphell!

---

