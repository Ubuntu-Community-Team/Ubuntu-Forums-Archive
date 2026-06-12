---
title: "Error : cant run Synaptic Package Manager"
date: 2007-06-06
forum: General Help
---

### Post by Labrada001 on 2007-06-06
Im running Ubuntu 7. I cant open Synaptic Package Manager. I get this error: 
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Can anyone help?

---

### Post by NeoLithium on 2007-06-06
Open up a terminal (Applications -> Accessories -> Terminal) and type:
```

sudo dpkg --configure -a

```
Let it do it's thing and then you should be all good again.

---

### Post by Labrada001 on 2007-06-06
thanks. It worked !

---

### Post by NeoLithium on 2007-06-06
You're welcome :)  It happens once in a while if the package installation or updates gets interrupted. All you have to do is run that command from terminal and it will be all good again :)

---

### Post by taavi7 on 2007-11-07
i have the same problem in 7.04 but when i enter the code (sudo dpkg --configure -a) i gives me this:

Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

i downloaded the file (jdk-6-doc.zip) but im new in ubuntu and i dont know what i have to do :oops:..can someone please help me?

---

### Post by qamelian on 2007-11-07
> **taavi7 said:**
> i have the same problem in 7.04 but when i enter the code (sudo dpkg --configure -a) i gives me this:

Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

i downloaded the file (jdk-6-doc.zip) but im new in ubuntu and i dont know what i have to do :oops:..can someone please help me?
Open a terminal by going to Applications > Accessories > Terminal. At the terminal prompt, type cd Desktop (or the name of the dir where you downloaded the file). Then, type ```
sudo chown root:root jdk-6-doc.zip
```and press enter. Type in your password when prompted. This will change ownership of the zip file to user=root and group=root. 

Next, in the terminal, type: ```
sudo cp jdk-6-doc.zip /tmp/
``` and press enter. Then try installing the package again.

---

### Post by Maestro23 on 2007-11-07
.

---

### Post by taavi7 on 2007-11-07
thank you..it worked:)

---

