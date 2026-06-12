---
title: "Add a title to a process started from terminal"
date: 2013-10-31
forum: General Help
---

### Post by setprem on 2013-10-31
Hi,
 This is my first post. I m not sure whether this is the right place to ask this question. 

Is there any way to set a title/description to a process started from terminal.?? i am running three different programs. using ps aux i can get the details of process ids. but if i want to stop a particular program using a script, how can i know the respective process id. If i can set a title/description, i can take that value and find the respective process id and then kill it. Kindly suggest any other good methods to handle such a requirement.

Note: currently ps aux displaying the details of all three programs in same way. no attributes i could find to distinguish between them. 

Thanks in advance
Prem

---

### Post by steeldriver on 2013-10-31
Hello and welcome to the forums

I don't know the *right* way to do this, but if nobody offers a better solution you could consider wrapping your command in a minimal script and adding a "dummy parameter". Then you could grep for (and kill) the parent script. If your command takes no arguments, then it could be as simple as

```

#!/bin/sh
*yourcommand*

```

Then for example
```

$ ./mycommand.sh foo &
[3] 32355
$ ./mycommand.sh bar &
[4] 32358
$ ps aux | grep '[m]ycommand.sh'
steeldriver  32355  0.0  0.0   2236   544 pts/0    S    07:42   0:00 /bin/sh ./mycommand.sh foo
steeldriver  32358  0.0  0.0   2236   544 pts/0    S    07:42   0:00 /bin/sh ./mycommand.sh bar
$ 

```

If you need to pass arguments, you would need to strip off the "dummy", something like

```

#!/bin/sh

if [ $# -gt 1 ]; then
  shift 1
fi

*yourcommand* $@

exit

```

then you can do something like (I'm illustrating it here using the 'xeyes' command)
```

$ ./xeyes.sh foo -geometry 200x100 -center 'blue' &
[1] 32380
$ ./xeyes.sh bar -geometry 200x100 -center 'blue' &
[2] 32382
$ ps aux | grep '[x]eyes.sh'
steeldriver  32380  0.0  0.0   2236   548 pts/0    S    07:45   0:00 /bin/sh ./xeyes.sh foo -geometry 200x100 -center blue
steeldriver  32382  0.0  0.0   2236   544 pts/0    S    07:45   0:00 /bin/sh ./xeyes.sh bar -geometry 200x100 -center blue
$ 
$ pgrep -f 'xeyes.sh foo'
32380

```

---

### Post by btindie on 2013-10-31
It is possible to do as I've seen it in my ps listing, e.g. "udisks-daemon: not polling any devices"

But I don't think it's possible to modify it directly from a shell script. The easiest way to achieve the same result would simply be to create a symlink to your original script.

You can then use
```
pkill -HUP -x bar1.sh
```
to kill it.

---

### Post by setprem on 2013-11-01
Thanks a lot for the replies.
I tried the suggested methods. But my scenario seems little more complicated. i created a run.sh. Funny thing is after running when i did ps aux | grep run.sh it was showing no processes. i am listing the output below.

run.sh
#/bin/bash
mvn clean compile camel:run

i ran ./run.sh foo & ,  ./run.sh foo1 &,  ./run.sh foo2 &
ps aux | grep run.sh
ourput : 
prem      5050  0.0  0.0  13588   940 pts/1    S+   13:51   0:00 grep --color=auto run.sh

then i checked actually the processes are running, ps aux | grep camel
output:
prem      5506 24.6  2.8 4463552 221124 pts/1  Sl   13:54   0:16 /usr/lib/jvm/java-7-openjdk-amd64/bin/java -classpath /usr/share/maven/boot/plexus-classworlds-2.x.jar -Dclassworlds.conf=/usr/share/maven/bin/m2.conf -Dmaven.home=/usr/share/maven org.codehaus.plexus.classworlds.launcher.Launcher clean compile camel:run
prem      5538 24.8  3.3 4463552 266116 pts/1  Sl   13:54   0:16 /usr/lib/jvm/java-7-openjdk-amd64/bin/java -classpath /usr/share/maven/boot/plexus-classworlds-2.x.jar -Dclassworlds.conf=/usr/share/maven/bin/m2.conf -Dmaven.home=/usr/share/maven org.codehaus.plexus.classworlds.launcher.Launcher clean compile camel:run
prem      5673  107  3.7 4462524 292596 pts/1  Sl   13:55   0:13 /usr/lib/jvm/java-7-openjdk-amd64/bin/java -classpath /usr/share/maven/boot/plexus-classworlds-2.x.jar -Dclassworlds.conf=/usr/share/maven/bin/m2.conf -Dmaven.home=/usr/share/maven org.codehaus.plexus.classworlds.launcher.Launcher clean compile camel:run
prem      5733  0.0  0.0  13588   928 pts/1    S+   13:56   0:00 grep --color=auto camel

means the processes are actually running. 
i think the maven project gets detached from its parent script process. i dont know exactly, just my guess. It seems running the command from script may not be a solution for his case.
Also my actual requirement is some more complicated. Here i ran 3 instances of same program. Actually i will run 3 different programs. same command "mvn clean compile camel:run". Output of ps aux will be same as above, since internally all the three programs first triggers camel classes.

I am still stuck :) 

Thanks & Regards
Prem

---

### Post by setprem on 2013-11-13
Finally i got a solution. It is a solution for my scenario. We can set a profile name to a maven project as follows.
mvn clean compile camel:run -P myProjectName

so when we do ps aux | grep camel, this profile name also will be listed. 

Thanks for your support :)

---

