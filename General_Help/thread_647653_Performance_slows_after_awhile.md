---
title: "Performance slows after awhile"
date: 2007-12-22
forum: General Help
---

### Post by dlegend on 2007-12-22
I am currently running Ubuntu 7.10 on my laptop (Dell D600 Latitude, 1.4 ghz with 32mb video and 1.25 gb of ram). When I first start my laptop and log into Ubuntu everything runs really smooth. I have compiz-fuzion running and spinning the 3D cube (as a test) is very smooth -- that is, until after awhile of using my laptop it seems that everything slows down.

Even after closing all the opened applications performance isn't as smooth as when I first reboot and login. I was wondering what the potential causes of this could be -- and what I could do to fix it. 

I'll eventually be putting Ubuntu on a better machine but until now, I'd like to get the best performance out of it as possible, while still have the effects and eye-candy of compiz-fuzion / emerald.

If anyone needs extra info let me know and I'll try and provide it (let me know how I can if the info requires special commands to access). Thanks in advance.

**Note:** Please read my reply here before responding: [http://ubuntuforums.org/showpost.php?p=4000491&postcount=4](http://ubuntuforums.org/showpost.php?p=4000491&postcount=4)

---

### Post by ed-koala on 2007-12-22
Seeing as how no one has responded I'll throw out a suggestion, for what it's worth :)

I know Firefox has a lot of memory leak issues that are being addressed for the next release. Perhaps it is slowly eating up memory as it runs???  I'll have to check this on my system as well, just to see if that's even possible.

No other ideas at present except to keep an eye on your system monitor and see if anything else is growing as it runs, and hogging resources.

---

### Post by lgambett on 2007-12-22
Open a terminal window and launch;
top
It shows you the most CPU-consuming tasks, memory allocation, swap usage, etc....

---

### Post by dlegend on 2007-12-22
As I've already stated, even after closing all opened applications performance is slow. So I'm not sure as to how those applications could be affecting performance. Let me explain the situation that I just ran through:

1. I started my laptop and logged into Ubuntu. I tried spinning the desktop cube and it runs smoothly (no lag whatsoever).

2. I try running several applications -- terminal, firefox, gedit, calculator, gnu-chess and play around with them for awhile. At this point I can spin my desktop cube but it lags (looks pretty bad).

3. I closed all previous applications I was running. I try spinning the desktop cube again but it doesn't run smoothly like it did when I first logged in.

4. Then I tried logging out and logging back in. The desktop cube still doesn't rotate smoothly.

5. Rebooting the machine and logging back in will make the system run smooth again (desktop cube will no longer lag while rotating it -- smooth transitions).

Any suggestions / any knowledge of why this would be happening?

PS. Information from top provided below:
> 
Tasks: 119 total, 2 running, 117 sleeping.
6.6-7.5%us, 6-7%sy, 0-23%ni, 60-80%id
Mem: 1295456k total, 915620k used, 379712k free, 51924k buffers
Swap: 1646620k total, 0k used, 1646620k free, 511024k cached


From the System Monitor: Memory usage is at 339.1 MB of 1.2 GB and 0 bytes of swap. CPU usage is high from system monitor but nothing else.

**Update:**

After rebooting my system and running top from the terminal I get around 617000k of memory used...
> 
Mem: 1295456k total, 617000k used, 678024k free


---

### Post by dlegend on 2007-12-23
Any help? This problem is basically the only other thing preventing me from having a seamless experience with Ubuntu. Also let me note that this doesn't happen when I am using Windows XP on the same laptop so it has nothing to do with the hardware -- must be something in Ubuntu but I don't know what.

---

### Post by lgambett on 2007-12-23
Ok, you have no RAM problems. Memory seems fully used, but this is normal in Linux; swap usage at 0 is a good sign. Using top can you understand what is the process that uses your CPU time  (it is the first on the list, probably)

---

### Post by dlegend on 2007-12-24
I'm wondering if this could have anything to do with having many applications running on a slow machine and after closing them it just takes awhile for it to speed up again? Seems like after I close the applications and I don't do anything on it for awhile then it is more speedier.

---

### Post by tgalati4 on 2007-12-24
Sometimes firefox leaves itself in memory:

>sudo killall firefox-bin

Try using htop:

>sudo apt-get install htop

>htop

Also look for any system error messages like hard disk read errors:

>dmesg | tail -25

Do that every half hour or so when your machine starts to feel slow.

The other distinct possibility is thermal slow down.  If your power settings are not set correctly, your processor will heat up and as a safety measure it will slow down.

>sudo apt-get install lm-sensors

>sudo sensors-detect (answser yes to most/all questions)

>sensors

Put a temperature monitor on your task bar (right-click on the upper taskbar and add a temp display).

---

### Post by dlegend on 2007-12-24
Wow (tgalati4) thanks for the suggestions. htop is a lot nicer then top for monitoring through terminal. I shouldn't be complaining too much about performance as my laptop isn't very powerful and I do have graphic effects like compiz-fuzion enabled -- but I like to do what I can. 

These tips will be very useful to me on the next machine I install Ubuntu on I'm sure =)

---

