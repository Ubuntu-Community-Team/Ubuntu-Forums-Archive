---
title: "Installing only one java instance"
date: 2014-12-05
forum: General Help
---

### Post by emayayess on 2014-12-05
I just installed oracle jdk7 by following [this url]("http://blog.bekijkhet.com/2014/04/install-oracle-jdk-in-ubuntu.html"). now when i did java -version, I got java 1.6 in response though i am expecting oracle java 1.7.

When i browsed to usr/lib/jvm/ I can see there are at least 3-4 different versions of java there

1. java-1.7.0-openjdk-amd64
2. java-6-oracle
3. java-7-oracle
4. java-6-openjdk-amd64
5. java-7-openjdk-amd64

I don't want these many installations there. All i want is Oracle java 1.7_0_55. Can someone help. 

Thanks

---

### Post by nerdtron on 2014-12-05
Did you install any java version before you installed the one from your link?

You should have uninstalled them first before you installed the one from your link.

---

### Post by emayayess on 2014-12-08
I didn't install anything bnefore the link. I know i should have but it never occured to me. now i want to make sure there is only one version of java and that is Oracke 1.7u55

---

### Post by QIII on 2014-12-08
Hello!

First -- Any number of Java versions can be resident on your machine at any time without interfering with each other.  In fact, you can switch between them by updating your alternatives (see the command at the end of this post).  So unless space is a problem, there's no reason at all to uninstall any of them.  If you want to, however, you can do so.

Oracle Java 7 Update 55 is not the most recent update anyway -- so what you should be getting from webupd8 would be newer than what is shown on that website.

Since Oracle Java 6 has been dropped (and shouldn't be used due to security issues), the fact that it is installed would seem to indicate that at some point it was deliberately installed. Might you have installed something from the web that might also have brought along Java 6 as a dependency?

What release of Ubuntu are you using?  OpenJDK 6 would not likely have been installed by default in any recent release of Ubuntu.  I don't think OpenJDK is even installed by default lately.

As for why you are getting what you see when you do

```
java -version
```

I think something must have gone wrong.  The webupd8 scripts should have set Oracle Java 7 as your chosen alternative.

Did you get any error messages?

Could you issue the following in the terminal and copy the results back here without making a selection?

```
sudo update-alternatives --config java
```

---

### Post by emayayess on 2014-12-08
> **QIII said:**
> Hello!

First -- Any number of Java versions can be resident on your machine at any time without interfering with each other.  In fact, you can switch between them by updating your alternatives (see the command at the end of this post).  So unless space is a problem, there's no reason at all to uninstall any of them.  If you want to, however, you can do so.

Oracle Java 7 Update 55 is not the most recent update anyway -- so what you should be getting from webupd8 would be newer than what is shown on that website.

Since Oracle Java 6 has been dropped (and shouldn't be used due to security issues), the fact that it is installed would seem to indicate that at some point it was deliberately installed. Might you have installed something from the web that might also have brought along Java 6 as a dependency?

What release of Ubuntu are you using?  OpenJDK 6 would not likely have been installed by default in any recent release of Ubuntu.  I don't think OpenJDK is even installed by default lately.

As for why you are getting what you see when you do

```
java -version
```

I think something must have gone wrong.  The webupd8 scripts should have set Oracle Java 7 as your chosen alternative.

Did you get any error messages?

Could you issue the following in the terminal and copy the results back here without making a selection?

```
sudo update-alternatives --config java
```


```
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-oracle/jre/bin/java          1072      auto mode
* 1            /usr/lib/jvm/java-6-oracle/jre/bin/java          1         manual mode
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual mode
  3            /usr/lib/jvm/java-7-oracle/jre/bin/java          1072      manual mode


Press enter to keep the current choice
[*], or type selection number: 



```

---

### Post by QIII on 2014-12-08
OK.  Good.

If you select 0 there, you'll be using Oracle Java 7. If at a later time you want to use OpenJDK, you can select that.

After you choose Oracle Java 7, I would be interested to see which browser plugin is being used.  Do you use Firefox?

---

### Post by emayayess on 2014-12-10
> **QIII said:**
> OK.  Good.

If you select 0 there, you'll be using Oracle Java 7. If at a later time you want to use OpenJDK, you can select that.

After you choose Oracle Java 7, I would be interested to see which browser plugin is being used.  Do you use Firefox?
I use chrome. most of the time.

---

