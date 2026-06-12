---
title: "[SOLVED] Is there a crossword solver available for Ubuntu?"
date: 2008-05-05
forum: General Help
---

### Post by Rytron on 2008-05-05
Hi,
Is there a crossword solver available for Ubuntu?
When I used Windows Xp as my primary OS (back in the dark days), I used a superb program titled Foreword. It was useful for crosswords. When you typed in a word for example p?pe?, it would give back suggestions. The ? marks represented the missing words. For the above example the suggested word(s) would be paper. 

Here is the link to the Windows program to further explain.

[http://www.topshareware.com/ForeWord-download-10385.htm]("http://http://www.topshareware.com/ForeWord-download-10385.htm")

If there isn't a program to do this in Ubuntu, is there a method in the command line to do this?

Any help would be greatly welcomed.

Thank.

---

### Post by sindhu_sundar on 2008-11-30
bump

---

### Post by PocketDog on 2008-11-30
I'm not aware of any software sorry. But [here](http://www.allmixedup.com/xword.cgi)'s a web one I use.

---

### Post by blackened on 2008-11-30
I tried two different versions of Foreword through WINE and couldn't get either one to work properly, nor could I find a viable linux-native replacement. Give PocketDog's suggestion a shot.

---

### Post by Rytron on 2008-11-30
I have settled for 
[http://www.crosswordsolver.org/](http://www.crosswordsolver.org/)
and
[http://www.oneacross.com/](http://www.oneacross.com/)

---

### Post by glymph on 2009-03-07
I started looking around for a commandline application for this, then realised that the tools are already available, using the word list, e.g.

$ grep -i ^g....h$ /etc/dictionaries-common/words 
Gareth
Gienah
Grinch
Guelph
Gullah
galosh
garish
glitch
grouch
growth

There may be a better way, I don't know. I leave the process of creating this as an alias or script as an excercise for the reader.

Dom

---

### Post by Rytron on 2009-03-08
> **glymph said:**
> I started looking around for a commandline application for this, then realised that the tools are already available, using the word list, e.g.

$ grep -i ^g....h$ /etc/dictionaries-common/words 
Gareth
Gienah
Grinch
Guelph
Gullah
galosh
garish
glitch
grouch
growth

There may be a better way, I don't know. I leave the process of creating this as an alias or script as an excercise for the reader.

Dom

Hi glymph. Thank you so much. Thats got to be one of the coolest lines of code ever.
:popcorn:

---

### Post by pabc on 2011-05-01
just a step on for a zenity gui for the code above

requires zenity (which i think is installed as a base app

```
sudo apt-get install zenity
``````
#!/bin/sh
#
#
# Simple script to grep possible crossword solutions against simple words
# Phil Abbott - abbott_pa@yahoo.co.uk

mask=`zenity --entry --text="enter your letters and blanks(.) eg h.lp" --title "word finder"`

grep -i ^$mask$ /etc/dictionaries-common/words > /tmp/results.txt
result=`cat /tmp/results.txt`

for word in $result
    do
    wrappedresult="$wrappedresult $word"
done


zenity --info --title="Results" --width=400 --text="               \n$wrappedresult"

```

then add it as a launcher

---

### Post by Rytron on 2011-05-03
Hi pabc. Your code did not work for me.

---

### Post by gandaran on 2011-05-03
> **Rytron said:**
> Hi pabc. Your code did not work for me.
what are the errors?
first you have to change permissions, mark the file executable 
the code works very well with a launcher or even as a nautilus script.

---

### Post by Rytron on 2011-05-04
> **gandaran said:**
> what are the errors?
first you have to change permissions, mark the file executable 
the code works very well with a launcher or even as a nautilus script.

I made it executable and selected 'run in terminal'. Here are the results:

---

### Post by pabc on 2011-05-05
i admit defeat. I can't think why you are getting that error. The code I provided is a copy/paste from a working script.
 
You have zenity installed as shown by the first image.
 
in a terminal enter
 
```
 
grep -i ^h.ll$ /etc/dictionaries-common/words > /tmp/results.txt
cat /tmp/results.txt


```
 
and paste the result so I can see if the raw command is working or if it is something in my script

---

### Post by Rytron on 2011-05-05
Sure pabc, here you are:

```
$ grep -i ^h.ll$ /etc/dictionaries-common/words > /tmp/results.txt
$ cat /tmp/results.txt
[COLOR="Indigo"]Hall
Hell
Hill
Hull
hall
hell
hill
hull[/COLOR]
```

It works properly, yes?

---

### Post by pabc on 2011-05-05
that is the exact output it shoud produce so you have zenity, grep and the dictionary to check against.
 
in a terminal can you navigate to the folder where you have saved the script and type
 
```
 
sh scriptname

```
 
(swapping 'scriptname' for whatever you saved it as)
 
then enter your search term as before in the prompt. when it fails paste all the text from the terminal you ran it from to try and give me more of a clue?
 
Anyone else spot the problem I'm missing?

---

### Post by Rytron on 2011-05-05
Same as before, pabc.

```
$ sh CS.sh 
grep: progname=zenity;: No such file or directory
grep: RGBA=on: No such file or directory
grep: h.lp$: No such file or directory
```

---

### Post by satanselbow on 2011-05-05
You know know this is one of the coolest threads on the forum at the mo - I gotta learn me some bash :popcorn::popcorn::popcorn:

---

### Post by Rytron on 2011-05-05
I've slightly modified the previous code line by pabc.

This should suffice:
```
grep -i ^dr.l.$ /etc/dictionaries-common/words > /tmp/results.txt; gedit /tmp/results.txt
```

---

### Post by Rytron on 2011-05-06
I just ran the bash script in a VirtualBox Ubuntu 10.10 and it works fine. Therefore the issue is with my main OS!

---

### Post by coldraven on 2011-05-06
Just install Artha from the Software Centre then add it to your Startup applications.
If you highlight a word anywhere pressing Ctrl+Alt+W will invoke Artha.
See the screenshot

---

### Post by Rytron on 2011-05-06
> **coldraven said:**
> Just install Artha from the Software Centre then add it to your Startup applications.
If you highlight a word anywhere pressing Ctrl+Alt+W will invoke Artha.
See the screenshot

Sweet! Thank you coldraven. Although I was given the combo "[COLOR="Indigo"]*Ctrl+Alt+a*[/COLOR]" when I launched Artha.

---

