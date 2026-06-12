---
title: "Several Problems I can't seem to solve."
date: 2008-05-11
forum: General Help
---

### Post by carl99fan on 2008-05-11
I am using Ubuntu 8.04
I have been reading and searching for days on ways to solve these problems and I seem to have made things worse now. I have been looking for a way to fix what seems to be some kind of Flash, java, plugin, problem I guess.
When I go to Photobucket click on a picture in myalbum, and click on edit, after allowing flash nothing happens. you are supposed to go to an advanced editing program and be able to add lettering along with other photoshop type options.
Also I can not see Dizzler or other streaming music programs on people's "pages" and wonder if I can fix that in any way.
I also like to go to NASCAR.com and watch video clips. they use media-player popup windows to play the video with no other choices to view or download. is there anyway I can view these videos or am I sol?

I have been messing around in the package manager and now my frostwire no longer works. I uninstalled it and reinstalled it and when I click it it does nothing, when I open from terminal it says :
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)


I thank you in Advance for any suggestions.

---

### Post by ad_267 on 2008-05-11
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by carl99fan on 2008-05-11
> **ad_267 said:**
> [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
Did that before must have doen something wrong.. I get this now.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by ad_267 on 2008-05-11
Did you run that? You will need to use sudo
```
sudo dpkg --configure -a
```

Installing the ubuntu-restricted-extras package should sort out the java and flash problems.

---

### Post by carl99fan on 2008-05-11
> **ad_267 said:**
> Did you run that? You will need to use sudo
```
sudo dpkg --configure -a
```

Installing the ubuntu-restricted-extras package should sort out the java and flash problems.

Yea I'm working on this now....
....Maybe I should start from scratch again....:confused:

---

### Post by carl99fan on 2008-05-11
"This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/"
I wen there and downloaded some stuff... it also says this now....

"The file should be owned by root.root and be copied
to /tmp."
I don't understand this

---

### Post by ad_267 on 2008-05-11
If you install ubuntu-restricted-extras that should install the latest version of java. You don't need to download anything from a website.

---

