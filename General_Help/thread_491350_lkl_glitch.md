---
title: "lkl glitch"
date: 2007-07-03
forum: General Help
---

### Post by joriad on 2007-07-03
I came across a glitch in the LKL keylogger program. It worked fine for a long time but then started to print strange characters and NULL and became unreadable, it also stopped logging the date and time. Here is a sample output.  

<Ret>
Tue Jul  3 13:17:31 2007
asdfghjkl;'\<Ret>
Tue Jul  3 13:18:44 2007
<Ret>
Tue Jul  3 13:18:44 2007
<Alt>æßðNULLNULLNULLjNULLNULL@NULL«<Alt>æßðNULLNULLNULLjNULLNULL@NULL«

It seems after pressing the alt key, "asdfghjkl;'\" recorded as "æßðNULLNULLNULLjNULLNULL@NULL«".

Is there a way to prevent this from happening? 

Also when I start LKL in terminal with ```
sudo lkl -l -k '/usr/share/lkl/keymaps/us_km' -o /home/john/log.txt
``` it starts fine, but if i close terminal it also closes LKL. 

How can I run LKL and have terminal closed?

---

### Post by sgusto on 2007-07-19
LKL isn't quite ready for prime time but can be somewhat usable. On my system LKL will not, for example, differentiate between the left cursor key and keypad 4.  It will also not differentiate between the 6 dedicated Ins,Home,PgUp,Del,end,PgDn keys and the ones on the keypad. ALL of those type keys simply appear in the log as KP1 KP2 KP3 etc regardless of its function state so you won't know whether KP7 in the log was a "7" or a "Home".

The LKL keymap files need a bit of tweaking to use with a std PC 105 kybd. I have a vanilla US "Corded Deluxe Access" Logitech PS/2 keyboard. Assuming you're using Gedit, the line numbers apply. 

us_km 

1. Line 19: replace <Del> with <Bksp>
2. Line 46: is empty. add `  (no spaces)
3. Line 62: is empty but is the location of the space bar. Locate the cursor there and hit the space bar once. This will add a visible space between words in the log file. If you want, you can add <Spc> instead but it clutters the log file and makes it harder to read. 

us_kmUp (do these corrections in order as line numbers will change after #2)

1. Line 19: replace <Del> with <Bksp>
2. Line 9: The LKL program is set to ignore # in the keymap files as remarks. Line 9 is for the pound sign but when it reads line 9 containg a naked #, it ignores it because it thinks it's a remark instead of data (duh). This then throws the rest of the file off because what should be line 10 is line 9 because 9 has been ignored. To correct this replace the naked # with <#> as with the <Shift>, <Alt>, <Ctrl> and other control keys. The log file will show <#> but at least it works. This corrects the transposing problem from line 9 to 46.
3. Line 47: is | -Delete this line letting everything below shift up one line making line 47 now <Shift>. Probably because whoever did the keymap file was unaware of the # problem and was trying to correct the transposing going on.
4. Line 48: is blank. add |
5. Line 59: is blank. add <Shift>
6. Line 60: is <Shift> change it to * without the <>
7. Line 61: is <Alt> and stays.
8. Line 62: is empty but is the location of the shift+space bar. Locate the cursor there and hit the space bar once. This will add a visible space between words in the log file. If you want, you can add <Spc> instead but it clutters the log file and makes it harder to read.
9. Line 63: is <CapsLck> and stays.
From Line 64 containing F1 the rest of the file should be correct as is.  

us_kmALT

In my system, whenever an Alt key is pressed, LKL gets confused and records "NULL" and "Euro" and other odd stuff into the log file instead of the proper keystrokes and remains screwed until a reboot. I don't know what causes this but I found a bit of work around. Move the original us_kmALT file to a safe place. Make a duplicate of the corrected us_km into the keymaps directory and rename it us_kmALT. At least when it freaks out it will continue to record proper keystrokes. It could be because of msttcorefonts but I don't know.

YMMV

---

