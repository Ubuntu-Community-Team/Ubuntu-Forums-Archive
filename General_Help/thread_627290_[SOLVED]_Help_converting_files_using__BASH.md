---
title: "[SOLVED] Help converting files using  BASH"
date: 2007-11-29
forum: General Help
---

### Post by uclalinux on 2007-11-29
hi I am trying to write a Bash scrip that will read a bunch of files in a directory and convert them one at a time using mencoder. I am a nood when it comes to programming. 
. 

This is what I have,  I know its way wrong. Could someone point me in the right direction
Thanks 

```
#!/bin/sh 
for i in '/home/uclalinux/Desktop/familyguy/*'
do
mencoder '$i.avi' -vf scale=176:144 -oac mp3lame -ovc lavc -o '$i'.3gp
done
```

---

### Post by fatmano on 2007-11-30
#!/bin/sh 
for i in '/home/uclalinux/Desktop/familyguy/*'
do
mencoder '$i.avi' -vf scale=176:144 -oac mp3lame -ovc lavc -o '$i'.3gp
done

So here is the basic problem:

for i in '/home/uclalinux/Desktop/familyguy/*' 

is taking /home/uclalinux/Desktop/familyguy/* and putting that into i
so in your 3rd line you would end up with something like:
mencoder /home/uclalinux/Desktop/familyguy/*.avi -vf .....

I believe what you want to do would be to:
```

for i in `ls /home/uclalinux/Desktop/familyguy/*.avi`
do
  pre=${i%%\.avi}
  mencoder $i -vf scale=176:144 -oac mp3lame -ovc lavc -o ${pre}.3gp
done
```

please take note that the for statement is a back tic not a single quote.  The character is typically underneath the ~ on the keyboard.

HTH

-eo

---

### Post by geirha on 2007-11-30
Your thinking is correct, but the syntax is wrong. Take the following test case:
```
$ mkdir /tmp/test
$ touch "/tmp/test/file a" "/tmp/test/file b"
$ ls -l /tmp/test
total 0
-rw-r--r-- 1 geirha geirha 0 Nov 30 09:43 file a
-rw-r--r-- 1 geirha geirha 0 Nov 30 09:43 file b

```

And then try using different types of quoting with a for-loop:
```

$ for file in '/tmp/test/*';do echo $file; done
/tmp/test/file a /tmp/test/file b
$ for file in "/tmp/test/*";do echo $file; done
/tmp/test/file a /tmp/test/file b
$ for file in /tmp/test/*;do echo $file; done
/tmp/test/file a
/tmp/test/file b

```
Quoting here puts all files in one string, so you want to remove the quotes in this case.

On your mencoder-line, you should realize that there's a significant difference with using single quotes and double quotes. Test with:
```
for file in /tmp/test/*; do cat $file; done
for file in /tmp/test/*; do cat "$file"; done
for file in /tmp/test/*; do cat '$file'; done
```

As you'll notice, double-quotes is what you want to use here.

---

### Post by uclalinux on 2007-11-30
Thanks Geirha & Fatmano, Fatmano your code worked could, you tell me what this ```
pre=${i%%\.avi}
``` does? 

Also what are the best books or websites to learn coding. 

Thanks


Oh, also why do I  use tic's (`) instead of single quotes(')

---

### Post by geirha on 2007-11-30
I would recommend reading [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
Chapter 3.3 explains the differences of the quotes
Chapter 3.4(.5) explains the `back ticks`
Chapter 10.3(.3.2) explains the ${i%%\.avi}

---

### Post by uclalinux on 2007-11-30
Thanks for the follow up Geirha

Would you know the correct wget command to download the web page for off line viewing?

---

### Post by fatmano on 2007-11-30
> **uclalinux said:**
> Thanks Geirha & Fatmano, Fatmano your code worked could, you tell me what this ```
pre=${i%%\.avi}
``` does? 

Also what are the best books or websites to learn coding. 

Thanks


Oh, also why do I  use tic's (`) instead of single quotes(')

The code pre=${i%%\.avi} is a way to split a variable.  Let me break it up for you:

obviously pre=   is assigning a variable called pre

using a $ in this case says I am looking for a variable, also obvious to you based on your previous post

the { } in this case are going around my variable name so the parser knows where my variable name begins and ends. These are optional, but become needed in cases like this. I used it in the previous post around ${pre} so the parser would recognize my variable and know where the name stopped and other constants began.

the %% inside the {} says : in the variable i look for the string .avi and return everything to the left of it.  This basically got me the file name w/o the extension.  ## works the other way. 

there is also a \ in there before the . (dot)  the dot is a special character so I need to escape it.  The \ says dont interpret the dot just look for it.  You can use that infront of * as well if you have a file that has a * in it and you are looking for that line.  Useful for finding comments in code etc.

so the code
pre=${i%%\.avi}
takes the variable i and grabs everything to the left of .avi and assigns it to a variable pre
ie
   episode1.avi becomes just episode1

As for the back tic this is very powerful I use it all the time.  It is a way to run a command in a command.  So in the for statement that I gave you there where back tics around the ls command.  So the ls command gets run first all of the information from that command is fed into the for loop's in statement and then read out one at a time.  Other useful uses of the back tic is moving files ie
mv someFile.txt someFile.txt.`date +%F`
This will move the file and append yyyy-mm-dd to it

HTH

-eo

btw as for books I am a _huge_ fan of the animal books (O-Reilly ).  Always written well and loads of real world examples

---

### Post by uclalinux on 2007-11-30
Thanks fatmano

---

### Post by HermanAB on 2007-11-30
The reason looping in Bash is difficult, is because you don't need it...

Here is a kezample doing a mass conversion of oggs to mp3s in one line:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

---

### Post by uclalinux on 2007-11-30
Thanks HermanAB, maybe you could explain a little about the code.. possibly  a small walk though for the less knowledgeable such as myself.

---

### Post by HermanAB on 2007-11-30
Hmm, the 'find' command is just one of those things where you have to read the man page.  It is one of the most useful commands, so it is worth the effort.

Find can do recursive searches in a directory tree and when it finds a match, it can call another program(s).  It also has the ability to pass the name of the match to this sub program (the braces).  Finally, for some odd reason, it has to terminate with a semicolon. 

So, it is one of those darned things that I keep an example around for...

Usually, with Bash, if you think you need a loop, then you should probably use 'find' and if that cannot do it either, then you should use Perl!

---

### Post by fatmano on 2007-11-30
> **HermanAB said:**
> The reason looping in Bash is difficult, is because you don't need it...

Here is a kezample doing a mass conversion of oggs to mp3s in one line:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

> **HermanAB said:**
> The reason looping in Bash is difficult, is because you don't need it...

Here is a kezample doing a mass conversion of oggs to mp3s in one line:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

Yes one can use the find command, but he was not trying to search a directory tree.  I personally like the for command, just because I find it easier to read.  As for one line you and I both know that I can make the for loop one line, but does that make it any more readable?  Here is your command in a for loop...5 characters longer and I think more difficult to grasp for someone new to the game.

for i in `find . -name '*.ogg';do sox $i $i.mp3;done

now if I only have to look in one directory, not the whole tree
for i in `ls *.oog`do sox $i $i.mp3;done
which is 9 chars shorter than the find -exec command

Here is my solution to his problem in one line:

for i in `ls /home/uclalinux/Desktop/familyguy/*.avi`;do pre=${i%%\.avi};mencoder $i -vf scale=176:144 -oac mp3lame -ovc lavc -o ${pre}.3gp;done

But why is that more understandable?

Having written code for 25 years now, IMHO unless it makes it more readable to put on one line, two lines is *way* better...unless you can make it three :D

Dont go dis-in my shell scripting for pearl.  Next you will be telling me that vi is _not_ your editor of choice, or that there is no such thing as the Tooth Fairy or Santa Claus.

The wonderful thing about computers is there no *wrong* way, as long as you get the right answer :)

-eo

---

