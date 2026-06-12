---
title: "I need help to install this program"
date: 2007-04-06
forum: General Help
---

### Post by Eduardo Serra on 2007-04-06
Im trying to install 360 mediaserve and this are the instructions:

```
Linux



install lame,faad,flac and sox where they will be found by a bash script

run start


```

I already installed the four of those using synaptic, and when i click the "start" file they tell me to run, it opens a text file that contains this:

```
#!/bin/bash
java -cp x360mediaserve.jar:lib/cyberlink/clink170.jar:lib/cyberlink/cmgatejava120.jar:lib/jetty/commons-logging.jar:lib/entagged/entagged-audioformats-0.15.jar:lib/jetty/javax.servlet.jar:lib/jetty/org.mortbay.jetty.jar:lib/xerces/xercesImpl.jar:lib/xerces/xml-apis.jar Run $1
```

What should i do with that? i already tried copying that in the terminal, but it will tell this:

```
Exception in thread "main" java.lang.NoClassDefFoundError: Run

```

and if i put all except the "run", it says this:

```
eduardo@eduardo-desktop:~$ java -cp x360mediaserve.jar:lib/cyberlink/clink170.jar:lib/cyberlink/cmgatejava120.jar:lib/jetty/commons-logging.jar:lib/entagged/entagged-audioformats-0.15.jar:lib/jetty/javax.servlet.jar:lib/jetty/org.mortbay.jetty.jar:lib/xerces/xercesImpl.jar:lib/xerces/xml-apis.jar
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image

```

What am i supposed to do with the start file?

---

### Post by Eduardo Serra on 2007-04-06
bump

---

### Post by spankymasterc on 2007-04-06
i could help if u give me link to where u got this 360 media serve...... i could try to do it on my box and tell u how :D

---

### Post by Eduardo Serra on 2007-04-06
Thanks a lot really, its a very small download, heres the link: [http://sourceforge.net/project/showfiles.php?group_id=159861&package_id=179653&release_id=430485]("http://sourceforge.net/project/showfiles.php?group_id=159861&package_id=179653&release_id=430485")

---

### Post by spankymasterc on 2007-04-06
Dis this....

---

### Post by Eduardo Serra on 2007-04-07
all right, i did exactly the same, but after i type sudo run, nothing happens: 

```
eduardo@eduardo-desktop:~$ cd Desktop
eduardo@eduardo-desktop:~/Desktop$ cd x360mediaserve-0.0.1
eduardo@eduardo-desktop:~/Desktop/x360mediaserve-0.0.1$ 
eduardo@eduardo-desktop:~/Desktop/x360mediaserve-0.0.1$ sudo start
Password:
eduardo@eduardo-desktop:~/Desktop/x360mediaserve-0.0.1$
```

---

### Post by spankymasterc on 2007-04-07
hey wait i got it for you sorry here we go lol i got it now i forgot some steps :D

ok 

Step 1. Download it Extract it to desktop
Step2. Open terminal type 
> 
cd Desktop
Step 3. Type

> cd x360mediaserve-0.0.1

Step 4. open the file on desktop and rename the start to start.sh

step5. make the start.sh runnable by doing this 

> chmod a+x ./start.sh

step6. Run start.sh by doing this 
> 
sudo ./start.sh 

and your done :D

sorry bout that :D

one more thing when u do that its gonna stay in one step go here

[http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure)

and configure it ::cheers:: if you ever need help hit me up on msn :D [email]spankymasterc@hotmail.com[/email]

---

### Post by Eduardo Serra on 2007-04-07
Oh thanks! that did it. I didn't understand what i did, i really want to learn so i don't have to ask every time i get a problem, would you care to explain me ?

---

### Post by spankymasterc on 2007-04-07
lol well all that did was make it in to a .sh file then u made it a runnable to it would run on ubuntu diff linux use diff, then u ran the script :D

---

