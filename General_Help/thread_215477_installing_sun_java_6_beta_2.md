---
title: "installing sun java 6 beta 2"
date: 2006-07-14
forum: General Help
---

### Post by nismohasan on 2006-07-14
how would i go about installing the latest beta from sun onto my ubuntu dapper system?

---

### Post by slimdog360 on 2006-07-14
try [here]("http://www.ubuntuforums.org/showthread.php?p=1158769")

---

### Post by nismohasan on 2006-07-14
yeh that was no help at all lol

---

### Post by slimdog360 on 2006-07-14
did you download the .bin file then type
```
sh jdk-6-beta2-linux-i586.bin
```

If you did, and making sure you had the directory right, can you post up a link of where to download it and I'll give it a go

---

### Post by nismohasan on 2006-07-14
i should of made it clear that im after the jre not jdk but anyway yeh i downloaded it from the java site, typed sh filename.bin it extracted it to a folder on the desktop, then what was meant to happen exactly? couldn't find any futher instructions in the readme..

[http://java.sun.com/javase/downloads/ea.jsp](http://java.sun.com/javase/downloads/ea.jsp)

---

### Post by Bokonon on 2006-07-14
Hmm, before it was in the repositories, I installed the sun packages by using [this thread]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+package").

I assume it would still work fine for Java6, just change the appropriate sections.  8)

---

### Post by nismohasan on 2006-07-14
blah double post delete this

---

### Post by nismohasan on 2006-07-14
> **Bokonon said:**
> Hmm, before it was in the repositories, I installed the sun packages by using [this thread]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+package").

I assume it would still work fine for Java6, just change the appropriate sections.  8)

i tried to use fakeroot like described in that thread

got this error:

> 
hasan@&&:~/Desktop$ fakeroot make-jpkg jre-6-beta2-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found


---

### Post by Bokonon on 2006-07-14
You installed the packages as per the first line of the code section?

If I install fakeroot, but not the others, I get the same error as you.  With all the packages/dependancies, I do not.

---

### Post by nismohasan on 2006-07-14
> **Bokonon said:**
> You installed the packages as per the first line of the code section?

If I install fakeroot, but not the others, I get the same error as you.  With all the packages/dependancies, I do not.

there already installed

---

### Post by slimdog360 on 2006-07-14
I don't know what you done but when I followed the instructions on the page everything went fine. 
I changed the permissions,
then extracted it to the folder that I wanted.
done

---

### Post by nismohasan on 2006-07-14
> **slimdog360 said:**
> I don't know what you done but when I followed the instructions on the page everything went fine. 
I changed the permissions,
then extracted it to the folder that I wanted.
done

well it didnt work here lol ](*,)

---

### Post by slimdog360 on 2006-07-14
Okay sorry I must have misread one of your earlier posts. You said you extraccted it to the desktop, well thats basically it. thats whats meant to happen.

edit: you just had to extract the folder to where you wanted to install it. If you then wanted to use the plugin for firefox or whatever there is a file in that folder which you have to link to the mozilla plugins folder. Its all on the website.

link to install instructions [here]("http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html")

link to installing of firefox plugin [here]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")

---

