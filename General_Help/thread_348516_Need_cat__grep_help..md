---
title: "Need cat | grep help."
date: 2007-01-28
forum: General Help
---

### Post by test on 2007-01-28
My problem is that i cant get specific lines from multiple files at once...

Files could include things like:
**word**9a12**word**
**word**12e31**word**
**word**12x*312**word**

If i use **"cat *.txt | grep -o 'word*word' >list.txt"** it doesnt give anything...
And with **"cat *.txt | grep -o 'word....word' >list.txt"** it gives output if there are as many chars as i used dots, not for less or more...
And before and after of the specific words are other text that i dont want to output.

So, how can i exactly get a nice output from words that have random number of letters and things between them ?

And yes, i tried googling and tested every odd '^, $' things between them and they didnt seem to work :(

---

### Post by yigal.weinstein on 2007-01-28
"*" is repeat or match depending on the program ad infinitum the character before the "*".  So for instance grep word*word matches,

wordword
worddword
worddddddddddword

etc. 

"." is match any regular character, i.e.  anything except sometimes \n a newline but grep doesn't seem to care if you have a \n in your pattern and will match it. 

So the pattern ```
[SIZE="3"]word.*word[/SIZE]
``` is what you want,
```
cat *.txt | grep -o 'word.*word' >list.txt
```

best

---

### Post by WW on 2007-01-28
By the way, you don't have to pipe the output of cat to grep. This will work:
```
grep -o "word.*word"  *.txt
```
If you don't want the file names at the beginning of each line of output, use the -h option:
```
grep -h -o "word.*word" *.txt
```

---

