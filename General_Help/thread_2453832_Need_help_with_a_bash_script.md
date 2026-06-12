---
title: "Need help with a bash script"
date: 2020-11-17
forum: General Help
---

### Post by coley9225 on 2020-11-17
Hello again friends and neighbors. I recently finished writing a bash script to do simple addition problems. It uses a lot of different thing, zenity, function, while loop,etc. Now I'm trying to write one to do simple subtraction problems, but having trouble with number generation. I need to generate 2 random numbers, $x and $y, so that $x is a number between 1 and n (never return o), and $y is a number between 0 and $x. I've multiple searches and can't find a way to do this. I can duplicate my addition script for everything else, if I can get the numbers to do like I need for this. I'm writing these scripts( and soon a multiplication and division) to teach my grandchildren simple math skills, and the CLI versions to teach them some command line use as well.  I added attachments with my addition script and my (failed) attempt at my subtraction script so you can see what I'm trying to achieve. Any help would greatly appreciated, as always. Thanks
[ATTACH]287380[/ATTACH][ATTACH]287381[/ATTACH]

---

### Post by Holger_Gehrke on 2020-11-18
Random numbers can be read from the variable RANDOM. The numbers generated when reading from RANDOM are between  0 and 32767. You can use the modulo / remainder operator ('%') to get a random number smaller then a given upper bound. So
```

echo $(( RANDOM % 50 + 1 ))

```
will print a number between 1 and 50 (RANDOM % 50 produces a number from 0 to 49 inclusive). To get two random numbers with the second being smaller than the first you'd do something like
```

a=$(( RANDOM % 100 + 1 ));b=$(( RANDOM % a + 1 )); echo $a $b

```
This produces a random number a from 1 to 100 and b from 1 to a.
Holger

---

### Post by dragonfly41 on 2020-11-18
To create a zenity like GUI where you can add popup quiz questions you might like Actiona which is in repo.
Takes a bit of time to understand and since the Code widget uses Actionscript2 (extension *.as from old Flash days) 
I use Sublime Text Editor with Actionscript2 package. The script is first developed using GUI then it runs without GUI through command ```
actexec myquiz.ascr
```.

If you prefer making a visual quiz game you can look at [SnapSVG]("http://snapsvg.io/start/") and similar.

---

### Post by coley9225 on 2020-11-18
First...Holger, thanks for the input. From what I've read and experienced,  [FONT=Ubuntu Mono, monospace][COLOR=#000000]a=$(( RANDOM % 100 + 1 )) will return a number between 0 and 100, I need to be sure that 0 doesn't come up for first number. As for the second number, I've tried my way around this idea, y=$(RANDOM% <$x+1), etc. I will give this a shot and see what happens. Dragonfly, I started using zenity because in was installed with lubuntu 20.04, but I will definatly check this out. If I can make a script that can run with GUI or from command line without rewriting my script, I would save me some time, plus it is an opportunity to expand my knowledge base. I've only been using linux since Feb. of this year, so still learning and willing to explore new avenues to get to my destination. Thanks so much for the tip.I'll reply( and mark solved if successful) after I try the new number method. You guys are great, I really appreciate the fact that the linux community is so very helpful, and patient,  to beginners such as myself. Keep up the good work.[/COLOR][/FONT]

---

### Post by ActionParsnip on 2020-11-18
The
```

+1

```
part of the code ensures that zero is never chosen

Without it the number is from 0 to 99, with the +1 it's from 1 to 100

HTH

---

### Post by coley9225 on 2020-11-18
OK...so I ran the subtraction script 4 or 5 times, and it works perfectly. I can now mark this as solved. Thanks so much for the help, I really appreciate it.

---

