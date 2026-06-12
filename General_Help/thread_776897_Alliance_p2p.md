---
title: "Alliance p2p"
date: 2008-05-01
forum: General Help
---

### Post by prem1er on 2008-05-01
Just wondering if anyone has tried to get the new release of Alliance p2p up and running on Hardy or Gutsy yet.  I just read that version 1.0 has been released and I know the previous betas were a pain to install.  Anyone have success?

---

### Post by lenu on 2008-05-07
i tried to, but it was just too complicated for me. i really would want it up and running though.

---

### Post by prem1er on 2008-05-08
Version 1.1 is supposed to be coming out soon.  I will see if any fixes have been made to the linux version and keep you posted.

---

### Post by prem1er on 2008-05-12
Sorry.  Version 1.0.1 has just been released.  I am trying the install now and will let you know.

---

### Post by prem1er on 2008-05-12
Just got it up and running.  Still a couple hacks involved with the 'tray icon'.  If anyone is interested let me know and I'll post a HowTo.

---

### Post by maff on 2008-05-12
yes please

---

### Post by prem1er on 2008-05-12
Ok...I'm running this on Hardy.  Don't see it being a problem on Gutsy.  Also running the new version of alliance 1.0.1.

Download the alliance jar file from here 
[http://sourceforge.net/project/platformdownload.php?group_id=166584&sel_platform=8344]("http://sourceforge.net/project/platformdownload.php?group_id=166584&sel_platform=8344")

Save the file and unzip it into the directory you plan on running it in!

I created a directory in my /home folder named 'alliance' which I will use for the rest of this howto.

Next go to [https://jdic.dev.java.net/servlets/ProjectDocumentList?expandFolder=4183&folderID=5497]("https://jdic.dev.java.net/servlets/ProjectDocumentList?expandFolder=4183&folderID=5497") and download the linux version of JDIC.  Save the file and again unzip it into the directory you unzipped Alliance.

Next open up a text editor (nano) and create a bash script named something like 'alliance_start'.  Make sure again to save it in the same directory you have been using.

```
#!/bin/bash  
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 &
```

Now all you have to do is be in your 'alliance' directory and run the bash script by typing..."./alliance_start" or whatever you named your script.

Any errors or problems please post them in this thread and I'll get back to you.

---

### Post by mike70567 on 2008-05-12
I have found that you have to use Java 1.5.0

---

### Post by lilrabbit129 on 2008-05-13
I removed the error message redirection and got this error message:

Exception in thread "main" java.lang.NoClassDefFoundError: org/alliance/launchers/ui/Main

java version:

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

I'm still running Gutsy though. 

Thanks for the help.

---

### Post by prem1er on 2008-05-13
Make sure you are trying to run the "alliance_start" bash script in the directory that has all the files in it.

---

### Post by prem1er on 2008-05-13
Please post back if you have had success with this.

---

### Post by lilrabbit129 on 2008-05-13
I am running the script from the directory I extracted the jdic-20060613-bin-linux.zip to. Here is my directory listing:

alliance_start*
Alliance-v1.0.1.jar
cache/
ChangeLog
COPYING
data/
defmailer.properties
demo/
downloads/
javadoc/
jdic-20060613-bin-linux.zip
jdic.jar
libjdic.so
libmozembed-linux-gtk1.2.so*
libmozembed-linux-gtk2.so*
libtray.so
linux/
logs/
mozembed-linux-gtk1.2*
mozembed-linux-gtk2*
README.html
tray.dll


And the contents of alliance_start:

#!/bin/bash  
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main

I removed the output redirection so I could see the error messages it was outputting.

Please let me know if there's any other info about my system you require.

Thanks for all your help.

---

### Post by prem1er on 2008-05-13
I haven't had much time to look at it and I am about to leave work, but it looks like you forgot to unzip the Alliance-v1.0.1.jar into that directory also.  

Just 
```
unzip Alliance-v1.0.1.jar
```
into the current directory and I think you should be ok.

Before you do that however there is a new version available on the website.  Try that and post back I'll check back when I get home.

---

### Post by lilrabbit129 on 2008-05-13
That did the trick. I unzipped the .jar file ( after getting the newest version from the website ), and ran the script. 

Thank you for all your help. I never knew that .jar files could be "unzipped".

Thanks again!

---

### Post by RawDR on 2008-05-14
Is this working for people running 64 bit Ubuntu? I have followed the instructions but still get the same "library for system tray missing" errors.

---

### Post by prem1er on 2008-05-14
Haven't tested it on 64 bit sorry.  If you haven't tried this yet, you might want to check out the alliance forums.

---

### Post by Fped36 on 2008-05-19
Has anyone done this with Alliance-v1.0.3.jar. I have tried the script and it comes back with command not found.
I have unzipped everything needed, Do the files extracted from jdic-20060613-bin-linux stay within the Linux folder they are extracted into or do the seperate files go into the alliance folder?

I am running Hardy 8.04.

---

### Post by prem1er on 2008-05-19
Copy and paste the contents of the directory you created with the .jar file and the bash script into your next post.

---

### Post by Fped36 on 2008-05-20
The below is my directory contents

LICENSE.txt
README_ITP.txt
Alliance-v1.0.3.jar
linux                      
res
build
META-INF
Start_Alliance
com
net
cube                         
optiondialog
stopwatch.png
de
org
trace
errordialog
progressbarwindow.xui.xml
wizard
jdic-20060613-bin-linux.zip  
README_IDW.txt             
XUITest.xui.xml
junit                        
README_ILF.txt


and this is my bash 
```

#!/bin/bash 
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 & 
```

---

### Post by prem1er on 2008-05-20
> **Fped36 said:**
> The below is my directory contents

LICENSE.txt
README_ITP.txt
Alliance-v1.0.3.jar
linux                      
res
build
META-INF
Start_Alliance
com
net
cube                         
optiondialog
stopwatch.png
de
org
trace
errordialog
progressbarwindow.xui.xml
wizard
jdic-20060613-bin-linux.zip  
README_IDW.txt             
XUITest.xui.xml
junit                        
README_ILF.txt


and this is my bash 
```

#!/bin/bash 
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 & 
```

It looks to me as if you didn't unzip 'jdic-20060613-bin-linux.zip' or you unzipped it into the wrong directory.  That is why you are getting the error command not found, because it is trying to use a file that you don't have.

---

### Post by Fped36 on 2008-05-20
I now have the 'jdic-20060613-bin-linux.zip'unzipped into the same directory, but I still get the same result. the Jdic.jar is there as you can see my folder content below.

Alliance-v1.0.3.jar          
linux
build                        
META-INF
ChangeLog                    
mozembed-linux-gtk1.2
com                          
mozembed-linux-gtk2
COPYING                      
net
cube                         
optiondialog
de                           
org
defmailer.properties         
progressbarwindow.xui.xml
demo                         
README.html
errordialog                  
README_IDW.txt
javadoc                      
README_ILF.txt
jdic-20060613-bin-linux.zip  
README_ITP.txt
jdic.jar                     
res
junit                        
Start_Alliance
libjdic.so                   
Start_Alliance.sh~
libmozembed-linux-gtk1.2.so  
stopwatch.png
libmozembed-linux-gtk2.so    
trace
libtray.so                   
wizard
LICENSE.txt                  
XUITest.xui.xml

---

### Post by prem1er on 2008-05-20
Post me the exact error message you get when trying to run the bash script.

---

### Post by Fped36 on 2008-05-20
this is the message I get when I run the script

final@Compy:~/src/Alliance$ ./Start_Alliance
bash: ./Start_Alliance: Permission denied
final@Compy:~/src/Alliance$ sudo ./Start_Alliance
sudo: ./Start_Alliance: command not found

---

### Post by stranddrew on 2008-05-21
I actually get the exact same error. Is it something that we are doing wrong in trying to run the bash script?

---

### Post by prem1er on 2008-05-21
This may be a stupid question, but do you have Java 5 or Java 6 installed?

---

### Post by rodoyle on 2008-05-21
> **RawDR said:**
> Is this working for people running 64 bit Ubuntu? I have followed the instructions but still get the same "library for system tray missing" errors.

I am also running 64-bit Hardy and I am getting the same error. I think the compiled JDIC files are for 32-bit only? I don't really know enough about java to be sure.

---

### Post by Fped36 on 2008-05-21
I have Java 6

Edit:
I downgraded to Java 5 and I still receive the same thing.

---

### Post by prem1er on 2008-05-21
Yes.  I had this problem before and I'm trying to remember how I solved it.  I'll get back to you as soon as I remember.

---

### Post by stranddrew on 2008-05-21
i also have java 6 installed

---

### Post by Vinx Itak on 2008-05-22
> **Fped36 said:**
> this is the message I get when I run the script

final@Compy:~/src/Alliance$ ./Start_Alliance
bash: ./Start_Alliance: Permission denied
final@Compy:~/src/Alliance$ sudo ./Start_Alliance
sudo: ./Start_Alliance: command not found


Well, try that : chmod +x alliance_start.sh
Then it will work.



But for me --> when i launch alliance_start.sh, Alliance start, but stay on splash screen. How to resolve that ?

Java 6 (edit : same with java 5)
Ubuntu 8.04

Thanks

---

### Post by Fped36 on 2008-05-22
I had to ugrade to java 6 again but once I did that and the chmod I had no Problems starting up.


Thanks prem1er & Vinx Itak :guitar:

---

### Post by mD3m4r415 on 2008-05-27
i have done all the steps you said premier... but when i run my start_allaince there is no errors but it does not launch the gui..
please help me.. 
when i downloaded the java thing it extracted the zip into the correct folder but it is still in a folder called 'jdic-20060613-bin-cross-platform'.. i have copied all the contents of that into my main folder where all the files are... please help
this is a screenshot of my folder set up :
[http://tinypic.com/view.php?pic=10eh6iu&s=3]("http://tinypic.com/view.php?pic=10eh6iu&s=3")

please help soon because my friends are waiting for me to join their network

---

### Post by mD3m4r415 on 2008-05-27
ok so i got past that other error now i have this error 
```
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

```

PLEASE

---

### Post by prem1er on 2008-05-27
Why are you using the 'cross-platform' version of jdic if you are running linux?

---

### Post by mD3m4r415 on 2008-05-27
sorry by the time of my second post i had already fixed that problem

---

### Post by prem1er on 2008-05-28
> **mD3m4r415 said:**
> ok so i got past that other error now i have this error 
```
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

```

PLEASE

Copy and paste the commands you are running before you get this message and also a copy of your 'alliance_start' script.

---

### Post by mD3m4r415 on 2008-05-29
k sry

this is what i did
```

mike@mike-laptop:~$ cd /home/mike/p2p
mike@mike-laptop:~/p2p$ sudo ./alliance_start.sh
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

```

please help... will this work in wine or something else like it?

---

### Post by prem1er on 2008-05-30
> **mD3m4r415 said:**
> k sry

this is what i did
```

mike@mike-laptop:~$ cd /home/mike/p2p
mike@mike-laptop:~/p2p$ sudo ./alliance_start.sh
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.

```

please help... will this work in wine or something else like it?

Ok, but I also asked for a copy of your bash alliance_start bash script.  And I have never tested it on wine, but you shouldn't need it.

---

### Post by mD3m4r415 on 2008-05-30
i used the exact same script as the one u posted

i just copied and pasted yours

---

### Post by stranddrew on 2008-05-31
I had that same problem actually and I just got it to work on my computer. I had all of the problems but a couple of things that I noticed that fixed things were. Alright you had to do the chmod command. Once that worked i got the splash screen to launch and then it would say that it had a fatal error. So what I had to do from there was to not only extract what was in the jdic-20060613, but also take all of its contents out of the extracted folder (for me it was called linux) and put them in the folder I made for Alliance, which I called Alliance. When I ran it then it worked. I also had to make sure that I had the right version of jdic. I tried the most updated version at first and it wouldn't work, it just hung on the splash screen but never had a fatal error. So give those a try

---

### Post by prem1er on 2008-06-04
Did these suggestions work for you?

---

### Post by peitschie on 2008-06-05
Hi guys.

Here is a tiny improvement I made to the original script.  All this does it take care of changing to the proper directory when you run alliance_start
```

#!/bin/sh
# change to the current directory first
cd "$(dirname $0)"
# then run the program
java -classpath ./linux/jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 &

```

Be warned though, this version is NOT suitable for symlinking.  It gets VERY confused if you try ;)

---

### Post by h0tz3 on 2008-06-16
I used this howto for install, but when I start Alliance via ./alliance_start I always get this error message:

Human readable error: 
Error: java.lang.Exception: Native library for system tray missing. If you are running linux you need to download it manually. Look in the forum on sourceforge for more information.

System properties: 

java.runtime.name:
Java(TM) SE Runtime Environment

sun.boot.library.path:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386

java.vm.version:
10.0-b22

java.vm.vendor:
Sun Microsystems Inc.

java.vendor.url:
[http://java.sun.com/](http://java.sun.com/)

path.separator:
:

java.vm.name:
Java HotSpot(TM) Client VM

file.encoding.pkg:
sun.io

sun.java.launcher:
SUN_STANDARD

user.country:
DE

sun.os.patch.level:
unknown

java.vm.specification.name:
Java Virtual Machine Specification

user.dir:
/home/h0tz3

java.runtime.version:
1.6.0_06-b02

java.awt.graphicsenv:
sun.awt.X11GraphicsEnvironment

alliance.network.nfriends:
0

java.endorsed.dirs:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/endorsed

os.arch:
i386

java.io.tmpdir:
/tmp

line.separator:



java.vm.specification.vendor:
Sun Microsystems Inc.

os.name:
Linux

alliance.invites:
0

sun.jnu.encoding:
UTF-8

java.library.path:
/home/h0tz3/dLs:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib

java.specification.name:
Java Platform API Specification

java.class.version:
50.0

sun.management.compiler:
HotSpot Client Compiler

os.version:
2.6.24-18-generic

alliance.share.size:
0

user.home:
/home/h0tz3

user.timezone:
Europe/Berlin

java.awt.printerjob:
sun.print.PSPrinterJob

file.encoding:
UTF-8

java.specification.version:
1.6

java.class.path:
/home/h0tz3/dLs/Alliance-v1.0.4.jar

user.name:
h0tz3

alliance.share.nfiles:
0

java.vm.specification.version:
1.0

java.home:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre

sun.arch.data.model:
32

user.language:
de

java.specification.vendor:
Sun Microsystems Inc.

java.vm.info:
mixed mode, sharing

java.version:
1.6.0_06

java.ext.dirs:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext:/usr/java/packages/lib/ext

sun.boot.class.path:
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jsse.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jce.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/charsets.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/classes

java.vendor:
Sun Microsystems Inc.

file.separator:
/

java.vendor.url.bug:
[http://java.sun.com/cgi-bin/bugreport.cgi](http://java.sun.com/cgi-bin/bugreport.cgi)

sun.io.unicode.encoding:
UnicodeLittle

sun.cpu.endian:
little

alliance.build:
671

sun.cpu.isalist:


Error stack trace: 
java.lang.Exception: Native library for system tray missing. If you are running linux you need to download it manually. Look in the forum on sourceforge for more information.
    at org.alliance.launchers.ui.TrayIconSubsystem.initTray(TrayIconSubsystem.java:130)
    at org.alliance.launchers.ui.TrayIconSubsystem.init(TrayIconSubsystem.java:47)
    at org.alliance.launchers.ui.Main.initTrayIcon(Main.java:131)
    at org.alliance.launchers.ui.Main.main(Main.java:46)


my cpu is working on 98% - javaw takes 95% ...
but there is no Alliance ...

h0tz3

---

### Post by peitschie on 2008-06-16
hotz3, see this post on the earlier pages: [http://ubuntuforums.org/showpost.php?p=4944632&postcount=7](http://ubuntuforums.org/showpost.php?p=4944632&postcount=7)

Basically, your missing a jar file that is needed for the program to start.  Follow those instructions, and you should be up and running.

---

### Post by h0tz3 on 2008-06-19
hm, I did it with this manual, but I used Alliance-v1.0.4.jar and java-6-sun-1.6.0.06 and always get the same error-message. 

h0tz3

---

### Post by peitschie on 2008-06-19
Hmm... the program output shows that you are still missing some required files.  Can you navigate to the directory you extracted Alliance to and post back the results of doing the following commands:
```
ls -l
```
and
```
cat alliance_start
```

---

### Post by h0tz3 on 2008-06-19
the output . . . 

> h0tz3@h0meb0x:~/Alliance$ cat alliance_start
#!/bin/bash
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 &h0tz3@h0meb0x:~/Alliance$
h0tz3@h0meb0x:~/Alliance$ ls -l
insgesamt 184
-rwxr-xr-x 1 h0tz3 h0tz3   123 2008-06-16 16:29 alliance_start
-rw-r--r-- 1 h0tz3 h0tz3     0 2008-06-16 16:28 alliance_start~
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:25 build
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:29 cache
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:25 com
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:25 cube
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:30 data
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:25 de
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:29 downloads
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:25 errordialog
drwxr-xr-x 3 h0tz3 h0tz3  4096 2008-06-16 16:25 junit
-rw-r--r-- 1 h0tz3 h0tz3 18349 2008-06-05 18:43 LICENSE.txt
drwxr-xr-x 4 h0tz3 h0tz3  4096 2008-06-16 16:28 linux
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:29 logs
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:25 META-INF
drwxr-xr-x 4 h0tz3 h0tz3  4096 2008-06-16 16:25 net
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:25 optiondialog
drwxr-xr-x 6 h0tz3 h0tz3  4096 2008-06-16 16:25 org
-rw-r--r-- 1 h0tz3 h0tz3   752 2008-06-05 18:43 progressbarwindow.xui.xml
-rw-r--r-- 1 h0tz3 h0tz3  1353 2008-06-05 18:43 README_IDW.txt
-rw-r--r-- 1 h0tz3 h0tz3   894 2008-06-05 18:43 README_ILF.txt
-rw-r--r-- 1 h0tz3 h0tz3  1213 2008-06-05 18:43 README_ITP.txt
drwxr-xr-x 4 h0tz3 h0tz3  4096 2008-06-16 16:25 res
-rw-r--r-- 1 h0tz3 h0tz3  4269 2008-06-05 18:43 stopwatch.png
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:25 trace
-rw-r--r-- 1 h0tz3 h0tz3 57344 2008-06-16 16:29 tray.dll
drwxr-xr-x 2 h0tz3 h0tz3  4096 2008-06-16 16:25 wizard
-rw-r--r-- 1 h0tz3 h0tz3   877 2008-06-05 18:43 XUITest.xui.xml


h0tz3

---

### Post by peitschie on 2008-06-19
You're missing the jdic.jar file.  This should have been unzipped to the Alliance directory.  Double check that you followed this step correctly:
> **prem1er said:**
> 
Next go to [https://jdic.dev.java.net/servlets/ProjectDocumentList?expandFolder=4183&folderID=5497]("https://jdic.dev.java.net/servlets/ProjectDocumentList?expandFolder=4183&folderID=5497") and download the linux version of JDIC.  Save the file and again unzip it into the directory you unzipped Alliance.


Post back where abouts you extracted the file you download please :-).  It *should* be extracted to the Alliance directory, so that you can see the jdic.jar file when you do the 'ls' command...

---

### Post by h0tz3 on 2008-06-19
i found it here:

> h0tz3@h0meb0x:~/Alliance/linux$ ls -l
insgesamt 956
-rw-r--r-- 1 h0tz3 h0tz3  14519 2006-06-15 12:05 ChangeLog
-rw-r--r-- 1 h0tz3 h0tz3  27503 2006-06-15 12:05 COPYING
-rw-r--r-- 1 h0tz3 h0tz3     59 2006-06-15 12:05 defmailer.properties
drwxr-xr-x 8 h0tz3 h0tz3   4096 2008-06-16 16:28 demo
drwxr-xr-x 4 h0tz3 h0tz3   4096 2008-06-16 16:28 javadoc
-rw-r--r-- 1 h0tz3 h0tz3  98971 2006-06-15 12:07 jdic.jar
-rw-r--r-- 1 h0tz3 h0tz3  21447 2006-06-15 12:05 libjdic.so
-rwxr-xr-x 1 h0tz3 h0tz3 476540 2006-06-15 12:05 libmozembed-linux-gtk1.2.so
-rwxr-xr-x 1 h0tz3 h0tz3 249845 2006-06-15 12:07 libmozembed-linux-gtk2.so
-rw-r--r-- 1 h0tz3 h0tz3  18501 2006-06-15 12:05 libtray.so
-rwxr-xr-x 1 h0tz3 h0tz3   9511 2006-06-15 12:05 mozembed-linux-gtk1.2
-rwxr-xr-x 1 h0tz3 h0tz3   9547 2006-06-15 12:07 mozembed-linux-gtk2
-rw-r--r-- 1 h0tz3 h0tz3   4232 2006-06-15 12:05 README.html


h0tz3

---

### Post by prem1er on 2008-06-19
> **h0tz3 said:**
> i found it here:



h0tz3

Your not following what I posted in the howto.  Both the alliance files and the jdic (desktop tray) should be in the same directory.  You have some files in the directory /Alliance and some in /Alliance/linux.  You need to move all the files to the same directory.  Follow the instructions CAREFULLY.

---

### Post by h0tz3 on 2008-06-20
ok, I moved the files to the ~/Alliance folder. It's working now, thank you.

h0tz3 :popcorn:

---

### Post by endingexodus on 2008-06-22
Hmm I am still having some problems with getting it up and going.
I have extracted the alliance .jar file to my alliance folder, extracted the contents of the linux folder contained in the JDIC zip.
I nano'd and chmodded the alliance start file which contains:
#!/bin/sh
# change to the current directory first
cd "$(dirname $0)"
# then run the program
java -classpath ./linux/jdic.jar:. -Xmx256m -Djava.library.path=. 
org.alliance.launchers.ui.Main > /dev/null 2>&1 &

And my alliance folder contains:
-rwxr-xr-x  1 exodus exodus     209 2008-06-22 19:14 alliance_start.sh
-rw-r--r--  1 exodus exodus 3582922 2008-06-22 18:53 Alliance-v1.0.4.jar
drwxr-xr-x  3 exodus exodus    4096 2008-06-22 19:03 build
-rw-r--r--  1 exodus exodus   14519 2006-06-15 04:05 ChangeLog
-rw-r--r--  1 exodus exodus     288 2008-06-05 18:43 .classpath
drwxr-xr-x  3 exodus exodus    4096 2008-06-22 19:03 com
-rw-r--r--  1 exodus exodus   27503 2006-06-15 04:05 COPYING
drwxr-xr-x  3 exodus exodus    4096 2008-06-22 19:03 cube
drwxr-xr-x  3 exodus exodus    4096 2008-06-22 19:03 de
-rw-r--r--  1 exodus exodus      59 2006-06-15 04:05 defmailer.properties
drwxr-xr-x  8 exodus exodus    4096 2008-06-22 19:04 demo
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:03 errordialog
drwxr-xr-x  4 exodus exodus    4096 2008-06-22 19:04 javadoc
-rw-r--r--  1 exodus exodus   98971 2006-06-15 04:07 jdic.jar
drwxr-xr-x  3 exodus exodus    4096 2008-06-22 19:03 junit
-rw-r--r--  1 exodus exodus   21447 2006-06-15 04:05 libjdic.so
-rwxr-xr-x  1 exodus exodus  476540 2006-06-15 04:05 libmozembed-linux-gtk1.2.so
-rwxr-xr-x  1 exodus exodus  249845 2006-06-15 04:07 libmozembed-linux-gtk2.so
-rw-r--r--  1 exodus exodus   18501 2006-06-15 04:05 libtray.so
-rw-r--r--  1 exodus exodus   18349 2008-06-05 18:43 LICENSE.txt
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:06 linux
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:06 logs
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:03 META-INF
-rwxr-xr-x  1 exodus exodus    9511 2006-06-15 04:05 mozembed-linux-gtk1.2
-rwxr-xr-x  1 exodus exodus    9547 2006-06-15 04:07 mozembed-linux-gtk2
drwxr-xr-x  4 exodus exodus    4096 2008-06-22 19:03 net
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:03 optiondialog
drwxr-xr-x  6 exodus exodus    4096 2008-06-22 19:03 org
-rw-r--r--  1 exodus exodus     752 2008-06-05 18:43 progressbarwindow.xui.xml
-rw-r--r--  1 exodus exodus     381 2008-06-05 18:43 .project
-rw-r--r--  1 exodus exodus    4232 2006-06-15 04:05 README.html
-rw-r--r--  1 exodus exodus    1353 2008-06-05 18:43 README_IDW.txt
-rw-r--r--  1 exodus exodus     894 2008-06-05 18:43 README_ILF.txt
-rw-r--r--  1 exodus exodus    1213 2008-06-05 18:43 README_ITP.txt
drwxr-xr-x  4 exodus exodus    4096 2008-06-22 19:03 res
-rw-r--r--  1 exodus exodus    4269 2008-06-05 18:43 stopwatch.png
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:03 trace
drwxr-xr-x  2 exodus exodus    4096 2008-06-22 19:03 wizard
-rw-r--r--  1 exodus exodus     877 2008-06-05 18:43 XUITest.xui.xml

And finally this is the error I am getting when I run my alliance_start script:
exodus@XD:~/alliance$ ./alliance_start.sh 
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is server, 
                  because you are running on a server-class machine.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image


Any help would be greatly appreciated, I am running ubuntu 8.04
Thanks in advance
~Endingexodus

---

### Post by endingexodus on 2008-06-23
Ok, its been a day, and I would really love some help. I hate to do this, but BUMP.

---

### Post by peitschie on 2008-06-23
Hiya :)

Sorry for the delay... I'm recouperating from exams!  The problem you are suffering is caused by the fact you are using gjc ([http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)) rather than the sun-java (i.e., fake java as oppossed to the "real"(tm) one).  At least, this is what I'm guessing due to the earlier error you posted up and then took down, note the references to gij ([http://en.wikipedia.org/wiki/GNU_Interpreter_for_Java](http://en.wikipedia.org/wiki/GNU_Interpreter_for_Java))

You can verify this by running:
```
java -version
```
On the sun java, this is something like:
```
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

``` 

You will want to do the following to fix it.
First, install the sun-java:
```
sudo aptitude install sun-java6-jre
```
Next, select the sun-java as the default jvm (information from: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)):
```
sudo update-alternatives --config java
```
Ensure you select the Sun Java (usually /usr/lib/jvm/java-6-sun/jre/bin/java) not the GCC Java compiler!

---

### Post by endingexodus on 2008-06-24
Thanks for the response, but after following your instructions, I am getting the same error.
The output of java -version:
exodus@XD:/usr/lib/jvm/java-6-sun/jre/bin$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

I may have messed something up installing the jdic deal, can you verify the contents of my alliance folder are correct?
exodus@XD:~/alliance$ ls
alliance_start.sh     junit                        org
Alliance-v1.0.4.jar   libjdic.so                   progressbarwindow.xui.xml
build                 libmozembed-linux-gtk1.2.so  README.html
ChangeLog             libmozembed-linux-gtk2.so    README_IDW.txt
com                   libtray.so                   README_ILF.txt
COPYING               LICENSE.txt                  README_ITP.txt
cube                  linux                        res
de                    logs                         stopwatch.png
defmailer.properties  META-INF                     trace
demo                  mozembed-linux-gtk1.2        wizard
errordialog           mozembed-linux-gtk2          XUITest.xui.xml
javadoc               net
jdic.jar              optiondialog

I cannot think of anything else to put, hope that helps with a solution.
Thanks again in advance.
~Endingexodus

EDIT: When I configured java it did confirm that it is sun-java:
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

---

### Post by peitschie on 2008-06-24
Wait a sec....

You have this line:
```
java -classpath ./linux/jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 &
```

Is that one line or two lines in your script?... It should be one line, but I can't tell if it is two...

---

### Post by endingexodus on 2008-06-24
Ok, good, you were correct it was 2 lines, I have made it into one. 

But now I get a loading splash screen that sits at Loading core... Version 1.0.4 671 for as long as I let it. No errors pop up, just the never ending splash screen.
I tried just typing in the command by itself, it does the same thing but produces some output:
exodus@XD:~/alliance$ java -classpath ./linux/jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main
Launching Alliance v1.0.4 build 671
Program does not seem to be running. Starting.
Exception in thread "Thread-12" java.lang.UnsatisfiedLinkError: org.jdesktop.jdic.tray.internal.impl.DisplayThread.initTray()V
	at org.jdesktop.jdic.tray.internal.impl.DisplayThread.initTray(Native Method)
	at org.jdesktop.jdic.tray.internal.impl.DisplayThread.run(Unknown Source)
Scanning /home/exodus/alliance/cache/_incomplete_...
Scanning /home/exodus/alliance/downloads/_incomplete_...
Share scan complete.
<html><b><font color=blue>Please wait while flushing file database and search index to disk...</font></b></html>
Flushed file database and search index in 2.32ms

And it seems to sit here forever, I will let it sit here for the night, and report back in the morning as to whether it decided to go after a while. But if this is an easily fixed problem feel free to throw any thoughts out there.

I feel I am so close, thank you for all your help so far, if you could just get me over this last (hopefully) problem, I would be very grateful.
~endingexodus

---

### Post by peitschie on 2008-06-24
I'll notice that your run line is not quite correct:

You need the following exactly (just copy and paste):
```
java -classpath ./jdic.jar:. -Xmx256m -Djava.library.path=. org.alliance.launchers.ui.Main > /dev/null 2>&1 &
```

Major difference is "-classpath ./linux/jdic.jar" should is "-classpath ./jdic.jar"

See if that makes a difference :)

---

### Post by endingexodus on 2008-06-24
That was it, perfect! I don't know how that got messed up as I just copy/pasted the command each time, but hey its fixed, Thank you so much. Have a great day.

---

### Post by peitschie on 2008-06-24
Glad to hear it all works :-)

---

### Post by ipx on 2008-07-26
...

---

### Post by prem1er on 2008-07-26
> **ipx said:**
> ...

????

---

### Post by fatbastard spice on 2008-10-03
Well if you'd been turned off by the tray icon hoops you had to jump through to get this running previously, the latest version (1.0.5) has fixed that problem. 

From the changelog:

> 
2) Much better Linux support - added support for the Java 6 system tray - no more need for native libraries to run Alliance on Linux (thanks Kratos) 
 
3) Alliance is now allowed to start if system tray is not supported (thanks Kratos) 
 
4) Generally better management of the system tray on various operating systems 
 


[linky to annoucement thread]("http://sourceforge.net/forum/forum.php?thread_id=2272214&forum_id=568436")

Just grabbed a copy and on my hardy 64 bit system all it needed to run was a simple 'java -jar Alliance_v1.0.5.jar' command.

---

### Post by prem1er on 2008-10-08
> **fatbastard spice said:**
> Well if you'd been turned off by the tray icon hoops you had to jump through to get this running previously, the latest version (1.0.5) has fixed that problem. 

From the changelog:



[linky to annoucement thread]("http://sourceforge.net/forum/forum.php?thread_id=2272214&forum_id=568436")

Just grabbed a copy and on my hardy 64 bit system all it needed to run was a simple 'java -jar Alliance_v1.0.5.jar' command.

Thanks man.  I'll post back and let everyone know how it runs on a headless server for those that are interested.

---

### Post by DeathfireD on 2009-05-03
Sorry for reviving a dead topic but I figured it would be good to point out that Alliance has been updated several times this past month to address a lot of the Alliance bugs people where having. A "groups" or "Networks" feature was also implemented to allow people to set permissions on folders and let specific groups access them.

You can pick up the jar file or source for Beta 4 here [https://sourceforge.net/forum/forum.php?thread_id=3251655&forum_id=568436](https://sourceforge.net/forum/forum.php?thread_id=3251655&forum_id=568436)

There's also Beta 4.1 but right now we only offer a windows binary. If your still interested in it you can check it out here [https://sourceforge.net/forum/forum.php?thread_id=3256696&forum_id=568436](https://sourceforge.net/forum/forum.php?thread_id=3256696&forum_id=568436)

---

