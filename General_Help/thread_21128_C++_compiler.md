---
title: "C++ compiler"
date: 2005-03-20
forum: General Help
---

### Post by Arachnopuppy on 2005-03-20
What C++ compiler would you people recommend?  A free one would be nice.

I'm a long time windows user.  Just exploring my options.  I have installed both XP and ubuntu on my harddrive (don't worry, 2 different partitions) just so I could have one foot in unknown territory and one in the known.

Anyway, I'm writing some programs for my physics project and thought I'd try it out with ubuntu.

Thanks for the help :)

---

### Post by Hidden.Elf on 2005-03-20
g++ is a good one; you can obtain it via synaptic

---

### Post by DJ_Max on 2005-03-20
You should already have one installed. (g++). Pretty much the norm.
Also, for some other useful stuff.
open up Synaptic, and look for build-essential

---

### Post by Kimm on 2005-03-20
:-s 

g++ isnt installed with the system... is it? sure wasnt when I installed it...

Anyways, if you want a good and nice IDE to go with g++, download and install Anjuta, its a greate IDE!!

---

### Post by Arachnopuppy on 2005-03-20
[QUOTE=Hidden.Elf]g++ is a good one; you can obtain it via synaptic[/QUOTE]

I'm still new with synaptic.  How do I obtain it via synaptic?  I'm pretty sure it's not like windows where you click on the "setup.exe" application :D

---

### Post by njs12345 on 2005-03-20
```
sudo apt-get install g++
```

---

### Post by DJ_Max on 2005-03-20
[QUOTE=Arachnopuppy]I'm still new with synaptic.  How do I obtain it via synaptic?  I'm pretty sure it's not like windows where you click on the "setup.exe" application :D[/QUOTE]
 >>System >>> Administration >> Synaptic Package Manager

It's a program that allows you to install/update/remove programs from your comp.

If you are compiling & writing apps, you'll want
```
sudo apt-get install build-essential
```

---

### Post by Arachnopuppy on 2005-03-20
[QUOTE=DJ_Max]>>System >>> Administration >> Synaptic Package Manager

It's a program that allows you to install/update/remove programs from your comp.

If you are compiling & writing apps, you'll want
```
sudo apt-get install build-essential
```[/QUOTE]

I love it when you people assume I'm suppose to know the other half of your answer.  [size=1]Actually, I don't.[/size]

Ok, so I openned synaptic package manager... then what?  That code you wrote meant absolutely nothing to me.  How do I put it to use?

---

### Post by kaptk2 on 2005-03-21
To use that code open a terminal window, it is under the applications tab. It is labled terminal.

Once that window is open (it is like the command prompt in windows) you can type your code you are going to need to enter your password and then a c compiler will be installed on your system. Hope that this answers your other half of the question.

---

### Post by Arachnopuppy on 2005-03-21
Ok, I've done that.  My next question is how do I open up the compiler  to start using it?  In windows, it usually appears under start--->programs but here I can't seem to find the application anywhere.  I've installed both of the suggested compilers above.

Thank you, guys, for helping me with this.  When I'm more confident with this system, I will switch entirely to it.  Ubuntu is great!

---

### Post by DJ_Max on 2005-03-21
[QUOTE=Arachnopuppy]I love it when you people assume I'm suppose to know the other half of your answer.  [size=1]Actually, I don't.[/size]

Ok, so I openned synaptic package manager... then what?  That code you wrote meant absolutely nothing to me.  How do I put it to use?[/QUOTE]
If you need someone to hold your hand through such a simple process, then it's time to RTFM [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
Reading goes a long way in life

> Give a man a fish, he eats for a day, teach him how to fish, he eats for a lifetime. 
Or something to that tune. You get the picture.

To answer your other question...
In the **Terminal**, type:
```
g++ [OPTIONS] <FILE>
```
<File> is to be replaced with the C++ code.  in a .cpp extenstion.
[OPTIONS] are the 'tags' that may be used, even though I forgot if any are needed, as I don't care much for C++.
For more info, in **Terminal**
```
g++ --help
```

---

### Post by kanem on 2005-03-21
[QUOTE=Arachnopuppy]Ok, I've done that.  My next question is how do I open up the compiler  to start using it?  In windows, it usually appears under start--->programs but here I can't seem to find the application anywhere.  I've installed both of the suggested compilers above.[/QUOTE]

It sounds like you use an integrated developer environment (IDE) in XP? The g++ compiler is run from the command line in a terminal. It doesn't have an entry in the Gnome (or KDE) menus. If you want a graphical application for writing and compiling code try Anjuta. 

So, go to Synaptic Package Manager and install Anjuta and build-essential as suggested above. In Anjuta when you try to configure and compile your first app there will be some errors. This is because there are some more necessary programs (which should have been dependencies of Anjuta or at least a part of build-essential). Fortunately the errors Anjuta spits out will clue you in on which ones are missing. They are all available via synaptic. If the error messages aren't helpful, there is already a thread on these forums about how to get Anjuta fully working.

---

