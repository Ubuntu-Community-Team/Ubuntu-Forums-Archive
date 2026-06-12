---
title: "Computer Freezes Every Time I Try to Compile"
date: 2007-05-02
forum: General Help
---

### Post by Mr_Mxyzptlk on 2007-05-02
Hi! I'm getting on with Ubuntu fairly well so far. Fortunately I have a fairly high tolerance for tinkering, so for the most part I don't mind the occasional glitch.

However, I'm consistently having one problem that's particularly annoying: I can't compile anything. Every time I try to compile source code, my computer freezes. The only way I can escape is to press the reset button.

My computer has an AMD64 dual-core 4400+ processor and 2GB RAM. I *was* running the AMD64 version of Feisty, but switched a couple of days ago to the i386 version in an effort to alleviate this problem. Unfortunately it didn't work.

Has anyone else encountered this problem? If so, do you know of a solution? Thanks in advance!

---

### Post by taurus on 2007-05-02
What are you trying to compile?

---

### Post by Mr_Mxyzptlk on 2007-05-02
I tried to compile Audacity beta 1.3.2, using the instructions at [http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/]("http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/"). (For those who don't know, Audacity is a digital audio recorder and editor. There's a stable version in Synaptic, but the beta is much better, in my opinion.) I finally gave up, and found and installed a Debian package.

I also tried to compile LAME 3.97 (again, there's an earlier version in Synaptic), but gave up. I think I might have tried one or two other apps as well, but none of them were that important to me so I just moved on. I have not yet successfully compiled anything.

---

### Post by flostre on 2007-05-02
I have experienced a similar problem when running a PC on a non-standard power supply. The problem was, that it could only do 3 amperes. So when I compiled something, the processor would use more power and the system would crash. This is just guessing, but maybe this has something to do with your case. You could try to do something as ressource hungry as compiling to see if your computer also crashes.

flostre

---

### Post by Mr_Mxyzptlk on 2007-05-02
Thanks for the suggestion. I had a *suspicion* that the problem might have to do with the power supply, as I also occasionally (rarely) experience random freezes when I'm not compiling. This seems to be happening much more frequently in Ubuntu than in the much-reviled commercial OS I was using previously.

I'm not at my home computer now, so I'm not sure exactly what power supply I have. However, I know it's a pretty hefty Antec model - 500 or 550 watts, I believe. What do you mean by "non-standard"? What steps did you take to fix the problem?

---

### Post by canadianwriterman on 2007-05-02
I managed to compile Audacity beta 1.3.2 from source, although it at up lots of CPU and took about half an hour. By the way, I was disappointed with the Audacity beta in that all the import capability was disabled. So, I wasn't able to import any audio files to edit. Bummer. Went back to the stable version.

---

### Post by Mr_Mxyzptlk on 2007-05-02
I'm surprised that you had a problem with Audacity beta. I've used it in W-----s, and was able to import audio with no problems.

Anyway, I wonder if folks would mind telling me the sort of power supplies they're using - power ratings, etc. I don't play games or have an extravagant number of peripherals (not even a printer - just a couple of IDE HDs and an external USB HD), but I'm wondering if in order to get reliable performance from Ubuntu I need to upgrade from my current measly 500W PS.

---

