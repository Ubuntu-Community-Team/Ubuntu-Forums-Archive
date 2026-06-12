---
title: "question about gimp."
date: 2005-06-11
forum: General Help
---

### Post by graigsmith on 2005-06-11
i have a question about the gimp.  if anyone is familiar with photoshop?  there is an extract command.  its the second thing on the filter menu.

does such a thing exist in the gimp?  

heres what extract can do.

it can pull a black ink, or pencil drawing off the white page that it was scanned from. and make it transparent.   so you are left with a black drawing, surrounded by transparent pixels. and if there was some light shading, it will drop the gray colors and make a transparent black. 

it also lets you remove something from a background.  such as a blue screen or what ever. without sharply cutting the edges.  so if you have fine hair thats against a blue backdrop. it cuts the hair out and removes the blue parts.  and the hair is still correct, that way you can put it on whatever background you want and it looks great.

---

### Post by skoal on 2005-06-11
yes, sir.  No problemo.

There are many possible ways, but here's one:

1. Use the color chooser ('o') to select that color you want to remove.
2. When the "color picker" dialog pops up, run your mouse over the "hex" color to copy it, or simply write it down.
3. Right click over image > layer > transparency > color to alpha.
4. Paste in the hex number or write it in.
* The preview window will show you the effect.

\\//_

---

### Post by cwaldbieser on 2005-06-11
I am no expert, but in GIMP 2, there is a select by color tool that might help you do what you want.  I drew a black line drawing, used the select by color to select it and cut it.  Then I brought up the layers dialog, created a new transparent layer, threw away the other layer, and pasted the line drawing into the transparent layer.

It's not all in one command, but I think it's doable.  Maybe there is something under one of the menu options which does all that for you, but I would not be sure what it would be called.

---

### Post by graigsmith on 2005-06-11
Sweet, color to alpha worked perfectly :)

thank you very much.  :)

another quick question,  i haven't seen this feature so i thought i would ask if its there, mabey im just missing it.

can you record macros a'la photoshop where you just hit record, do it. and then play it back later?

---

