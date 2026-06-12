---
title: "Join two files, but start on the same line"
date: 2007-05-25
forum: General Help
---

### Post by nvonkorff on 2007-05-25
Hi,

This isn't an Ubuntu specific question - more of a general Linux/Unix question.

Let's say I have a.txt and b.txt, and I want to join them together in a new file called c.txt.... simple:

cat a.txt b.txt > c.txt

My problem is, that I want the last line of a.txt and the first line of b.txt to continue on from each other. e.g:

**a.txt:**
[I]Hello
I want something to be joi
[/I]
**b.txt:**
[I]ned together with no line break
That would be good[/I]

If I just cat the files together, I get:
**c.txt**
[I]Hello
I want something to be joi
ned together with no line break
That would be good[/I]

I am at my wit's end, hence the post. I just can't figure it out. Could someone please let me know of a way to end up with this result?

**c.txt**
[I]Hello
I want something to be joined together with no line break
That would be good[/I]

Thanks and regards,

Nick.

---

### Post by spin2cool on 2007-05-25
'cat' will work fine for this purpose.  The problem is with your files.  There must be a trailing newline at the end of your first file.

In your example, a.txt actually looks like this:
```

Hello**\n**
I want something to be joi**\n**

```

Remove the trailing newline and you'll be fine.

---

### Post by hartz on 2007-05-25
tricky.  But possible.

Script: Newcat
====
```
#!/bin/sh
N=$#
C=1
while [ $C -lt $N ]
do
  IFILE=$1
  < $IFILE awk '{if(NR>1) {print(PREV)}; PREV=$0} END {printf("%s",PREV)}'
  shift
done
cat $1
```

Put the above into a text file, maybe call it "newcat".
then make the script executable, with this command
```
chmod +rx newcat
```

Then use the script like this
```
./newcat file1 file2 file3 file4
```

---

### Post by hartz on 2007-05-25
> **spin2cool said:**
> 'cat' will work fine for this purpose.  The problem is with your files.  There must be a trailing newline at the end of your first file.

In your example, a.txt actually looks like this:
```

Hello**\n**
I want something to be joi**\n**

```

Remove the trailing newline and you'll be fine.

The problem with this solution is that it is easier to just manually join the files than it is to remove only that last newline.  This implies that the OP wants a repeatable process (Or else he would just manually join the files)

The script I wrote does what th OP asked - it removes the last newline from every input file except the last input file.

---

### Post by spin2cool on 2007-05-25
Yes, your solution is definitely more robust.  I (perhaps incorrectly) assumed that he was creating the files in another process.  In that case, it would probably be easier to edit the original script to no longer add that last newline.

---

### Post by WW on 2007-05-25
Here's different version, using perl:

**newcat2**
```

#!/usr/bin/perl

undef $/;
while (<>) {
    s/(.*)\n$/\1/;
    print;
}
print "\n";

```
Example:
```

~$ cat a.txt
aaa
123
~$ cat b.txt
bbb
456
~$ newcat2 a.txt b.txt
aaa
123bbb
456
~$ newcat2 a.txt b.txt a.txt
aaa
123bbb
456aaa
123
~$

```

---

### Post by ruy_lopez on 2007-05-25
Try "paste"

```
paste a.txt b.txt > c.txt
```

Paste adds a tabspace between the columns, so we can filter them out.

```
paste a.txt b.txt | sed 's/\t//' > c.txt 
```

This should get you closer to what you want.

eg

```

cat a.txt
hello
hello

cat b.txt
world
world

paste a.txt b.txt
hello   world
hello   world

paste a.txt b.txt | sed 's/\t//'
helloworld
helloworld
```

---

### Post by WW on 2007-05-25
But he only wanted the end of the first file to join with the beginning of the second.

(And what happens if the files already contain tabs?)

---

### Post by stylishpants on 2007-05-25
"paste" is cool but  it's not what the OP wanted.  Line 1 of the resulting file is a collection of the line 1s from all the files, and so on.  The OP wanted something like 'cat' that doesn't mix the text of the files.


My contribution is in ruby:
```
fhanson@fhanson:/tmp/test$ cat one
I want something to be joi

fhanson@fhanson:/tmp/test$ cat two
ned together with no line break

fhanson@fhanson:/tmp/test$ ruby -e 'print ARGV.map {|f| File.open(f).read.chomp}' one two
I want something to be joined together with no line break


```

---

