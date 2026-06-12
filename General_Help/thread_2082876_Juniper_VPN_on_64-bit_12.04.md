---
title: "Juniper VPN on 64-bit 12.04"
date: 2012-11-10
forum: General Help
---

### Post by BenWhitey on 2012-11-10
I'm somewhat new to linux but I've dabbled in it before. i installed the 64bit 12.04 version a few weeks ago.

I'm having trouble signing into the VPN for my work in Ubuntu. I've been reading a lot about this and it seems that there is a problem with Juniper and how it handles Ubuntu.

I've installed Oracle jdk1.7.0_09 and then I was able to sign into my VPN and then a java box popped up asking me to accept and I selected "always" and "allow."

Then the actual VPN client doesn't load when I click "start connection" or whatever the button says.

I've seen the Mad Scientist's things and I tried his script. What I ended up getting was the network connect box appears and wants me to put in the information for the VPN server which I do not know and I don't know if it would work if I did know the VPN address.

Any thoughts on other things I could try?

---

### Post by BenWhitey on 2012-11-15
Bump and adding more information.

When I try to do the "Network Connect" in Firefox for the first time (or after deleting the folder ~/.juniper_networks) a window pops up asking me to allow 


Otherwise nothing happens and the Network Connect fails. If I click "Check broswer combatibility" during the network connect it says:

> Your browser is incompatible with Network Connect.
&#8226; 	You must sign in from a Windows or Macintosh or Linux system for full compatibility with Network Connect. While signing in from a Linux box, you must sign in from a REDHAT 9.0 or SUSE 9.3 variant for full compatibility with Network Connect.
&#8226; 	Or, you must install a Sun Java Virtual Machine (JVM) (version 1.4.2_03 or above). To download the latest supported version of the Sun JVM, click here. Choosing not to trust the certificate presented by the compatibility checker causes your system to be incompatible with Network Connect.

This is even though I have Java(TM) Plug-in 1.7.0_09 installed according to the about: plugins page.

The same thing happens on chromium as well as this text appearing in the terminal I lauched it from:
```
java.lang.InterruptedException
	at java.lang.Object.wait(Native Method)
	at sun.plugin2.message.Queue.waitForMessage(Unknown Source)
	at sun.plugin2.message.Pipe$1.run(Unknown Source)
	at com.sun.deploy.util.Waiter$1.wait(Unknown Source)
	at com.sun.deploy.util.Waiter.runAndWait(Unknown Source)
	at sun.plugin2.message.Pipe.receive(Unknown Source)
	at sun.plugin2.main.server.JVMInstance$WorkerThread.run(Unknown Source)
```




```

ben@:~$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.5) (6b24-1.11.5-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

```

I do think that it is weird that 1.7.0_09 doesn't show up even though it is used by firefox and chromium. The reason I installed 1.7.0_09 was that I read that Juniper doesn't work well with non-Oracle versions of Java so I went ahead and installed an Oracle version.

---

