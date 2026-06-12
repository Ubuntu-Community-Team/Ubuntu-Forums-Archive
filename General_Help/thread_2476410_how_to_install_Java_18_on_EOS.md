---
title: "how to install Java 18 on EOS"
date: 2022-06-25
forum: General Help
---

### Post by straitsfan on 2022-06-25
Hello.   don't know if this is the right place, but here goes.  My apologies if it isn't.

I've posted back in December, when I was starting to get into Linux.  But I still had my MB Pro, and was used to Unix/OS X.   But sadly, I think my MB pro is dying (A backlight issue, and the machine is 12 or 13 years old.  It's a MB Pro 7,1, and I'm not sure that it can be fixed.) I like it, but I've become disappointed with Apple recently, given the changes they've made to their machines and attitude toward customers (all the new fangled changes, dongles' etc.).   

I eventually realized that I wanted to go to Linux, if for no other reason than I don't want Windows, either.   I'm familiar with the terminal, having done and learned things on OS X.  But I'm understanding that the commands are not always the same, etc.

I use my MB for java programming; just something I wanted to learn, and the MB was fine.  Downloading java is a breeze over there.  Not so much here in Linux.

So for the most part here's my question(s).

I've downloaded Java 18 from the Oracle website.  It's a debian package, jdk-18_linux-x64_bin.deb.  I had another site, linuxcapable.com, where I downloaded Java 17, but for some reason I can't compile and run the programs I have( a couple of error messages about not having the most update JRE, and/or an "Unsupported link error".  I can post those if you want, if that would make a difference, but I don't want to give TMI).

  I went around to various sites with these concerns, and was told that since the program I'm working on was written in Java 18, and I have Java17 on my machine, then it won't work.   I'm not sure how to update Java 17 if it can be done. 

So I figured that I'd just install -- or try to install -- java 18.  I downloaded the above file, and it's in my Downloads folder.

What I want to ask now is -- can anyone tell me the commands I have to run in the terminal to do this?  I've been to various sites and gotten different answers.   I just want to get Java going, and then I can learn about Linux as I go.   

Some sites told me that I can install it with:

[B]sudo apt install jdk-18_linux-x64_bin.deb



[/B]But at this point I'm confused as to what else if anything needs to be done.  I came across some site that also had something about dpkg, but I can't remember where that was.

Can anyone out there help?  if I do a search on "how to install Java 18 in elementary os" I get different sites that say different things, etc, different commands, etc.

As well, if anyone out there can point me to some kind of tutorial(s) on getting familiar with Linux (commands, etc), that would be greatly appreciated. 

I get the sense that there's more work at the command line than in Win or OS X.  But that could just be me.

Please let me know if you need any other information.  I've tried to be as brief as possible.

---

### Post by #&amp;thj^% on 2022-06-25
The correct way is to change directory pointing to Downloads and run:
```
cd Downloads
sudo apt install ./jdk-18_linux-x64_bin.deb
```

---

### Post by straitsfan on 2022-06-25
Thanks, but is there anything else needed to 'install it' and run it?  Or can I just run it as is?

---

### Post by #&amp;thj^% on 2022-06-25
It should be all you need to do for the install, after install and all is good I will provide a link for you view. ;)
[https://computingforgeeks.com/install-oracle-java-18-on-ubuntu-debian/](https://computingforgeeks.com/install-oracle-java-18-on-ubuntu-debian/)
```
 java --version
openjdk 18.0.1.1 2022-04-22
OpenJDK Runtime Environment (build 18.0.1.1+2)
OpenJDK 64-Bit Server VM (build 18.0.1.1+2, mixed mode)


```

---

### Post by straitsfan on 2022-06-25
Oh, one more thing -- I think the Java 17 will be in the same folder as Java 18 -- 

How can I remove Java 17, and/or set Java 18 as the default version (I read something about a command with 'config java' in it)

---

### Post by #&amp;thj^% on 2022-06-25
You can have both, List all java versions:

```
update-java-alternatives --list
```

Set java version as default (needs root permissions):

```
sudo update-java-alternatives --set /path/to/java/version

```
...where /path/to/java/version is one of those_ listed by the previous command_ (

Or you could just set it with:
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-18/bin/java 1
```
```
java --version
java 18.0.1.1 2022-04-22
Java(TM) SE Runtime Environment (build 18.0.1.1+2-6)
Java HotSpot(TM) 64-Bit Server VM (build 18.0.1.1+2-6, mixed mode, sharing)

```

---

### Post by straitsfan on 2022-06-25
okay -- i've got it downloaded and installed in the /usr/bin/lib/jvm folder.  I can see it:

/usr/lib/jvm$ ls
java-1.17.0-openjdk-amd64  java-17-openjdk-amd64  jdk-18

But I can't set it to the default version.   When I enter your command:

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-18/bin/java 1

it does nothing.  the java version is still Java 17.

---

### Post by #&amp;thj^% on 2022-06-25
Can you show me this:
```
update-java-alternatives --list
```

---

### Post by straitsfan on 2022-06-25
Sure -- here it is:

update-java-alternatives --list
java-1.17.0-openjdk-amd64      1711       /usr/lib/jvm/java-1.17.0-openjdk-amd64

---

### Post by straitsfan on 2022-06-25
I don't know what "1711" is, if that makes any difference.

---

### Post by #&amp;thj^% on 2022-06-25
Install did not work then, show me this now
```
apt policy jdk-18
```

---

### Post by #&amp;thj^% on 2022-06-25
> **1fallen said:**
> Install did not work then, show me this now
```
apt policy jdk-18
```
Why did you place it here>>" /usr/bin/lib/jvm folder. I can see it:"???
I don't recall telling you to do that. :(

---

### Post by straitsfan on 2022-06-25
I didn't place it there.  That's where it installed.

here's the result of your most recent post:
jdk-18:
  Installed: 18.0.1.1-ga
  Candidate: 18.0.1.1-ga
  Version table:
 *** 18.0.1.1-ga 100
        100 /var/lib/dpkg/status

I just used the sudo install command, and it installed.

---

### Post by #&amp;thj^% on 2022-06-25
Ok moving forward:
```
sudo apt install -y libc6-x32 libc6-i386
```
and again run
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-18/bin/java 1
```
then show:
```
update-java-alternatives --list
```

---

### Post by straitsfan on 2022-06-25
okay -- here it is:

ava-1.17.0-openjdk-amd64      1711       /usr/lib/jvm/java-1.17.0-openjdk-amd64

---

### Post by #&amp;thj^% on 2022-06-25
paste this back to see please:
```
sudo update-alternatives --config java
```

---

### Post by straitsfan on 2022-06-25
Here it is -- I think this is what I was looking for:

Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-17-openjdk-amd64/bin/java   1711      auto mode
  1            /usr/lib/jvm/java-17-openjdk-amd64/bin/java   1711      manual mode
  2            /usr/lib/jvm/jdk-18/bin/java                  1         manual mode

Press <enter> to keep the current choice
[*], or type selection number:

I've seen this before.  I'm going to assume to choose number 2, press enter, and try it out?  But I'm not going to do anything untill you advise:), then try it out and see if it works.

I had entered this earlier today, but when I did, I got a message saying that 17 was the only version, and there was nothing to configure.

---

### Post by #&amp;thj^% on 2022-06-25
yep your spot on>>>2 /usr/lib/jvm/jdk-18/bin/java 1 manual mode

---

### Post by straitsfan on 2022-06-25
Will do.  Will let you know.  Can I keep in contact with you?  You've been very helpful.

---

### Post by #&amp;thj^% on 2022-06-25
> **straitsfan said:**
> Can I keep in contact with you?  You've been very helpful.
Sure, either in the forums here or you can drop me a PM for a non help related message.
We do all support questions in public view for the benefit of all.

---

### Post by straitsfan on 2022-06-25
I cannot thank you enough for this.  All seems well.  A very big thank you.

While I have you here, could you tell me what the problem was?  I ask because I can't tell you how many pages I've searched/read, and how many posts I've made asking these questions,only to get non-answers or partial answers that assume I know about all these commands and Linux file structure, etc.  

I'm literally getting into it the last few days.  Sooner or later my beloved MB pro will die.  It really upsets me that it still works, but there's a stupid backlight issue.  I'm going to have to buy an external monitor, because I don't want to forget how to use it.  And I'll learn a new OS.

I do mostly programming.  I simply wanted to learn java, and it's kind of fun.  I'm working on a little contacts program right now, as a way of implementing what I'm learning, rather than try to look for a contacts app online (Although if you know of one as a backup, I'd be happy of you could recommend it, or a couple)

Last question for now:  Is there a book, or some kind of site, etc.  where I could learn about Linux in one spot?  It gets very frustrating having to go all over the net.  Especially since it seems that Linux is more command line oriented for a lot of things.  

If you don't mind, I'd like to keep you in mind should I have any other questions.  

Once again, a big thanks.  I'll be in touch should I need more help.

---

### Post by straitsfan on 2022-06-25
Just one thing -- out of curiosity, can you tell me what the problem was?

---

### Post by #&amp;thj^% on 2022-06-25
> **straitsfan said:**
> Just one thing -- out of curiosity, can you tell me what the problem was?

My failure to just jump to this below, after you reported a good install:
```
sudo update-alternatives --config java
```

---

### Post by straitsfan on 2022-06-25
that's strange -- I tried that command after the install and was told that there was only one version and there was nothing to configure.

---

### Post by #&amp;thj^% on 2022-06-25
> **straitsfan said:**
> that's strange -- I tried that command after the install and was told that there was only one version and there was nothing to configure.

Oh! that makes sense now to me, probably missing these dependencies "libc6-x32 libc6-i386" we installed those before you ran that code for a second time.

---

