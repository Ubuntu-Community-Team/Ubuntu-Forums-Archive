---
title: "unable to install .jar files"
date: 2007-09-25
forum: General Help
---

### Post by flats on 2007-09-25
hey everyone... im getting another weird error when trying to install .jar files... i get the error

"Failed to load Main-Class manifest attribute from file.jar"

any help? im not sure but i do not think i have java installed either and no idea exactly what file i should get. (i had ubuntu installed before but that was a long time ago).

---

### Post by Maestro23 on 2007-09-25
If you have the JDK installed, you can use the jar command.  It's available thru Synaptic.

sun-java6

Also, from Sun's Java site: [http://java.sun.com/docs/books/tutorial/deployment/jar/basicsindex.html](http://java.sun.com/docs/books/tutorial/deployment/jar/basicsindex.html)

---

### Post by flats on 2007-09-25
hmm couldnt find it in synapatic (using fiesty) i checked the site and read something about setting a application entry point but i dont understand...

---

### Post by flats on 2007-09-25
just downloaded java.. and some reason when i try to install the .bin file as well it wont do anything. i type in "chmod +x java_ee_sdk-5_03-linux.bin" and nothing happens.

---

### Post by Maestro23 on 2007-09-25
> **flats said:**
> hmm couldnt find it in synapatic (using fiesty) i checked the site and read something about setting a application entry point but i dont understand...

JDK is there.  Do you have all your repos enabled?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

*Installing .bin files: [http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/](http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/)

> chmod + x filename.bin

./filename.bin

---

### Post by flats on 2007-09-25
ah thanks...  forgot to do the ./file.bin after you locate it. got java installed..

the link to the extra repositories is for dapper. things are alot different in fiesty. how can i add them in fiesty?

---

### Post by Maestro23 on 2007-09-25
> **flats said:**
> ah thanks...  forgot to do the ./file.bin after you locate it. got java installed..

the link to the extra repositories is for dapper. things are alot different in fiesty. how can i add them in fiesty?

Same procedure.  Sorry, forgot that was for Dapper.  Just got done linking that for a dapper person. :smile:

*Just make sure your universe/multiverse are enabled.

---

### Post by flats on 2007-09-25
well still some reason my file is still not letting me install.. same error!

"Failed to load Main-Class manifest attribute from file.jar"

---

### Post by flats on 2007-09-26
ok, i fixed that problem but now got a bigger one :(. when i try to install the .jar file now it says "unable to access file.jar" i tried "sudo java -jar file.jar" and simply trying su username. still wont let me access the file :(

---

### Post by Maestro23 on 2007-09-26
> **flats said:**
> ok, i fixed that problem but now got a bigger one :(. when i try to install the .jar file now it says "unable to access file.jar" i tried "sudo java -jar file.jar" and simply trying su username. still wont let me access the file :(

Look at the man page for the jar command.

> man jar

Gives you the syntax.

Try jar xv ...

*Make sure you are in the directory of where the file is located.

---

### Post by flats on 2007-09-26
i dont understand what you mean.. but i am in the correct location.

---

### Post by Maestro23 on 2007-09-26
> **flats said:**
> i dont understand what you mean.. but i am in the correct location.

Did you try the jar command on the file.  It's just like the examples I linked you to earlier at the java site. A lot of good info over there.

As for man pages.  Those are manual pages stored on your system for linux commands.  Accessed by typing "man" in terminal and then the command.

---

