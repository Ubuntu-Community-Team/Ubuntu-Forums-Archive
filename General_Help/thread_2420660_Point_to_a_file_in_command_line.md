---
title: "Point to a file in command line?"
date: 2019-06-08
forum: General Help
---

### Post by PDA1 on 2019-06-08
[SIZE=3]I'm trying to use PDFTK to combine several pdfs by referring to the pdf location....but can't figure it out.  I want to be able to work in any folder, have pdftk "go get" the pdfs (no matter what folder they're located in), combine them and then send the output to the folder I'm working in.

I can combine (cat) the file quite easily using pdftk when they're in the same folder but referring to them in other assorted folders doesn't work.

Command line always says there's some error such as it can't find the file, etc.  I suppose I'm using the incorrect format for referring to a file.

[FONT=Ubuntu]Example- 

2 files needed to be combined (notice there are spaces in the folders and file names) Notice this is from the command line-[/FONT]
 [FONT=Ubuntu]
Paul@Paul:~/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits$[/FONT]
 [FONT=Ubuntu]
Disclaimer for 1993.pdf [/FONT] 
 
[FONT=Ubuntu]Paul@Paul:~/My Documents/AAA- My Method/Supplement/1- Covers for The Book$ [/FONT] 
 [FONT=Ubuntu]
The Cover for 1993.pdf  [/FONT][/SIZE] 
  


[SIZE=3]Here's what I'm come up with so far (this is all pasted into command line)[/SIZE]

```
*[FONT=Ubuntu][SIZE=3]**pdftk**[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=3] \[/SIZE][/FONT]*
 [FONT=Ubuntu]*[SIZE=3]/My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \[/SIZE]*[/FONT]
 [FONT=Ubuntu]*[FONT=Ubuntu][SIZE=3]/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=3]\[/SIZE][/FONT]**[SIZE=3]Disclaimer for 1993.pdf \[/SIZE]*[/FONT]
 *[FONT=Ubuntu][SIZE=3]**cat**[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=3] \[/SIZE][/FONT]*
 [FONT=Ubuntu]*[SIZE=3]/My Documents/AAA- My Method/Supplement/1- Covers for The Book\The Cover for 1993.pdf \[/SIZE]*[/FONT]
 [FONT=Ubuntu][SIZE=3]*[FONT=Ubuntu]/My Documents/AAA- My Method/Supplement/0- Disclaimer and Credits[/FONT]**[FONT=Ubuntu]\[/FONT]**Disclaimer for 1993.pdf \*[/SIZE][/FONT]
 
 *[FONT=Ubuntu][SIZE=3]**output**[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=3]FinalFile[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=3].pdf[/SIZE][/FONT]*
  
```

Can you solve this for me?

Thank you,

Paul

---

### Post by wildmanne39 on 2019-06-08
Thread closed. Please do not post duplicates, it dilutes community effort.

Please use your other thread here:

[https://ubuntuforums.org/showthread.php?t=2420659](https://ubuntuforums.org/showthread.php?t=2420659)

---

