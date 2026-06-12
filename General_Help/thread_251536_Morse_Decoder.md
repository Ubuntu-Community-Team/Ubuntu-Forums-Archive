---
title: "Morse Decoder"
date: 2006-09-05
forum: General Help
---

### Post by n4znv on 2006-09-05
I am not sure if I am in the right place for this question. If I am not I apologize and need direction.

My question is: has anyone found  a Morse Code Decoder program that is compatible with Ubuntu (debian based).  If not can someone direct me to a good source file that can be compiled to work.  I have tried a couple such as RSCW but apparently there is not enought information in the tar file to allow it to be configured.  Any guidance on this would be greatly appreciated.

Thanks

---

### Post by Jussi Kukkonen on 2006-09-05
There are 13 packages in the repositories that have something to do with morse... I know nothing about it, so I can't say if the results are usable for you.

Anyway, *apt-cache* is your friend ( feel free to use Synaptic if you want to):
```
jku@luna:~$ apt-cache search morse
aldo - Portable morse code trainer
bsdgames - a collection of classic textual unix games
codegroup - Convert any file, including binary, into 5 letter code
cw - Command-line frontend to unixcw
cwcp - Ncurses frontend to unixcw
cwdaemon - morse daemon for the parallel or serial port
cwirc - X-Chat morse plugin
morse-x - morse "practicing" tool for X
pileup - Morse code pileup trainer for SB compatible soundcards
tlf - Console mode purpose CW keyer, logging- and contest program
unixcw - Shared library for Morse programs
unixcw-dev - Development files for Morse programs
xcwcp - Qt frontend to unixcw

```

---

### Post by ell02 on 2006-09-05
did you check synaptic package manager? click sections and amateur radio will be at the top if you have universe enabled. this might also be of help.   radio.linux.org.au          
you could even try mfj enterprises they have all kind of decoders, cheap too.i just use my ears. gud luck es 73 de aa1sp.

---

### Post by n4znv on 2006-09-06
All of the packages in the repository appear to be generators not decoders.  In other words they make the sounds for morse but do not take morse sounds and convert them to text.  Thanks for the input though, I really appreciate it.  New to Linux so I have a good sized learning curve.;)

---

### Post by WheelsOfSteel on 2008-05-05
Hi guys - yes, the packages seem to be trainers rather than decoders.  I know of CW get in the windows world but I would also like to know of a decoder in the linux/ubuntu world?  Anyone know??

Thx.

---

