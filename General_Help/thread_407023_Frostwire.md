---
title: "Frostwire"
date: 2007-04-11
forum: General Help
---

### Post by kevindubrow on 2007-04-11
Hi, I just installed the latest version of Frostwire on my computer and I am not able to open the program. There is no picture icon for Frostwire in the applications menu and I get no error message when trying to open the program, it just wont open. Any help opening the program would be great. Thanks!

---

### Post by jputman01 on 2007-04-11
where did you get the package? did you get it from frostwire website? i remember i had this same issue when i got it from frostwire website then i got the package from the repos (i think) and it worked fine.

---

### Post by kevindubrow on 2007-04-11
Yes, I got it from the website. Ill look for the website youre talking about. Thanks.

---

### Post by Maestro23 on 2007-04-11
> **kevindubrow said:**
> Yes, I got it from the website. Ill look for the website youre talking about. Thanks.

I installed the .deb from the frostwire website with no problems.  I'm running Feisty w/ java6.

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by InuyashaDuelist on 2007-04-11
Make sure Java is installed first, or the program won't open.

---

### Post by kevindubrow on 2007-04-11
If Java didn't come with Ubuntu 6.1 i need to go get it, do i just grab the Linux file off of Java's website?

---

### Post by Maestro23 on 2007-04-11
> **kevindubrow said:**
> If Java didn't come with Ubuntu 6.1 i need to go get it, do i just grab the Linux file off of Java's website?

Should be in the repositories.  Open up Synaptic, search for java

---

### Post by kevindubrow on 2007-04-11
Ok I did the search, should I just mark each file that has anything to do with Java? or is there a specific file I need?

---

### Post by jputman01 on 2007-04-11
DOH!! i totally didnt even think to ask if you have java installed, i believe if you mark your file for download synaptic should take care of it for you


should have read it better, you need the JRE file for java runtime environment, dont need the development package unless you plan on developing

---

### Post by kevindubrow on 2007-04-11
Thanks so much everyone, the files are downloading now...apparently I don't know much about Ubuntu yet. Thanks again, ill tell you if it works.

---

### Post by kevindubrow on 2007-04-11
Ok, after installing Java, Frostwire still will not open, any other ideas? Thanks.

---

### Post by divisionbyzero on 2007-04-11
what java version are you using? i found out that frostwire on my machine doesn't run with java 6 - only with java 5 runtime.

also, if you have beryl running, even if you did get frostwire to run - it might only show up as a blank screen. in this case, disabling beryl fixes this problem.

---

### Post by kevindubrow on 2007-04-11
Hi, well when I look at my internet applications, I have Java web start 5.0. I don't know what beryl is and I don't believe I have it. Did I download the wrong Java file (i got it from the repos)?

---

### Post by Franscisco on 2007-04-14
How can I desable Beryl? what are the steps. I am having the same problem.

---

### Post by Cris(c) on 2008-01-30
Hi guys,

    There must be something wrong with the arch or so, because even though I comply with all the java requirements I keep getting the following error:

cristian@cristian-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b825629ce25, pid=16067, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid16067.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 16067 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)


Any suggestion about what could be done to have FrostWire working? I am running Ubuntu 7.10  .

Thanks!

---

### Post by Cris(c) on 2008-02-04
UPDATE: Solved...there was a problem with the PATH of java. Though I had installed the correct version of Java, for some reason the PATH was not updated correctly. So, you should make sure the path is pointing toward the correct version of Java. After this is solved, Frostwire runs very smoothly!

---

### Post by TestTubeBaby on 2008-02-08
> **Cris(c) said:**
> UPDATE: Solved...there was a problem with the PATH of java. Though I had installed the correct version of Java, for some reason the PATH was not updated correctly. So, you should make sure the path is pointing toward the correct version of Java. After this is solved, Frostwire runs very smoothly!

How do you fix that? I'm having the exact same problem and am still very new to ubuntu and linux.

---

### Post by NovaAesa on 2008-02-09
> **TestTubeBaby said:**
> How do you fix that? I'm having the exact same problem and am still very new to ubuntu and linux.
I need to know this as well.

---

### Post by tgrisier on 2008-02-11
> **NovaAesa said:**
> I need to know this as well.

Add me to the growing list of "need to knows".

---

### Post by apetresc on 2008-02-11
For those of you having problems with java:

what is the output of ```
java -version
``` ?

---

### Post by tgrisier on 2008-02-11
> **AdrianP said:**
> For those of you having problems with java:

what is the output of ```
java -version
``` ?


anthony@anthony-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
anthony@anthony-desktop:~$

---

### Post by NovaAesa on 2008-02-11
```
ps@inspiron:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)
ps@inspiron:~$ 
```

---

### Post by y-lee on 2008-02-11
```
sudo update-alternatives --config java
```

and see if you can select java version 1.5 if it is not there you need to install it. I always install suns java as it causes me less problems.


**EDIT:** see [ java- Community doc]("https://help.ubuntu.com/community/Java") for more info

---

### Post by rainwalker on 2008-02-11
Also, the latest version of FrostWire runs find with Compiz/Beryl running, no need to try and disable it

---

### Post by tgrisier on 2008-02-12
> **y-lee said:**
> ```
sudo update-alternatives --config java
```

and see if you can select java version 1.5 if it is not there you need to install it. I always install suns java as it causes me less problems.


**EDIT:** see [ java- Community doc]("https://help.ubuntu.com/community/Java") for more info

Well I installed version 5 and selected it but frostwire still throws an error while startng. This is maddening.

---

### Post by y-lee on 2008-02-12
> Well I installed version 5 and selected it but frostwire still throws an error while startng. This is maddening.

Post the error that might help :confused:

```
frostwire
```

---

### Post by tgrisier on 2008-02-12
> **y-lee said:**
> **This post could be related to an Ubuntu bug filed at**: I added another one to general [stream0](&quot;http://stream0.org/&quot;) it is about Linux Multimedia - Video and Audio discussion, review and How-To.

I read a few more too. In time I'll go thru my RSS feeds  and add the rest if they are not already there :) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

Post the error that might help :confused:

```
frostwire
```


Sorry, I knew that...

```
anthony@anthony-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/usr/lib/frostwire/runFrostwire.sh: line 125:  5061 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

anthony@anthony-desktop:~$ 
```

---

### Post by y-lee on 2008-02-12
Well that seems to be a bug in Java, see the link in the script below.

You can try the script below I found at [`c->xlib.lock' failed error on Java applications]("http://daveshuck.instantspot.com/blog/2008/01/29/cxliblock-failed-error-on-Java-applications")

```
#!/bin/sh
# S. Correia
# 2007 11 21
# A simple script to patch the java library in order
# to solve the problem with "Assertion 'c->xlib.lock' failed."
# see bug http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373
LIB_TO_PATCH=libmawt.so
for f in `find /usr/lib/jvm -name "$LIB_TO_PATCH"`
do
echo "Patching library $f"
sudo sed -i 's/XINERAMA/FAKEEXTN/g' "$f"
done
```

Copy the script into your favorite text editor and save it. Change the permissions to make it executable and run it as root.

I don't know if it works so run it at your own risk. the worst i think it would do is mess up java. This error doesn't effect me so I can't test it or anything. Plus this is a little over my feeble minded head. :lolflag:

---

### Post by seventhc on 2008-02-12
I know you ran this before but run it again as you have more than one choice. I had to do this to make mine work and had to run it 2 or 3 times trying each one until it worked.
```
sudo update-alternatives --config java
```
or install java iced tea...I think thats what its called, search java in synaptic you'll see something with a similar name.

---

### Post by tgrisier on 2008-02-12
> **y-lee said:**
> Well that seems to be a bug in Java, see the link in the script below.

You can try the script below I found at [`c->xlib.lock' failed error on Java applications]("http://daveshuck.instantspot.com/blog/2008/01/29/cxliblock-failed-error-on-Java-applications")

```
#!/bin/sh
# S. Correia
# 2007 11 21
# A simple script to patch the java library in order
# to solve the problem with "Assertion 'c->xlib.lock' failed."
# see bug http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373
LIB_TO_PATCH=libmawt.so
for f in `find /usr/lib/jvm -name "$LIB_TO_PATCH"`
do
echo "Patching library $f"
sudo sed -i 's/XINERAMA/FAKEEXTN/g' "$f"
done
```

Copy the script into your favorite text editor and save it. Change the permissions to make it executable and run it as root.

I don't know if it works so run it at your own risk. the worst i think it would do is mess up java. This error doesn't effect me so I can't test it or anything. Plus this is a little over my feeble minded head. :lolflag:


Absolutely fabulous -- worked like a charm.  Thanks a million!

---

### Post by y-lee on 2008-02-12
Glad that worked cause i was just taking a chance dave on that blog knew what he was talking about.:lolflag:

Go ahead and mark this as solved, it is in thread tools above. Makes the forums easier to use for those that are here trying to help :)

---

### Post by tgrisier on 2008-02-12
> **y-lee said:**
> Glad that worked cause i was just taking a chance dave on that blog knew what he was talking about.:lolflag:

Go ahead and mark this as solved, it is in thread tools above. Makes the forums easier to use for those that are here trying to help :)


I don't see an option to mark as solved. I don't think it's going to let me mark it  since I didn't start the thread.  Unless I'm missing something somewhere.

---

### Post by apetresc on 2008-02-12
> **tgrisier said:**
> I don't see an option to mark as solved. I don't think it's going to let me mark it  since I didn't start the thread.  Unless I'm missing something somewhere.

You have to be either the thread creator or a moderator to mark a thread as solved. Since the thread creator hasn't posted in this thread for nearly a year, I think it's a safe bet that we'll be needing a moderator here :)

---

### Post by y-lee on 2008-02-12
> don't see an option to mark as solved. I don't think it's going to let me mark it since I didn't start the thread. Unless I'm missing something somewhere.

Sorry I thought you did start it forgot to look at page 1 :lolflag:

---

### Post by tgrisier on 2008-02-12
> **y-lee said:**
> Sorry I thought you did start it forgot to look at page 1 :lolflag:

No problem.  So how do we go about getting a moderator to mark the thread?

---

### Post by skippi90 on 2008-02-12
Wow! I didn't know there was a LimeWire clone for Ubuntu! Excellent :)

Installed fine from the .deb on the site. :)

---

### Post by tgrisier on 2008-02-12
> **skippi90 said:**
> Wow! I didn't know there was a LimeWire clone for Ubuntu! Excellent :)

Installed fine from the .deb on the site. :)



Oh yeah, it's an excellent program.

---

### Post by y-lee on 2008-02-12
> **tgrisier said:**
> No problem.  So how do we go about getting a moderator to mark the thread?

I suppose you would write one, but I wouldn't worry about. The original poster might still have issues or might be gone for good. Maybe tho one of them will notice on their own, they read these post just like we do. Either way I feel i learned something valuable here and this post will help others :)

> Wow! I didn't know there was a LimeWire clone for Ubuntu! Excellent

Installed fine from the .deb on the site.

Yep it is a great program, been using it about a year with no problems :popcorn:

---

### Post by Chimera76 on 2008-02-15
> **y-lee said:**
> ```
sudo update-alternatives --config java
```

and see if you can select java version 1.5 if it is not there you need to install it. I always install suns java as it causes me less problems.


**EDIT:** see [ java- Community doc]("https://help.ubuntu.com/community/Java") for more info

That fixed it for me! Cheers!

---

### Post by tango_ninja on 2008-02-16
you mentioned at the beginning of this thread that you downloaded frostwire from a repository....i've been searching for a repo with frostwire, can't find anything. which one did you use?

---

### Post by Chimera76 on 2008-02-16
> **Chimera76 said:**
> That fixed it for me! Cheers!

I stand corrected....now it opens, but I can't seem to open the correct port for it....I tried opening the port coming up in Firestarter and my router...but its still not working...which I find kind of odd...

---

### Post by y-lee on 2008-02-16
> **tango_ninja said:**
> you mentioned at the beginning of this thread that you downloaded frostwire from a repository....i've been searching for a repo with frostwire, can't find anything. which one did you use?


Yeah somebody did mention it but I don't think there is a [repo for frostwire]("http://ubuntuforums.org/showthread.php?t=412012&page=2"), Go to[ their  web site]("http://www.frostwire.com/") and get it is the best way. Whoever mentioned repo probably meant they used automatix which is [really a bad idea. ]("http://mjg59.livejournal.com/77440.html").

Anyway frostwire is easy to install they provide a deb for I think, download and click is about it. You might have a Java issue as it requires it, read this thread for help on that. :lolflag:

Maybe in time frostwire will be added to the repos here, it is a good program and deserves it. See [Rumor: Frostwire might make it to Ubuntu&#8217;s Repos]("http://www.frostwire.com/blog/?p=21")

---

### Post by y-lee on 2008-02-17
> **Chimera76 said:**
> I stand corrected....now it opens, but I can't seem to open the correct port for it....I tried opening the port coming up in Firestarter and my router...but its still not working...which I find kind of odd...

Check the ports in Frostwire>Tools>Options>Advanced>Firewall Configuration

and is Use UPnP checked?

---

### Post by locorogue on 2008-04-15
Ubuntu is a !@#$%^ pain in the !@#, at least crappy windows is pug and play without the instant brain tumor, ubuntu is garbage

---

### Post by seventhc on 2008-04-15
> **locorogue said:**
> Ubuntu is a !@#$%^ pain in the !@#, at least crappy windows is [COLOR=DarkRed]**pug and play**[/COLOR] without the instant brain tumor, ubuntu is garbage
First, learn how to spell, then learn how to ask questions....then learn how to use a computer! If after you've done these things and you still want to use windows, then use it, but don't complain here. I haven't used windows in years and have had no problems.

---

### Post by y-lee on 2008-04-16
> **locorogue said:**
> Ubuntu is a !@#$%^ pain in the !@#, at least crappy windows is pug and play without the instant brain tumor, ubuntu is garbage

One bean and this is what ya have to say, hmmm. Some win fan boy trolling for kicks i suppose :confused:

this is off topic for this thread but ubuntu has been remarkably stable for me installed painlessly and never crashes. I never had any problems with it and adopting to it from a windows dos past experience was just as easy as googling and reading man pages. Windows on the other hand has never been stable for me not since the beginning with win 3.0 and certainly not now with the resource  hog known as vista. Ubuntu is hardly garbage and it is as user friendly as any os. If ya like windows stay with windows just be prepared to pay and pay and pay as well as fight spyware crapware and viruses and hunt down missing dlls and so on. No OS is perfect and no OS is problem free. But most times the problem is the user and not the os but not always.

Anyway post your own thread if ya feel that way, this forum has a place for those kind of remarks. This thread was on frostwire problems and hasn't been used in a while and if frostwire is your problem we will be glad to help ya tho it might be better to post another newer thread. If you are trolling or hunting for a flame war we really don't need that here and it can get you banned from these forums by the mods or admins here.

---

