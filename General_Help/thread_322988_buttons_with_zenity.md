---
title: "buttons with zenity"
date: 2006-12-21
forum: General Help
---

### Post by Green_Star on 2006-12-21
I want to write (using zenity or some thing else) a program which will have buttons on the window and when ever i click the buttons it should execute assigned unix commands in the back ground without closing that window. for example like calculator. can some one give some idea like how to write such things?

---

### Post by mrunion on 2006-12-21
I would think many things would work to give you a GUI and execute code/functionality.  Python, Java, etc.

---

### Post by christhemonkey on 2006-12-21
For Zenity, which seems to fit your bill perfectly,
You should read:
```
man zenity 
```

or for an online version:
[http://pwet.fr/man/linux/commandes/zenity](http://pwet.fr/man/linux/commandes/zenity)

You then put the Zenity code into your bash script.
Sorted!

---

### Post by Green_Star on 2006-12-21
I saw about zenity, but zenity is more like a dialog box, it will close after clicking a button(i am not sure whether i can create a custom button with my own name). If i am missing any thing about zenity please let me know.

I can do a good shell programs, but i am not good at programming languages like python, java ...etc. that is the reason i am looking for something which can use with bash programs.

---

### Post by bodhi.zazen on 2006-12-21
I second the vote for zenity.

It will do more then dialog boxes.

christhemonkey: Nice links ;)

---

### Post by Green_Star on 2006-12-22
let me take an example, i have three buttons called "A", "B" and "C" and one display box(or kind of test area), so when ever i click a button then that button lable should be shown in display box. As per my understanding about zenity, i can not do that. 

Any suggissions?

---

### Post by christhemonkey on 2006-12-22
**@bodhi.zazen** Cheers ;)


**@Green_Star**,

I dont think Zenity can do that no, just taking a quick look at dialog which might be close to what you want if you use it with the --nocancel option (although its not quite what you want:()

Thats about it for scriptable options, you can always use Glade not sure if it hs support for bash commands, but that would do the job nicely.

---

### Post by koenn on 2006-12-22
I've only done e few little things with zenity, but from what I know its oriented toward getting user input, then proceed with the script, so at best you could get a new enity dialog box. Might work, if the 2nd window appears at the same place on screen where the previous window was. 

'dialog' can probably be used the same way - just 'redraw' the screen with new output.

---

### Post by koenn on 2006-12-22
here's a quick and dirty attempt that does more or less what you describe, with zenity
```

REPLY=$(zenity  --list --column="check" --column="Label" --radiolist \
                false "A" \
                true "B" \
                false "C" \
);

zenity --info --text=$REPLY


```
as said before, zenity (and dialog' are design to produce dialogs for interaction with users, so they have standard yes/no OK/Cancel buttons (and info/warning/ ...icons). dialog has some options to overwrite the standard labels, zenity may have too, but even then you probably will never get more than 1, 2 or 3 buttons, de. If you want to use this for real applications, you'd have to start looking at a real programming language, or create html for your user interface + scripting behind it for the logic.

---

