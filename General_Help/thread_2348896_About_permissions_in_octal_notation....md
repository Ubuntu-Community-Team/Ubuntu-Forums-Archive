---
title: "About permissions in octal notation..."
date: 2017-01-08
forum: General Help
---

### Post by javierdl on 2017-01-08
I'm just trying to better understand this...

I understand the following: 755

[COLOR=#111111][FONT=Ubuntu]For **owner** it is 4+2+1=7
For **group** it is 4+0+1=5
For **other** it is 4+0+1=5 
However, (here is where I don't get it): Let's go with a slightly different example, still with 755 though. But instead of the break down we have above, couldn't it have been the one below, too?: 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For [/FONT][/COLOR]**owner**[COLOR=#111111][FONT=Ubuntu] it is 4+1+2=7[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For [/FONT][/COLOR]**group**[COLOR=#111111][FONT=Ubuntu] it is 4+0+1=5[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For [/FONT][/COLOR]**other**[COLOR=#111111][FONT=Ubuntu] it is 4+1+0=5

I hope the answer is "no".

Thanks guys,

JDL[/FONT][/COLOR]

---

### Post by Dennis N on 2017-01-08
The right-most bit in a binary number is 0 or 1 and the place value is 1, so the value is either 0 or 1 - thats why you cant get a 2 there.

Permission numbers 7,5,5 are octal ( base 8) and you convert them to binary (base 2) to read the permissions that are set:
The calculation for owner is 7 = (1x4) + (1x2) + (1x1) = 111 binary representing r,w,x permissions all set (1).  for group, 5 = (1x4) + (0x2) + (1x1) = 101 binary, representing r,x permissions are set (1) and w permission is not set (0).

And working in reverse, permissions = read and write only = rw- = 110  binary = 6 octal

---

### Post by ajgreeny on 2017-01-09
Here's a simple text file I saved a long time ago as a reminder to me of how these octal permissions work.
I hope you may find it useful as well.
> Summary of the meanings for individual octal digit values:

The digits are in the order:-  owner:group:others

0 --- no permission
1 --x execute 
2 -w- write 
3 -wx write and execute
4 r-- read
5 r-x read and execute
6 rw- read and write
7 rwx read, write and execute

These are the examples from the Symbolic notation section given in octal notation:

    * "-rwxr-xr-x" would be represented as 755 in three-digit octal.
    * "-rw-rw-r--" would be represented as 664 in three-digit octal.
    * "-r-x------" would be represented as 500 in three-digit octal.

---

### Post by Morbius1 on 2017-01-09
Octal 4 in binary = 100
Octal 2 in binary = 010
Octal 1 in binary = 001

rwx
100 Read
010 Write
001 Execute
=== 
111 That&#8217;s a 7 in octal.

100 Read
001 Execute
010 Write
===
111 That's a 7 in octal

The "combination" of each column will be a Logical OR of it's components so a "0 OR 1 OR 0" = 1 just as a "0 OR 0 OR 1" = 1

I recon' it don't matter none which way you think it's converting octal to binary.

---

