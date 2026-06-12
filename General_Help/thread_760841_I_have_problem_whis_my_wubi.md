---
title: "I have problem whis my wubi"
date: 2008-04-20
forum: General Help
---

### Post by elonlon on 2008-04-20
I have problem whis my wubi.
When i open the computer and enter to the Wubi it say to me error
it was something whis 1280X1024 60Hz.

---

### Post by ago on 2008-04-20
[https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3](https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3)

---

### Post by elonlon on 2008-04-21
what do i need to download and what i need to do whis this download???

and thanks you very much for the halp

---

### Post by ago on 2008-04-21
Nothing to download all is done automatically. Press esc at boot after "Ubuntu" and choose safe graphic mode

---

### Post by elonlon on 2008-04-21
i enter to the grafic mode but it still tell me the same problem
what can i do now?

---

### Post by ago on 2008-04-21
What is the exact error message?

---

### Post by elonlon on 2008-04-21
it tell me the same problem like befor this thing whis 1280X1024 and 60Hz
what can i do?

---

### Post by hora48 on 2008-04-21
When I reboot and choose Ubuntu, it says ***upper memory*** and gets stucked there, what should I do? (windows XP 2nd ed)

---

### Post by elonlon on 2008-04-21
can someone halp me please?:(:(:confused::confused:

---

### Post by ago on 2008-04-21
I will need more details, when exactly does that happen?
If it is just after selecting "ubuntu" at reboot try pressing insert rapidly for more verbose output

---

### Post by elonlon on 2008-04-21
you told me to run grafic mode after i run him it hapend and if i dont select grafic mode it's hapend after i select ubuntu

ok?

---

### Post by elonlon on 2008-04-21
it's hapend after i select ubuntu or when you told me to select grafic mode it's run the grafic mode an right after this he tell me this problem

---

### Post by elonlon on 2008-04-21
you told me to run grafic mode after i run him it hapend and if i dont select grafic mode it's hapend after i select ubuntu

ok?

---

### Post by elonlon on 2008-04-21
sorry on this 3 message in the same time i dont anderstand where they go so i send lot of times

---

### Post by elonlon on 2008-04-22
Halp me please....:( i so want to enter to the ubuntu

---

### Post by ago on 2008-04-22
Press esc after you select "Ubuntu" and try the other option. If there is any error pls post here the text EXACTLY as it appears on screen. Or take a screenshot with a camera.

---

### Post by elonlon on 2008-04-22
the other select i have is APTI or something like this
to select it?

---

### Post by elonlon on 2008-04-22
here i have the message that i see:
Not Optimum Mode
Recommended Mode:
1280X1024 60Hz

i hope this can halp

---

### Post by elonlon on 2008-04-22
Ago are you there?????......

---

### Post by ago on 2008-04-22
I think that is a Monitor error correct? Not an OS error (i.e. you are not thrown into a shell). Which means that the installation should still proceed. Let it go (check that there is some disk activity). If I am right it should reboot after about 10-20 minutes, and when you press esc the menu should be different.

---

### Post by elonlon on 2008-04-22
after he is difernt do i need to do something?

---

### Post by ago on 2008-04-22
> **elonlon said:**
> after he is difernt do i need to do something?

If you get there, the second option should be "recovery mode". Choose that one. You will land in a console. You will now be able to install extra video drivers and or change the resolution to match the one of your monitor.

See first if you get to that stage.

---

### Post by elonlon on 2008-04-23
yes i get there and when i select recovery mode he run something and it's give me something blue that let me select 3 things
what to select?

---

### Post by ago on 2008-04-23
Your installation was successful then! And your issue is "only" your monitor. 
You are now better off to follow this up in the general Ubuntu forum! They will explain how to set up your video card output to match your monitor. I think it is the second option though.

---

### Post by elonlon on 2008-04-23
so i need to click on the second option i have?

---

### Post by ago on 2008-04-23
If I remember correctly yes, but I would suggest continuing the discussion on the general Ubuntu forum, since Wubi job is done and your system is installed. This is a standard graphic configuration issue.

---

### Post by elonlon on 2008-04-23
the first option i have is resume
the second option i have is root
the third option i have is xfix


and i try to select i second option and he write something with my name on it and this symbol #
if i need to select the second option i have what i do after this this happened?

and i have one more question how i change between my languish and English Alt+Shift don't work on Linux
how can i change between my languish and English??

and thanks

---

### Post by elonlon on 2008-04-23
ah and how i can open programs that work on windows but they don't work me on Ubuntu?

---

### Post by ago on 2008-04-23
elonlon, 

try the third option first,

otherwise use the second option and run

dpkg-reconfigure xserver-xorg

change the screen resolution/frequency to match the one of your monitor

---

### Post by elonlon on 2008-04-23
OK thanks and how i change the languish so i can write in my languish

and how i can use programs that i can use them on widows but i can't use them on Ubuntu

---

### Post by elonlon on 2008-04-23
i try to select the third option but he send me back to this blue screen so i tried to select the second option and i write what you told me to write and then he told me something about keyboard.
this is telling you something? 
what i need to do next?

---

### Post by elonlon on 2008-04-23
there is new problem
when i try enter to ubuntu it send me this message:
busybox v1.1.3(debian 1:1.1.3-5ubuntu12) built-in shell (ash enter 'help' for a list of commend

what i need to do now?

---

### Post by elonlon on 2008-04-23
ago are you there?

---

### Post by ago on 2008-04-23
elonlon, you need to be careful when you are root (admin) in Ubuntu, you can easily ruin the system...

I suggest to start with a fresh installation
Then, as mentioned earlier ask for support here: 

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Mention that your installation was successful but you cannot use X since your monitor will only take a specific resolution, so you can only boot in rescue mode. They will be able to guide you through.

---

### Post by elonlon on 2008-04-23
what you mean when you write"X" ...cannot use X since your ...
so send them like you write whis the "X"?

---

### Post by ago on 2008-04-23
X is the base of the Unix/Linux graphical interface

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

To be more precise, you can run X quite well (or installation would have failed), it is your monitor that is very picky about screen resolution, so you need to reconfigure X in order to make your monitor happy.

---

### Post by elonlon on 2008-04-23
and to do this i need to ask in other forum that you gave me?

---

### Post by ago on 2008-04-23
Yes, that forum is dedicated to video issues so you should find capable users to help you through.

---

### Post by elonlon on 2008-04-23
ok and one more thing my ubuntu was on Hebrow i see everything on Hebrow but i can't write on Hebrow how can i fix it?

---

### Post by ago on 2008-04-23
That's the layoutcode settings for the console. [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by elonlon on 2008-04-23
ok thanks man you are the basttttt
thanksss

---

