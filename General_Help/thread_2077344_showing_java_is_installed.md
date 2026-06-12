---
title: "showing java is installed"
date: 2012-10-28
forum: General Help
---

### Post by jdzimme on 2012-10-28
I followed the wikihow 18 steps and installed Oracle Java 7 JKE and JRE.  I verified it is right in FireFox and did the Java -version command in a terminal window. All is OK. However the software center does not show it installed. How do I solve this? My next question is how do I use/start/run the JDK to write Java applicaitons?  I am running Ubuntu 11.10.
I did multiple searches on the forum and the only thing I could find was all the steps which I have already completed to install. Then test the install. But nothing to answer my two question. I am a novice users so make answer complete and as simple as possible.

thanks in advance

Jerry

---

### Post by roudy1989 on 2012-10-28
The Ubuntu Software Center only show packages installed via the Package Manager. Since you managed to install the Oracle JDK manually it is not tracked by the Software Manager. 

To begin writing Java applications just open an editor of you favour. For example you couldt use Gedit.
Write any Java Code you want. The file name is the classname.java. Thats a requirement of Java. Now run the Terminal (Ctrl+Alt+T) and cd into the folder where you saved the file. Now type ```
javac classname.java
``` in the terminal and submit. Make sure your class contains a main() method.

Good luck!

---

