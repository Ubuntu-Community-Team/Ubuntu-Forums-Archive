---
title: "Help with grep and regex"
date: 2008-03-25
forum: General Help
---

### Post by raichle on 2008-03-25
Hi all, not sure if this is the right place to post this or not, but figured it was worth a try.

I am new to Linux and trying to learn grep/sed and regex but can't figure out how to do a few things.

I have a file w/  13,000 lines in this format

name - location

I want to grep out all of the names to one file and the locations to another.  In addition, I have some that have hypenated names so I need to first grep out the ones that have more than 1 "-".

Can anyone help me figure this out?   I guess the first step is to find out which lines have more hyphens right?  Is there a better way to approach this?

---

### Post by finer recliner on 2008-03-25
grep is used as pattern matching for whole lines of text. it sounds like you're trying to use it to grab a specific portion of each line (rather than the whole line).

i would recommend the command awk instead, though i dont have as much experience using it.

enjoy

---

### Post by nick_h on 2008-03-25
Have a look at the *cut* command:
```
man cut
```

---

### Post by finer recliner on 2008-03-25
cut probably wont work, because every name is going to be a different length, so you cant  use a static number that just grabs the first 12 (or something) characters of every line. you also cant use the delimiter option with the hyphen (-) because as the OP said, some of the names have a hyphen in it.

---

### Post by lloyd_b on 2008-03-25
> **raichle said:**
> Hi all, not sure if this is the right place to post this or not, but figured it was worth a try.

I am new to Linux and trying to learn grep/sed and regex but can't figure out how to do a few things.

I have a file w/  13,000 lines in this format

name - location

I want to grep out all of the names to one file and the locations to another.  In addition, I have some that have hypenated names so I need to first grep out the ones that have more than 1 "-".

Can anyone help me figure this out?   I guess the first step is to find out which lines have more hyphens right?  Is there a better way to approach this?

A question: are there *always* spaces on both sides of the dash that separates name and location?  If so, the first step would be to replace that "<space><dash><space>" with a unique separator (I'll use ":" in this example, as that shouldn't appear in the data):
```
sed -i "s/ - /:/g" datafile
```
(note that this changes the file - you may want to work from a copy just in case)

With that done, the "cut" command can handle the rest:
```
cut -d ':' -f 1 datafile > names.txt
cut -d ':' -f 2 datafile > locations.txt
```

Needless to say, this assumes that that separator is in fact "<space><dash><space>" as in your example, and that any hyphenated names do *not* have spaces around the dashes (a reasonable assumption).

Lloyd B.

---

### Post by tomchuk on 2008-03-25
Assuming that the delimiter is a space, followed by a hyphen, followed by a space, and the same pattern is not used for hyphenated names, the following should work:
```

awk -F' - ' '{print $1; print $2 > "/dev/stderr"}' > names.txt 2> locations.txt < input.txt

```

The above will read from input.txt and create (or overwrite!) the files names.txt and locations.txt

---

### Post by ghostdog74 on 2008-03-27
```


awk -F"-" '{
 print $1 >  "name.txt"
 print $2 > "location.txt"
}' file

```

---

