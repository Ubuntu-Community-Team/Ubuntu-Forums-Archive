---
title: "[q] Cannot use signapk.jar to sign apks"
date: 2013-05-16
forum: General Help
---

### Post by elesbb on 2013-05-16
Hey guys, i just installed ubuntu in a Virtual Box, everything is great, but, i cannot sign apks with it. here is the error that comes up.

[COLOR=#222225][FONT=Arial]Exception i[/FONT][/COLOR][COLOR=#222225][FONT=Arial]n thread "main" java.lang.NoClassDefFoundError: javax/crypto/EncryptedPrivateKeyInfo[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at com.android.signapk.SignApk.decryptPrivateKey(Sign Apk.java:124)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at com.android.signapk.SignApk.readPrivateKey(SignApk .java:154)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at com.android.signapk.SignApk.main(SignApk.java:436)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]Caused by: java.lang.ClassNotFoundException: javax.crypto.EncryptedPrivateKeyInfo[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.net.URLClassLoader$1.run(URLClassLoader.java: 366)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.net.URLClassLoader$1.run(URLClassLoader.java: 355)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.security.AccessController.doPrivileged(Native Method)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.net.URLClassLoader.findClass(URLClassLoader.j ava:354)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.lang.ClassLoader.loadClass(ClassLoader.java:4 23)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at sun.misc.Launcher$AppClassLoader.loadClass(Launche r.java:308)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]at java.lang.ClassLoader.loadClass(ClassLoader.java:3 56)[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]... 3 more[/FONT][/COLOR]

---

