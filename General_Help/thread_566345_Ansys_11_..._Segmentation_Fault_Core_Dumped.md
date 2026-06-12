---
title: "Ansys 11 ... Segmentation Fault Core Dumped?"
date: 2007-10-03
forum: General Help
---

### Post by dmontalvao on 2007-10-03
Hi!!

I have installed Ansys 11 in Ubuntu Feisty (7.04). Everything seems to be ok when I run the launcher. However, when I choose to run a specific app, like Ansys Mechanical, it seems it will run, but suddenly it crashes along with the message: "Segmentation Fault (Core Dumped)".

I have searched a lot in the forums, and I realized this is a problem that may happen with several programs. So, I haven't found a specific solution for my case. Does anyone have an idea on how to solve this problem? I also wonder if it's possible... Any lib conflicting?

As far as I can recall I got a similar message with Labview7.1 (terminal window). But in this case, I am aware Ubuntu is not a supported Linux distro by Labview from National Instruments. Anyway, some people have succeded with Labview 7.0 and Ubuntu 6.06, and I read that with later Labview versions (8+) I might be able to deal with the problem. Concerning Labview, it is easy to find lots of things over the internet related to Ubuntu. However, that doesn't seem to be the case with Ansys.

If it isn't possible to run it, has anyone tryed running Ansys using VMWare or Wine? Also, I would like to know if u have experienced running other problems like Solidworks or Labview with VMWare (because of the 3D support problem) and if they behaved reasonably in terms of speed.

Thanks very much!!

Cheers!

---

### Post by dmontalvao on 2007-10-04
OMG!!! I feel so stupid!!!!

After all, everything is ok... The problem is I was choosing as "Simulation Environment" on the launcher "Ansys Workbench" instead of "Ansys". Now I can run Ansys Mechanical on Ubuntu Feisty! Woo hoo!

Well, I just posted this here because I think others might be stuck with this aswell.

(I still don't understand why I can't run Ansys Workbench, but, what the heck!)

Cheers!

---

### Post by raphha on 2007-10-13
Hello,
same problem here. However, I got one step further:

From the ansys linux installation manual, I took this:
start the launcher from a command window after running "ulimit -s unlimited".

This took me beyond the secfault, but then I ran into another error about "temp dir not found" and an error message wich just says "internet explorer", and then I end up with an empty workbench window (no buttons, nothing) which looks very much like a ms w$ window (no kde-window bar at the top). The only thing I can do is closing the window...

Maybe someone else has an idea for the next step??

best regards,
raph

BTW: I am using ansys v11SP1
and: one can actually click on the system information link on the bottom of the empty window, but that's it as far as I know

---

### Post by Steph_fr_37 on 2007-10-15
I have the same problem, i found something interesting here : [http://www1.ansys.com/customer/wb/forum/forum_posts.asp?TID=2030](http://www1.ansys.com/customer/wb/forum/forum_posts.asp?TID=2030)
It seems that its language problem, but it did not work on my french ubuntu distribution. Is it working for you. 
I hope someone have the answer for this trouble.
Steph

---

### Post by duni on 2007-10-26
Hi,
I was having allmost the same "Segmentation fault" message (Note: Only "Segmentation fault") and after trying "ulimit -s unlimited" and "ulimit -Sd 262144" I achieved the following:

- **./launcher110** is still unable to start Workbench, I get the same xterm window with "Press any key"

- **./startpage** still gives 
*"./startpage: line 24: 14875 Segmentation fault $DS_INSTALL_DIR/workbench -StartPage $*"*

- BUT when I run **./workbench** I get the logo screen and It stays for some more seconds, after that Workbench exits with "Aborted" instead of "Segmentation fault". And when I run **./startpage** again, after this empty ./workbench command I'm able to start workbench with the empty Workbench window and the small window to choose "empty project", "mesh project" and so on \\:D/ .
BUT then, when I choose a project and Workbench starts to load the environment :shock: it exits with the message 
*"./startpage: line 24: 14875 Segmentation fault      $DS_INSTALL_DIR/workbench -StartPage $*"*

With other words: ulimit is doing something right and I suppose the problem is exactly there, but I'm out of ideas what to try out next.
Hope that helps others to go that far to see the cool workbench window :) , and to further solve the problem.

my ulimit -a output:
[i]core file size (blocks, -c) 0
data seg size           (kbytes, -d) 262144
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 4095
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) unlimited
cpu time               (seconds, -t) unlimited
max user processes              (-u) 4095
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
[/i]

---

### Post by duni on 2007-10-26
Well, after playing with ansys I discovered that my previous post was not quite right. The "Segmentation fault" error comes "occasionally". When I run ./startpage for 5-6 times it finally starts workbench, but after some actions, aka starting a project, opening a file, etc., the "Segmentation fault" comes up.
I have only 512MB of memory and want to buy me another 512, I think that could change something.
What really bothers me is, that "Segmentation fault", or as far as I know "Signal 11", is a serious memory issue, so either the hardware or the software isn't quite right. I'm thinking that if I don't understand and remove the problem, even if the additional 512MB help, Workbench will still be unstable.

At this point I have to admit, that I hate to be isolated like that because of using linux. I used to love the idea of PTC and Ansys to make their products available on linux, but why do the linux installations have to be so painful in comparison to the windows ones. Why aren't there students/educational licenses for linux as for windows. Mostly engineers and programmers tend to use linux as desktop OS and one has to learn these programs before starting to work with them for commercial purposes...
It's not my goal to make a debate out of it, just after some days of trying and after the whole enthusiasm is gone I wanted to state my opinion on that.

---

