---
title: "xgl screwed up my computer"
date: 2008-03-17
forum: General Help
---

### Post by lilalmond on 2008-03-17
Hey

I installed xgl from the terminal and since then weird things happened..
I have black lines appearing all over the screen
Dunno what to do

---

### Post by forrestcupp on 2008-03-17
First, turn off your desktop effects.  Then, in a terminal, type:
```
sudo apt-get --purge remove xgl
```

This removes xgl.  That should get you back to not having that problem.  Now we can figure out how to get things working.  If you do things right, you probably don't need Xgl anymore.

1. What kind of video card do you have?
2. Did you install the proprietary drivers for it with the Restricted Drivers Manager?

---

### Post by lilalmond on 2008-03-17
I typed the code in a terminal but the lines obviously wont really disappear...
I have no idea what video card is in my laptop, its a dinosaurus.I believe its ATI something.
I also have problems with my keyboard,some keys doesnt type what they are supposed to
Anyway everything was working perfectly before i installed xgl from the terminal
Compiz fusion was running smoothly even tho my laptop probably doesnt have a recent graphic card

---

### Post by lilalmond on 2008-03-17
Is there any way to reboot the puter as it was 2 days ago?
everything is screwed up and im going nuts
This is insane :mad:

---

### Post by lilalmond on 2008-03-17
Please anyone :mad:

---

### Post by lilalmond on 2008-03-17
Help...

---

### Post by lilalmond on 2008-03-17
I dont know how long im supposed to wait to beg for help but my puter is a mess...
Im just waiting to know if theres a way to reboot the puter as it was 2 days ago
Thx

---

### Post by duncan.hawthorne on 2008-03-17
i think 6 posts in 3 hours is probably considered too much, but anyway....

could you describe the video errors in more details, can you see and use your desktop, just with weird artifacts?

did the command: "sudo apt-get --purge remove xgl" work. ie what was the output (you should always post the output on forums)
have you tried 
sudo apt-get --purge xserver-xgl

have you installed the ati proprietary driver, ie in system>administration>restricted drivers.

as much detail as possible is good.
you'll certainly need to restart your computer to test the effects of these  things.

---

### Post by duncan.hawthorne on 2008-03-17
ok i mean sudo apt-get --purge remove xserver-xgl

---

### Post by abalone on 2008-03-17
Have you checked if the black lines appear when you boot into another operating system (installed on the laptop, or from a Live CD/DVD)?

---

### Post by lilalmond on 2008-03-17
First of all thanx a lot to reply...
I know i was a bit desperate to get an answer
Anyway i typed in "sudo apt-get --purge remove xserver-xgl" in a terminal and rebooted the puter and everything works much faster and the lines all over my screen disappeared.
As for the ATI proprietary driver in System>administration>restricted drivers it tells me "Your hardware does not need any restricted drivers".
Im really new at linux :(
Thank you for helping me out on that one

---

### Post by lilalmond on 2008-03-17
Reply to abalone: I dont have any other os, i ran ubuntu over xp from a live CD
But Duncan got my problem fixed about the lines all over my screen
Thx anyway

---

### Post by abalone on 2008-03-17
> **lilalmond said:**
> Reply to abalone: I dont have any other os, i ran ubuntu over xp from a live CD
But Duncan got my problem fixed about the lines all over my screen
Thx anyway

Ah, cool, I'm pretty certain I've damaged video cards with XFree86 before (back in the late 90s). Lines and little squares and dots appeared out of the blue at some point - and stayed, on any OS

---

### Post by duncan.hawthorne on 2008-03-17
note that you could have uninstaled xgl by unchecking xserver-xgl in synaptic (in system>administration>synaptic)

it looks like you probably dont have an ati graphics card, you can find more info about your computer in system>preferences>hardware information or by typing lspci in terminal, and looking for the line to do with your graphics card.
for example mine says:
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

if you are trying to run compiz.... if you dont have anything in the restricted drivers manager, and compiz isnt already running, its very unlikely that your computer supports it

---

### Post by lilalmond on 2008-03-17
Well before i installed xgl everything was running perfectly, (even tho i have some problems with my window boarder sometimes)
Now that i uninstalled xgl my compiz doesnt work anymore
I have had compiz running properly since i installed the os on laptop
Cant seem to make it work anymore
Weird stuff

BTW i do have ATI Radeon IGP

thats what i get when i type "compiz" in a terminal

amandine@amandine:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:4337 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by duncan.hawthorne on 2008-03-17
you could try skip checks: quote from another thread:

"mannheim
October 18th, 2007, 05:46 PM
In gutsy, the script that launches compiz checks your graphics card against a blacklist of cards which are "known" to behave badly with compiz. But you can overrule these checks: create file under your home directory with the path ~/.config/compiz/compiz-manager and put in it the line:
SKIP_CHECKS=yes
Then compiz will be launched regardless."

delete the file to get back to where you were if it doesnt work. but it could break things (until you delete the file, but you might loose the ability to see your desktop so you might have to go into a terminal to delete the file). It'll probably be fine however, ie will just fail if something goes wrong

post more if you want help getting compiz back

---

### Post by lilalmond on 2008-03-17
Stupid question... How do u create file under home directory?
I tried to type "~/.config/compiz/compiz-manager" in a terminal and it said permission denied
I hope you can help me out getting back compiz...

This is what i get now when i type in "compiz" in terminal

amandine@amandine:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:4337 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by duncan.hawthorne on 2008-03-17
ok i'll try and help

typing "~/.config/compiz/compiz-manager" would try and run "~/.config/compiz/compiz-manager" which isnt a program or a least isnt allowed to be run as a program.

as you are new to ubuntu, you should probably try to use the graphical tools. 

Go into your  home folder  in nautilus (home folder is generally called ~), then click view > hidden files. then go into the directory .config , then compiz inside that, or create these if they dont exist (capital letters matter)

then create a file called compiz-manager

(this could have been done in terminal by typing
gedit ~/.config/compiz/compiz-manager
which tells gedit (the text editor) to open the file ~/.config/compiz/compiz-manager or create it if it doesnt exist)

then type in the file: SKIP_CHECKS=yes
and save


then type open a terminal compiz, and output what happens here for me to see.

[does anyone else reading this thread know of a good place to point people for general ubuntu help for these kind of things at this level?]

---

### Post by lilalmond on 2008-03-17
This is what i get now when i type in "compiz" in terminal

amandine@amandine:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:05.0 0300: 1002:4337 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by duncan.hawthorne on 2008-03-17
ok in nautilus click "filesystem" on the left. this is called folder /
then browse into etc/X11/
look for files in this folder called xorg.conf.[a number]
write here when the current file xorg.conf was modified
and when the other files xorg.conf.[a number] were modified
you can do this by changing the view in nautilus from icons to list

---

### Post by duncan.hawthorne on 2008-03-17
might also be good to do:
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
just in case, and restart

---

### Post by lilalmond on 2008-03-17
xorg.conf was modified today
xorg.conf.original-0 was modified the 2nd of march

---

### Post by forrestcupp on 2008-03-17
> **forrestcupp said:**
> First, turn off your desktop effects.  Then, in a terminal, type:
```
sudo apt-get --purge remove xgl
```
Sorry about earlier.  I meant sudo apt-get --purge remove xserver-xgl.

give us the output of
```
lspci | grep VGA
```
So we can see exactly what video chipset you have.  This will determine if you need proprietary drivers or not, depending on how new it is.

If your video card is an X series or newer, you probably need to install the proprietary drivers.  If you download [Envy](http://www.albertomilone.com/nvidia_scripts1.html), it will automatically download and install the very latest ATI drivers, which don't need Xgl.  The drivers in the Restricted Drivers Manager are old enough that they still need Xgl.

If you use Envy to get the drivers, Compiz should just work, since you've already done the skip checks workaround.


But if your video card is older than the X series, you don't need Envy or proprietary drivers, and we'll have to figure something else out.

---

### Post by duncan.hawthorne on 2008-03-17
he said compiz was working for him before
he just needs to switch back to his old xorg.conf file
was compiz working between 2nd and the 17th?

---

### Post by duncan.hawthorne on 2008-03-17
if it was working between those dates:
do in terminal:
cd /etc/X11
sudo mv xorg.conf xorg.conf.17.03.08
sudo mv xorg.conf.orginal-0 xorg.conf

make sure both of those have worked correnctly, then restart.
wait for someone else to confirm this is right if you want

the commands in terminal do the same as renaming the file xorg.conf in the folder /etc/X11 to xorg.conf.17.03.08 and renaming xorg.conf.orginal-0 (ie the working file) to xorg.conf which is the file your computer reads.

---

### Post by lilalmond on 2008-03-17
Thanx a lot for your precious help duncan
I typed in terminal 
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

And i rebooted and now i can enable desktop effects again
I just dont know enough about linux...
Million thanx again

---

### Post by duncan.hawthorne on 2008-03-17
no problem, ubuntu gets easy pretty quickly, after you make the usual couple of mistakes

for future reference, xgl is the less good way to use compiz, for graphics cards that dont do compiz normally
if it works without xgl (this is the direction in which graphics cards drivers develop) you should be happy, your computer supports it the proper way. installing xgl is then not want you want

enjoy ubuntu, and spread the word of its coolness

---

