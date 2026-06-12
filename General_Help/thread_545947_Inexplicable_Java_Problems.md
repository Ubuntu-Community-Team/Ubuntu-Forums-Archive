---
title: "Inexplicable Java Problems"
date: 2007-09-08
forum: General Help
---

### Post by LodeRunner on 2007-09-08
As I previously mentioned in [this]("http://ubuntuforums.org/showthread.php?p=3321298#post3321298") thread, I've been using Interactive Broker's [TWS]("http://individuals.interactivebrokers.com/en/control/twscontrol.php?ib_entity=llc") platform for a year now when it suddenly quit on me.  No error, no nothing it just sits there in bash without producing the GUI.  This happened on my laptop and desktop simultaneously, so I figured an system update (which lately I've just been blindly installing, 'cause the pop-up notifiers are annoying and there isn't an obvious STFU button--a wee bit too Windows-like if you ask me, but that's a rant for another day) was to blame.

After a few hours of tinkering I've still gotten nowhere (can't seem to find a recently installed package to blame), so I decide to confirm that TWS will run like it used to with a fresh feisty install.  BUT... this is what I get when trying to install the JDK while running the livecd:

Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared
libraries: libjli.so: cannot open shared object file: No such file or
directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127

Same error if I try using the java5 JDK instead.

I'm too tired to make sense of it anymore.  The install disc is the same and the repository I downloaded it from is the same.  I've installed Feisty damn near a half dozen times in the past few months, always with the JDK, and never seen this before (ok, so I'm trying to "install" it while running the liveCD but that shouldn't matter.)  

Basically, I've got one baffling Java problem making it impossible for me to troubleshoot another baffling Java problem. I would say that they're related, except I can't see how that could possibly be the case--neither the JDK nor anything else obviously Java-related was updated on my machines in the past week (in fact, I can say with 95% certainty that nothing other than kerberos was updated since the last successful TWS login.)

I guess I could try a manual jdk install...

---

### Post by alguin2 on 2008-05-29
[Copying you directly on this reply to your post of 2007/08/08]

How did you finally resolve the problem?  I have 8.04 hardy heron installed, and I'm just getting my interactivebrokers.com setup on Linux.  

One point of confusion regarding java on Linux is that there are several java run-time engines available.  With the Ubuntu package manager, one can go crazy and install any package that has "java" in it.  
After installation one of the versions is the default java, and the others have to be explicitly used (eg. by a wrapper script that prepends the preferred java "bin" directory to the PATH environment variable).

I saw a community doc regarding this issue: 
[INDENT][https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)[/INDENT] 

Actually, I'm still going nuts trying to consistently get TWS running.  Here is my problem: 
1.  I can definitely get TWS to come up.
2.  I can log in to TWS using my production IB account.
3.  When I log in using the paper trading account, TWS hangs.
4.  Tinkering with the java setups, I was able to get TWS started via Firefox (uses a JNLP Java Web Start). The JNLP version works with both my real account and the paper trading (test) account.  However, I want the option of being able to start TWS for both accounts without JNLP. One reason: in a dialup-only situation, it would take a long time to run the JNLP version because of the overhead in (re-)sending the application, but the local TWS version will/should be able to function much better (albeit with slow response due to degraded speed) because it doesn't have to be downloaded. 

I'll post any updates on this from my end, and would appreciate if you share any findings.


Thanks.

---

### Post by alguin2 on 2008-05-30
I've found that the Interactive Brokers TWS app runs best in java5.  Below are the relevant lines of my startup script:

[B]
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
export PATH="$JAVA_HOME/bin:$PATH"

cd $HOME/IBJts/.
java -cp "jts.jar:**p**luginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:**o**ther.jar:riskfeed.jar:rss.jar" -Xmx256M jclient.LoginFrame . 
[/B]

---

### Post by jamesstansell on 2008-05-31
> **alguin2 said:**
> 
[B]
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
export PATH="$JAVA_HOME/bin:$PATH"
[/B]

Setting the JAVA_HOME and PATH variables shouldn't hurt but really shouldn't be necessary either.  I'd be glad to tell you more if you like.

Just curious - when you say this runs best with Java 5 what do you mean?  Are you comparing it with Java 6?  Does the app feel slower?  Are there functions that don't work?  Something else?

---

### Post by jamesstansell on 2008-05-31
> **alguin2 said:**
> The JNLP version works with both my real account and the paper trading (test) account.  However, I want the option of being able to start TWS for both accounts without JNLP. One reason: in a dialup-only situation, it would take a long time to run the JNLP version because of the overhead in (re-)sending the application, but the local TWS version will/should be able to function much better (albeit with slow response due to degraded speed) because it doesn't have to be downloaded.

Theory does always stand up to real-world needs.  Theoretically, though, JNLP should be the preferred installation method.

1) it allows the developer to specify start-up instructions in a platform-independent way, including short-cut creation
2) if the application is already up-to-date it just runs it - no need for another download
3) if the application is out of date it can download just the parts that have changed, making it easy for you to run the correct version

That said, there have been problems with the debian/ubuntu packaging of the JNLP launcher.  Also if the developer doesn't know what they're doing they may be able to prevent the up-to-date checking from working the way it needs to.

---

### Post by gollybegully on 2008-06-20
Hi All, 

I'm also trying to get TWS running, but I haven't been able to install it at all.

Interactive brokers says to download the file and then execute "jar xf unixmacosx.jar" (jar command not found)

can somebody please take me step by step and really break it down cause im ignorant when it comes to this stuff, i still cant even untar anything without the most detailed instructions.

thanks, and good luck trading!

---

### Post by jamesstansell on 2008-06-21
Hi gollybegully,

The command "jar xf unixmacosx.jar" can generally be replaced with```
$ unzip unixmacosx.jar
```

The idea of the command is to extract the files from the archive, so it could also be done with some graphical tools.

I'm not familiar with TWS, so I hope some of your fellow traders can help you with more information.

---

