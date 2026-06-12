---
title: "Windows ok, kubuntu disconnects in a few minutes"
date: 2023-08-28
forum: General Help
---

### Post by bjngchn on 2023-08-28
Ultra new computers.
One has windows, everything disabled as much as possible, but 
still an unwanted browser running in the background whole time.
BUT INTERNET IS FAST AND HAS NO PROBLEMS.

The other has ultra new KUBUNTU.
Worked ok for a few weeks. 
NOW, has stupid problems when logging in, LOGGING OUT, shutting down
MOREOVER DISCONNECTS FROM WIRED INTERNET IN 10 MINUTES.

How can any version of any operating system can be counted as reasonable,
when internet disconnects for no reason at all
(maybe because I disabled blutooth and wireless, WIRED SHOULD NOT WORK EITHER???)

and whenever I bring a very important topic to the table anywhere, 
I see total silence. Maybe noone sees my posts. 
Because something needs to be exposed if it is discussed.

---

### Post by Holger_Gehrke on 2023-08-28
Please, stop the confrontational tone. All the people here who could potentially help you are volunteers who do this because they've got the time and like to help.

Without knowing a lot more about your system nobody will be able to understand the problem well enough to even guess at a solution.

So, please post the output of 'inxi -nNz' which will tell us what network devices are recognized and what drivers are used for them. Also useful would be the last 100 or so lines of the Kernel message buffer and the main system log file just after the connection has failed. To capture those run 'sudo dmesg|tail -n 100 > kernel_messages.txt' and 'tail -n 100 /var/log/syslog > syslog.txt' after cold booting the system and waiting until the network connection fails.

Holger

---

### Post by yancek on 2023-08-28
It's rare to find and 'ultra new' computer that works perfectly on Linux.  The home computers are designed to run windows and have it preinstalled so all the necessary software is available.   Linux developers do this without the same help from manufacturers so it is usually a few months before new works well.

If your Kubuntu worked for several weeks, what changed?  Something must have.  Did you update any software/hardware that might be related.  I would suggest you post the information requested in post 2 for starters and also use on thread for the login problem and one for the internet problem.  Much more detail is needed for anyone to help.

---

### Post by MAFoElffen on 2023-08-28
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and post the URL of where it uploads the report to.

RE: [https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

I am interested to see the Network section of that reports, as well as other hardware related sections...

I am one of those volunteers. I am fortunate to own one of those "ultra new" computers, as I just upgraded my 13 year old Workstation recently. I can tell you with Ubuntu 22.04.3 LTS, it just installed and ran out of the gate. I would have expected there to be some problems with 13th Gen i9, Z790 chipset, and PCIe Gen 5... But there wasn't. There was one firmware file for ARC A780. It still worked, but to upgrade that was inconsequential. 

That was not the story for Windows 11 (I have done dual-boots since 2005). I had to load "many" vendor motherboard device drivers for Windows just to see the new Z790 chipset, so that Windows could see the other hardware controllers on the bus, let alone many other attached devices. The Windows Device Manager was full of errors and warnings until then. It didn't help that it affected the networkign not working, so i could not get any drivers through Windows Update. But that is just "usual" and had to be dealt with.

Here is some stat's from that 'ultra new' hardware:
```

mafoelffen@msi-ubuntu:~$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Comcast Cable (71.197.252.194)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Ziply Fiber (Bothell, WA) [85.17 km]: 28.43 ms
[COLOR=#ff0000]Testing download speed................................................................................
Download: 427.44 Mbit/s
Testing upload speed......................................................................................................
Upload: 5.76 Mbit/s
[/COLOR]
```
Not a problem here on 'ultra new' hardware...

Waiting to see more info from you and your hardware.

IMHO--- Starting out by ranting about a problem without providing what the hard facts are, provided by supporting data, may not be a way to ask for voluntary support. That is sort of like biting the hand that you would like to feed you. LOL I'm thinking you were just a bit frustrated.

We, here, are not employed by Canonical and get nothing back from doing Ubuntu Community support that we voluntarily provide, except our own satisfaction that it is just the right thing to do. 

Fellow members here have been around and have had to resolve things ourselves. We share that experience with others. Some of us are involved with various testing, but we have no direct control of how Ubuntu is put together, nor the directions they take with things. We just have to deal with what is given us to work with, just like everyone else.

---

### Post by bjngchn on 2023-09-07
Ok, since I don't expect a real /easy /logical solution, I tend to not visit my posts often.   

Because things are fundamentally wrong. Not slightly wrong.   
For example I download kubuntu .iso file, and I need to use something else to burn it. 
Things were better in the past: I would just click on .iso file and it would burn via k3b.    
We all know everyone wants our info, our phone number and email as our starting point, 
and connect  everything to those. 
And connecting to internet while installing, updates, feedback/help links,  bluetooth, 
unremovable batteries, cameras on both sides, closed source operating systems,vaxxes .. 
all part of the same agenda, invading everything secrectly.  

So here we use user friendly linux, namely kubuntu, and get rid of closed source operating system. 
Others can be disabled one by one. But then internet doesn't work, or stops working after 10 minutes. 
Looks like linux community is part of the same game (or has no power to counter such things)

I will give all my info, namely output of some command, and it may secretly contain my pw, or create a backdoor, 
and most people here may not know about such possibilities when trying to help either. 
 I'm not looking for individualized help.
   Newest kubuntu doesnt work, so it must be fundamentally wrong. 
Then I prefer an older more stable version, or maybe even another user friendly linux.   

WHAT I DID since installing the kubuntu: Installed audacity, avidemux, kaffeine. 
 I don't think they discconnect me from wired internet; I don't use them normally, 
they sit there to be used in future, or if I edit/watch something offline. 
  Maybe this bug came with an update.  
Disconnecting me from internet is not in anyone's best interest, 
except if they think they can force me to use blutooth or wireless.
 I would prefer dying to using BT or wireless. 
  Enormous waste of time just because I don't want to be a slave (and everyone ok being a slave). 
 The whole summer wasted with failed kubuntus of past and today.
  I have to use windows (so I'm slave) and everything seems to be ok, but I don't use anything except firefox.

---

### Post by bjngchn on 2023-09-07
Let me be more clear.

I can't logout normally, computer freezes and shows me nonsense lines, 
I'm forced to press on/off button  for a while to force shutdown, to be able to use the computer ever again.


Let me tell you what while lines on the black screen shows me:

[           1.67.........2]  nouveau 00001:00.0: sec2:  TRACEPC:      000....17

20 lines like this.

And 1 line like this:

[   163.3..........9]  Bluetooth: hci0 Malformed MSFT  vendor event:  0x02

one line like this:

[  172.9........8]  nouveau 0000:01:00.0: sec2: halted

one line like this: 

[  172.9.        4] nouveau 0000:01:00.0: sec2:  TRACEPC  SCTL 000007021 TIDX  1b1f0000

and about 30 lines like this:

 [  172.9.        5] nouveau 0000:01:00.0: sec2:  TRACEPC:  00......3ac

SO THERE ARE ABOUT 50 lines of nonsense,
1 of them mentions BLUETOOTH (isn't it supposed to be Blutooth)  

All except 1 has noveau
All execpt 2 has TRACEPC

So, there is an obvious evil here... WHY, because I'm logging out of an operating system,
this MUST have nothing to do with wireless or bluetooth or blutooth, or tracing my PC.

Someone wrote those lines in advance, otherwise I wouldn't see them  Question:

WHO WROTE THOSE LINES. 

Is it hardware or softare related? 

I mean, at least someone wrote words like Bluetooth Malformed, nouveau, TRACEPC,
and the rest might be computer generated.

....And disconnecting from wired internet in 10 minutes is realted to this, because both problems started simultaneously.

---

### Post by Autodave on 2023-09-07
You do realize that your attitude is probably going to keep a lot of people from trying to help you, don't you?

Re-reading your initial post, you have 2 machines.  And they both worked at the outset.  Have you possibly considered that some hardware possibly failed in the Linux machine?  Have yo checked the internet cabling to make sure that it is OK to the Linux machine?  Exactly what version of Kubuntu are you using?  What kernel are you using?

People have asked for info, but you refuse to give it and then criticize them for not being able to help???  Really?

---

### Post by bjngchn on 2023-09-07
Let me comparethis with a real life situation. I have a new house, and there is a furniture and everything inside,
I trust someone (linux) to take care of my house.

I leave, and when I come back, I see many things are wrong, like TV not working, 
water leaked from somwhere, window broken, and I ask the person who was helping me for free
what the hell got worng, or might have gone wrong, 
and instead of answering he asks questions, like 
what I was doing outside, when I first noticed something is wrong, etc.

Is this a reasonable thing...I mean, that person may have good intentions,
and may have worked for free, but he didn't take care of my home correctly, 
and instead asking questions; as if he wants to know whether he can invent a story
based on my answers, and get away with his actual mistakes, and at the end appear as a trustable helper.

This may be an extreme example, but this is the key point: Someone wrote those lines
with TRACEPC, BLUETOOTH.. they are not supposed to be there.

(Of course I'm not blaming any innocent person, 
and such a person doesn't need to get panicked or offended )

20 minutes passed still logout is not complete , probably it will never be complete.
Also the computer is a little bit more noisy: it is working hard while doing nothing visible.
 Shutdown would take long as well, but complete in 10 minutes.

---

### Post by bjngchn on 2023-09-07
Ok, two identical brand new  machines, 
one has windows which is ok, 
another has brand new kubuntu

kubuntu worked correctly for a few weeks.
sometime avidemux, audacity, kaffeine were installed

not sure exactly when, but login-shutdown-LOGOUT problem started out of nowhere.
About the same time, wired internet stopped working after 10 minutes. 
(wired internet works for 10 minutes after starting the computer and logging in as a user,
so it works but disconnect without a reason, because windows pc is ok with wired internet)

This is very abnormal. 
Someone is connecting LOGOUT PROCESS to BLUETOOTH which is disabled anyway.

There are 4 possibilities here:

1.HARDWARE IS GUILTY.. but if so, how does hardware know what I'm doing.
2.SOFTWARE IS GUILTY , it is a BUG: If so, take this as valuable feedback.
3.SOFTWARE IS GUILTY, and this is INTENTIONAL: Would cause panic
4. DOWNLOADED PROGRAMS TOOK OVER THE PC: Complete control over
the PC just because used those programs a few times, is this even possible. 
They are well known programs previously in repo.

---

### Post by Autodave on 2023-09-07
Let me compare this with a real life situation: I have a new house and the roof is leaking.  Someone who lives in another country asks me where it is leaking from: into what room.  I refuse to tell him because I am afraid that he will use that info to try and break into my home.  So, instead of telling him where it is leaking, I demand that someone else help me and then I get angry when no one seems to want to help me.

---

### Post by bjngchn on 2023-09-07
So, I install kubuntu, all kubuntus should be exactly the same. they have the same hash etc. If it works in one computer it must work on another computer, unless  there are hardware problems, such old computer, being exposed to high magnetic field etc.   Let's say I multiply 2 numbers on a calculator, one gives correct answer, and the other doesn't. How can a calculator fail to give the correct answer. In atomic level everything can be different,  but the output should be exactly the same. Same commands  ---> same output.   
For example can this happen: I watch a cartoon on TV in the morning and the computer doesn't like it, so it decides to not connect to internet. These should be unrelated things.  Some hidden forces mixing things up in an unreasonable and unacceptable way. 

So I repeat the same question: WHO WROTE THOSE WORDS INTO HARWARE OR SOFTWARE: Bluetooth malformed, TRACEPC. 
This question must have a clear answer and noone knows? Noone here may know if it is a hardware issue.
If it is a kubuntu issue someone must know.
And then what would be the purpose
Why prevent a normal logout with these unexplainable errors
why disconnect from wired in ternet after 1 minute (less than 10 minutes this time)

---

### Post by Autodave on 2023-09-07
I am done here.  And I don't think that anyone is going to try and help at this point.

---

### Post by bjngchn on 2023-09-07
They must help (answer meaning of those errors), otherwise this is like admitting things.
(or being worried about admitting things). 

One responder should not block others' responses.

---

### Post by Autodave on 2023-09-07
I am not, and cannot block anyone else from answering.  But your attitude makes it very hard for anyone to want to help.  You come in here *demanding *that someone helps you.  In return, a couple people tried to do that by asking you for some info that you are afraid to give.  If you are that paranoid about your privacy being invaded then you really need to quit using computers!  Without the info that was requested, no one here is *capable *of helping you......can't you understand that?  Kinda like going to the doctor and telling them you are sick but then refusing to answer any of their questions or undergo any testing.  The doctor will *never* be able to help you.

---

### Post by bjngchn on 2023-09-07
I didn't even look at those commands, it is not all about privacy. 

If this is all about typing commands and posting the output, then I will never know what went wrong,
and the same thing can repeat, something else can get worse, same problem can appear again
in another computer with kubuntu installed with the same flash-disk.

Solutions should be universal, not personalized.
For example it can be added to updates.
If there is a bug from the beginning, then,
I expect people to have some idea about it. For example, they can say, such things may have happened,
or they can explain what bluetooth have anything to do with logout.
If my problem is visibly fixed, was it really fixed. 
You can give painkiller to an arthiritis patient, and things will just get worse, and you can't just say
"doctor gave me that drug, I trust my doctor, he is smart,.."
I would want to know why I have arthiritis, and what his will drugs do to my body. 

So, "being cured" may not be my priority here.

I'm asking: How is logout process related to bluetooth in any way.
Does it make slightest sense.
And what is TRACEPC

Also asking: Is it normal that wired internet disconnects in 1 minute 
on kubuntu (while it never disconnects on windows). 

Maybe I can try those commands but first some basic questions need to be answerable. 

In other cases people were saying things like, for the best result backup your files,
format your computer with the newest version of everything, ..
ok here, there is not much to backup, I can format the computer with the newest version,
but the newest version is the problem itself. If it is supposed to be this way, then 
we shouldn't use newest kubuntu, use older nicer version  
(and who cares about updates, they seem to be making things worse).

For example my old browsers on on older computer were not working 
(cloudflare was demanding newer version, probably for bad reasons), 
and I reinstalled browsers, and then after shutting down the computer I was unable to start.
So just because I have newer better something, computer dies (hopefully not permanently). 

Let's say I  buy a new house, and one of colons is weak,.. what am I supposed to do in such a case.
First I ask builders, is this normal. I don't say: let's make this colon stronger, let me send you samples
from the colon and so you can analyize them in the lab..You can say such things about historical buildings,
not brand new ones.

---

