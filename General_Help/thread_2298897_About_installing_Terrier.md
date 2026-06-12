---
title: "About installing Terrier"
date: 2015-10-14
forum: General Help
---

### Post by satimis on 2015-10-14
Hi all,

[http://terrier.org/](http://terrier.org/)

I have Terrier tarball terrier-4.0.tar.gz download to Download folder.  Please advise on which folder shall I install it?

/etc/terrier ?

OR
/home/user/terrier

Thanks

Regards
satimis

---

### Post by ajgreeny on 2015-10-14
Is there a readme or Install file in the archive?  That may tell you exactly how to install it, if it needs installing, or which file to execute to run it.

It is a java application, as far as I can see, so there may be an executable terrier.jar file that runs the program, or a shell script which is used to execute the .jar file.

Have a search and come back again if you can't figure it out.

---

### Post by satimis on 2015-10-14
> **ajgreeny said:**
> Is there a readme or Install file in the archive?  That may tell you exactly how to install it, if it needs installing, or which file to execute to run it.

It is a java application, as far as I can see, so there may be an executable terrier.jar file that runs the program, or a shell script which is used to execute the .jar file.

Have a search and come back again if you can't figure it out.
Hi,

I followed below document to install Terrier;
[http://terrier.org/docs/v4.0/quickstart.html](http://terrier.org/docs/v4.0/quickstart.html)

It just mentions .....
```

After having downloaded Terrier, copy the file to the directory where you want to install Terrier.

```

Regards
satimis

---

### Post by tristan16 on 2015-10-14
> **satimis said:**
> Hi,

I followed below document to install Terrier;
[http://terrier.org/docs/v4.0/quickstart.html](http://terrier.org/docs/v4.0/quickstart.html)

It just mentions .....
```

After having downloaded Terrier, copy the file to the directory where you want to install Terrier.

```

Regards
satimis

Then by all means, install it wherever you want to.

---

### Post by satimis on 2015-10-15
> **tristan16 said:**
> Then by all means, install it wherever you want to.
Hi,

Thanks

Performed following steps to install Terrier

Download terrier-4.0.tar.gz to a VM
[http://terrier.org/download/agree.shtml?terrier-4.0.tar.gz](http://terrier.org/download/agree.shtml?terrier-4.0.tar.gz)
->  to /home/satimis/Downloads/

&#10219; mkdir /home/satimis/Terrier
&#10219; mv Downloads/terrier-4.0.tar.gz Terrier/
&#10219; cd Terrier/
&#10219; ls
terrier-4.0.tar.gz

&#10219; tar -zxvf terrier-4.0.tar.gz

&#10219; ls
terrier-4.0  terrier-4.0.tar.gz

&#10219; ls terrier-4.0```

bin        doc  lib       LICENSE.txt  share  var
build.xml  etc  licenses  README.txt   src

```

&#10219; echo $JAVA_HOME
No output

Install JRE
========
&#10219; sudo mkdir /usr/java
&#10219; ls -ald /usr/java```

drwxr-xr-x 2 root root 4096 Oct 15 16:30 /usr/java

```

&#10219; sudo chown satimis:satimis /usr/java
&#10219; ls -ald /usr/java```

drwxr-xr-x 2 satimis satimis 4096 Oct 15 16:30 /usr/java

```


Download JRE on
[http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)
Download```

Linux x64	68.36 MB  	jre-8u60-linux-x64.tar.gz

```

Open with [Archive Manager (default)]
-> OK

Location: [/jre1.8.0_60/    ]
Extract it to;
/usr/java

/usr/java/jre1.8.0_60


Ran:-
&#10219; export JAVA_HOME="/usr/java/jre1.8.0_60"
&#10219; echo $JAVA_HOME```

/usr/java/jre1.8.0_60

```

Terrier installation completed.  Thanks

Regards
satimis

---

