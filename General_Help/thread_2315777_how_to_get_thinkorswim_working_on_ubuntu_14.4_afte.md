---
title: "how to get thinkorswim working on ubuntu 14.4 after their recent update"
date: 2016-03-02
forum: General Help
---

### Post by a-you on 2016-03-02
Recent updates to the thinkorswim java program caused that to stop working on my system. It was pretty frustrating because it wasn't clear what was wrong. All that would happen was that the launch process never got past the "installing updates" stage.

Btw I have ubuntu studio 14.4 64 bit.

Searching around I discovered that on Jan 23rd they had posted this:
[https://tlc.thinkorswim.com/center/release/rel-1-23-2016.html](https://tlc.thinkorswim.com/center/release/rel-1-23-2016.html)
saying that they had moved their code base to java 8.

Fortunately some of the people in thinkorswim tech support are sympathetic to linux users even though linux is not officially supported. I managed to have a chat session with one of them, who was very helpful.

First, you now need to have java 8, and you need to get the Oracle version. The best way imo to get that is to use the ppa from the wonderful folks at webupd8.org:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update 
sudo apt-get install oracle-java8-installer
```

In my case since I had already used their ppa to install java 7 I only had to do:
```
sudo apt-get update 
sudo apt-get install oracle-java8-installer
```

But after that the system was still treating java 7 as the goto version, so I had to do:

```
sudo update-java-alternatives -s java-8-oracle
```

After that java -version now shows:
```
java version "1.8.0_74"
Java(TM) SE Runtime Environment (build 1.8.0_74-b02)
Java HotSpot(TM) 64-Bit Server VM (build 25.74-b02, mixed mode)
```

Then this critical step. The thinkorswim tech support people sent me this link to a different installer script:
[URL="https://mediaserver.thinkorswim.com/installer/install.html"]https://mediaserver.thinkorswim.com/installer/install.html
[/URL]
You obviously need the "[Install thinkDesktop (10 MB)]("https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh")" script. Note that the script you get from the TDA website is some 7.3MB or so so this is a different installer script.

Since I had originally installed thinkorswim for my non-root user I wanted to try doing it that way again (even though the tech support people had recommended using sudo). I'd rather not run any app as root if at all possible, and especially a complex app that might possibly have bugs, and especially a complex app that faces the internet. This meant that I had installed it at /home/myusername/thinkorswim. I trashed that folder along with this folder /home/myusername/.thinkorswim, which seemed to contain only a lock file. I also trashed the launcher from the desktop.

Then I installed from scratch using the alternate installer script. cd to where the installer script is and:

```
sh ./thinkorswim_installer.sh
```

When it asked me if I want to install for all users or only the current user I chose only the one user. This meant that it proposed installing again in /home/myusername/thinkorswim, which I accepted.

When it was done installing and I had clicked "finish" it launched and went through the usual "installing updates" stage. It took a while but it did launch thinkorswim and that's now running just fine on my system.

---

