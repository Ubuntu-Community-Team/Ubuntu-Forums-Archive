---
title: "Move cursor in an Ubuntu terminal with the mouse"
date: 2013-02-21
forum: General Help
---

### Post by choinul on 2013-02-21
Hello everyone, 

When I have long command lines in my Ubuntu Terminal, I want to be able to use the mouse to move the pointer to directly modify the command in this position. I didn't find if it is possible to make it. Any ideas?

Thanks for your help. :)

---

### Post by dino99 on 2013-02-21
i'm using the right/left/up/down arrows from the numpad, its fast / easy.
by the way, the mouse works inside the terminal of course.

---

### Post by choinul on 2013-02-21
On my Ubuntu Terminal, Up and Down shows last commands. And I will prefer to use the mouse. 

But I just discover CTR + Right and CTR + LEFT that are quite useful too.

---

### Post by dino99 on 2013-02-21
> **choinul said:**
> On my Ubuntu Terminal, Up and Down shows last commands. And I will prefer to use the mouse. 

But I just discover CTR + Right and CTR + LEFT that are quite useful too.

is your mouse working normally  everywhere, or is it only an issue inside the terminal ? which kind of mouse is it ?

---

### Post by choinul on 2013-02-21
Yes, I have no problem with my mouse. ;) For example, I can select something in the terminal, but I can't move the text cursor.

I think the default behaviour of the mouse on Ubuntu Terminal is like that. And I want to see if it is possible to modify it?

---

### Post by rnerwein on 2013-02-21
> **choinul said:**
> On my Ubuntu Terminal, Up and Down shows last commands. And I will prefer to use the mouse. 

But I just discover CTR + Right and CTR + LEFT that are quite useful too.
hi
this comes from (up / down) bash-history. it is set global or in your ~/.bashrc.
you can even serach vor prefiouse commands by hitting:
Esc then type /mor  --> if you type before the command will come up and you can run it again (you can even edit the line - but this another story).
type in a terminal: env | grep HISTSIZE to see the size of your bash-history.
and by the side: terminal don't know mice :-)
ciao

---

### Post by choinul on 2013-02-21
Ok, good to know.

But if it is possible to select with the mouse in terminal, it should be possible to move the text cursor also?

---

### Post by rnerwein on 2013-02-21
> **choinul said:**
> Ok, good to know.

But if it is possible to select with the mouse in terminal, it should be possible to move the text cursor also?
hi
oh i forgot. you can copy text from terminal to terminal or terminal to editor and .....
bring your mouspointer to the beginning of the text you want to copy.
pull down the left mouse buttom and (left mouse buttom down) and mark the text you want. release the mouse buttom and go to the place where you want the copied text.
now --> middle klick --> must be there.
ciao

---

### Post by choinul on 2013-02-21
Yes, I know, but what I am looking for is to move the cursor with the mouse. :confused:

---

### Post by dcstar on 2013-02-22
> **choinul said:**
> Yes, I know, but what I am looking for is to move the cursor with the mouse. :confused:

A terminal is a text based interface that was in use decades before the mouse (and GUI) was invented. Do not expect it to do things it was never designed for.

You can try using the **gpm** package as it can add **some** mouse functionality to a terminal session.

---

### Post by Habitual on 2013-02-22
> **dcstar said:**
> a terminal is a text based interface that was in use decades before the mouse (and gui) was invented. Do not expect it to do things it was never designed for.+1

---

### Post by stinkeye on 2013-02-22
You may find this doc useful.
About two thirds down the page under the heading "Change the text".
> ctrl+a or Home 	
 Moves the cursor to the start of a line.

ctrl+e or End 	
 Moves the cursor to the end of a line.

esc+b 	
 Moves to the beginning of the previous or current word.

ctrl+k 	
 Deletes from the current cursor position to the end of the line.

ctrl+u 	
 Deletes from the start of the line to the current cursor position.

ctrl+w 	
 Deletes the word before the cursor.

alt+b 	
 Goes back one word at a time.

alt+f 	
 Moves forward one word at a time.

alt+c 	
 Capitalizes letter where cursor is and moves to end of word.
[**_[COLOR="DarkRed"]https://help.ubuntu.com/community/UsingTheTerminal[/COLOR]_**]("https://help.ubuntu.com/community/UsingTheTerminal")

---

