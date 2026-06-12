---
title: "problem booting from live cd"
date: 2007-03-01
forum: General Help
---

### Post by lnxn00b on 2007-03-01
this is my first post in the forums and Im having a problem booting ubuntu (6.10 edgy) from the live cd. the thing that confuses me was that it was working perfectly until i got rid of some arbitrary hardware in my system now it just messes up.

my computer was built by me:
asus a8n sli premium motherboard
amd athlon 64 x2 3800+ cpu
1 gb kingston hyper x ddr ram
nvidia gforce 7800gt 256mb video card
sony dual layer dvd burner
80gb western digital ide hdd
250gb western digital ide hdd
soundblaster audigy 2zs sound card

thats all the hardware i have, i recently made 3 minor changes:
1. removed my tv tuner card
2. removed my floppy drive (i dont even know why i put it in there to begin with)
3. changed my ide cables around on my motherboard (switched the ide cable with the 2 hdds as the primary and made the ide cable with the dvd burner as the secondary)

for some reason now when i try to boot ubuntu it doesnt work. i get the main menu when booting from the disc, i select start or install ubuntu as usual it starts to load the kernel then a weird little graphics glitch happens with the loading bar and it freezes for a second, then it starts to load up i get mouse support then nothing. ive uploaded some images of my problem to my space on my schools website:

[http://webpages.uncc.edu/~macatala/ubuntu_problem.htm](http://webpages.uncc.edu/~macatala/ubuntu_problem.htm)

i am using the same cd as before, even burned a new one and i am running dual monitors, which wasnt a problem before it would just show everything exactly the same on both. now my second monitor just starts flashing a blue-ish green color and on my primary monitor i just see the mouse and a small line of pixelated graphics. i even tried unplugging the second monitor but i still got the same problem (minus the blue flashy screen) 

i am using the live cd because im slowly trying to convert to linux completely but i wanted to get used to it first, and i had nothing but good experiences when it was working. ubuntu seems to be the right distro for me and i really want to get it working properly so i can make the switch. im not an idiot when it comes to pc, i work at a pc repair shop and after fixing tons of windows problems daily i have grown to hate it, all the licenses and viruses and foolish errors and resource hogging etc.... also i like how customizable linux is so switching to linux i think would make me happy if i could only get it to work again. 

please let me know if you guys have any suggestions or any ideas on what to do to get me up and running again, i would appreciate it greatly, thanks for your time, hope to hear from you soon.

---

### Post by lnxn00b on 2007-03-01
bump.

---

### Post by bodhi.zazen on 2007-03-01
Hard to know ...

since it was working I assume you have a hardware problem. Loose or misconfigured connection :?

Put the hardware back the way it was and see what happens.

Then make one change at a time until you isolate the problem.

---

### Post by lnxn00b on 2007-03-03
thats for the quick reply, i tried all of that, put everything back to the way it was with no luck still. ive done numerous hardware tests the only 2 things i could think of are:
1. the dvd drive is messing up while reading the necessary files

2.the cd has gone bad.

ive tested the cd in other computers and it works fine however, i even ran the cd test in the options menu which passed everything. got any more ideas?

---

### Post by lnxn00b on 2007-03-05
well its not either of the 2 possibilites above, ive replaced the dvd drive to no avail, and reburned the iso as well. anyone ever have anything like this happen to them or have an idea what could be causing it?

---

### Post by s3amonster on 2007-03-06
I'm having a similar problem as you, with some differences:

1) I don't get the blue/white screens shown on your monitors--apparently my computer just skips that step.
2) That final grey bar forms out completely into a rectangular mess while appears to be a garbled graphic of the actual desktop. Completely unfunctionable, of course.

Also what's interesting is my machine's specs are very similar to yours (I have the 4200 instead of the 3800, and a different sound card. The DVD drive is different, too). Maybe there's some sort of connection there?

Any help is greatly appreciated!

---

### Post by blackstealth007 on 2007-03-06
My friend is trying to install Ubuntu Edgy 6.10 x86-64 on his laptop with some differing problems. He is able to boot from the live  cd, then when he begins his install, (it will vary where exactly during the install it goes wrong), and mouse will stop responding, and bar will stop moving. Please PM me if you find fix.

---

### Post by lnxn00b on 2007-03-06
> **s3amonster said:**
> I'm having a similar problem as you, with some differences:

1) I don't get the blue/white screens shown on your monitors--apparently my computer just skips that step.
2) That final grey bar forms out completely into a rectangular mess while appears to be a garbled graphic of the actual desktop. Completely unfunctionable, of course.

Also what's interesting is my machine's specs are very similar to yours (I have the 4200 instead of the 3800, and a different sound card. The DVD drive is different, too). Maybe there's some sort of connection there?

Any help is greatly appreciated!

it could be something with the hardware, the thing that makes me wonder though is that it was working flawlessly until i removed that arbitrary hardware, im always very careful when messing around inside my machine, and ive ran numerous hardware tests on pretty much every piece of hardware in my machine and still no success which sucks because ive just recently got everything ready to switch over to Linux, so far ive tried different versions of Ubuntu including the 64bit version with no success same graphical problems. once in a while the loading bar will work all the way but after the mouse gets loaded i get the same graphical problems with the flashing blue screen and the useless gray bar distortion. it looks almost as if the panels in Ubuntu were trying to load and it just messes up.

when i get some more time i may take apart my entire system and re-build piece by piece if i have to, but after swapping out and switching around numerous parts i don't think that will fix my/our problem. anyone else having this problem? or maybe have an idea why the graphics and loading screw up?

---

### Post by s3amonster on 2007-03-08
So I did some browsing around and I found the solution (that worked for me, anyway). Apparently it's a problem with our graphics card. The 7800 has some incompatibility with the basic nvidia driver that comes on the CD. To boot from the live CD...

- press F6 at the first menu screen.
- delete "quiet-splash" and replace it with break=bottom
- let all the stuff run and load and whatnot and then when the prompt comes type

```
chroot /root nano /etc/X11/xorg.conf
```

- scroll down to one of the sections entitled "Device" that has your graphics card listed. Below it should be "Driver" and next to it "nv". This is the default nvidia driver on the Live CD, but apparently it has problems with our precious 7800 GTs. Replace "nv" with "vesa"

-then hit control + O
-hit enter
-and hit control + X

- at the prompt, type:

```
exit
```

The live CD should work now.

You might also run into the same problem after you've installed Ubuntu. I haven't had the time to completely install it yet--just mess around on the CD, but nevertheless I've got some apparent info about how to get past that part as well.

After you've installed ubuntu, the log-in screen will appear scrambled. Hit control alt F1. If this gives you a scrambled screen as well, reboot and select "Recovery Mode" from the bootloader.

Log in from the bootloader terminal then type:

```
sudo nano /etc/X11/xorg.conf
```

This is, essentially, the same thing you browsed before, so scroll down to the nvidia device and change the "nv" to "vesa" again. control + O, enter, and control + X to exit.

At the prompt, type:

```
sudo /etc/init.d/gdm restart
```

Now you'll log in with the vesa drivers, but since they kinda suck and will give you a big performance hit, you'll want to go ahead and install an nvidia driver.

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

There's also a program called envy which installs everything for you, found [here.]("http://www.albertomilone.com/nvidia_scripts1.html")

Apparently there's some security hole in the nvidia drivers. I'm not sure if envy fixes it for you or not but to fix it (if you followed the instructions and didn't use envy), bring up a terminal and type

```
sudo gedit /etc/X11/xorg.conf
```

Once again, go to the device section and, above the line that says "nvidia" add this line:

```
Option "RenderAccel" "false"
```

Then log out and press control-alt-backspace. Apparently there's a slight performance hit but I guess it's better than a security hole. Not sure what exactly what it (the security hole) is.

And I'm not one to steal the credit, so I got some of this from this guy ([http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)). I patched together the rest of the stuff in here though (mainly by looking at peoples' problems with the ATI X800 series and tinkering around).

Hope it works

---

### Post by euxneks on 2007-05-23
Just thought I would add that my 7100GS from work here needed the same treatment.  Perhaps there is a fix on the horizon for the liveCDs?:KS

---

