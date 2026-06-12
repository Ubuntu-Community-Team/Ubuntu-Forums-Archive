---
title: "Optimize PDF?"
date: 2018-05-07
forum: General Help
---

### Post by PDA1 on 2018-05-07
I just upgraded from Ubuntu 12.04 to Ubuntu Mate 18.04.  Previously when using Ubuntu 12.04 I used a series of commands to work on a 250 page PDF so that it would be just the way that is needed.  The result was perfectly and the file was about 5 meg.

Here are the commands I used to use;

```
[LEFT][FONT=Ubuntu][SIZE=2]pdfcrop **outp**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**ut**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**filename.pdf**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]\[/SIZE][/FONT]
[/LEFT]
 [LEFT][FONT=Ubuntu][SIZE=2]&& pdfjam **outputfile**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**name-**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**crop**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**.pdf**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]  --nup 2x1 --landscape --outfile [/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**BIGONE**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]**.pdf**[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]\[/SIZE][/FONT]
[/LEFT]
 [LEFT][FONT=Ubuntu][SIZE=2]&& pdf2ps **BIGONE.pdf outputfilename.ps\**[/SIZE][/FONT]
[/LEFT]
 [LEFT][FONT=Ubuntu][SIZE=2]&& ps2pdf **outputfilename.ps FinishedFile.pdf**\[/SIZE][/FONT]
[/LEFT]
  
```

The commands cropped the file then put 2 pages on 1 page in Landscape.
Then pdf2ps and ps2pdf were used to shrink the files down to a good quality finished file.


Since upgrading and using the same commands, pdf2ps only produces and empty file.

I've tried using variations of ghostscript settings but only get down to about 9 meg from a 17 meg file.

Any suggestions of what to do?

Thanks,

PDA1

---

