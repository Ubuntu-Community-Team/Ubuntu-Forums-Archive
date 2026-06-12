---
title: "Print jobs queue but do not print"
date: 2007-07-26
forum: General Help
---

### Post by jphekman on 2007-07-26
HI all.

I'm running Dapper and printing has worked fine on it since I installed it. However, it's now hosed.

A few days ago I tried to print a particular PDF, and the printer froze partway through. After attempting various workarounds (printing with a different PDF viewer; printing to PS and then printing that), I gave up on the file. However, I then discovered that nothing else would print. The jobs got queued and sat there.

I restarted cups; no change. I rebooted; no change.

Test page DOES print just fine, but nothing else (plain text via lpr queues and sits, for example).

I set output in cups to "debug" and checked the logs, which say:

[...]
D [26/Jul/2007:09:56:47 -0400] [Job 871] foomatic-gswrapper: gs '-dBATCH' '-dPA\RANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDevice\Manufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 6122' '-dDEVICEWIDTHPOINTS\=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=true' '-dTumble=false' '-r600' '-sIj\sParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSe\t=2,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0'\ 3>&1 1>&2
[...]
D [26/Jul/2007:09:56:49 -0400] [Job 871] Found:
D [26/Jul/2007:09:56:49 -0400] [Job 871] (cortex) 2.66 Tj
D [26/Jul/2007:09:56:49 -0400] [Job 871] --> Output goes directly to the renderer now.
D [26/Jul/2007:09:56:49 -0400] [Job 871]
D [26/Jul/2007:09:56:49 -0400] [Job 871]
D [26/Jul/2007:09:56:49 -0400] [Job 871] Closing renderer
D [26/Jul/2007:09:56:49 -0400] [Job 871] KID4 exited with status 0
D [26/Jul/2007:09:56:49 -0400] [Job 871] KID3 exited with status 3
D [26/Jul/2007:09:56:49 -0400] [Job 871] Renderer exit stat: 3
D [26/Jul/2007:09:56:49 -0400] [Job 871] Renderer process finished
D [26/Jul/2007:09:56:49 -0400] [Job 871] Killing process 32272 (KID3)
D [26/Jul/2007:09:56:49 -0400] [Job 871] Process dying with "Error closing renderer", exit stat: 3
D [26/Jul/2007:09:56:49 -0400] [Job 871] error: Bad file descriptor (9)
D [26/Jul/2007:09:56:49 -0400] [Job 871] Error closing renderer
E [26/Jul/2007:09:56:49 -0400] PID 32268 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
D [26/Jul/2007:09:56:49 -0400] cupsdAcceptClient: 6 from localhost (Domain)
D [26/Jul/2007:09:56:49 -0400] cupsdCloseClient: 8
D [26/Jul/2007:09:56:49 -0400] PID 32269 (/usr/lib/cups/backend/hp) exited with no errors.
D [26/Jul/2007:09:56:49 -0400] [Job 871] File 0 is complete.
[...]

I've googled, but other people seem to have this problem on first trying to set up printing. I would think I have all the right drivers, etc already, as printing worked just fine before things got horked.

The printer is an HP 6122.

Thanks for any advice you can give!

Jessica

---

### Post by phidia on 2007-07-26
I'm not at my ubuntu install right now, but I think you need to delete the job that got snafued.
You have to go into the printer que and delete that job then restart cups.

---

### Post by jphekman on 2007-07-26
Hi phidia -- I have indeed removed that job (and all other jobs that got queued after it), and also restarted cups multiple times (including rebooting my computer), and it's still just queueing!

Jessica

---

### Post by phidia on 2007-07-26
> **jphekman said:**
> Hi phidia -- I have indeed removed that job (and all other jobs that got queued after it), and also restarted cups multiple times (including rebooting my computer), and it's still just queueing!

Jessica

I'm sorry what do you mean by it's still just queuing? Are you saying that even though you've removed the job it continues to be in the work queue?

Trying to offer useful advice...you can try printing from the command line i.e a terminal with "lp"
You might also check [here]("http://www.linux-foundation.org/en/OpenPrinting") for an answer to this. They have a forum devoted to linux printing problems, Hope that helps.

---

### Post by jphekman on 2007-07-27
No, I mean that new jobs submitted just queue. They do not get printed.

Jessica

---

### Post by phidia on 2007-07-27
Open System>Administration>Printing.
In the "Printers" applet click on "Edit" and select "Resume".

If that doesn't work you may need to try and print from CLI and then copy and paste the errors you get i.e in a terminal you would type "lp <some-text-filename>" and copy and paste the output.

---

### Post by jphekman on 2007-07-27
OK -- when I System>Administration>Printing->Edit, "edit" is greyed out. I also tried selecting one of the printers listed in that applet, and "edit jobs" is greyed out there.

From the CLI:

jphekman@pendaran:~/src/readinglist$ lpr ~/tmp/toprint.txt
jphekman@pendaran:~/src/readinglist$

OMG, it just printed -- I guess I never did try printing plain text. Huh! Excellent.

I also tried printing a postscript file from the command line:

jphekman@pendaran:~/projects/vet/articles$ lpr BiolPsychiatry-Mind-reading07.ps
jphekman@pendaran:~/projects/vet/articles$

...no errors, but it sits in the queue:

root@pendaran:~# lpq -PDeskJet-6122
DeskJet-6122 is ready
Rank    Owner   Job     File(s)                         Total Size
1st     jphekma 875     (stdin)                         312320 bytes
2nd     jphekma 876     BiolPsychiatry-Mind-reading07.p 312320 bytes

(You can see that I also tried printing it from xpdf, which sent it as (stdin).)

Thanks,
Jessica

---

### Post by phidia on 2007-07-27
Well I'm glad something worked :) Still you should be able to print from the GUI. Those edit menu items shouldn't be greyed out either.
I'm not sure what's up with that...
For PDF printing you may want to look at the ubuntu community doc on that [here]("https://help.ubuntu.com/community/PrintToPDF").

---

### Post by jphekman on 2007-07-27
Hmm -- looks like that is about how to print *to* PDF, rather than about how to get my printer to accept a PDF document. (Good to know about, though.)

I just tried asking Firefox to print a plain text doc, and that printed fine too. So I'm guessing the problem is only with postscript printing (ie, the problem is not CLI vs GUI, the problem is with the content of the document that gets sent to the printer).

I'm considering just upgrading to Edgy this weekend, but I'd really rather not have to do that! Postscrpt printing did work before. I'm flummoxed as to how it could just stop working.

Thanks for your help...

---

### Post by Hei Ku on 2007-12-14
Did you have a solution to your problem? I have the exact same problem in Gutsy, since I upgraded. The test page prints fine, but I try to print PDF and I get an error in foomatic-rip

---

### Post by jphekman on 2007-12-14
I never did find a solution, sorry; I upgraded to Feisty and the problem went away. I'd be curious to hear if you find an answer at some point.

Jessica

---

### Post by mondy on 2007-12-14
try to shotdown the computer then reinsert the printer cable to different usb port

---

### Post by mondy on 2007-12-14
it was that easy to fix you should not have gave up

---

