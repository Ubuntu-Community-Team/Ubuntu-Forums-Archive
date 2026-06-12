---
title: "Citrix ICA Client - Java Update - Ubutnu 7.04"
date: 2007-07-27
forum: General Help
---

### Post by tombott on 2007-07-27
After the recent Java update on Ubuntu 7.04 my install of Citrix ICA Client would no longer load.

I proceeded to download and install the latest version from [[COLOR="Red"]Citrix[/COLOR]]("http://www.citrix.com") extracted the files and ran the setup:

```
sudo ./setupwfc
```

However this did not resolve the issue.

I then remember that there was recently an updated version of Java downloaded and installed via Update Manager, so I did the following via a terminal:
```

sudo update-alternatives --config java

```

The following results where returned:


```
  
There are 3 alternatives which provide `java'.

Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```

I then selected 3

```
Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
```

And checked the changes had taken effect:

```
tomb@tb-lapbuntu:~/Install/citrix$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java
*         3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

I then ran the ICA Client and this time it opened without any problems.

Tom.

---

