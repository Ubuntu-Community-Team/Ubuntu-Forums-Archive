---
title: "System completely unstable ( clean updated install )"
date: 2008-01-02
forum: General Help
---

### Post by SystemParanoia on 2008-01-02
Hello there, ive been browsing the forums for a few days trying to find the soloution to my problem but alas i cannot.

i have installed ubuntu studio 7.10 onto a relatives machine

( a compaq ey993aa ) [http://h20195.www2.hp.com/V2/GetDocument.aspx?docid=0900a5a5816e73bf&cc=uk&lc=en](http://h20195.www2.hp.com/V2/GetDocument.aspx?docid=0900a5a5816e73bf&cc=uk&lc=en)

and the problems that i am having are as follows.

Sometimes the computer on boot up, will hang just before it gets to the GDM login screen, and it will just be blank. i am able to ssh into the machine to reboot it

i cannot "logout" or "switch user" without the system hanging with a blank screen with a locked out keyboard.

sometimes the computer will just hang for no reason.

if i try to use any full screen apps i.e vmware server, or tuxmath, or gcompris. the computer will either hang immidiately, or hand when the app is closed.


my main comuter at home is running open suse 10.2 and have never experience problems like this.

i can paste any cli information anyone needs to help me get some stability onto this system. as if i cannot stablise it with linux, i will be forced to re-install windows onto it :(

---

### Post by Craigus on 2008-01-02
Run the memory test from the live cd to make sure there isn't a RAM problem.

Is the system equally unstable if booting / running from the live cd ?

---

### Post by SystemParanoia on 2008-01-02
memory has tested good. using the xubuntu 7.10 live cd

just about to test the system stability using it as a live cd now. ( ubuntu studio doesnt have a live option u see.... )

---

### Post by SystemParanoia on 2008-01-02
with xubuntu live cd, the system doesnt crash or freeze... but if i log out and log back in, the mouse cursor becomes invisible, but still functional


logged in and out a few more times, and now the desktop bg has vanished along with all the desktop icons.

the colour is ubuntu brown, and i have no right click menus on the screen apart from the upper and lower task panel

---

### Post by SystemParanoia on 2008-01-02
bump

---

### Post by SystemParanoia on 2008-01-02
i forgot to mention.

i am using the amd 64bit version of ubuntu studio

---

### Post by snakeeyes on 2008-01-02
Maybe Ubuntu 7.10 is just not compatible on that hardware, many people have had succes with Linux Mint 4.0. Its based on Ubuntu 7.10, maybe u would like to try that.

---

### Post by SystemParanoia on 2008-01-02
hmm, it looks alright.

its gnome implementation is similar to that used in suse 10.2

i guess i'll just give it a try

---

### Post by SystemParanoia on 2008-01-02
it seems slightly more stable. i.e it hasnt crashed at all, through numerous log in and outs while running on the live cd.

i did encounter an issue with the arrow cursor vanising and becoming invisible, but functional though.

any idea what that could be?

maybe the graphics driver ?

---

### Post by snakeeyes on 2008-01-03
Yeah it could be the graphics driver is not upto date, did u check the cd for errors though?

---

### Post by SystemParanoia on 2008-01-04
System is still unfortunately unstable.

i have tried various flavours of linux, and all of them behave the same way.

im in the process of downloading suse 10.3 and burning it to a dvd to give this hardware soloution one last chance before switching back to windows.

---

### Post by snakeeyes on 2008-01-04
Ok, try openSUSE 10.3. I used to use 10.2 before and its probably the most stable distro I ever used. 10.3 is excellent as well, give that a try no doubt.

---

### Post by SystemParanoia on 2008-01-04
yes, one of my machines already runs 10.2

it does crash every-so-often due to lack of ram and there being 5+ users logged in because everybody seems to be unable/unwilling to log out... ever! and the fact that the fsck doent automatically run after a crash is VERY annoying.

---

### Post by SystemParanoia on 2008-01-05
Opensuse 10.3 has solved all instability issues with this machine.

---

### Post by snakeeyes on 2008-01-05
Excellent, openSUSE 10.3 is an excellent distribution. I use it all the time. It probably has a lot less bugs and application crashes as well compared to Ubuntu or Kubuntu. Glad it worked for u.

---

