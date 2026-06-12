---
title: "[yet another] Java SDK Install Question"
date: 2005-10-08
forum: General Help
---

### Post by James_Nostack on 2005-10-08
I have been trying to install the Java 2 SDK on my Ubuntu computer.  I have seen this site [https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions) and tried my best to follow along.  But I am still having problems. 

Here are the steps I followed - please advise.
**STEP 1 - Download software from Java website**
This is harder than it looks, because I find Sun's website confusing.  But, I downloaded j2sdk-1_4_2_09-linux-i586.bin to /usr/java/

**STEP 2 - Get Extra Repositories from Multiverse**
I did this step.  (It was a few weeks ago, when I tried to do this the first time, so I don't remember all the details.)

**STEP 3 - Changes to Java Package Files**
Since I am using Ubuntu 5.04 Hoary Hedgehog, I did not perform this step.  

**STEP 4 - Package Build Steps**
This step makes reference to a line in **dpkg-architecture** which is supposed to read,

[INDENT]*DEB_BUILD_GNU_TYPE=i486-linux-gnu*[/indent]

except, that line in my **dpkg-architecture** reads, 

[indent]*DEB_BUILD_GNU_TYPE =i386-linux*[/indent]

In other words--I DID NOT FOLLOW THE SCRIPT AT THIS STAGE.  I did the best I know how, which isn't saying much, because I know so little.  I checked /usr/share/java-package/sun-j2sdk.sh and went to line 6, and made sure line 6 said referred to "i386-linux" so that the sun-j2sdk.sh would match my dpkg-architecture.

So, having done this, I typed
[indent]*fakeroot make-jpkg j2sdk-1_4_2_09-linux-i586.bin*[/indent]

And a lot of text began to appear-----
[indent][i]Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)[/i][/indent]

This warning is repeated for each of the missing plugins.

Then it detects the product, asks me for my name, e-mail, and agreement to the license.  Then it begins to unpack.  After a lot of unpacking, it ends this way....

[indent][i]Testing extracted archive... okay.

Create debian package:
    dh_testdir
    dh_testroot
    dh_installchangelogs
    dh_installdocs
    dh_compress
    dh_fixperms
    dh_installdeb
    dh_shlibdeps
    dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
    dh_md5sums
    dh_builddeb
dpkg-deb: building package `sun-j2sdk1.4' in `/tmp/make-jpkg.XXXXymo1Xu/sun-j2sd k1.4_1.4.2+09_i386.deb'.
    copy sun-j2sdk1.4_1.4.2+09_i386.deb into directory /usr/java/
cp: cannot create regular file `/usr/java/sun-j2sdk1.4_1.4.2+09_i386.deb': Permi ssion denied

Aborted (/usr/java/)[/i][/indent]

========
So, even though I am trying to follow the [Java Package Build New Versions wiki page](https://wiki.ubuntu.com/JavaPackageBuildNewVersions) I am still having problems.

For one thing, that page refers to **jdk-1_5_0_(x)** but the only version of the SDK I can find on Java's website is **j2sdk-1_4_2_09**.... does that make a difference?

Anyway, if anyone could advise me I would appreciate it.  I am a n00b at Linux.  How stupid am I?  I am so stupid that I do not know how stupid I really am.  So, any help would be wonderful and I will thank you very much.

---

### Post by brentroos on 2005-10-08
*
[]("http://ubuntuguide.org/#extrarepositories")

---

### Post by Leif on 2005-10-08
add this to your /etc/apt/sources.list, sudo apt-get update, sudo apt-get install sun-j2sdk1.5. this is, imho, the simplest way.

if you want to go the jpkg way, sudo apt-get install build-essentials first. also, you definitely can download the 1.5 sdk from sun, look again.

---

### Post by James_Nostack on 2005-10-08
[QUOTE=brentroos]Have you tried this way?

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

It worked flawlessly for me.[/quote]

that's the JRE and not the full SDK, right?  Anyway, I tried it just now, and received--

[indent][i]james@bender:/usr/java$ sudo apt-get install sun-j2re1.5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5[/i][/indent]

---

### Post by James_Nostack on 2005-10-08
[QUOTE=Leif]add this to your /etc/apt/sources.list, sudo apt-get update, sudo apt-get install sun-j2sdk1.5. this is, imho, the simplest way.[/QUOTE]

I received this error message
[indent][i]james@bender:/usr/java$ sudo apt-get install sun-j2sdk1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2sdk1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2sdk1.5 has no installation candidate[/i][/indent]

PS - I'm very dumb, and do not understand this line you wrote -- "add **this** to your /etc/apt/sources.list" - what do you mean by "this?"  I am sorry for not knowing, and appreciate any help you can give.

---

### Post by Leif on 2005-10-08
[QUOTE=James_Nostack]
PS - I'm very dumb, and do not understand this line you wrote -- "add **this** to your /etc/apt/sources.list" - what do you mean by "this?"  I am sorry for not knowing, and appreciate any help you can give.[/QUOTE]

doh ! you're not dumb for not knowing how to do that, I left some stuff out. I'll try to do it right this time. open a terminal, and type "sudo gedit /etc/apt/sources.list". at the end of that file, put in "deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java". close it, then type "sudo apt-get update", and "sudo apt-get install sun-j2sdk1.5". that should do it.

---

### Post by James_Nostack on 2005-10-08
Hello Leif, thank you for explaining that!  Now when I type
[indent]*java -version*

I get this message.....
[indent][i]java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)[/i][/indent]

TERRIFIC!  Everything works....

Except now when I go to [the Virtual Machine Test Page](http://www.java.com/en/download/help/testvm.xml) I still get a "click here to download plugin" error, saying that the JRE is not installed.  The JVM is part of JRE isn't it?

The site mentions three fixes--
1.  Enable JRE through the browser (in my case, Firefox 1.07) -- already done.

2.  Enable JRE through "Java Plugin Control Panel" -- I'm not sure if this applies to Unbuntu.  If so, I'm not sure how to do it.

3.  Clear your browser cache -- done, but doesn't help.

Thank you very much for all your help so far, I hope that other people who have this problem will learn from your good advice!

---

### Post by Leif on 2005-10-08
to get it working for firefox, you need to do this : "sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins". a bit obscure, isn't it ?

---

### Post by James_Nostack on 2005-10-08
Actually, I get
[indent][i]james@bender:~$ sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
ln: `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': File exists
[/i][/indent]

...and it doesn't appear to make any difference, still getting the "click here to download plugin" thing.  I'll try rebooting, just on general principles.

Thanks for being so patient.  It certainly is obscure!  I keep telling myself that I am learning new and useful skills, but it's so slow and requires the help of so many friendly people!

---

### Post by Leif on 2005-10-08
I'm happy to try to help. stick with it, there are a few bumps, but soon you'll feel nicely in control, and it keeps on getting better.

try deleting the existing plugin link and redoing it :

sudo cp /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so ~/Desktop/libjavaplugin_oji.so.backup
sudo rm /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

and restart firefox. if it works, delete the backup on your desktop

---

### Post by Leif on 2005-10-08
alternatively, try what this post says :

[http://ubuntuforums.org/showpost.php?p=258533&postcount=3#top](http://ubuntuforums.org/showpost.php?p=258533&postcount=3#top)

---

### Post by James_Nostack on 2005-10-08
Okay, this is weird -- 
[indent][i]james@bender:~$ sudo cp /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so ~/Desktop/libjavaplugin_oji.so.backup
Password:
cp: cannot stat `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': No such file or directory
[/i][/indent]

Huh?!  So, I went to File Browser, found that folder, and saw two files --
**libjavaplugin_oji.so** and **libjavaplugin.so**!  Strange (at least to me).  And when I clicked on them to look at the file properties, the icons disappeared!

And when I hit "reload" on the File Browser they reappear.  And when I click on them, they vanish again.

Yet they are still listed in the terminal view---
[indent][i]james@bender:/usr/lib/mozilla-firefox/plugins$ dir
flashplayer.xpt  libflashplayer.so  libjavaplugin_oji.so  libjavaplugin.so
[/indent][/i]

And when I tried again to copy it to the desktop again, it says the file does not exist.

I am either smarter than I was a few hours ago, or much more confused...

---

### Post by James_Nostack on 2005-10-08
[QUOTE=Leif]alternatively, try what this post says :

[http://ubuntuforums.org/showpost.php?p=258533&postcount=3#top](http://ubuntuforums.org/showpost.php?p=258533&postcount=3#top)[/QUOTE]

Okay, we must have cross-posted.  

EUREKA!  THE ADVICE IN THAT LINK WORKED.  Thank you thank you, this was driving me crazy.  (And I was driving you crazy, so it all worked out in the end.)

Leif = helpful super-genuis to idiots like me.

I appreciate it.  I am actually heading to a bar right now, but we will offer a toast to you.

---

### Post by Leif on 2005-10-08
[QUOTE=James_Nostack]Okay, we must have cross-posted.  

EUREKA!  THE ADVICE IN THAT LINK WORKED.  Thank you thank you, this was driving me crazy.  (And I was driving you crazy, so it all worked out in the end.)

Leif = helpful super-genuis to idiots like me.

I appreciate it.  I am actually heading to a bar right now, but we will offer a toast to you.[/QUOTE]

dude, knowing to link some random file to some other random location has nothing to do with intelligence, so stop putting yourself down. I started using linux full-time about a year ago, and hung around the forums, keeping a log of all the weird tidbits I had to do to get everything working. stick with it, and I'm sure you'll be handing out advice yourself in no time.

also, have fun !

---

### Post by t_ras on 2005-10-10
I'm using AMD64 with 5.04.
I tried adding the path "deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java"but it still didn't find it.
I tried goign to http.... but it has only 386 version.
I tried the "Ubuntu unofficial guide" - same...
is it only for 386? 
can I install directly form SUN?

---

### Post by t_ras on 2005-10-10
it's wired, but I typed "Java -version" and got 1.4.2?!!
but when I install openoffice 1.1.5 it doent recognize any java!!??
any ideas?

---

### Post by Leif on 2005-10-10
try these instructions to install java : [http://ubuntuforums.org/showthread.php?t=70428&highlight=java](http://ubuntuforums.org/showthread.php?t=70428&highlight=java)

---

### Post by t_ras on 2005-10-10
ti looks the right solution, thanks

---

### Post by gdlx on 2005-10-18
A BIG thanks to all  of you. I have been following dead-ends for over two weeks trying to get a small java program to run. I could not get j2sdk to work until now. The switch to Ubuntu has been a bupppy one. The install was flawless but trying to get extra software going is like running thru a maze. There are so many suggestions that lead to nowhere.:D 
Next, I will work on the printer link.
Thanks again.

---

### Post by brentroos on 2006-03-03
*[URL="http://ubuntuforums.org/showthread.php?t=138405"]
[/URL]

---

