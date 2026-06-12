---
title: "Unable to start Eclipse - ubuntu has experienced an internal error"
date: 2014-02-25
forum: General Help
---

### Post by ginar2 on 2014-02-25
Hi;
So far eclipse on my Ubuntu 13.10 has worked greatly. But recenty something has broken down. 
When I want to run Eclipse it starts up to when I might choose the project: 
(foto1)
[http://zapodaj.net/77eff9b413d82.png.html](http://zapodaj.net/77eff9b413d82.png.html)
and then dissapears (regardless which location/project I choose) and 
this message occured:
(foto2)
[http://zapodaj.net/502061e69b35b.png.html](http://zapodaj.net/502061e69b35b.png.html)

Of course PC was reseted but the situation still is the same. 
Any solution? 
Thx

---

### Post by monkeybrain20122 on 2014-02-25
Hi

[https://bugs.launchpad.net/ubuntu/+source/openjdk-7/+bug/1241532](https://bugs.launchpad.net/ubuntu/+source/openjdk-7/+bug/1241532)
 
The work around mentions something about oxygen theme, are you using kde?

Also
[https://bugs.launchpad.net/ubuntu/+source/openjdk-7/+bug/983207](https://bugs.launchpad.net/ubuntu/+source/openjdk-7/+bug/983207)
This one is deemed invalid since the guy's system is not up to date.

I have experienced no problem with eclipse or other java applications using openjdk-7 on Ubuntu 13.10 (see screenshot)

If the links above are not useful you may try to install Oracle's java in place of openjdk and see if it helps.

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

To choose your default Java version, after installing Oracle Java run
```
sudo update-alternatives --config java

```

Then run
```
java -version
```
If you have chosen Oracle's java as your default java you should see something like 
```
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)
```

See [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by ginar2 on 2014-02-26
Hi
> The work around mentions something about oxygen theme, are you using kde?
Yes, I have recently upgrated KDE.
Yes, solution: 
---------------------------
Go to: System Settings->Application Appearance->Style - change 'Oxygen' theme to any 
---------------------------
works

Thanks

---

