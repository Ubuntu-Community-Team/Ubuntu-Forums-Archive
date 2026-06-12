---
title: "Firefox Crashes Viewing Pages with Java Applets"
date: 2007-11-13
forum: General Help
---

### Post by rdemars on 2007-11-13
I have Kubuntu 7.10 installed on two systems with Firefox 2.0.0.8 and Java(TM) Plug-in 1.6.0_03 installed.  Every time I browse to a web page that has a Java applet on it, the Firefox application crashes and disappears.  It even happens when I start Firefox with the -safe-mode option.  An example site is Java test page at: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
If anyone has any ideas on this issue, I would be most appreciative.

---

### Post by taurus on 2007-11-13
Did you also install the java plugin?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by rdemars on 2007-11-13
Yes, it was all installed using synaptic.

---

### Post by malfist on 2007-11-13
I installed the latest version of the SDK for my programming use and I have the same problem with firefox, about half the time.

---

### Post by minus198 on 2007-11-13
Does this get autoinstalled when installing sun-java6-plugin

sun-java6-jre

---

### Post by rdemars on 2007-11-13
Yes, that is installed with the plugin.  Java appears to be working on my systems.  I can start the Java Console and can run Java Apps right on the system.  It is just when Firefox calls Java (like the Java Install Test Site), it crashes.

---

### Post by rdemars on 2007-11-13
I have just found a Java error file from one of my browser crashes:

#  SIGSEGV (0xb) at pc=0xb7eb2cbc, pid=14336, tid=3034065808
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x71cbc]  memcpy+0x1c
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0xb5ade800):  JavaThread "Thread-4" [_thread_in_native, id=14359]

siginfo:si_signo=11, si_errno=0, si_code=2, si_addr=0xb4d32000

Registers:
EAX=0xb5261001, EBX=0xb7f86ff4, ECX=0x0000021e, EDX=0x00000fff
ESP=0xb4d016f0, EBP=0xb4d01714, ESI=0xb5261788, EDI=0xb4d32000
EIP=0xb7eb2cbc, CR2=0xb4d32000, EFLAGS=0x00210207

Top of Stack: (sp=0xb4d016f0)
0xb4d016f0:   b7e9afda b4d31879 b5261001 00000fff
0xb4d01700:   b4d31879

---

### Post by rdemars on 2007-11-15
JRE tries to call the libnss_files.so library to find localhost name and it forwards it onto the libc.so.6 file.  If the localhost entry in the host file is too long, it will crash the JRE.  It appears that on my system, the Network Manager Application had grouped all my 127.0.0.1 localhost entries (used to block spyware and adware sites) into one 127.0.0.1 line.  The 127.0.0.1 in my host file was huge.  I separated the line back out into individual lines and the JRE started working again.

---

### Post by donmiguel on 2007-12-08
I don't really get what you've done.. Would you be so kind and explain exactly what you had do do? And how i can be sure I have the same problem?

would be great. Thanks

---

### Post by Ghydda on 2008-01-13
[QUOTE="rdemars"]If the localhost entry in the host file is too long, it will crash the JRE.[/QUOTE]
[QUOTE="rdemars"]I separated the line back out into individual lines and the JRE started working again.[/QUOTE]

This fixed my setup as well!!!
Great tip!!! Thanks a lot.



Regards
Ghydda

---

### Post by TelQuessir on 2008-01-14
Can anyone list the steps on how this can be done? I am not able to find the localhost file.

Thanks.

---

### Post by JohnCraickkciarc on 2008-01-28
The file to fix is /etc/hosts. 
Look for a line that starts ...

127.0.0.1	localhost ... <lots of stuff after this>

and make sure it's not too long

This fixed the problem I'd been chasing for days on my system. In my case firefox was crashing AND the opera browser wouldn't run at all -well, it would load but just said there was a "network error" and then wouldn't do anything else. 

Many thanks to the discoverer of the fix

Regards,

JohnC

---

### Post by donmiguel on 2008-01-28
i have nothing at all after "127.0.0.1 localhost"!
could that also be a problem?!

---

### Post by sayeo87 on 2008-04-23
Yup I have the same problem and there's nothing after "127.0.0.1 localhost" for me too

---

