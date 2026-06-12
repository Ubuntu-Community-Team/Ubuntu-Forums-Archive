---
title: "Another java install question ..."
date: 2005-10-10
forum: General Help
---

### Post by dbee on 2005-10-10
I know that everyone is probably saying to themselves ... not another java install question. But anyway here goes...

I downloaded and installed jre1.5 as per instructions, and it seems to be working which is cool. But when I try to run the azureus script it tells me that it needs jre1.5 and my version is too low.

When I hit 

java --version

it tells me that I'm on SableVM 1.1.8, when I check my path, I get these java bins in it's view 

java 
javac
javadoc
javah
java-cp
javap
javasablevm
javawm

all in the same folder ... so what do you think the problem might be here ???

cheers

---

### Post by Zelut on 2005-10-10
From what I understand Azureus needs the JDK installation.. the development kit.  Not sure why but download & install that one and see if that helps.

---

### Post by sanjose on 2005-10-10
if you have installed sun jre correctly you can try this

**sudo update-alternatives --config java**

this will give you a list of installed java you should choose the appropriate
java you wish to be the default one.

> There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

in my case i have 3. i choose **3** then hit enter.


then try **java --version** again see what version it is now.

---

