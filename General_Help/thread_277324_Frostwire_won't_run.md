---
title: "Frostwire won't run"
date: 2006-10-14
forum: General Help
---

### Post by BlueStreak on 2006-10-14
I installed Frostwire via automatix but can't get it to run.  It shows up in the Applications menu but when i click it nothing happens.  Same when I use Alt F2, I type the first few letters and it appears but click run and nothing happens.I tried "ps -e" from a terminal and found no instances of frostwire running.  What else should I try?  Thanks

---

### Post by Cable on 2006-10-14
My first suggestion would be to open a terminal and type
```

frostwire

```
That way you can see any erros that are thrown when it tries starting Frostwire.  If it throws errors, copy and paste them here and we can help you from there.

---

### Post by BlueStreak on 2006-10-14
Ok, thanks, this is what I got:



mike@mike-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by taurus on 2006-10-14
You need to install java before you can run frostwire.  You can use Automatix to install java as well...

---

### Post by BlueStreak on 2006-10-14
I think I have java installed.  I went to java.com and clicked the verify installation button, it said I have the latest version

---

### Post by Cable on 2006-10-14
Make sure you have the multiverse repository enabled in Synaptic, then install the "sun-java5-bin" package.  I believe that's all you need to run Frostwire.

OR

You can open Automatix back up and use that to install Java, which may be the easier route (it's called SUN JAVA5 JRE in Automatix).  Either way, it'll get the correct Java installed.

---

### Post by BlueStreak on 2006-10-14
Thanks a TON!  Works now :)

---

