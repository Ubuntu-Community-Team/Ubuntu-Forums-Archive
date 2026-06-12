---
title: "Java CPU usage is really high"
date: 2008-03-22
forum: General Help
---

### Post by coolkid5 on 2008-03-22
I'm wondering about Java's cpu usage because when I run a java applet I made, it slows down a lot when I open a program or a large web page and it never speeds back up unless I restart the applet.  

So I looked at the system monitor: I have a dual core 2.6 amd64 processor (on 32-bit Gutsy) and the graphs of the cpu usage show that one cpu is almost 100% most of the time and the other is around 5%.  The graph shows the load switching between the two processors but they add up to about a constant 105% (out of 200% for 2 processors).  When I look at the processes it says java is using around 40-50% of the cpu.  I have eclipse open which I know uses java but it isn't doing anything it's just open.

Why is java using so much cpu?

---

### Post by Sam Lars on 2008-03-22
Is this in Firefox?  There's a bug in its Java routine.

---

### Post by coolkid5 on 2008-03-22
I was running my applet with eclipse's applet viewer and sometimes it starts to go slowly and never speeds back up.  Since I saw it was running slowly I stopped the applet and checked the system monitor.  The only things I had open were eclipse firefox and the system monitor and the java cpu usage was very high even though eclipse was the only java application open and it wasn't even doing anything.  Should the java process have been using up so much  CPU?

---

### Post by Sam Lars on 2008-03-22
Any specific time when it starts to use a lot of CPU?  Could you try any other applets in it to see if they do the same?  If you just run Eclipse and not the applet, does it do the same thing?
You might want to report this as a bug.

---

### Post by coolkid5 on 2008-03-23
Strangely, now I get different results.  With just firefox open right now I had average 3% usage on both cpus.  When I started eclipse the usage jumped up to start the program.  It went down again and java didn't use any processor at all when I let eclipse sit after it finished loading.  When I start my applet both cpus go to 100% and java goes up to 50% of my total cpu usage.  When I stop the applet java goes down to zero again.  When I made my last post java was not at 0% even though my applet was closed and eclipse was not doing anything.  That problem did not occur this time, but when my applet runs it uses 100% of both cpus?!

---

