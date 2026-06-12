---
title: "Change the color"
date: 2007-08-20
forum: General Help
---

### Post by hraposo on 2007-08-20
Hello,

Excuse me for these basic questions that I made, but I want to ask something more:
In my script, appears to the user, the sentence: ** Wait a little. **

** This sentence appears in black color… How I can the color on sentence? Which is the command in script? **

---

### Post by Spr0k3t on 2007-08-20
What language are you programming the script in and where is the output to?

If this is a bash script, you can use the escape sequences right in line with the output.

Use the following format where ^] is the escape, ## is the following numbers, and m; is the end of the command.  This is an ANSI standard.

"^]##m;"

Foreground Colours
30	Black
31	Red
32	Green
33	Yellow
34	Blue
35	Magenta
36	Cyan
37	White

Background Colours
40	Black
41	Red
42	Green
43	Yellow
44	Blue
45	Magenta
46	Cyan
47	White

---

