---
title: "[SOLVED] how to show harddisk space left in gkrellm"
date: 2008-02-22
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-02-22
how to show harddisk space left in gkrellm?
also i can't figure out what the mem and swap show. why doesn't it just say e.g. 300MB left?
what do those 5 'LED's of eth0 mean? they keep blinking

---

### Post by yabbadabbadont on 2008-02-22
1) Disk space.  Configuration->Builtins->File System.  Add the ones you wish to monitor.
2) Left click on the Mem and Swap meters for text display.
3) Network activity.  One is receive and the other is transmit (Rx/Tx)

---

### Post by afeasfaerw23231233 on 2008-02-23
thanks but the text is moving. that's not so nice!

---

### Post by yabbadabbadont on 2008-02-23
Under General options, make the gkrellm width wider until it stops.

Edit: You can also change the format strings that are used to display the usage to something shorter.

---

### Post by afeasfaerw23231233 on 2008-02-23
thanks. just one more question: what does the graph of proc mean?

---

### Post by yabbadabbadont on 2008-02-23
Average load and process fork information.  From the Info tab:
> Proc Chart
The krell shows process forks with a full scale value of 10 forks.
While both load and fork data are drawn on the chart, the grid
resolution can be set for load only.  The resolution per grid for forks is
fixed at 10 when using the auto number of grids mode, and at 50 divided by
the number of grids when using a fixed number of grids mode.

Chart Labels
Substitution variables for the format string for chart labels:
	$L    maximum chart value (load)
	$F    maximum chart value (forks)
	$l    load
	$f    forks
	$p    processes
	$u    users

Substitution variables may be used in alert commands.


---

### Post by afeasfaerw23231233 on 2008-02-23
one more question: how to get rid of the stroke? it blocks the text! thanks

---

### Post by yabbadabbadont on 2008-02-23
I don't understand the question.  If you are talking about grid lines, no idea.  If you are talking about the krells in the meters, you can't.  (to the best of my knowledge)  You can, however, create your own set of images to be used as krells.  You'll need to read, then reread, then rereread the gkrellm theme information at the gkrellm website.  Then you'll need to experiment.  I would suggest examining gkrellm themes that replace the default krells with their own to see how it is done.  Finally, you will come to the realization that it wasn't worth the effort.  :D

Edit: OK, just create a transparent png that is 8x10 pixels.  Name it krell_meter.png and put it into your theme directory.

---

### Post by afeasfaerw23231233 on 2008-02-23
i mean the " | " you see it blocks the letter M of 396M, the number 1 of 12.1G and the number 2 and letter G of 71.2G

---

### Post by yabbadabbadont on 2008-02-23
Yeah, that's what I thought you were talking about.  In anticipation that I was correct, I created a transparent png image to use with your theme.  I tested it on mine, and it works.

Edit: OK, that didn't go quite like I planned...  as you can see, or not in this case, it is a transparent image...  I'll gzip it so that it won't be displayed by the forums software.  :)

---

### Post by afeasfaerw23231233 on 2008-02-23
thanks. i download another theme from [http://www.muhri.net](http://www.muhri.net) and problem solved

---

