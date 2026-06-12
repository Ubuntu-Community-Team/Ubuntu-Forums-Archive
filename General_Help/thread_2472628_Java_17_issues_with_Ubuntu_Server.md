---
title: "Java 17 issues with Ubuntu Server"
date: 2022-03-06
forum: General Help
---

### Post by alexrocks on 2022-03-06
Hello,


Recently I have been getting into virtual machining, testing out various things. I play Minecraft and decided that I wanted to spin up a server using QEMU on my arch install.


I chose the Ubuntu Server LTS 20.04 version to host the MC server in.


After installing, I downloaded the "openjdk-17-jdk" package which is all that I would need, and the Minecraft jar file. I created a directory and used wget to get the jar file. Then, I ran the command "java -Xmx4096M -Xms1024M -jar server.jar nogui"


I have run servers before, and when I ran it previously, the server simply started up. But on this VM, it does not. Here is what I get after typing in that command.


```
"
Unpacking 1.18.2/server-1.18.2.jar (versions:1.18.2) to versions/1.18.2/server-1.18.2.jar
Unpacking com/github/oshi/oshi-core/5.8.5/oshi-core-5.8.5.jar (libraries:com.github.oshi:oshi-core:5.8.5) to libraries/com/github/oshi/oshi-core/5.8.5/oshi-core-5.8.5.jar
Unpacking com/google/code/gson/gson/2.8.9/gson-2.8.9.jar (libraries:com.google.code.gson:gson:2.8.9) to libraries/com/google/code/gson/gson/2.8.9/gson-2.8.9.jar
Unpacking com/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.jar (libraries:com.google.guava:failureaccess:1.0.1) to libraries/com/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.jar
Unpacking com/google/guava/guava/31.0.1-jre/guava-31.0.1-jre.jar (libraries:com.google.guava:guava:31.0.1-jre) to libraries/com/google/guava/guava/31.0.1-jre/guava-31.0.1-jre.jar
Unpacking com/mojang/authlib/3.3.39/authlib-3.3.39.jar (libraries:com.mojang:authlib:3.3.39) to libraries/com/mojang/authlib/3.3.39/authlib-3.3.39.jar
Unpacking com/mojang/brigadier/1.0.18/brigadier-1.0.18.jar (libraries:com.mojang:brigadier:1.0.18) to libraries/com/mojang/brigadier/1.0.18/brigadier-1.0.18.jar
Unpacking com/mojang/datafixerupper/4.1.27/datafixerupper-4.1.27.jar (libraries:com.mojang:datafixerupper:4.1.27) to libraries/com/mojang/datafixerupper/4.1.27/datafixerupper-4.1.27.jar
Unpacking com/mojang/javabridge/1.2.24/javabridge-1.2.24.jar (libraries:com.mojang:javabridge:1.2.24) to libraries/com/mojang/javabridge/1.2.24/javabridge-1.2.24.jar
Unpacking com/mojang/logging/1.0.0/logging-1.0.0.jar (libraries:com.mojang:logging:1.0.0) to libraries/com/mojang/logging/1.0.0/logging-1.0.0.jar
Unpacking commons-io/commons-io/2.11.0/commons-io-2.11.0.jar (libraries:commons-io:commons-io:2.11.0) to libraries/commons-io/commons-io/2.11.0/commons-io-2.11.0.jar
Unpacking io/netty/netty-all/4.1.68.Final/netty-all-4.1.68.Final.jar (libraries:io.netty:netty-all:4.1.68.Final) to libraries/io/netty/netty-all/4.1.68.Final/netty-all-4.1.68.Final.jar
Unpacking it/unimi/dsi/fastutil/8.5.6/fastutil-8.5.6.jar (libraries:it.unimi.dsi:fastutil:8.5.6) to libraries/it/unimi/dsi/fastutil/8.5.6/fastutil-8.5.6.jar
Unpacking net/java/dev/jna/jna/5.10.0/jna-5.10.0.jar (libraries:net.java.dev.jna:jna:5.10.0) to libraries/net/java/dev/jna/jna/5.10.0/jna-5.10.0.jar
Unpacking net/java/dev/jna/jna-platform/5.10.0/jna-platform-5.10.0.jar (libraries:net.java.dev.jna:jna-platform:5.10.0) to libraries/net/java/dev/jna/jna-platform/5.10.0/jna-platform-5.10.0.jar
Unpacking net/sf/jopt-simple/jopt-simple/5.0.4/jopt-simple-5.0.4.jar (libraries:net.sf.jopt-simple:jopt-simple:5.0.4) to libraries/net/sf/jopt-simple/jopt-simple/5.0.4/jopt-simple-5.0.4.jar
Unpacking org/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.jar (libraries:org.apache.commons:commons-lang3:3.12.0) to libraries/org/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.jar
Unpacking org/apache/logging/log4j/log4j-api/2.17.0/log4j-api-2.17.0.jar (libraries:org.apache.logging.log4j:log4j-api:2.17.0) to libraries/org/apache/logging/log4j/log4j-api/2.17.0/log4j-api-2.17.0.jar
Unpacking org/apache/logging/log4j/log4j-core/2.17.0/log4j-core-2.17.0.jar (libraries:org.apache.logging.log4j:log4j-core:2.17.0) to libraries/org/apache/logging/log4j/log4j-core/2.17.0/log4j-core-2.17.0.jar
Unpacking org/apache/logging/log4j/log4j-slf4j18-impl/2.17.0/log4j-slf4j18-impl-2.17.0.jar (libraries:org.apache.logging.log4j:log4j-slf4j18-impl:2.17.0) to libraries/org/apache/logging/log4j/log4j-slf4j18-impl/2.17.0/log4j-slf4j18-impl-2.17.0.jar
Unpacking org/slf4j/slf4j-api/1.8.0-beta4/slf4j-api-1.8.0-beta4.jar (libraries:org.slf4j:slf4j-api:1.8.0-beta4) to libraries/org/slf4j/slf4j-api/1.8.0-beta4/slf4j-api-1.8.0-beta4.jar
Starting net.minecraft.server.Main


"
```
(I apologize if there is an easier way to paste in the code, I am very new to forums lol). The terminal simply hangs at "Starting net.minecraft.server.Main" and never goes any further.


I have tried forum searching but cannot find any answer to this hang. I tried to look up what the specific net.minecraft.server.Main file was but I still could not find anything useful.


I have tried reinstalling java, and the vm, as well as re-downloading the server.jar file. I have even tried this on the base ubuntu install on QEMU, but the same hang occurs. (Yes, I even tried manually giving my user execute perms on the file, but still nothing. Going to su produces nothing new.)


I even tried to boot up a vanilla server on my main arch install, and I did the exact same process of downloading and executing, and the server boots up. At this point, the only thing that I can think of is that there is an issue with QEMU and my specific use case. (Normally, I would highly think of a missing package, but there is zero feedback on a missing package...)


Has anyone had a similar issue or know how to fix this? I would appreciate any help with this. Thank you for your time in advance!

---

### Post by MAFoElffen on 2022-03-07
What commands did you use to download and install 'openjdk-17-jdk'? because reading guides on installing MineCraft Server to Ubuntu Server 20.04 say to use package 'openjdk-17-jre-headless(?)... Start 'screen' before,then use some flags that you didn't, when running the jar file:
[https://www.digitalocean.com/community/tutorials/how-to-create-a-minecraft-server-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-minecraft-server-on-ubuntu-20-04) 

Just saying the first thing I saw was the wrong type of OpenJava utilities on a machine that is console, not GUI.

---

### Post by alexrocks on 2022-03-11
I realized at first that I had the development kit package instead of the runtime environment package installed (which was quite dumb haha). I did get openjdk-17-jre-headless installed, but as soon as I run the jar file it hangs again at (Starting net.minecraft.server.Main). I have followed the listed article given by @MAFoElffen, but still can't get anywhere. Many thanks for looking into this!

---

