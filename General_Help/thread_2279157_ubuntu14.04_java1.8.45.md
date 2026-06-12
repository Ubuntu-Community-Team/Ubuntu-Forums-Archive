---
title: "ubuntu14.04 java1.8.45"
date: 2015-05-21
forum: General Help
---

### Post by ttalin on 2015-05-21
This is regarding "Application blocked by Java security" issue that comes up with the newer java releases.
       In windows 7, by adding trusted sites to the exception list, I was able to address the java security issue. In Ubuntu, despite  editing the exception list using jcontrol in a similar manner, I'm still getting 
        "Your security settings have blocked a self-signed application from running" message and the Java plugin is crashing. What else can be done to address this issue?

---

### Post by dino99 on 2015-05-21
hm, java+security, that's a strange couple

---

### Post by ttalin on 2015-05-26
I'm replying to my own thread (know what the problem is, but still unresolved). The sites added to the exception list using sudo jcontrol are not there when you check with jcontrol alone and obviously firefox is being run as a regular user. Running firefox as sudo does not seem to be working. There are also other issues: 
     When default-java is linked to java-8-oracle, you can view the exceptions list both by sudo jcontrol and jcontrol. It is not possible to modify the exceptions list  either way though.
     When default-java is linked to java-8-openjdk, you can modify the list with sudo jcontrol, however you are unable to view the list without being sudo.  Changing permissions/owners etc is not helping that much, either.
     What a strange problem. Do you want to step in and help?

---

### Post by ttalin on 2015-05-27
If jcontrol does not respond immediately when running it as a regular user, take a break for an hour or two. You might just find it responding after that wait. Then you can modify your exceptions list. Issue resolved.

---

