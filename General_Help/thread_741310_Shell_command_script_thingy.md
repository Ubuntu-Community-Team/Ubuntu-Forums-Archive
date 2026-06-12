---
title: "Shell command script thingy"
date: 2008-03-31
forum: General Help
---

### Post by Redcard on 2008-03-31
Hey all ..

I'm looking for a script/command that will go through a set of files and strip everything out between certain areas.

This does it:

grep "Opening" -A 10000 Test.txt | grep "Closing" -B 10000 > prepared.txt

But I need a way to issue it on a single directory.. and get everything in every file between "Opening" and "Closing" all concatenated into one file.  

It can be multiple steps, but not too many.

---

### Post by nickoli_02 on 2008-03-31
So.. you want to issue that command to every file in one directory and save the output in another file, is that correct?

---

### Post by Redcard on 2008-03-31
Yes, that's correct. 

Every file in the directory will get the "middle" section saved and everything else discarded.

I'd rather the output go to one file, but it can go to multiple files that I can cat in a followup step, as well

---

### Post by nickoli_02 on 2008-03-31
Oh, that should be pretty simple. Instead of test.txt, use *.txt to match all files with .txt extensions

```
grep "Opening" -A 10000 *.txt | grep "Closing" -B 10000 > prepared.txt
```

If you care about formatting then you could use awk to get the output in a form that you like.

---

### Post by Redcard on 2008-03-31
The problem is, nickoli , that includes TOO much after the second Closing.

---

### Post by nickoli_02 on 2008-03-31
What do you mean includes too much? Can you give me some examples and the output you get to help me help you? lol

---

### Post by Redcard on 2008-03-31
The files are kind of proprietary, so I can't show them.. but.. for example.. 

I think what's going on is the first command is piping the entire string to the second command, which is going up from the file.

The end result is that it's getting BEYOND the CLosing tag... 

So.. it'd be like: 

"Opening"
asfj kljalsdfjal daldsfjal;dfj alsdlfh9q485712 nlg jaskfasdf
asdkja;tj 34t ujh la
"Closing" 
324589 jasgjaldsfjlad jalu0q2475 a
asdqw4t
asfliahsdf

(The quotes are just so you can find it easier.)

When I run it on a single file, it works fine.  I'm beginning to think a foreach script might be better.

---

### Post by ghostdog74 on 2008-03-31
```

# more file
this is line 1
this is line 2
this is line 3
opening
this is line 4
this is line 5
this is line 6
closing
this is line 7
this is line 8
this is line 9
opening
this is line 10
this is line 11
this is line 12
closing
# awk '/opening/,/closing/{sub(/opening|closing/,"");print $0}' file

this is line 4
this is line 5
this is line 6


this is line 10
this is line 11
this is line 12


```
use > to redirect to new file.

---

### Post by Redcard on 2008-03-31
Sweet.  Throw an xargs on that and it does precisely what I need.  Thanks Ghost!

---

