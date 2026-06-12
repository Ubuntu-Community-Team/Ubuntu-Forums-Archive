---
title: "Mercury Native library files for Linux found: Failed"
date: 2007-03-30
forum: General Help
---

### Post by alek66 on 2007-03-30
I am trying to get my webcam to work under mercury msn
I downloaded everything but I still get  a Native library files for Linux found: Failed 
Dont know how to fix it... and the wiki does not explain tu much on how to configure this.

---

### Post by muratbaba on 2007-04-01
Hey,

I am having the same problem. On the wiki page of mercury, it says: 
[INDENT][/INDENT]"If you installed Mercury with the 1.8 setup, it should allready have [INDENT][/INDENT]the correct library path and you don't need to change anything.".

And my startup_linux.sh confirms that: 
[INDENT][/INDENT]"java -Djava.library.path=jni/linux:jni/linux/jmf -classpath $classpath [INDENT][/INDENT]com.dMSN.Main"

I spent hours to find a solution but couldnt. Is there anyone that can help? Thanks in advance.

P.S: I wish wiki page of mercury could be more explanatory for new people who doesnt know anything.

---

### Post by muratbaba on 2007-04-02
Hi,

Special thanks to the guys at mercury forum, I got the solution now:

Check the file types in jni/linux/jmf, and you will se that they are all dll files. These are the JMF files for WindowsSo we made the same mistake by installing library files for windows but not linux. 

You must get the NativeLibs-linux.zip and extract the *.so files inside '%programdir%/jni/linux/jmf' .
You can retrieve detailed info from: [http://www.mercury.to/index.php?page=Wiki&wikipage=InstallingJMF](http://www.mercury.to/index.php?page=Wiki&wikipage=InstallingJMF)

and this is replies to my forum query: 
[http://forum.mercury.to/index.php?showtopic=16225](http://forum.mercury.to/index.php?showtopic=16225)
good luck

---

### Post by alek66 on 2007-04-03
thanks a lot!!!

---

### Post by alek66 on 2007-04-03
I could install the libraries but this appear in the wizzard "Looking for video capture devices...
- Finished detecting V4LAuto classes.
Starting detected classes... (This might take some time)
- Done.
  
There are no video capture devices present."

and i have 2 webcams connected.

---

### Post by deepesh on 2007-04-06
Did you find a solution to this? I am facing the same problem. My webcam is properly detected by gnomemeeting and camorama webcam viewer.
Deepesh

---

### Post by alek66 on 2007-04-06
nope....:(

---

