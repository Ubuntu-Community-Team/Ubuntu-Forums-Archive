---
title: "Package dependencies cannot be resolved: installing Eclipse on Ubuntu 14.04"
date: 2014-07-08
forum: General Help
---

### Post by hojjat on 2014-07-08
I get the following error when trying to install Eclipse using the Ubuntu Software Center:

> 
The following packages have unmet dependencies:

eclipse-platform: Depends: eclipse-platform-data (>= 3.8.1-5.1) but 3.8.1-5.1 is to be installed
                  Depends: eclipse-rcp (= 3.8.1-5.1) but 3.8.1-5.1 is to be installed
                  Depends: liblucene2-java (< 2.9.5) but 2.9.4+ds1-4 is to be installed
                  Depends: sat4j (< 2.4.0) but 2.3.2-1 is to be installed


This is very confusing, because it seems all the items that are listed as *to be installed* actually meet the dependecies! Anyways, any help in how to fix this is appreciated. I should clarify that I have done the following to no avail:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f

```

And here is the result of *java -version*

> 
java version "1.6.0_45"
Java(TM) SE Runtime Environment (build 1.6.0_45-b06)
Java HotSpot(TM) 64-Bit Server VM (build 20.45-b01, mixed mode)


---

### Post by ian-weisser on 2014-07-08
Try installing using the terminal instead of software center.
If you get an error, post the entire terminal output here.

---

### Post by hojjat on 2014-07-09
```

$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 eclipse : Depends: eclipse-jdt (>= 3.8.1-5.1) but it is not going to be installed
           Depends: eclipse-pde (>= 3.8.1-5.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


PS: I have a feeling it is because I have tomcat6 installed. Here is why I think so:

```

$ sudo apt-get install -f eclipse-platform-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 eclipse-platform-data : Depends: libtomcat7-java but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ian-weisser on 2014-07-09
Have your previously had eclipse installed?
Do have any relevant PPAs or non-Ubuntu repositories installed?
What version of Ubuntu are you running?

---

### Post by hojjat on 2014-07-10
ian-weisser, thanks for your thoughtful questions. As I was determining the answers, I accidently broke my OS by deleting the original copy of the home directory (instead of an old backup). Therefore, I had to reinstall the OS and cannot replicate the problem right now. I will post here again, if I end up having the problem again.

---

