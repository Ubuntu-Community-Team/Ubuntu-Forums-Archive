---
title: "Danish letters in kile."
date: 2006-10-18
forum: General Help
---

### Post by stefanC on 2006-10-18
Hello, making my first post here, hope it is the right forum else feel free to move it.

I just got my duel-boot system to work, and I was thinking about making my first LaTeX text in kubuntu. But I cant get the Danish letters (æ, ø  and Å) to work.
If I make a LaTeX to pdf in kile I can just see some strange characters. But if I make a LaTeX to pdf in TeXniCenter whit the same file, It works just fine.
So anyone know what to do?

---

### Post by aktiwers on 2006-10-18
Havent used LateX much but isnt it just:

\ae                     becomes æ
\o                      becomes ø
\aa                     becomes å

Og det samme med store bogstaver.

Edit:
Velkommen til! :KS

---

### Post by stefanC on 2006-10-18
well I run in XP I can just type a ø and then it becomes ø. So I would like the same in kubuntu

---

### Post by pkslot on 2006-10-18
Have you tried with the html code:

&aelig;    = æ
&oslash;   = ø
&aring;    = å

Maybe that does the trick ;)

..... og ja, velkommen til :mrgreen:

---

### Post by stefanC on 2006-10-18
well I there is no problem in getting it to show æ, ø and å in the pdf.. I would just like that my .tex file would look like this:
på
And not
p\aa

Then I dont have to type that much :P

---

### Post by stefanC on 2006-10-19
bump

---

### Post by terrax on 2006-10-24
You can just change the ascii set to utf8 from latin1.

Did the trick for me.

--------------------------------EDIT

Det er dejligt ikke at skulle skrive de kommandoer :-)

---

### Post by McDuff on 2006-11-27
i'm not danish, but i'm having the same problem entering non-ascii-letters (german, french, spanish,...). i haven't found any solution yet. but this seems generally to be a problem with kde/qt-apps in ubuntu. amarok and firstclass client show the same problem (non-ascii-input giving nonsense-output). what's more, non-ascii-letters in file- and directory-names aren't schown correctly, whereas those inside the texts are.

could anybody help to find the bug?

---

### Post by Sharpeee on 2007-03-01
I've had the same problem. With a lot of Googling I found this solution:

\usepackage[utf8]{inputenc}

You just have to save the file in the same encoding.

---

