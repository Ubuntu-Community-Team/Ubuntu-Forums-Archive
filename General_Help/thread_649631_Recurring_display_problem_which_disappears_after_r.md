---
title: "Recurring display problem which disappears after reboot under windows XP"
date: 2007-12-25
forum: General Help
---

### Post by leilujapan on 2007-12-25
Hi, I am getting a very peculiar problem with my computer lately, and I believe it is connected with Ubuntu.

Here is the description of the problem:

1) Since about 10 days ago, when I start my computer, I often (not always) do 
not get anything on screen: the computer is on, but no signal goes to the screen.
2) After a reboot by pressing the reboot button, I get the Asus motherboard screen, 
but the display is very bad, with horizontal and vertical lines which make colored 
squares all over the screen. The boot sequence goes on and I get to the Ubuntu 
screen, still with lines on the screen (quite strangely the Ubuntu loading screen 
with the orange bar only has lines on the left half of the screen).
3) I can log on and use ubuntu normally it seems, appart from the fact that the screen 
is very hard to read. (The vertical lines have a finer resolution than for the motherboard
screen. They look like dotted lines, as shown on the attached picture)
4) Even after several reboots under Ubuntu, nothing changes.
5) Now comes the funny part: if I reboot under windows XP (fighting to recognize the XP
line on the Grub screen...), the display is still scrambled up to the BLACK windows XP 
loading screen, but becomes completely normal at the BLUE windows "Welcome" screen!
XP works perfectly fine as well.
6) If I now reboot under Ubuntu, no problem at all!!

I have tried several numbers (0, 2, 3) of Ubuntu reboots before trying the XP boot, 
always with the same result: nothing changes with Ubuntu, problem solved with XP.

The fact that these weird lines appear from the motherboard screen seems to mean
 that it is a hardware problem. This makes me think (what follows is pure beginner
speculation) that Ubuntu might be changing some video settings (something connected
to the graphic card??) which the computer doesn't support after a restart, and that XP
is able to fix. Again, this does not happen every time, but tends to happen more and 
more often.

My system is up-to-date (with kernel 2.6.22-14-generic). I ran a memory test during 
one night, and stopped it after 22 passes without error. Are there any tests I could 
do to have more insights on what is going on?
I run Gutsy 7.10 on a desktop with the following specs:
Pentium 4 3.2GHz, 1GB RAM, Asus P4P800-E deluxe motherboard, 
ATI Radeon 9600 XT, Samsung SuncMaster 172N (17" TFT monitor).

Thank's in advance for any piece of advice!

Pictures:
Asus screen; 
Grub screen; 
Only hjalf affected Ubuntu load screen;
Screen after login + detail;

---

### Post by chewearn on 2007-12-25
Quite a difficult problem, no definite solution, but I have a suggestion.
Maybe it's gunk collecting inside your case, do a thorough cleaning, detach PCI cards, etc, clean the contacts and reattach.

---

### Post by bodhi.zazen on 2007-12-25
Try reducing the default (color) depth.

Open a terminal, enter this command :

```
gksu gedit /etc/X11/xorg.conf
```

In the "Screen" Section, change the Depth to 16 :

(Do not change anything else, your xorg.conf will look different then mine)

> Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    [color=blue]**16**[/color]
    SubSection     "Display"
        Modes      "1920x1200" "1600x1200"
    EndSubSection
EndSection

Then re-start X (Ctrl-Alt-Backspace or log off and back on)

---

### Post by leilujapan on 2007-12-28
Thanks for your reply.

I tried to change the depth but I still get the problem.
It now happens every time I start the computer after a few hours of cooling down.

I realized by coincidence (I had left the speakers on) that the first time I start the PC and nothing appears on screen, the BIOS is actually saying "System fail, CPU test"!

I looked on the web for more info and found many people having the same kind of problem, most of them with the Asus motherboard, but there was no definitive conclusion (some mentionned the heatsink, others the power supply, others the graphic card, etc.).

I still don't understand if it is a pure hardware problem, or if it is triggered by a wrong software setting (through Ubuntu?). I'll try to shut down the PC through windows XP and see what happens.

Just in case, I attach my xorg.conf if someone may find something interesting there.

---

### Post by Jordinho on 2008-02-28
> **bodhi.zazen said:**
> Try reducing the default (color) depth.

Open a terminal, enter this command :

```
gksu gedit /etc/X11/xorg.conf
```

In the "Screen" Section, change the Depth to 16 :

(Do not change anything else, your xorg.conf will look different then mine)



Then re-start X (Ctrl-Alt-Backspace or log off and back on)

Doing this screwed up my Ubuntu install. This is the first time in three weeks I've been able to login. It was just  a blank screen after I did that. Even after I replaced my faulty power supply and video card (the former of which probably did something to the latter to make it crazy) it booted windows just fine but Ubuntu was still messed up. I had to go [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4056315&postcount=2") to solve my problem although I'd probably advise people to get a different video card to test it out first.

---

