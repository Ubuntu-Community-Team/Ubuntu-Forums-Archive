---
title: "installation problem, code=2"
date: 2006-08-12
forum: General Help
---

### Post by satimis on 2006-08-12
Hi folks,

Ubuntu-6.06-amd64

I need to install "jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin" and have it download to /path/to/folder

$ cd /path/to/folder
$ sudo ./jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin```

Extracting 0%..................................................................................................../tmp//fileKNCXni/linux_x86_64_jrockit150_06_sdk.zip  bad CRC 46156a89  (should be 25642528)
100%
** Error during extraction, error code = 2.
```
Please advise how to fix the problem.  What is "code = 2"

TIA

B.R.
satimis

---

### Post by vijirajan on 2006-08-12
It looks like the downloaded file is corrupt. If you look at end of the "Extracting 0%..." line there is a Bad CRC error. This usually happens if the zip file is corrupt.

I would try dowloading it again.

Hope this helps!

-Rajan

---

### Post by satimis on 2006-08-13
Hi Rajan,

Tks for your advice.

Problem solved.

Download "jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin" again.

$ sudo chmod +x -c JBoss_package/jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin
Password:```

mode of `JBoss_package/jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin'
changed to 0755 (rwxr-xr-x)
```

$ cd JBoss_package/
$ sudo ./jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin```

Extracting
0%....................................................................................................100%

Done.
```

After agreed licence terms, "jrockit-R26.4.0-jdk1.5.0_06" started and closed down automatically afterwards.

$ which jrockit
$ sudo which jrockit

Can't find its execute.  Please advise how to start it.  TIA

B.R.
satimis

---

### Post by vijirajan on 2006-08-13
Usually these types of installers extract the contents to the current directory. Are you sure "jrockit" is the name of the executable?

Do a ```
find . -name "jrock*"
``` in the directory where you executed the .bin file and see if it shows up. Also, I downloaded the 32-bit version of the JRockIt installer and it popped up a wizard when I ran it, I am not sure if the 64-bit version also supposed to show a wizard or not. If it is then the installer might have failed some how.

Hope this helps!

---

### Post by satimis on 2006-08-13
Hi Rajan,

When I ran the installer "jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin", it popup a wizard.  Then it continued asking to confirm accepting the terms on the licence.  After finish acceptance the wizard closed.

I don't know whether I can start this package alone.  Neither I know its execute.

$ find . -name "jrock*"```

./JBoss_package/jrockit-R26.4.0-jre1.5.0_06-linux-x64.bin
./JBoss_package/jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin
./JBoss_package/jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin_old
./JBoss_package/jrockit-R26.4.0-jdk1.5.0_06-linux-x64.bin_old1
./jboss-4.0.4.GA-src/thirdparty/jboss/aop/lib/jrockit-pluggable-instrumentor.jar
./jrockit-R26.4.0-jdk1.5.0_06
./jrockit-R26.4.0-jdk1.5.0_06/jre/lib/amd64/jrockit
```

I'm sure the package has been installed on;

$ ls /home/satimis/jrockit-R26.4.0-jdk1.5.0_06/```

bin  console  demo  include  jra  jre  lib  LICENSE  memleak  mercuryprofiler  README.TXT  sample  src.zip
```

$ ls /home/satimis/jrockit-R26.4.0-jdk1.5.0_06/bin/```

appletviewer  idlj       javac    jconsole  jrcc    keytool  memleak       policytool   serialver
apt           jar        javadoc  jdb       jrcmd   kinit    native2ascii  rmic         servertool
console       jarsigner  javah    jps       jstat   klist    orbd          rmid         tnameserv
extcheck      java       javap    jra       jstatd  ktab     pack200       rmiregistry  unpack200
```

B.R.
satimis

---

### Post by vijirajan on 2006-08-13
Can you tell me what exactly you are trying to do with JRockIt? Are you trying to execute a Java program with JRockIt? If so, you would use the command **java** not jrockit.

---

### Post by satimis on 2006-08-13
Hi vijirajan,

> Can you tell me what exactly you are trying to do with JRockIt?

I'm prepared testing JBoss, the Business Intelligence.  JBoss needs jdk to run.  A folk recommended me installing this package developed by BEA saying that it works better than Java's package.

B.R.
satimis

---

### Post by vijirajan on 2006-08-13
OK that makes sense. Now all you have to do is configure JBoss Business Intelligence to use this jdk. I haven't worked with that software before, so I don't know where you would configure that. Please refer to the software documentations.

One thing that I can suggest is that, you can add this JDK installation to the path so that everytime somebody runs the command **java** it will run the JRockIt.

---

