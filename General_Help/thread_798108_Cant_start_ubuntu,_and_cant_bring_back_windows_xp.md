---
title: "Cant start ubuntu, and cant bring back windows xp"
date: 2008-05-17
forum: General Help
---

### Post by .Scy on 2008-05-17
A friend said that ubuntu is better than windows, had more in it.


Then i went to a site and converted ubuntu into an image. I started the pc with this and went through everything i had to fill out (i did this a few times) then when the computer reboots and it says to enter

login: (i enter my login name)
password: (it wont let me type at all!)

Now I'm trying to change it back to windows xp (i have the install disk too)


Anyone know how to either be able to log in with ubuntu or be able to login with windows xp!?

---

### Post by louieb on 2008-05-17
Do you know which version of Ubuntu you downloaded?
Sounds like you did a server install. If so. 
At the password prompt just go ahead and type it in and press enter. (The server install doesn't show anything at the password prompt)
once logged in enter the following two commands. (These will take a while to run)
```
sudo aptitude update
```and 
```
sudo aptitude install ubuntu-desktop
```when you reboot you should get a GUI login screen and the Desktop.
welcome to Ubuntu forums.

---

### Post by .Scy on 2008-05-17
Where do i enter the commands? :lolflag:

---

### Post by .Scy on 2008-05-17
Its not doing anything when i try to enter pass, i even tried doing entering in the pass without spaces moving.

also, where do i put in those commands you gave me???

I think it was a dsktop, but i have no idea. :confused:

---

### Post by .Scy on 2008-05-18
I think i'm going to kill my self now...

---

### Post by Cap'n Skyler on 2008-05-18
> **.Scy said:**
> I think i'm going to kill my self now...
now dont do that.
can you either go and get another ISO image and make sure you have the correct image for your comp?then just re install would be easiest.for now,maybe learning the command line/shell is too forward for you until you get further along the linux learning curve.
if you have a magazine store.stand near you,go look for some linux magazines and see if you can then get a Ubuntu cd/dvd to install from. 
i have tinkered with just about all of the more common linux distros and as a newb i can assure you this is by far the best going.
for play and general purpose use,and even for emergency access to the 'net try some of the live cd's.
like puppy linux
damn small linux
knoppix
slax
all of those should get you up and running to get ubuntu help or a new iso image to download and burn(if you get to a locked out situation and cant get online.)

---

### Post by Cap'n Skyler on 2008-05-18
AND best of luck,and post back with what you have going on,and welcome to teh 'Buntu forums :)

---

### Post by Cap'n Skyler on 2008-05-18
> **.Scy said:**
> Its not doing anything when i try to enter pass, i even tried doing entering in the pass without spaces moving.

also, where do i put in those commands you gave me???

I think it was a dsktop, but i have no idea. :confused:
when the screen comes up with just a place for a log in and then asks for password,that is a text based? or command line (non GUI)  it is for the real pros.command line has something like 18,000 different commands.it does exactly the same as the graphical screen does.i prefer the gui.
linux also has the annoying habit of when things go right,it does nothing to really let you know you did it right.so for now,stay clear of it and try to study it and then take small steps to learn it.
  the command line is done in a shell.windows users know it as a DOS prompt?
the shell is also called a terminal in linux.
to get up and running,i'd skip the shell for now.did you confirm the correct ISO for your comp is correct?

---

### Post by .Scy on 2008-05-18
When it boots up it said [ OK ] by almost everything, the list wasn't that long though.

---

### Post by .Scy on 2008-05-18
Would using this program to erase my hard-drive make it so i can install windows XP?

[http://www.aevita.com/eraseharddrive/](http://www.aevita.com/eraseharddrive/)

---

### Post by the8thstar on 2008-05-18
**[COLOR="Red"]IMPORTANT: when you type your password, nothing shows up? This is _NORMAL_. Just enter your password and press enter.[/COLOR]**

Once you're done with that, at the terminal prompt, type

> sudo aptitude update

Then

> sudo aptitude install ubuntu-desktop

It's gonna take a while, but just follow the directions on the screen.

---

### Post by .Scy on 2008-05-18
Even though i'm entering the password that doesn't show up, it still asks me to reenter my password when i'm sure its right!

---

### Post by the8thstar on 2008-05-18
Check the Caps Lock and Num Lock keys. That can make a difference.

---

### Post by .Scy on 2008-05-18
then why can i enter in the id? 

i also tried that.

---

### Post by the8thstar on 2008-05-18
> **.Scy said:**
> then why can i enter in the id? 

i also tried that.

I don't know. Why not?

It's also possible that you entered the wrong password twice when you installed the system. One different letter is enough to screw things up.

---

### Post by .Scy on 2008-05-18
i did the install about 5 times, and i did the same pass for each one, the pass i use for everything...

---

### Post by the8thstar on 2008-05-18
Do you have the LiveCD?

---

### Post by .Scy on 2008-05-18
I have the windows xp disk, and the ubuntu disk i made too... thats it.

---

### Post by the8thstar on 2008-05-18
OK, when you put the Ubuntu disk in the drive, reboot with it, what happens? Do you see a screen with icons on it?

---

### Post by vladi11 on 2008-05-18
When you insert your Ubuntu disc and boot up, it looks like this ?
[ATTACH]70591[/ATTACH]

If not, download right away Ubuntu 8.04 Desktop Edition ( you have Server Edition) from [[COLOR="DarkOrange"]here[/COLOR]]("http://www.ubuntu.com/getubuntu/download").
Choose the type you need ( 32 bit or 64 bit) from your nearest location.
That will solve all your problems.

PS : next time give us more information about your PC (to get proper help)

---

### Post by the8thstar on 2008-05-18
Agreed with **Vladi11**. Thanks for the picture BTW.

---

### Post by .Scy on 2008-05-18
Thats the very site i downloaded it from, and thats what the image looks like too.

---

### Post by the8thstar on 2008-05-18
Select the first option, that should load up Ubuntu LiveCD.

Once this is all done, look at the screen, click on Applications, Accessories and Terminal. A terminal window should open.

---

### Post by .Scy on 2008-05-18
it says Cannot configure the network? is that normal? also right when i clicked the first thing, a black page came up saying error something.

---

### Post by the8thstar on 2008-05-18
Well, then I guess either your CD is bad or you don't have enough RAM to run the LiveCD. How much RAM do you have?

---

### Post by .Scy on 2008-05-18
120MB i think >.>

---

### Post by vladi11 on 2008-05-18
> **.Scy said:**
> 120MB i think >.>

Sad news. you need at least 192 MB to run Ubuntu ( alternate Cd).
For Live cd it requires 384 MB.
I don't think your pc can handle Ubuntu.

I see 2 solutions : 
1. buy more ram ( it's almost free these days)
2.Start learning to work in command line ( CLI).

Cheers

---

### Post by .Scy on 2008-05-18
>.<



couldn't i just use that hard-drive eraser then reinstall windows XP???

---

### Post by the8thstar on 2008-05-18
You mean the one cited earlier? Sure, give it a try.

---

### Post by .Scy on 2008-05-18
I'm using my mac now, and i dont have any blank CDs that will work on my mac right now, guess i have to get some...

---

### Post by the8thstar on 2008-05-18
If your Mac is recent, you can try to install Ubuntu there and dual-boot.

You might want to look for an easy HOW-TO in the Mac forums: [http://ubuntuforums.org/forumdisplay.php?f=165]("http://ubuntuforums.org/forumdisplay.php?f=165")

There's a ton of OS you can install on small configs. Check this: [http://ubuntuforums.org/showthread.php?t=575456]("http://ubuntuforums.org/showthread.php?t=575456")

---

### Post by .Scy on 2008-05-18
I could, but its not my computer...

---

