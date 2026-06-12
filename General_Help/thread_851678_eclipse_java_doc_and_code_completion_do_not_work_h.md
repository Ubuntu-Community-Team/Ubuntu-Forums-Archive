---
title: "eclipse java doc and code completion do not work help!"
date: 2008-07-06
forum: General Help
---

### Post by efplaya on 2008-07-06
Hi i have been trying to figure out why neither the java doc or code completion work on eclipse, i have installed both the jdk 6.0 doc and the jdk src from synaptic and still no luck any one have any pointers that could help me out?

---

### Post by efplaya on 2008-07-07
bump

---

### Post by jespdj on 2008-07-07
In Eclipse, go to Window / Preferences / Java / Installed JREs.

Click on the installed JRE and click Edit...

Select rt.jar from the list and click Javadoc Location...; make sure this is set correctly (either to Sun's website or a directory on your machine that contains the Javadoc documentation).

Then click Source Attachment... and make sure it points to the file **src.zip** which is included with the JDK. This file should be in the following location:

/usr/lib/jvm/java-6-sun-1.6.0.06/src.zip

If you don't have it, make sure you install the package sun-java6-source.

(Note: I've assumed you're using Hardy and the latest version of Sun Java).

---

### Post by efplaya on 2008-07-07
Thank you for your advice, i have just did that and that fixed the problem with the java doc showing up but code completion still does not work, do you have any idea on what the problem is?

---

### Post by efplaya on 2008-07-07
nevermind.. i figured it out. All i had to do was just start a new project and indlude all the jvm files

---

### Post by pablosanchezuy on 2008-07-07
any idea getting java doc with openjdk ?

Regards .

Pablo .

---

### Post by pablosanchezuy on 2008-07-07
ok, i figured out. Installed openjdk-6-doc, then pointed as you noted the docs to file:/usr/share/doc/openjdk-6-doc/api/ .

many thanks for the tip.

Pablo .

---

### Post by brijesht on 2009-01-05
I am facing same problem with code completion. I have all default JVM files included in it. Can you please send me list of files you included to resolve this issue? 

Thanks for your help.

Brijesh

---

