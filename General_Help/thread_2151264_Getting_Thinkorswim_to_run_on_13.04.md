---
title: "Getting Thinkorswim to run on 13.04"
date: 2013-06-03
forum: General Help
---

### Post by ProlongWealth on 2013-06-03
[COLOR=#000000]I am trying to get thinkorswim, a stock options and futures tradeing platform to run on ubuntu and having some trouble. [/COLOR]

[COLOR=#000000]Here is what is happening:[/COLOR]

[COLOR=#000000]1. I downloaded software and moved it to desktop.
2. I enabled software to allow executing file as a program and change to read and Write access.
3. Doble click to install
4. box open thinkorswim_installer.sh called gedit and just sits there for about 5 min retuned with there was a problem openig file.

5. not sure how to make screen shot and post it.

program worked ok with 12.04 before I installed complete new upgrade 13.04

Thx.[/COLOR]

---

### Post by 3rdalbum on 2013-06-04
Go to the terminal.

Type 'sudo ' and leave a spacebar at the end.

Drag the file to the terminal and hit Enter.

---

### Post by ProlongWealth on 2013-06-06
Thanks for the reply.  I followed your instruction but it launched the same "gedit" like from double clicking the icon and nothing...

---

### Post by jfosella on 2013-10-10
I'm having the same issue. Did you ever solve the problem?

---

### Post by rgoddard on 2013-10-25
I got it working by installing sun Java  1.6.  I used [this site to install java 6]("https://help.ubuntu.com/community/Java") (go to the Oracle (Sun) Java 6 section).  You will have to [sign in with (or create)]("http://www.oracle.com/") an oracle ID in order for the wget command to work.  You also need to accept their license agreement before downloading (otherwise you just download an html error response)...just go to the download page on any program on their site (I [used this]("http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html")) and check the license agreement radio  button.  Now you are ready for the wget :)

Once I did that I was able to install and use Thinkorswim in ubuntu 13.04.  The program sometimes crashes on startup, but I just close it and re-start and it works.  Another thing that helps is disabling the "Home" screen on startup, you can do this now from the "Home" screen itself instead of calling TD Ameritrade to disable it for you.

Overall I have been verfy disatisfied with the linux support since TDA took over the platform.  There have been an increasing amount of annoying bugs/issues and the installation instructions they provide are woefully out of date.

UPDATE:

After retracing my steps and reading the stern security warning for Sun Java 1.6....I went back and installed openjdk-6-jre....this did not go well.  The trade desk confirmed that TOS will not run on the openJDK and confirmed that Oracle Java 6 is the only option.  They also assured me that TOS would run on Java 7 soon....

---

### Post by davisd7796 on 2013-11-21
This does get irritating.  I applaud your efforts.  I have been using TD Ameritrade on 12.04 LTS x86_64 for several months with no problems (with my limited options trading, anyway), however, in the last couple of days, the mini charts and symbol links cause errors that look like a website error, but after trying on my Windows Server 2003 VirtualBox I verified that it's most likely a problem with my IcedTea browser plugin and/or OpenJDK6.  

I do not, however, wish to install Oracle Java, because, for one thing, it has caused problems in the past with other pages that I use more frequently and would rather hope that IcedTea gets an update soon that will restore this.  

I also just got bunch of package updates and a new kernel update (3.2.0.56-generic) a few days ago, so there might have been something in there that broke it, for all I know.  

I'm also curious about thinkorswim and would like to try it eventually, but my trading mentor has me using other web-based tools that work fine for what I'm learning now.  He's teaching me about options trading and I'm teaching him about open source.  It would be nice if at least these relatively basic popup chartlets worked to pull a quick check on moving averages.  I'm not even talking about the streaming thing, LOL!

---

### Post by davisd7796 on 2013-11-23
UPDATE:  Today, a new update to OpenJDK and IcedTea.  Now the site works better, the chartlets come up fine, the research links work, and my positions gained half a point on average, so, good day!

---

### Post by rgoddard on 2014-01-24
TD Ameritrade has also updated the TOS Desktop to run on version 7 of Oracle Java (woo hoo).  Haven't been using it long but it seems to work well so far.  It also seems to have made the VIX explode ;)

---

