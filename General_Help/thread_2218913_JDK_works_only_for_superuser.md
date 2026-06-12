---
title: "JDK works only for superuser"
date: 2014-04-22
forum: General Help
---

### Post by Rashmil on 2014-04-22
Hi,
I have xubuntu 14.

I installed JDK but it can be accessed only as SU. Can not access without login in as SU.

[PHP]rush@ubuntu:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre 
* gcj-4.8-jre-headless
 * openjdk-7-jre-headless 
* gcj-4.6-jre-headless 
* openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
[/PHP]


However it recognizes on SU mode
[PHP]
rush@ubuntu:~$ suPassword: 
root@ubuntu:/home/rush# java -versionjava version "1.8.0_05"Java(TM) SE Runtime Environment (build 1.8.0_05-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.5-b02, mixed mode)root@ubuntu:/home/rush# 

[/PHP]

I created the symbolic link for firefox java plugin. However mozilla doesn't show any plugins.

I think this is something to do with SU settings. Can anyone suggest a fix for this.

---

### Post by Rashmil on 2014-04-22
I found a solution by myself.

The permission problem was solved by the following command

sudo chown -R 777 /usr/lib/jvm/jdk1.8.0_05

---

### Post by QIII on 2014-04-22
Um...

I'm not so sure that recursively setting everything in that directory to 777 was a very wise idea.

One, it is dangerous to do that recursively.  In some directories, the operation of the applications may be dependent on specific permissions -- and might balk if something that it expects to be 755, for instance, is 777.

It looks to me like most of the files there should be 755 at best.

What you have done is given everyone -- any casual user who logs on, you without sudo, an intruder -- the keys to the kingdom.  Anyone who wants to can now alter things like your includes, the java virtual machine itself, everything.  They can delete them and replace them with spurious files if they want to.

Be extremely careful about assigning permissions recursively in directories -- it would have been better to wait for an answer.

Edit:  Just noticed something.  I think you meant chmod, not chown

---

