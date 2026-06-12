---
title: "Running a looped script file"
date: 2014-05-29
forum: General Help
---

### Post by abhishek11 on 2014-05-29
If i have an input file which has a value that needs to be changed over a range (suppose the input file has value 'a=0' and this 'a' belongs from 0 to 10 in steps of 1). Is there a way to make a sort of a loop in the script file for the terminal, where I would be using the input file with an appropriate program ? Many thanks, in advance ! P. S. I am not very sure if I am being very clear, please ask me to add details you may think, is appropriate.

---

### Post by steeldriver on 2014-05-29
Hello and welcome to the forums

Can you give us a (minimal) example - as well as just trying to explain it in words?

---

### Post by abhishek11 on 2014-05-29
So, I have an executable called pipe_sb. Now this takes an input file (say stab.in ) with certain values (let's say one of them is 'a') ,given in a defined order, that it uses to compute other stuff. To execute this, I have written a script file takes this file (i.e. stab.in ) and is used to run pipe_sb. Now the thing is, pipe_sb only takes one value of 'a' (which means that the input file was defined to have only one value of 'a') . I need to run the pipe_sb for a large number of 'a' s with different values. I was hoping to know if inside the script file, there a way to change the stab.in (input file) in a sort of a 'for loop' for the value of 'a', say from 1 to 100 in steps of 1.

---

### Post by steeldriver on 2014-05-29
It's still not clear - do you want to loop over different **file names** (stab1.in, stab2.in ...), or loop through the **lines** of one stab.in file each **line** containing a different value of 'a'? 

Or do you just want to do something for values of 'a' from 1 to 100 (without bothering with a file at all)?

---

### Post by abhishek11 on 2014-05-29
I want to make a loop such that the value of 'a' would be **edited** every single time in the loop ***within*** the stab.in file. 
[FONT=courier new]
for i from 1 to 100, in steps of 1:

 edit stab.in so that it updates 'a'( a=i),
 run the executable pipe_sb which takes the edited stab.in as input file

end loop

[FONT=arial]I hope this helps. [/FONT]


[/FONT]

---

### Post by steeldriver on 2014-05-29
What is the exact format of the stab.in file?

---

### Post by Impavidus on 2014-05-29
Something along these lines could work.
First create a file which is identical to your stab.in except that it doesn't say **a=1** or **a=2**, but **a=placeholder**, and name the file stab.in.template.

Then write a little script:```
#!/bin/bash
for i in {1..100}
do
  sed s/placeholder/$i/ stab.in.template >stab.in
  pipe_sb
done
```
Details depend on how you call pipe_sb and the exact formatting of stab.in. This also assumes the word **placeholder** doesn't occur anywhere in stab.in, but as it is an arbitrary word this can't be a problem.

---

### Post by davea42 on 2014-05-29
If stab.in, and if you have permissions such that you can edit it and write back to it, then
you could simply use sed or equivalent tool to update stab.in and write it back
and rerun the thing using stab.in.  Of course you have to carefully consider
exactly what is going on and considering what might happen if you make a small
mistake in the script along the way...

---

### Post by davea42 on 2014-05-29
Ok. Impavidus got there first. Nice example.

---

### Post by abhishek11 on 2014-05-30
Thank you ! This worked for me.

---

