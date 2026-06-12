---
title: "Uniq Command"
date: 2016-12-13
forum: General Help
---

### Post by AUDIOTEK on 2016-12-13
```
Use the uniq command to remove duplicate lines from the custList2.txt file. After that, use sort to pipe the custList2.txt file through uniq.
```

```
 uniq custList2.txt 
```

```
 sort custList2.txt | uniq 
```

First command works but "use sort to pipe the file through uniq I get incorrect"

I don't need the answer I'd like to know what I'm missing!!!

---

### Post by TheFu on 2016-12-13
Please use default fonts here.

Try -u option.

I was hit by uniq not working as expected last week as well.  The manpage has the option needed now. Don't know why they changed the behavior, just that there is an option, -u, to make it do what you/I need.  Seems strange to need to specify an option for a 1-trick-tool like uniq to print the unique lines ....  Perhaps it is a bug?

---

### Post by SeijiSensei on 2016-12-13
I use 
```
sort < file | uniq
```
and it seems to work as expected.  This is in 14.04 and also on CentOS 6.  

Maybe a subtle difference between the way sort handles a piped input versus the file name on the command line?

---

### Post by TheFu on 2016-12-13
Been using sort|uniq like the op for 20+ yrs.  It was just recently that it stopped working the expected way. Maybe it is a 16.04 thing?  I dunno.

---

### Post by AUDIOTEK on 2016-12-14
I sent an email to my instructor but no replies yet.  if I run the same command on my machine with Ubuntu 16.04 I get no error.   Could it be the online simulator?  It's chopped but at the bottom of the picture it says INCORRECT.


[IMG][IMG]http://i65.tinypic.com/14mqlpy.png[/IMG][/IMG]

---

### Post by steeldriver on 2016-12-14
I think it's going to be hard to pinpoint exactly what's going on without knowing the exact contents of the custList2.txt file

It kind of looks like it contains multiple blocks of adjacent duplicates - and that 'uniq' is aliased to 'uniq -c'. Try with

```

\uniq custList2.txt

```

to ensure that no aliasing is involved

---

### Post by AUDIOTEK on 2016-12-14
That's the idea   Multiple entries with same value in a text file, I think the output has to remove duplicates that are not side by side using uniq and pipe sort (will list output of the file in order in accordance to the first column) through uniq.  

In the tutorial it's simple it's the following command

```
 sort custList2.txt | uniq 
```

Works on my Ubuntu machine but not on the online simulator.  It's for my Linux+ course it's not a test question but a lab question. I usually do my research myself when I'm stuck and find the answer but I'm really stuck with that one.

---

### Post by TheFu on 2016-12-14
Completely understand the situation.  I don't have an issue helping.

$ sort file.txt | uniq 

That should work. Input:
```
33
334
335
3336
335
1
2
43
5
6
7
88
88

```
```
$ sort TTTT | uniq

1
2
33
3336
334
335
43
5
6
7
88

``` Works on 16.04 with bash as my shell and ZERO aliases related to these commands.  Only 1 "335" and only 1 "88".  Also worked the same on Debian 8.6. And also worked on 14.04.5, as expected.  Need to see your custList2.txt.

---

### Post by Habitual on 2016-12-14
> **steeldriver said:**
> I think it's going to be hard to pinpoint exactly what's going on without knowing the exact contents of the custList2.txt file

It kind of looks like it contains multiple blocks of adjacent duplicates - and that 'uniq' is aliased to 'uniq -c'. Try with

```

\uniq custList2.txt

```

to ensure that no aliasing is involved

```
type uniq
``` is very verbose also.

---

### Post by AUDIOTEK on 2016-12-14
I think the answer is this ```
$ sort file.txt | uniq 
``` like you mentioned.   I'll wait for the instructor to get back I have a feeling there's something wrong with their online simulator.

> **TheFu said:**
> Completely understand the situation.  I don't have an issue helping.

$ sort file.txt | uniq 

That should work. Input:
```
33
334
335
3336
335
1
2
43
5
6
7
88
88

```
```
$ sort TTTT | uniq

1
2
33
3336
334
335
43
5
6
7
88

``` Works on 16.04 with bash as my shell and ZERO aliases related to these commands.  Only 1 "335" and only 1 "88".  Also worked the same on Debian 8.6. And also worked on 14.04.5, as expected.  Need to see your custList2.txt.

---

### Post by AUDIOTEK on 2016-12-15
So I think there's an issue with their online simulator  I tried it again this morning just for fun
[COLOR=#000000]Use the uniq command to remove duplicate lines from the custList2.txt file. After that, use sort to pipe the custList2.txt file through uniq.

[/COLOR]
[COLOR=#000000][/COLOR]


```
 uniq custList2.txt
```

then use sort to pipe the .txt file through uniq

```
sort custList2.txt | uniq 
```

And got a correct.  Same issue with question 2 for the lab  That one was super easy but  I still got an incorrect.  

Q:Make a new directory called dir2. After the new directory is built, move all the cust files to dir2. ( There's a bunch of .txt  files in that directory many using custListxx.txt for exemple; custList1.txt  custList2.txt    custList3.txt etc...)

To create directory;

```
mkdir dir2
```

Use the move command to move all the files with wild card cust

```
mv cust*.txt dir2/
```

Anyways  I passed that lab but it was very frustrating!!!!    Now to the post assessment exam!  Wish me luck!!

---

### Post by Habitual on 2016-12-15
> **AUDIOTEK said:**
> Wish me luck!!You should be fine, You are asking "the right questions" IMO. ;)
Good Luck!

---

