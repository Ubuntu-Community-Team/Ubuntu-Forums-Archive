---
title: "~&gt; Capitalize the first letter &lt;~"
date: 2016-03-04
forum: General Help
---

### Post by ramin6 on 2016-03-04
Hi guys.
I use pidgin as yahoo messenger. 
I want something like a program, script, etc. that capitalize the first letter of every words that I type.

For ex. when I add you as an contact to my yahoo account (in pidgin) and then send you this message : "hi, dude this is ramin. pidgin is awesome"

I want it to become something like this:  "Hi, Dude, This Is Ramin, Pidgin Is Awesome"


Please help me.

---

### Post by jim_deadlock on 2016-03-04
Do you have any idea how annoying that is? Why not just use CAPS LOCK if you want to irritate people.

---

### Post by him610 on 2016-03-04
You could press the Shift key while simultaneously pressing the first character key of each word as you type. Wouldn't That Be Neat If One Could Do That!;)

---

### Post by ramin6 on 2016-03-04
> **jim_deadlock said:**
> Do you have any idea how annoying that is? Why not just use CAPS LOCK if you want to irritate people.

No, I have no idea. why is it annoying? The final goal is something else. Actually It's really useful when you chat in Persian by English letters.
Please solve the problem if you can.


> **hgh9mrp said:**
> You could press the Shift key while simultaneously pressing the first character key of each word as you type. Wouldn't That Be Neat If One Could Do That!;)
Yup, I see.
Why you people just talk? Please give me an answer. Solve the problem if you can.

Thanks.

---

### Post by sudodus on 2016-03-05
Since such a tool is useful in your language, I will try to help you make one. It is simple and not perfect, but I think useful for chats and other texts, where the formatting is not very important.

If you create a file ***caper*** with the following content and make it executable

```
#!/bin/bash

while read -ra word
do
 echo "${word[@]^}"
done < /dev/stdin
```

you can let it read from standard input and write to standard output. You can also redirect from/to files or pipe from to other commands/programs.

Example 0:

```
$ [COLOR="#0000FF"]./caper
hi, dude this is ramin. pidgin is awesome[/COLOR]
Hi, Dude This Is Ramin. Pidgin Is Awesome
```
Press the *Enter* key for caper to process the text string. 
Press *ctrl D* to finish.

Example 1:

```

$ [COLOR="#0000FF"]echo 'kalle stropp och grodan boll
voro två små snälla troll' | ./caper[/COLOR]
Kalle Stropp Och Grodan Boll
Voro Två Små Snälla Troll

```

Example 2:

```
< input-file.txt ./caper > output-file.txt
```

-o-

Maybe someone else can figure out how to get something like this into Pidgin.

-o-

Example 3:

But at least you can write a piece of text in a text editor, write it to a file and process it with caper into another file that you read into a text editor. Then you can copy and paste from that other file into your editing window in Pidgin. (Use your favourite editor, ***gedit*** is only one alternative.) You can create a file ***caperedit*** with the following content and make it executable

```
#!/bin/bash

infil=$(mktemp)
utfil=$(mktemp)

gedit "$infil"

while read -ra word
do
 echo "${word[@]^}" >> "$utfil"
done < "$infil"
rm "$infil"

gedit "$utfil"
rm "$utfil"
```

---

### Post by ramin6 on 2016-03-06
**[COLOR=#DD4814][B]@sudodus **[/COLOR][/B]
Thank you very much.

Actually I just need it when I'm typing in Pidgin**[COLOR=#DD4814][/COLOR]**. Excuse me but Example 3 is really useless for me.

---

### Post by sudodus on 2016-03-06
You can use this shellscript ***caper*** as a preprocessor. It might be useful for a longer text, but not for short replies in a chat. As I wrote in post #5

> Maybe someone else can figure out how to get something like this into Pidgin.

I don't how to integrate it into Pidgin. I think the best solution would be to do something similar in the source code (of Pidgin), and that is beyond what I can do.

But the source code of Pidgin is free, available for you to use and to change. I think you can learn how to do it yourself, maybe together with some other linux enthusiast in a linux local user group :-)

---

### Post by ramin6 on 2016-03-06
I'm newbie. Do you know how should I do it?

I have an idea. It just work in terminal, right? so can you make it an  script that works everywhere in gnome-area not just terminal? that way  it will become a very usefull scipt.

---

### Post by sudodus on 2016-03-06
This script works in a terminal, and between files (with redirection) and between programs (with piping). It is possible to start it from a desktop icon, but it will still not work inside Pidgin. I don't know how to make it work inside Pidgin, and I haven't got the time to learn about it.

If you find out what language is used in Pidgin, and learn that language, you can do something similar, that works where you want it, in Pidgin. Or you can find a programmer who is speaking Persian, and also wants the first letter in every word to be upper-case (capitalized).

---

