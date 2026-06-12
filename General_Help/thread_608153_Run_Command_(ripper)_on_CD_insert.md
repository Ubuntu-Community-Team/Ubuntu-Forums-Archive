---
title: "Run Command (ripper) on CD insert?"
date: 2007-11-09
forum: General Help
---

### Post by sev(n) on 2007-11-09
I have a headless server running gutsy at home right now and I already have abcde set up to rip just the way I want it to, but I want to be able to pop in a cd, go about my business, then download the mp3s off my server later. Is there a way to have abcde run when an audio cd is detected?

---

### Post by snkmad on 2007-11-09
Go to System/Preferences/Removable Drives and Media.
Then go to the Multimedia tab, under Audio CD Discs, after command, put the command to start your abcde program.
But i dont know about parsing parameters to it, since ive never used that program before.

Hope this help you.

---

### Post by logos34 on 2007-11-11
I have mine set up like snkmad describes.  Just the command '**abcde**'.  The cd spins up and starts ripping+encoding all the tracks without opening the terminal or a single interactive prompt, which is what I normally get when I run it manually.  You end up with the format(s) specified in OUTPUTYPE line in .abcde.conf.

Now if I can just figure out how to specify formats and options for one or several tracks rather than the ENTIRE cd.

these commands work:

abcde [tracks] 

abcde -o [filetype][:filetypeoptions] 

but NOT

abcde** [tracks] ** -o [filetype][:filetypeoptions] 

Does anyone know if this is possible?

---

### Post by mcduck on 2007-11-11
> **logos34 said:**
> I have mine set up like snkmad describes.  Just the command '**abcde**'.  The cd spins up and starts ripping+encoding all the tracks without opening the terminal or a single interactive prompt, which is what I normally get when I run it manually.  You end up with the format(s) specified in OUTPUTYPE line in .abcde.conf.

Now if I can just figure out how to specify formats and options for one or several tracks rather than the ENTIRE cd.

these commands work:

abcde [tracks] 

abcde -o [filetype][:filetypeoptions] 

but NOT

abcde** [tracks] ** -o [filetype][:filetypeoptions] 

Does anyone know if this is possible?
Have you tried putting the command into a script, and then using the script as the program to run when audio CD is detected?

---

### Post by logos34 on 2007-11-11
> **mcduck said:**
> Have you tried putting the command into a script, and then using the script as the program to run when audio CD is detected?

I should have been clearer: actually, I want to be able to do that manually in the terminal.  I haven't come across any mention of that anywhere (if even possible), and I've been scouring the web (there's not a lot about abcde compared to the other rippers).  The only other way I know is to use the '**-c [filename]**' option so that abcde parses an alternate config file before .abcde.conf.

---

### Post by logos34 on 2007-11-12
Nevermind--got it.  It's

**abcde [options] [tracks]**

It was at the very top of the man page.  Duh!  Time to clean out the cobwebs in my brain and get some new glasses...

So the tracks go after the options.  But I've found some interesting things experimenting with it last night.  It seems you can either delimit the outputtype/format, or specify custom options for a single output, but not both:

$ **abcde -o ogg:"-q 3", -o mp3:"-V 6" 7**

rips track 7 only to an mp3 file at VBR quality 6 setting, but SKIPS the ogg
> ...

Ripping...

Done.

Encoding track 07 of 7: Livre pour Cordes - 1b. Mouvement...
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
Using polyphase lowpass filter, transition band: 15115 Hz - 15648 Hz
Encoding /home/zazen/abcde.5f109a07/track07.wav
      to /home/zazen/abcde.5f109a07/track07.mp3
Encoding as 44.1 kHz **VBR(q=6) **j-stereo MPEG-1 Layer III (ca. 13x) qval=3...


While this

$ **abcde -o mp3,ogg:"-q 3" 7  ** 

rips and encodes track 7 to both formats according to values in .abcde.conf, instead of doing the ogg at specified "-q 3"

I don't get the 'ERROR: Multiple input files with specified output filename: suggest using -n' with either command, I just get the wrong result.  So until I figure out the arcane details of abcde command syntax, I'll just have to be content with specifying one custom option per format at a time:

e.g., either

$ **abcde -o mp3,ogg 7**

or

$ **abcde -o ogg:"-q 3" 7**

or 

$ **abcde -o mp3:"-V 6" 7**

or even 

$ **abcde mp3,ogg** (-->entire cd)

but not both at same

---

