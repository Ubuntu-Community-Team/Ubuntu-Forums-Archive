---
title: "Anyone got Denemo working in Ubuntu?"
date: 2005-07-19
forum: General Help
---

### Post by abovett on 2005-07-19
Hi

I'm running Hoary and trying to get Denemo and LilyPond to work. I'm new to them both so guessing a lot here. The packaged version of Denemo didn't seem to be compatble with the available LilyPond version so I installed LilyPond v 2.2.6 from the Ubuntu repositories and built Denemo 0.7.3beta2 from source.

It sort of works - I've got a GUI (though some icons are missing) and I've persuaded it to use timidity to play MIDI stuff. The problem comes when I hit "print". It runs lilypond and generates various files, but then I get an error message from TeX. I'm not quite sure what it's trying to do at this point - expecially since it's already produced some printable output. Here's the output I get (I ran denemo from the command line, by the way) - note at the end it's waiting for m3e to supply a file name:

[FONT=Courier New]
lilypond (GNU LilyPond) 2.2.6
Running lilypond-bin...
Now processing `/home/andrew/.denemo/denemoprint.ly'
Parsing...
Interpreting music... [3]
Preprocessing graphical objects...
Calculating line breaks...

paper output to `denemoprint.tex'...
writing header field `title' to `denemoprint.title'...
writing header field `piece' to `denemoprint.piece'...
writing header field `head' to `denemoprint.head'...
writing header field `poet' to `denemoprint.poet'...
writing header field `opus' to `denemoprint.opus'...
writing header field `instrument' to `denemoprint.instrument'...
writing header field `subtitle' to `denemoprint.subtitle'...
writing header field `footer' to `denemoprint.footer'...
writing header field `meter' to `denemoprint.meter'...
writing header field `composer' to `denemoprint.composer'...
writing header field `arranger' to `denemoprint.arranger'...
writing header field `dedication' to `denemoprint.dedication'...

Interpreting music...
MIDI output to `denemoprint.midi'...
Track ...

Analyzing denemoprint.tex...
Running ...
Running dvips...
Running ps2pdf...
DVI output to `denemoprint.dvi'...
MIDI output to `denemoprint.midi'...
PDF output to `denemoprint.pdf'...
PS output to `denemoprint.ps'...
This is TeX, Version 3.14159 (Web2C 7.4.5)
! I can't find file `/home/andrew/.denemo/denemoprint.tex'.
<*> /home/andrew/.denemo/denemoprint.tex

Please type another input file name:
[/FONT]


At this point, the .denemo directory contains the following files:

[INDENT]
denemocsoundplayback
denemoplayback.ly
denemoplayback.mid.ly
denemoplayback.mid.midi
denemoprint.dvi
denemoprint.ly
denemoprint.midi
denemoprint.pdf
denemoprint.ps
denemorc
keymaprc
timidity.mid
[/INDENT]

No sign of denemoprint.tex - should it be there? It is mentioned several times before the error message.

Hope someone can help.

Cheers

Andy B

---

### Post by dawynn on 2005-08-28
Oh, boy!  You're bold.  Never tried doing much with denemo besides using it as a frontend to build lilypond files.  I do my initial editing in denemo, then save as a lilypond file.  Then I use Lilypond to do everything else.

Denemo is kind enough to actually put a version in the .ly file that it creates (I just use the Ubuntu denemo, straight out of the box).  This is helpful, because if your Lilypond version is more recent then what denemo builds, program convert-ly depends on the version found in the .ly file.

Note that I've updated to the autopackage version of Lilypond ([www.lilypond.org](www.lilypond.org)) and it works great.  You also may want to upgrade since Ubuntu is two generations behind (Lilypond is in the 2.6 series, Ubuntu still has the 2.2 series).

General process:
1) Use denemo to lay down the basic music staffs with notes
2) Save file as lilypond (.ly) file
3) Run convert-ly to bring denemo's file up-to-date
4) Edit .ly file with favorite text editor, adding in lyrics and other stuff
5) Run lilypond to convert file to printable output & midi
6) Run midi through favorite midi player to check accuracy of work
7) Review and print the PDF file from favorite PDF viewer

 -- David

---

