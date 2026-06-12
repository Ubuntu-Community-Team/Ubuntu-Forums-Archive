---
title: "New Happy User: A few Audio Questions Though"
date: 2007-12-24
forum: General Help
---

### Post by studiesinsound on 2007-12-24
Hello,

Just bought a new Dell Vostro 1000 with the 2.0 Gig AMD X2 64 bit processor and 2 gigs ram.
Using outboard usb soundcard M-Audio FastTrack Pro.
Also using a trigger finger and fcb1010 pedal for midi.

The short story is, tried 64 Studio, Install went fine but the OS never booted, kept hanging up when initializing my cd drive.

So switched quickly to Ubuntu Studio, installed and runs like a champ.
All Hardware detected and works fine.  Even got the wireless up and running based on a previous thread I read on this board.

I'm loving it. \\:D/

I have a few questions/issues though, and these are probably due to me being new to Ubuntu and Linux so bear with me:

1: I want to use my laptop for live performance so I want my base set of performance applications to open up on startup.  I found a post here tht advised to add them to the startup tab in the Sessions window.  That works great except: 2 of the applications are Jack Control(configured to automaticallystart the Jack Server on launch with patchbay persistence on and configured) and Timemachine, to capture the output of my performance.  However it appears that Timemachine tries to launch too soon, and never fully launches because the Jack Server is not yet started.  Is there a way to somehow insert a pause in there so Timemachine waits say 5 seconds before launching?

2: SooperLooper: I've used this on the Mac OSX and am familiar with the app and Jack but I think I must be missing something.
I think I have everything configurd correctly, Jack Server is running, launch SooperLooper, and it is slow to launch and then the gui shows up, and then an error, somethign to the effect of "could not connect to host, make sure jack server is running"  if I hit okay on this, then the GUI finishes launching and it is connected to Jack.  Why am I getting that error each time?  I did note that Synaptic lists the latest version of SooperLooepr as 1.0.8 but the SooperLooper site lists it as 1.14.  I will try a manual install fo the latest version of SooperLooper but was wondering if someone had any other advice on this problem.


thanks fro any information.

---

### Post by alan34 on 2007-12-24
Try - (10 seconds)

sleep 10 && nameofyourapplication

Happy Christmas

---

### Post by studiesinsound on 2007-12-26
alan34,

Thanks for the reply.
I tried that but I must be doing something wrong.

I enter that command where?  
Becasue I tried in the Sessions-startup item for timemachine in the command line to enter what you wrote but still time machine does not launch.

Like I said I must be doing something wrong.

Sorry for being such a noob.

-John

---

### Post by terminal on 2007-12-26
yes he meant to edit startup entry of time machine in sessions . Click on edit if it already have or add new entry , name it whatever u like and suppose if timemachine is command to start it , if you enter "sleep 10 && timemachine" (without quotes ) instead of timemachine , then it will first wait for 10 seconds and then start timemachine command .

---

### Post by studiesinsound on 2007-12-26
thank you terminal.
I thought I tried that but maybe I fat fingered it.
I'll check when I get home
thanks.

---

### Post by studiesinsound on 2007-12-27
hi guys.
so yeah this didn't work.
I am able to get jack to startup fine.
i know the command to start timemachine is /usr/bin/timemachine

i double and triple checked te command plus the syntaxt f the preceeding sleep command, deleted it, re-entered it, no good
timemachine never launches on startup.

i can click on it fine, no poblem.

oh well.  thanks though.
maybe I'll try tonight to increase the time to something silly like 30 and see what happens.

---

