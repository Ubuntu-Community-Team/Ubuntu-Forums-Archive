---
title: "[SOLVED] Can Someone Pleeeeease Help?!?!?"
date: 2006-11-29
forum: General Help
---

### Post by tupesadilla on 2006-11-29
Ok big problem, before you read, remember, please try to help or reference me somewhere to where i can get help pleeease ive done lots of reasing and nothings worked!

Problem:

Using dapper, and everythings boots up whatever just fine, then i login, everythings fine im playin around having a good time, then all the sudden BAM! screen goes black, then the login screen shows up.... *what the...?* i login again.... start using the wonderful ubuntu system... then BAM!, straight to login screen...again.... so i log back on, and i let it sit... screen saver for about 5 minutes, then screen turns off, ok so i move the mouse, yep there i am.. login screen... the longest ive been able to stay on is 10 minutes without it kickin me off and makin me login. 

PLEEEAAAASSSSSSSEEEE HEELLLPPPP!!! this is giving me SUCH a headache. i mean i love ubuntu... but its kinda hard to absorb the love when i cant use it!!! ](*,)  ](*,)   :evil: 

thanks!!

---

### Post by pay on 2006-11-29
I once had that problem but it resolved itself.

---

### Post by wpshooter on 2006-11-29
Let me ask you, did you verify the integrity of your Ubuntu CD by running the verification check function found on the initial Ubuntu boot screen menu ?

If not, then I would advise that you check the CD integrity and IF it fails, I would advise that you re-download and reburn the ISO image at the slowest speed possible and the give installation another try after you have checked the CDs integrity.

---

### Post by strabes on 2006-11-29
wpshooter - good idea. You can do that by booting from the cd and then on the 1st menu, select check CD integrity, or something like that. 

why are you using dapper anyway?

---

### Post by denday on 2006-11-29
Same in here.. I think you use corrupted Ubuntu CD.

---

### Post by tupesadilla on 2006-11-30
i am using dapper because i upgraded to edgy before but i didn't like how unstable it was and i like the long term support from dapper. now this is the wierd thing. i did run cd check... and the first time i did it. it failed. but then i did it again. and it passed. but i had a lot of trouble starting any ubuntu cd.. none of the alternate cd's would install and the live cd(s) had a lot of trouble starting. as in, the initial boot up screen would usually stop at "adding live cd user" and then id reboot a couple times and it'd stop at configuring X and then etc..etcc. but when i finally got it runnin it installed flawlessly... maybe a bad cd drive???

---

### Post by d3v1ant_0n3 on 2006-11-30
Just basic troubleshooting- I have no idea what the trouble is- but:

a) What hardware are you running, and what flavour of Ubuntu are you running (i386,ppc, 64bit, etc), and what DM (Ubuntu, Kubuntu,Xubuntu)

b)What apps are you running when the computer drops back to GDM? Maybe try running 'top' command in terminal, and just watch what is using CPU before it logs you out?

c) I'm a little confused by your posts- did you manage a full and complete install of ubuntu?

d)Have you tried updating everything? In terminal: sudo aptitude update && sudo aptitude upgrade

Hopefully from answers to these, someone might be able to hep you more than me.

---

### Post by tupesadilla on 2006-11-30
Hardware - custom built computer, gigabyte board. SiS 640-gl, intel celeron 2.00 ghz processor, 512 mb of ddr ram, 266mhz,, using the dapper i386 ubuntu. 

-usually when the computer logs out im either using firefox, or the screensaver, but its done it while looking at syslog, using the terminal, and out of no where just sitting at the desktop, and yes i managed a full and copmlete install of ubuntu, and yes i have a script that i run that does the upgrade, (apt-get install update, apt-get install upgrade, apt get-install dist -y upgrade, updaetedb)(i think thats it) i will try the top command and see what happens. hopewfully this information helps...

---

### Post by tupesadilla on 2006-12-01
I believe i resolved the issue!!!! BAD RAM! because the computer is a dual boot computer, and windows was having lots of problems. so i did a memory dump on windows and come to find out the ram was messin everything up. so i put 2 new ram chips in and now windows runs fine and ubuntu has been up and running for 1 full day now. so im pretty sure resetting the ram fixed everything!

---

