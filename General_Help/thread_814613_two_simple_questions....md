---
title: "two simple questions..."
date: 2008-05-31
forum: General Help
---

### Post by PhDP on 2008-05-31
1 - I can't see diacritic marks, I only see a ?. I have installed the language support for french/latin, with complex characters, but it doesn't work.

2 - I want a program (in this case, Pidgin), to start automatically when I open my computer, how can I do that ?

---

### Post by noynac on 2008-05-31
> **PhDP said:**
> ...2 - I want a program (in this case, Pidgin), to start automatically when I open my computer, how can I do that ?
The easiest way is to use the sessions tool:

*System > Preferences > Sessions > Startup Programs > Add*

---

### Post by PhDP on 2008-05-31
ah, exactly what I was looking for...

Now, for question #1, anyone ?

---

### Post by TWO on 2008-06-01
> **PhDP said:**
> 1 - I can't see diacritic marks, I only see a ?. I have installed the language support for french/latin, with complex characters, but it doesn't work.


I would love to know the answer to that one. Firefox just doesn't seem to show some of them no matter which encoding I choose. It makes no sense and it's rather annoying!

---

### Post by Kinnza on 2008-06-01
maybe its not the language its the font?
did you try to change the fonts of the system?
what about console? if you cat a file do you see those ?

---

### Post by PhDP on 2008-06-01
"cat a file" ?

---

### Post by ibuclaw on 2008-06-01
> **PhDP said:**
> "cat a file" ?

Make a file in your home directory and put in some diacritic letters and save.

Then open up a terminal and type in:
```
cat ~/**filename**
```
Where filename is the name of the file that you saved it as.

What "**cat**" does is just print out the contents of the file to the screen in the terminal.

Regards
Iain

---

### Post by pbpersson on 2008-06-01
"cat a file" simply means from the console typing "cat <filename>" which will send the output of the file to the screen.

Do the characters appear in the web browser?

Can you open a file in Open Office and see them?

Can you copy them from a web page and copy them into an Open Office document and see them?

Can you use a character map to insert them into a document?

àáâãäåæèéêëìíîïðñòóôõöøùúû

I did those using a character map.  Now.....using the keyboard I have no idea because I live in Phoenix, AZ - no real need here - the little I use that stuff I would just run to the character map if needed.

---

### Post by ibuclaw on 2008-06-01
> **pbpersson said:**
> 
àáâãäåæèéêëìíîïðñòóôõöøùúû

I did those using a character map.  Now.....using the keyboard I have no idea because I live in Phoenix, AZ - no real need here - the little I use that stuff I would just run to the character map if needed.

There are two ways achieving it.

1) **AltGr + CHAR**
Press the AltGr key and a character key at the same time.
ie: From Q to M on the keyboard
```
@ &#322; e ¶ &#359; &#8592; &#8595; &#8594; ø þ æ ß ð &#273; &#331; &#295; j &#312; &#322; « » ¢ &#8220; &#8221; n µ 
```

2) **Compose + Symbol, CHAR**
Press the Compose key and a symbol. Then type in the character.
The compose key is disabled by default, but you can enable it in the Keyboard Preferences app. ("**System>Preferences>Keyboard**")
Then go into **Layout Options** and dropdown the bar that says "**Compose key position**".
For me, I prefer to use the Right Super Key.

Another example of use: Here are a few variations of **e**
(**Cmp + '**) (**Cmp + .**) (**Cmp + ,**) (**Cmp + SHIFT + ~**)
```
é &#279; &#281; ê
```

Regards
Iain

---

### Post by PhDP on 2008-06-01
I can see diacritic marks in PDF file created by LaTeX, for example, but I can't see them in the Tex file I used to create the PDF. Also, I can see diacritic marks on the internet.

However, I just saw a much bigger problem; I can't rename folders. If I create a folder and try to rename it, it won't work, it's like my keyboard doesn't work, I press F2 to start editing the name of a folder, and then I can't the name of the folder, I can't even use the ESCAPE key to finish editing the name.

Is Ubuntu 8.04 more reliable ?

---

### Post by neur0 on 2008-06-01
Try to change your keyboard layout with
System > Preferences > Keyboard
And then on "Layouts" tab set the keyboard model to som generic if its not already set, and try a different layout (button "Add...")

---

