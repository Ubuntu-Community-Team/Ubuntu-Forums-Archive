---
title: "Grub Questions"
date: 2007-01-24
forum: General Help
---

### Post by JoshuaH1 on 2007-01-24
Number One:

Is there way to separate options(Linux, Windows) on the grub menu, with like a space?


Number Two:

Is there a way to Delete/Change the text on the bottom of the grub menu (Use the [Up] and [Down] keys to select which entry...Or "C" for command-line)?

---

### Post by LotsOfPhil on 2007-01-24
[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

Check out this (big) tutorial on GRUB.

---

### Post by JoshuaH1 on 2007-01-24
Ok, On that tut, I found somewhat of what I was going for, for number one. Thanks :D 

Still no way to change the text on the bottom of the Grub Gui, anyone know how?

---

### Post by jbayone on 2007-01-24
You may be able to do that with GrubEd.  There is a link in my signature if you aren't familiar with it.

---

### Post by Tomosaur on 2007-01-24
Nope, you won't be able to do that with GrubEd :P

GrubEd will allow you to change most of the options availabel via Grub, but Grub itself is not modified. You will need to use a different boot-loader altogether if you want to get rid of the text.

You can, however, do some clever editing of the colours and background to make it LOOK like the text is missing. You can also hide the grub menu completely if you so choose. Unfortunately, the writing at the bottom of the screen is built into Grub itself, and as such, can't be removed or changed unless you want to mess around with the Grub source code.

---

### Post by Onimae on 2007-01-24
Sorry for a little post hijacking, but on the topic of colors in GRUB. Whenever I try to change the colors in the config it doesn't work and if I try to do it in the grub console, it doesn't work. I gives me an error which I found out meant it was looking for number and didn't get one. I was under the impression that you could use symbolic names and didn't have to use the HEX equivalent. What gives?

On the topic of spaces, I have seen it where there is a line of text saying "Other operating systems:" and then listing Windows. It's about the same thing as what you're going for, just with text. I'm sure it's possible, if you can do that.

**Onimae**

---

### Post by Tomosaur on 2007-01-24
Grub recognises only a limited number of colours, which differ for the purpose. For example, colours available for text are different from colours available for the highlight.

GrubEd allows you to change your Grub colours, with all of the colours available. Alternatively, you can see [this page](http://www.gnu.org/software/grub/manual/html_node/color.html) for the official grub colour scheme documentation.

---

### Post by Onimae on 2007-01-24
I used colors from the official page and they still didn't work.

Once I finish the download of Feisty's Live CD I'll try out GrubED.

**Onimae**

---

### Post by Tomosaur on 2007-01-24
Did you remember to uncomment the 'prettycolors' line from the menu.lst file?

---

### Post by Onimae on 2007-01-24
You have to uncomment that? I thought it was just a silly little label. hahah

Oh how wrong I was. I'll try that after this silly download finishes.

**Onimae**

EDIT--
Just kidding. Yes, I uncommented that. Still no dice.

---

### Post by JoshuaH1 on 2007-01-24
Yeah, I got the space thing :)

Just add a:

title        (Black Space)
root

Between them.


Thanks for the replies and help :). As for the text on the bottom, I will most likely just go the route of giving the illusion its not there.

---

