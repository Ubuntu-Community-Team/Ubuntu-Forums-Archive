---
title: "Text file manipulation in Linux/UNIX environment"
date: 2013-01-11
forum: General Help
---

### Post by ebodnaruk on 2013-01-11
Hi everyone,

I'm trying to do some text file manipulation in a UNIX environment because there are such powerful command line tools available.  But, I don't have much experience.  

I have a text file with 10 columns containing some data.   I have another text file that has a single column of data.  I want to take that single column of data and put it into the larger file by overwriting a column of my choice with this data.  

For instance I want to take the single column of data and overwrite the third column of data in the large text file.  

How would I do this?  I'm looking to use a unix command, not a programming language.  

One other possible method could be to treat each character as a column, and specify which "character" columns to add the data to.  
So if:
     * The data I want to replace takes up columns 12-14
     * I could use a command that would take the three-digit data I have and put it into columns 12-14 of the larger file.  
  
This would be a useful fix as well.  

Thanks for your help!

---

### Post by ebodnaruk on 2013-01-11
tried to paste some tables as an example but the formatting did not stay

---

### Post by steeldriver on 2013-01-11
How are the columns delimited? Probably some combination of the 'cut' and 'paste' commands should work, e.g.

```
$ cat myfile
a b c d e
f g h i j
k l m n o
p q r s t
$
$ cat myotherfile
1 2
3 4
5 6
7 8

``````
$ paste -d' ' - < <(cut -d' ' -f1-3 myfile) myotherfile <(cut -d' ' -f5 myfile)
a b c 1 2 e
f g h 3 4 j
k l m 5 6 o
p q r 7 8 t

```

---

### Post by ebodnaruk on 2013-01-11
Hi Thanks!  Columns are space delimited.  

I want this:

file1
a b c d e
f g h i j
k l m n o
p q r s t

file2
1 
2
3
4


new file
a b 1 d e
f g 2 i j
k l 3 n o
p q 4 s t

If you could give another example of code that would do this, I think I could figure it out from there.  Thanks!

---

### Post by steeldriver on 2013-01-11
you just need to specify the correct column numbers in the cut field parameter (the '-f' parts) I think

```
$ paste -d' ' - < <(cut -d' ' -f1-2 file1) file2 <(cut -d' ' -f4-5 file1)
a b 1 d e
f g 2 i j
k l 3 n o
p q 4 s t

```

---

### Post by ebodnaruk on 2013-01-14
That works great.  I've read about paste and cut and understand them pretty well, but I don't quite understand the syntax you use below.  I know it's terribly newbie of me, but if you could decode a bit of it I would really appreciate it.  

I understand that the delimiter being used is spaces.  And that the code cuts the first two columns, pastes it to the single column file, and pastes that to the cut 4th and 5th columns.  What I don't understand is the additional "<" signs and the extra hyphen.  What exactly do those signify?  

Thanks so much!

> **steeldriver said:**
> you just need to specify the correct column numbers in the cut field parameter (the '-f' parts) I think

```
$ paste -d' ' - < <(cut -d' ' -f1-2 file1) file2 <(cut -d' ' -f4-5 file1)
a b 1 d e
f g 2 i j
k l 3 n o
p q 4 s t

```

---

### Post by steeldriver on 2013-01-14
Well tbh my own understanding of shell redirects is not the best so don't take this as gospel but I will have a go

Basically the 'paste' command expects to be given a list of filenames from which to read its data, but the 'special' character [FONT=Courier New]-[/FONT] (dash) tells it to read input from the shell's standard input stream (aka 'stdin') instead. The parenthetical [FONT=Courier New](cut -d' ' -f1-2 file1)[/FONT] and [FONT=Courier New](cut -d' ' -f4-5 file1)[/FONT] bits execute the cut commands in their own subshells, and the [FONT=Courier New]<[/FONT] characters in front of them redirect each subshell's standard output stream (aka 'stdout') to the main shell's stdin where [FONT=Courier New]paste[/FONT] reads the results.

To be honest I was a bit surprised that it let us mix the 2 input redirects with a regular filename [FONT=Courier New]file2[/FONT] in between and somehow gets all the bits in the 'right' order - I'm not sure that behavior is guaranteed so if this is a critical application (or needs to be portable) you might want to think about doing the cuts one at a time and saving the intermediate outputs to temp files

Hope this helps

---

### Post by gardnan on 2013-01-14
> **steeldriver said:**
> Well tbh my own understanding of shell redirects is not the best so don't take this as gospel but I will have a go

Basically the 'paste' command expects to be given a list of filenames from which to read its data, but the 'special' character [FONT=Courier New]-[/FONT] (dash) tells it to read input from the shell's standard input stream (aka 'stdin') instead. The parenthetical [FONT=Courier New](cut -d' ' -f1-2 file1)[/FONT] and [FONT=Courier New](cut -d' ' -f4-5 file1)[/FONT] bits execute the cut commands in their own subshells, and the [FONT=Courier New]<[/FONT] characters in front of them redirect each subshell's standard output stream (aka 'stdout') to the main shell's stdin where [FONT=Courier New]paste[/FONT] reads the results.

To be honest I was a bit surprised that it let us mix the 2 input redirects with a regular filename [FONT=Courier New]file2[/FONT] in between and somehow gets all the bits in the 'right' order - I'm not sure that behavior is guaranteed so if this is a critical application (or needs to be portable) you might want to think about doing the cuts one at a time and saving the intermediate outputs to temp files

Hope this helps

Sorry, but this is slightly wrong. What you are doing with the <(...) construct is called 'process substitution' and it basically allows you to act on a programs output as a file. In fact, this is basically what bash ends up doing to perform a process substitution. 

[http://tldp.org/LDP/abs/html/process-sub.html](http://tldp.org/LDP/abs/html/process-sub.html)

---

### Post by steeldriver on 2013-01-14
Ah thanks for the correction 

So in hindsight the syntax could have been simpler I think? i.e. just

```
$ paste -d' ' <(cut -d' ' -f1-2 file1) file2 <(cut -d' ' -f4-5 file1)
a b 1 d e
f g 2 i j
k l 3 n o
p q 4 s t

```(no need for the [FONT=Courier New]- <[/FONT] which is probably just redirecting nothing to nowhere?) - ebodnaruk please take note, and my apologies for the bad information

---

### Post by Vaphell on 2013-01-15
just for kicks, pure bash

```
$ echo $'a b c d e\nf g h i j\n k l m n o\np q r s t' > f1.txt
$ echo $'1\n2\n3\n4' > f2.txt
$ while read -u3 a1 a2 _ a3 a4; read -u4 b1; do echo "$a1 $a2 $b1 $a3 $a4"; done 3< f1.txt 4< f2.txt
a b 1 d e
f g 2 i j
k l 3 n o
p q 4 s t
```

---

### Post by steeldriver on 2013-01-15
nice! I didn't know about [FONT=Courier New]read -u[/FONT]

---

