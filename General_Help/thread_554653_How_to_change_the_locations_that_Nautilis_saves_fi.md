---
title: "How to change the locations that Nautilis saves files"
date: 2007-09-19
forum: General Help
---

### Post by Alisdair Kelly on 2007-09-19
I am gettng frustrated with the default save file to locations that are offered by Nautilis. I don't want to save files to my $HOME directory. I don't really like saving files to the Desktop and then have to go back and move them to a new location. 

So, how do I go about changing the default location to somethine like $HOME/Things to check out or $HOME/cache? Or is this even doable?

---

### Post by ecor6633 on 2007-09-19
I've nerver seen "save file" in Nautilus.
Can you explain a bit how you access this functionnality ?

(Are you talking about firefox ?)

---

### Post by Alisdair Kelly on 2007-09-19
What I'm talking about is the location to which a file is saved. I frequently compse a file with gedit  then when I try to save the file (Save as) , the options open up and the number one option of where to save the file is in my home directory. You can browse  for other locations such as the Desktop or filesystem or shared folders (other resources).
 
I do *not* want to save a file to the /HOME$ directory by default. I want to be able to select 'save as:
filename.estension to a directory such as $HOME/Works in progress without having to click on the mouse to "Browse for other locations".

---

### Post by Alisdair Kelly on 2007-09-20
Well, I solved or resolved the issue by changing editors. I've switched to Vim with the Cream GUI. I'm a happer campe, now with 'creamy goodness' :)

---

### Post by ecor6633 on 2007-09-25
Anyway i found a trick to do it.
In a terminal, if you move to the folder you want and run gedit, it will be the default folder proposed in the save as...

You can write your own script that moves first in your folder and run gedit for you.

(I'm used to jedit but vim is a good choice)

---

