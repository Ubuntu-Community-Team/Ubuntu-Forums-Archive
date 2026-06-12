---
title: "HELP with firefox freezing? I has information for you..."
date: 2008-04-07
forum: General Help
---

### Post by nofrendo on 2008-04-07
I have been having this problem with Firefox 2.0.0.13 in Gutsy for a while, and it has been my girlfriend's only complaint (I'm finally converting her)

The browser freezes (turns grey) usually when visiting myspace.com, but occasionally youtube, or other sites. It was just an irritation at first, but then I decided hey, the whole reason I'm using Linux is because if there's something I don't like about the system, there's always a way to fix it. So my solution was to simply change my AWN icon to open Firefox in a terminal. Well I finally got the error, hopefully someone will be able to tell me what to do

the output was:

** (gecko:7694): WARNING **: Invalid borders specified for theme pixmap:
        /home/sweett/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image

GP plugin failed
GP plugin [something else]


The first part I get whenever I start Firefox, but as for the second part, the terminal window closed as soon as I highlighted it, but thats what I remember. Help anyone? I'll try to get the actual output if it happens again, but strangely opening it in a terminal every time lowered the incidence of this happening.

---

### Post by FuturePilot on 2008-04-07
This is a Flash problem. It's been around for a very long time and Adobe seems reluctant to fix it. There's nothing that can be done by us since it's closed source. As for the first error, that is related to the GTK theme you are using and is not related at all to Firefox crashing.

---

### Post by nofrendo on 2008-04-10
Yeah the first error doesn't worry me because it's not causing any problems.

Oh well, thanks for the info

---

### Post by zeronothing on 2008-04-11
are you using the x86 version of Ubuntu or are you using the 64bit edition. the reason I ask is because I currently use the 64bit version and I experience the same problem. I have noticed if I open up system monitor and their will be a process listed as "npviewer.bin" if you end that process it will actually unfreeze Firefox. then you can hit refresh on Firefox to try and fix the flash on the page you are viewing. just a thought.

---

### Post by nofrendo on 2008-04-20
I use x86 Ubuntu. I'll try the npviewer thing next time it happens though and possibly try to setup a bash script to kill it automatically? I'll have to figure out what it is first though.

---

