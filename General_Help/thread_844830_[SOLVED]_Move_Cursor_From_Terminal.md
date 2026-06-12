---
title: "[SOLVED] Move Cursor From Terminal"
date: 2008-06-29
forum: General Help
---

### Post by dinostabOMG on 2008-06-29
Is there a way to move the cursor using the terminal?

---

### Post by doorknob60 on 2008-06-29
Err...why? It might be easier to help if we knew why you wanted to do something like that :P

---

### Post by dinostabOMG on 2008-06-29
Oh, I just discovered xte, in the package xautomation. Perhaps this is the right path, I'll report back.

As for why, it started off because I want to be able to keep my monitor from switching off when I watch video for extended periods of time. I messed with the screensaver and power settings and that didn't do anything. So this might be easier. It's also an excuse to learn how to write csh scripts.

---

### Post by dinostabOMG on 2008-06-30
Well, it looked like this worked. Here is my script in case anyone is interested: 

```
#
#Optional parameters:
#  1 is the wait time (in sec) between cursor jumps. 
#  2 is the x position to jump to. 
#  3 is the y position to jump to.

#set defaults, if missing any user-provided params
if (! $1) then
	@ secs = 900;
	else
		@ secs = $1;
endif
if (! $2) then
	@ x = 1450;
	else
		@ x = $2;
endif
if (! $3) then
	@ y = 1190;
	else
		@ y = $3;
endif


echo Moving cursor to [$x, $y] every $secs seconds. Ctrl + C to quit, or close terminal.

#This variable keeps the cursor moving, instead of jumping to the same spot
@ flop = 0

while (1)
	@ adjusted = $y + $flop;
	xte 'mousemove $x $adjusted'
	#echo Jumped to [$x, $adjusted]
	if ($flop) then
		@ flop = 0;
		else
			@ flop = 50;
	endif
	sleep $secs
end


```

This is not a good way to break the script, I know, but I'm completely new to shell scripting. In fact, this is my first one. I picked CSH because I know C (learned in a Windows environment) and I felt very awkward with some of the ways bash does things.

---

