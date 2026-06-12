---
title: "Terminal Script Session Produces Unrecognised Characters"
date: 2014-01-15
forum: General Help
---

### Post by WP6r8PA on 2014-01-15
Sorry if this has been dealt with before but I couldn't find any posts related to my issue. I need to submit a script file of the compiling and running of java programs I write for school. When I open the script files after turning on the script within the terminal and compiling and running the programs and then turning off the script, there's unrecognised characters (unrecognized in Text Editor and LyX which I'm using to construct the assignments). It's really frustrating as when I try to attach it as a Child Document in LyX it gives me an error when attempting to export it. I could just go in an edit them, yes, but I'd rather figure out a fix so I don't have to edit every script file I ever create. Any input is appreciated. Thanks.

---

### Post by WP6r8PA on 2014-01-15
I'm running 12.04, forgot to include that.

---

### Post by Impavidus on 2014-01-16
I don't really follow what you're doing, but could this be an encoding issue? I know that TeX, for which LyX is a front end, uses a number of 8 bit character encodings and that most programs, including text editors and the terminal, use UTF-8 encoding. I can't say which encoding is used by your java programs. There are tools to convert text files from one encoding to a different one. The **iconv** tool may be able to help.```
iconv -f <input encoding> -t <output encoding> -o <output file> <input file>
```

---

### Post by dargaud2 on 2014-01-16
Pipe your output to uchardet and it will try to guess the character set in use by your script. But I wonder if your script may be outputing binary data instead of a mistaken charset...

---

### Post by WP6r8PA on 2014-01-16
Thank you for your responses. First, Impavidus, I'm creating a script file of running and interacting with a Java program, like as described here: [http://myweb.stedwards.edu/laurab/help/scripthelp.html](http://myweb.stedwards.edu/laurab/help/scripthelp.html)

However, when it's done and I open the file in Text Editor (it's a .txt file) there are strange characters that are unrecognisable which is preventing me from attaching the file to LyX documents. There are only 2-3 occurrences of the strange character and the rest looks normal. 

dargaud2, I'm not sure what you mean by "pipe" my output to "uchardet"? I'm a little new.

---

### Post by steeldriver on 2014-01-16
I suspect what you are seeing are terminal color control codes - I just don't know the best way to turn them off completely...

---

### Post by WP6r8PA on 2014-01-16
> Script started on Thu 16 Jan 2014 12:38:47 AM NSTsoftskeleton@softskeleton: ~/workspace/Discount/srcsoftskeleton@softskeleton:~/workspace/Discount/src$ java Discount
Please enter a purchase amount, -1 to quit: 
1000
Please enter a purchase amount, -1 to quit: 
2000
Please enter a purchase amount, -1 to quit: 
-1
Total sale, including discounts : 1700.0
]0;softskeleton@softskeleton: ~/workspace/Discount/srcsoftskeleton@softskeleton:~/workspace/Discount/src$ exit
exit


Script done on Thu 16 Jan 2014 12:39:07 AM NST


When copying and pasting it here doesn't show up as I see it in Text Editor, but you get the idea. When I try to paste the character in here nothing happens. It's a box with two 0's on top and 07 on the bottom. It either shows up as ]0; or absolutely nothing and links the text as a run-on with no spaces when it's not supposed to if I copy and paste it.

---

### Post by steeldriver on 2014-01-16
Try setting an explicit non-color terminal when you invoke the script command e.g.

```
**TERM=vt220** script *scriptfile*
```

That should be enough to suppress colors in the bash prompt (which is what's giving the leading **]0;** sequence I think)

---

### Post by Impavidus on 2014-01-16
A box with some numbers in it usually indicate a character not present in the current font. 0007 is the bell character, one of the non-printing control characters in ASCII. Any idea why they would show up in your file?

---

### Post by WP6r8PA on 2014-01-18
> **steeldriver said:**
> Try setting an explicit non-color terminal when you invoke the script command e.g.

```
**TERM=vt220** script *scriptfile*
```

That should be enough to suppress colors in the bash prompt (which is what's giving the leading **]0;** sequence I think)

This worked! Thank you!

---

