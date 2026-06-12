---
title: "[SOLVED] Problem installing java"
date: 2008-06-16
forum: General Help
---

### Post by pb_online on 2008-06-16
When I am trying to install java via synaptic I get this...

[IMG]http://www.imageshack.gr/files/0zv677hzz6dc12b85dcn.png[/IMG]

---

### Post by Zorael on 2008-06-16
This should pop as a accept/decline dialog during installation of it. I can't begin to imagine why it doesn't.

I'd try installing it via a terminal.
```
$ sudo aptitude install sun-java6-jre
```
Obviously, replace **jre** with **jdk** if you want the whole development kit. Add other packages to the list if you want more installed as well, while you're at it. For instance:
```
$ sudo aptitude install sun-java6-jdk sun-java6-plugin eclipse
```

---

### Post by pb_online on 2008-06-16
Thank you, I installed it via Console and I get the option to answer Yes.
Is that a bug? I mean, trying install it via Synaptic.

In order to install this package, you must agree to its license terms,   
  &#9474; the "Operating System Distributor License for Java" (DLJ), v1.1. Not     
  &#9474; accepting will cancel the installation.                                  
  &#9474;                                                                          
  &#9474; Do you agree with the DLJ license terms?                                 
  &#9474;                                                                          
  &#9474;                    <Yes>                       <No>  

Anyway, I installed it but firefox is still without java. I go to java.com and make the test without success.

I have java and java script enabled in my firefox options.

---

### Post by Sef on 2008-06-16
> I'd try installing it via a terminal.
Code:

$ sudo aptitude install sun-java6-jre

Obviously, replace jre with jdk if you want the whole development kit. Add other packages to the list if you want more installed as well, while you're at it. For instance:
Code:

$ sudo aptitude install sun-java6-jdk sun-java6-plugin eclipse



1) Since the OP has indicated that they use Kubuntu, then this should be the code:

```
kdesu aptitude install sun-java6-jre
```

and ```
kdesu aptitude install sun-java6-jdk sun-java6-plugin eclipse
```

2) > I have java and java script enabled in my firefox options. 

3) Java and Java Script are different, nonrelated programs.

4) > Anyway, I installed it but firefox is still without java. I go to java.com and make the test without success.

Are you using 32-bit or 64-bit Kubuntu?

---

### Post by Zorael on 2008-06-16
> **Sef said:**
> 1) Since the OP has indicated that they use Kubuntu, then this should be the code:

```
kdesu aptitude install sun-java6-jre
```

and ```
kdesu aptitude install sun-java6-jdk sun-java6-plugin eclipse
```
Sorry to tangent, but I don't see why. aptitude is *not* Adept. Much like apt-get shouldn't be run with gksu, aptitude shouldn't be run with kdesu.

End of tangent.

---

### Post by pb_online on 2008-06-16
What is kdesu?

I use 32-bit OS.

Is there any suggestion how to solve the problem with firefox java ?

---

### Post by avtolle on 2008-06-16
Did you install the plug-in?

---

### Post by Zorael on 2008-06-16
kdesu is KDE's variant of sudo to use for graphical applications. More specifically, it's a sudo frontend for KDE. Its Gnome equavilent is gksu.

For the Java plugin in Mozilla browsers (Firefox), you want to install the **sun-java6-plugin** package. Hopefully that should make it work right away.

---

### Post by pb_online on 2008-06-17
Thank you.

The problem solved with plugin.

---

