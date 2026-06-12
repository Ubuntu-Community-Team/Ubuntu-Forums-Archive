---
title: "How to make minecraft.jar executble sh file?"
date: 2013-08-31
forum: General Help
---

### Post by billysanders197 on 2013-08-31
Im new to minecraft on ubuntu and I don't know how to make minecraft run java jdk 6 when I double click it. Could I please get some help with making a .sh file to run it automtically through jdk6? 
Thanks

---

### Post by zero2xiii on 2013-09-01
Hay,

I'm guessing:
```
#!/bin/sh
java ./minecraft.jar
exit
```

Drop the file in the same folder as the *.jar file and make executable and run that. Although it seems overly complicated, cause you should be able to simply double click the jar file and it should launch. If it opens in archive manager simply right click and choose the java option.

Cheers

---

### Post by billysanders197 on 2013-09-01
> **zero2xiii said:**
> Hay,

I'm guessing:
```
#!/bin/sh
java ./minecraft.jar
exit
```

Drop the file in the same folder as the *.jar file and make executable and run that. Although it seems overly complicated, cause you should be able to simply double click the jar file and it should launch. If it opens in archive manager simply right click and choose the java option.

CheersThanks for the reply. I did what you said and nothing opened. I have javaJDK 6 and 7. When ever i want to run the jar i have to right click and open with java6. Is there a way to make the .sh file to make it to were it will open with java6?

---

### Post by steeldriver on 2013-09-01
If you want to make java-6 the default system wide, that should be possible using update-alternatives

```
sudo update-alternatives --config java
```

(note: this may break other things, if they rely on java-7). Otherwise, you may need to find where the binary is installed and call it explicitly e.g. on my 32-bit 12.04 system

```
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
```

Either way, you will probably need the **-jar** option

```

#!/bin/sh
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/java **-jar** ./minecraft.jar
exit

```

You will need to make the script executable

```
chmod +x *myscript*
```

Hope this helps

---

### Post by billysanders197 on 2013-09-02
Thanks for the reply but all it dose is open a terminal window and close real fast. any suggestions?

---

### Post by zero2xiii on 2013-09-02
> Thanks for the reply but all it dose is open a terminal window and close real fast. any suggestions?

Yea, run it in a terminal and see what errors are provided.

Also remember that "./minecraft.jar" should be renamed to the file you need to run (the full filename, correct capitalization etc) otherwise it will give a "file not found" error and exit.


Cheers

---

### Post by billysanders197 on 2013-09-04
Thanks again, but all it dose is quickly open and close the terminal, and no minecraft pops up

---

