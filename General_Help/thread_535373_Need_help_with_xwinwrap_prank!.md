---
title: "Need help with xwinwrap prank!"
date: 2007-08-26
forum: General Help
---

### Post by phibit on 2007-08-26
I want to play a prank on my buddy, just for a nice laugh. He's running Ubuntu and has an ssh server going, to which I have root access.

I know to any ACTUAL hacker it'd be obvious how to proceed, but I'm no such hacker and have no such linux skills. 

What I was thinking is to loop a (hilariously tasteless) video in the background of his desktop, using xwinwrap, and scheduling it to run every 10 minutes or so. 

I have already uploaded said video to his computer, but my attempts at scheduling the task using cron have apparently failed (I haven't gotten any angry phone calls from him, there's no mplayer process running in the background from ps aux)

what i've done is run 

crontab -e

and added the following line : 

*/10  * * * * xwinwrap -ni -o 0.9 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /home/hisname/.azureus/tmp/fun.mpeg > /home/hisname/.azureus/transfi.log

The "> /home/hisname/.azureus/transfi.log" bit was to see if a file was being created, which it was, so to me that means that it's running something.

From my understanding, that should run every 10 mins, but it doesn't seem to be working!

Anyone have any ideas?

---

### Post by dth4310 on 2007-08-28
okay - i'm ignorant too but have idea.

Would think that you would need to figure out the $DISPLAY setting for the xserver his user is running - typically this would be a variable in the shell that started his x session - but since you're obviously not part of that shell.....if you could determine this setting, i'd think you could embed the xwinwrap command you have in a shell script that:

1> sets display var
2> executes command

just a thought.

---

