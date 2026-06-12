---
title: "How do you run a java application in Ubuntu?"
date: 2007-10-26
forum: General Help
---

### Post by adx442 on 2007-10-26
Thanks for any help I can get on this one ... I've read a lot of web articles and some forum posts about setting the PATH environment, etc ... but I have not been able to do what I'm sure is a simple thing.

MusicIP Mixer (musicip.com), offers a Java based version of their software for Linux.  I've tried running the main "executable" (applet/whathaveyou) with the "Java MusicMagicMixer" command in Terminal, and setting the path manually before that.  Their site has no instructions on how to install or run their software under Linux.  I was so frustrated that I tried to install the Windows version under Wine (which did not work ... I have yet to find a piece of software I want that will run under Wine).

I can't be the only person to ask how to run a java application under Ubuntu, but I can't find anything on the web that is helpful, and I've tried for about 2 hours at this point.

Please help me feel a little less inept!

Also, to everyone involved in 7.10, thank you ... this is the best release yet, and Compiz is turning heads at the office.

---

### Post by mlissner on 2007-10-26
This should be pretty easy. Theoretically, all you need to do is have the MusicMagicMixer in your working directory, and then just run java MusicMagicMixer. That should really do it, unless it still needs to be compiled or something. 

What does ```
file MusicMagicMixer
```reveal?

---

### Post by adx442 on 2007-10-26
Thanks for the reply!

I get this from the terminal with "file MusicMagicMixer":

MusicMagicMixer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

When I run "java MusicMagicMixer", I get this:

Exception in thread "main" java.lang.NoClassDefFoundError: MusicMagicMixer

---

### Post by mlissner on 2007-10-26
Yeah, something is missing there. That error will occur if java can't find the main class, which, in java, is THE class. Without it, there's no starting point for the program. 

Where did you find this program? Perhaps I could help more if I knew where to look for the executable itself.

---

### Post by adx442 on 2007-10-27
It's something I've been using in Windows for a couple of years ... here's the site, and a link to the Linux download:

[www.musicip.com](www.musicip.com)

download: [http://www.musicip.com/downloads/MusicMixer_x86_1.8.tgz](http://www.musicip.com/downloads/MusicMixer_x86_1.8.tgz)

Thanks!

---

### Post by adx442 on 2007-11-04
Solved it myself.

The answer was in setting JAVA_HOME by using the terminal as follows:
```

JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.03"
```

I then added it to the top of the ```
/etc/environment
``` file for a permafix. 

I had previously been setting it to ```
"/usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin"
``` (the path to the executable), which threw absolutely no errors when I would try to run the software, it just silently failed.

The command to get MusicIP Mixer running was simply entering
```
 ./MusicMagicMixer
```
 into terminal while in the directory of the software.  

Now, it's working fine.  I hope this helps someone else out down the line.

---

### Post by money2themax on 2008-05-12
how do i make this work it makes no sense to me

---

### Post by money2themax on 2008-05-12
bump

---

### Post by mlissner on 2008-05-13
What is it exactly you are trying to do? Run musicip mixer, or something else?

---

### Post by money2themax on 2008-05-13
> **mlissner said:**
> What is it exactly you are trying to do? Run musicip mixer, or something else?

musicIp

---

### Post by money2themax on 2008-05-13
Bump!

---

### Post by mlissner on 2008-05-13
> **money2themax said:**
> Bump!

Alright already! Man, you need to lay off the bumping!

OK, so here's what I think will work for you. I went and downloaded the program in order to figure out the problem and how to solve it. What worked for me was to first determine where java is on my computer, then to set the JAVA_HOME variable to its location, and then to export that variable.

That's the short of it. The step by step goes like this. Download MusicIP, and extract it somewhere.

In your terminal, make your working directory MusicMagicMixer, and then we need to find where java is installed on your computer. I have java 6 installed, so for me, java is installed here: ```
/usr/lib/jvm/java-6-sun-1.6.0.06/
```

Once you know that, you need to set the JAVA_HOME variable to that location, and then make that a global variable. To do that, run the following:```
JAVA_HOME='/usr/lib/jvm/java-6-sun-1.6.0.06'
export JAVA_HOME
```

Once you've done that, you should be able to start the program by running ./MusicMagicMixer

That will fix it until the variable gets erased, which will be the next time you reset your computer, close the terminal, etc. To fix that, see above regarding the env file.

---

### Post by money2themax on 2008-05-13
it worked thx but it takes so long for it to read songs cuz i have to do it 1 diectory at a time it can't just read my entire music folder

---

### Post by mlissner on 2008-05-14
> **money2themax said:**
> it worked thx but it takes so long for it to read songs cuz i have to do it 1 diectory at a time it can't just read my entire music folder

yeah, I played with it a little since I installed it figuring out how to make it work, and I had the same problem. I imagine there must be a solution, but I'm baffled as to what it is. 

what does this program do, anyway?

---

### Post by money2themax on 2008-05-14
> **mlissner said:**
> yeah, I played with it a little since I installed it figuring out how to make it work, and I had the same problem. I imagine there must be a solution, but I'm baffled as to what it is. 

what does this program do, anyway?
it's like itunes shuffle [but with moods] i'm actually trying to link it up with my slimserver [or slimcenter i can't remember which] for my squeezebox

---

