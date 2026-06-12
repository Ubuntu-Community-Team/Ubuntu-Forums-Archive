---
title: "Permissions for X Windows"
date: 2008-04-29
forum: General Help
---

### Post by markhamg on 2008-04-29
I am trying to use a Java application in ubunto. Apparently the java virtual machine uses X windows to manage its displays. When I try to run the java program it fails, apparently because of a security problem accessing X11. If I sudo java -jar myapp.jar it works.

How do I set the permissions for X windows to allow all users?

I a new to Ubuntu; I have used some other flavors of unix.

Help would be appreciated

---

### Post by ajmorris on 2008-04-29
hi there,
permissions are set via individual programs/files, (groups are also used, but in your case, we dont need to touch these) So, if you would like a normal user to be able to run that jar file, do this:
```
1) ln -ls <file.jar> (this will print the current permissions of the file
```
now, you can either, change your user to grp, or to owner of the file, or give "others" permissions on the jar file, in this case, we will change you to owner.
so, do this:
```
sudo chown <user> <file.jar>
```
then you can do java -jar <file.jar> as a normal user to open it. If you prefer to do it without changing the owner, some commands you will need to know are:
sudo chrp
sudo chmod

AJ

---

### Post by markhamg on 2008-05-01
Thanks for the quick reply, but it isn't a problem with my jar file, but the java virtual machine.

If I run the command java -jar MyApp.jar (which is owned by me) I get the following display:

--------
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f7b767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7f7b8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xad5821bd]
#3 /usr/lib/jvm/jre1.6.0_05/lib/i386/xawt/libmawt.so [0xad67c8ce]
#4 /usr/lib/jvm/jre1.6.0_05/lib/i386/xawt/libmawt.so [0xad659067]
#5 /usr/lib/jvm/jre1.6.0_05/lib/i386/xawt/libmawt.so [0xad659318]
#6 /usr/lib/jvm/jre1.6.0_05/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xad65961f]
#7 [0xb5d0ce9d]
#8 [0xb5d05edd]
#9 [0xb5d05edd]
#10 [0xb5d03249]
#11 /usr/lib/jvm/jre1.6.0_05/lib/i386/client/libjvm.so [0x621c40d]
#12 /usr/lib/jvm/jre1.6.0_05/lib/i386/client/libjvm.so [0x6310378]
#13 /usr/lib/jvm/jre1.6.0_05/lib/i386/client/libjvm.so [0x621c2a0]
#14 /usr/lib/jvm/jre1.6.0_05/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#15 /usr/lib/jvm/jre1.6.0_05/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d1e96d]
#16 [0xb5d0ce9d]
#17 [0xb5d05d77]
#18 [0xb5d03249]
#19 /usr/lib/jvm/jre1.6.0_05/lib/i386/client/libjvm.so [0x621c40d]
------

So the java VM is using the library 'libmawt' to initialize Xwindows, but fails.  

If I sudo java -jar MyApp.jar it runs OK.

---

