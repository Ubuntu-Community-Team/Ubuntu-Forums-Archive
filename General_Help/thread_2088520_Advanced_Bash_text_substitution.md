---
title: "Advanced Bash text substitution"
date: 2012-11-26
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-11-26
[FONT=Courier New]Hello, looking for  a bit of advice on how to do some very complicated text substitution;
Here is a sample text:
[/FONT]```
[FONT=Courier New][#VERSION] 
UST Version1.2 
[#SETTING] 
Tempo=72.99 
Tracks=1 
ProjectName=oshnt 
VoiceDir= /path/to/voice
OutFile=oshnt.wav 
CacheDir=Hiru no Tsuki.cache 
Tool1=wavtool.exe 
Tool2=resampler.exe 
Mode2=True 
Flags=C100Y0H0BRE0 
**[#0000]** 
Length=9592 
**Lyric=R** 
NoteNum=48 
PreUtterance= 
Tempo=72.99 
**[#0001]** 
Length=420 
**Lyric=o** 
NoteNum=63 
PreUtterance=11 
VoiceOverlap=5 
Intensity=100 
Modulation=0 
PBType=5 
PitchBend= 
PBW=100 
PBS=-50 
Envelope=0,5,35,0,100,100,0 
VBR=50,170,20,49,49,42.845636265157,0,0 
StartPoint=0 
PBStart=-11 
**[#0002] **
Length=60 
**Lyric=R** 
NoteNum=63 
PreUtterance=0 
VoiceOverlap=0 
StartPoint=0 
Envelope=0,5,7,0,100,100,0 
**[#0003]** 
Length=420 
**Lyric=to**
NoteNum=65 
PreUtterance=115 
VoiceOverlap=60 
Intensity=100 
Modulation=0 
PBType=5 
PitchBend= 
PBW=100 
PBS=-38 
Envelope=0,5,35,0,100,100,0 
VBR=50,170,20,50,50,56.1040086433832,0,0 
StartPoint=0 
PBStart=-115 
**[#0004]** 
Length=60 
**Lyric=R** 
NoteNum=65 
PreUtterance=0 
VoiceOverlap=0 
StartPoint=0 
Envelope=0,5,35,0,100,100,0 
**[#0005]** 
Length=720 
**Lyric=no**
NoteNum=67 
PreUtterance=65 
VoiceOverlap=33 
Intensity=100 
Modulation=0 
PBType=5 
PitchBend= 
PBW=100 
PBS=-50 
StartPoint=0 
Envelope=0,5,29,0,100,100,0 
VBR=50,170,20,33,33,91.3717587246356,0,0 
PBStart=-65 [B]
[#0006][/B]
Length=240 
**Lyric=na**
NoteNum=67 
PreUtterance=63 
VoiceOverlap=29 
Intensity=100 
Modulation=0 
PBType=5 
PitchBend= 
PBW=100 
PBS=-50 
StartPoint=0 
Envelope=0,29,100,0,100,100,100,%,100 
VBR=50,170,20,50,50,83.4817139229139,0,0 
PBStart=-63[/FONT] 
```[FONT=Courier New]

The bold text is what I am concerned with. These signify which lyric [and lyric number] is sung by UTAU, a singing synthesis program, the other lines contain info about pitch and such, not important to what I am trying to achieve. What I am trying to do is convert this file, known as a *.ust, from cv (consonant- vowel) to vcv (vowel-consonant-vowel). This amounts to a simple text substitution, changing the above bold text to read:
[/FONT]```


[FONT=Courier New]From      To
[#0000]   [#0000] 
Lyric=R   Lyric=R
[#0001]   [#0001]
Lyric=o   Lyric=- o
[#0002]   [#0002]
Lyric=R   Lyric=R
[#0003]   [#0003]
Lyric=to  Lyric=- to
[#0004]   [#0004]
Lyric=R   Lyric=R
[#0005]   [#0005]
Lyric=no  Lyric=- no
[#0006]   [#0006]
Lyric=na  Lyric=o na[/FONT]
```[FONT=Courier New][FONT=Courier New][FONT=Courier New]
[/FONT][/FONT][/FONT][FONT=Courier New]
(The other text will remain, I just want to change these as shown) You may notice the pattern, R does not change, a note following R has "- " inserted between it and the =, and a note following another note has the last letter (usually a vowel, occasionally a single n) inserted instead of the -.

This is a very complicated substitution, and quite frankly I have no idea where to start. To reiterate, I do not want any other data to change, just "Lyric=*"
[/FONT]

---

### Post by Vaphell on 2012-11-26
```
awk '!/Lyric/   { print $0; next; } 
      /Lyric=R/ { print $0; last="-"; next; }
      /Lyric=/  { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }' file.txt
```

---

### Post by ntzrmtthihu777 on 2012-11-26
> **Vaphell said:**
> ```
awk '!/Lyric/   { print $0; next; } 
      /Lyric=R/ { print $0; last="-"; next; }
      /Lyric=/  { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }' file.txt
```
[FONT=Courier New]Haha, I can't escape you lol. Stalking me? Thank you, this does exactly what I need for the most part, seems to have a few small issues though, my fault it seems though for not including one other possible combos
if the first "Lyric=*" string is not an R, then you insert "- " also

It seems to have trouble with the non R lyrics that follow each other, its inserting a carriage return then a space, using my original example:
[/FONT]```
[FONT=Courier New][#0000]
Lyric=o
[#0001]
Lyric=to
[#0002]
Lyric=no
[#0003]
Lyric=na
[#0004]
Lyric=i
[/FONT]
```[FONT=Courier New]Is becoming
[/FONT]
```
[FONT=Courier New][#0000]
Lyric= o
[#0001]
Lyric=
 to
[#0002]
Lyric=
 no
[#0003]
Lyric=
 na
[#0004]
Lyric=
 i
[/FONT]
```[FONT=Courier New]
When it should be
[/FONT]
[FONT=Courier New]```
[FONT=Courier New][#0000]
Lyric=- o
[#0001]
Lyric=o to
[#0002]
Lyric=o no
[#0003]
Lyric=o na
[#0004]
Lyric=a i
[/FONT]
```Sorry if I am bugging you too much, lol, but as I said in the last post you helped me with, I am still a bit of a newb.

[EDIT] ah dammit, lol. I see why its not working, some how or another commas got inserted into my orignal text, I will edit it to reflect the actual situation.
[/FONT]

---

### Post by papibe on 2012-11-26
Hi ntzrmtthihu777.

If you are open to use other tools than bash, I would suggest taking a look at Python, as it has several modules that can handle config files. For instance, [ConfigParser]("http://docs.python.org/2/library/configparser.html").

Here's an example. This get the value of 'Lyric' under the '#0001' section and replace the value by adding a '- ' before it.
```
#!/usr/bin/python

import ConfigParser

path = "./config"

config = ConfigParser.RawConfigParser()
config.read( path )

value =  config.get('#0001', 'Lyric')
config.set('#0001', 'Lyric', '- ' + value)

with open( path, 'wb') as configfile:
    config.write(configfile)

```
The only caveat is that your config file is not 100% compatible, as this section:
```
[#VERSION] 
UST Version1.2 
```
is not actually a config entry. I changed to this so the above python code works:
```
[#VERSION] 
UST Version=1.2 
```
As usual, I'd recommend backing up your config files before trying this.

I hope it helps. Let us know how it goes.
Regards.

---

### Post by ntzrmtthihu777 on 2012-11-26
[FONT=Courier New]Hmm, I have considered using other interpreters, yes, but I am intending to insert this into an existing bash script to add another function to it and my understanding is that is difficult if not impossible, lol. Also I am attempting to stay within a language I know enough about to tinker with should the need arise.
[/FONT]

---

### Post by Vaphell on 2012-11-26
these broken lines are probably \r coming from windows. They are passed to the next Lyric instead of the actual last character. I've removed commas after = either way because they didn't look right

```
awk '    BEGIN { RS="[\r\n]+"; last="-"; }
      !/Lyric/ { print $0; next; } 
     /Lyric=R/ { print $0; last="-"; next; }
      /Lyric=/ { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }'
```

---

### Post by ntzrmtthihu777 on 2012-11-26
> **Vaphell said:**
> these broken lines are probably \r coming from windows. They are passed to the next Lyric instead of the actual last character.

```
sed 's/\r$//' file.txt | awk '    BEGIN { last="-"; }
                               !/Lyric/ { print $0; next; } 
                              /Lyric=R/ { print $0; last="-"; next; }
                               /Lyric=/ { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }'
```
[FONT=Courier New]Right right, I had ran into that once with a cat of a windows file. Question: Would these files with \r removed display properly in windows and if not, can you instead use the next to last character (just before \r) as "last"?[/FONT]

---

### Post by Vaphell on 2012-11-26
try this
```
awk '    BEGIN { RS="[\r\n]+"; ORS="\r\n"; last="-"; }
      !/Lyric/ { print $0; next; } 
     /Lyric=R/ { print $0; last="-"; next; }
      /Lyric=/ { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }' file.txt
```

---

### Post by ntzrmtthihu777 on 2012-11-26
> **Vaphell said:**
> try this
```
awk '    BEGIN { RS="[\r\n]+"; ORS="\r\n"; last="-";  }
      !/Lyric/ { print $0; next; } 
     /Lyric=R/ { print $0; last="-"; next; }
      /Lyric=/ { sub( /=,?/, "="last" ");  print $0; last=substr($NF,length($NF),1); }' file.txt
```
[FONT=Courier New]Much obliged, my knowledgeable friend! The first example you gave did the trick for my program on Ubuntu in wine, but I want to make sure that the resulting files are portable, there is a lot of trading of these files in the UTAU community and it would be a shame to only use songs produced with it to be used only on Linux.[/FONT]

---

