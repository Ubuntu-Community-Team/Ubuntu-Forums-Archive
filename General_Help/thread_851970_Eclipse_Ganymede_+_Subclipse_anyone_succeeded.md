---
title: "Eclipse Ganymede + Subclipse: anyone succeeded?"
date: 2008-07-07
forum: General Help
---

### Post by ominolore on 2008-07-07
Hello everybody.
I'm a JavaEE developer, currently using Ubuntu Hardy + Eclipse Europa. I'd like to upgrade to Eclipse Ganymede but I really can't get Subclipse to work.

I have problems with the installation of JavaHL libraries I really can go through, that's why I really need your help, Ubuntu community!):P

In order to operate, Subclipse needs to use an SVN interface (JavaHL), but I can't find a way to set it up in Ganymede. First I tried to install the JavaHL libraries from the Sublipse update, with no success.
Then I tried to use JavaHL binding in Ubuntu repositories installing the libsvn-javahl package. Again, with no success.

Anytime I try to configure the Subclipse plugin it tells that the JavaHL interface cannot be found. Anybody succeeded in such an upgrade? I really can't find how to get through it. 

Any help would be appreciated.
Thanks,
L.

---

### Post by jespdj on 2008-07-07
I have Eclipse 3.4 (Ganymede) and Subclipse here on my 64-bit Ubuntu 8.04 laptop.

As far as I know, the JavaHL stuff (native library for SVN access) is not absolutely required. Subclipse can either use JavaHL or a pure Java interface.

In Eclipse, go to Window / Preferences / Team / SVN. Select "SVNKit (Pure Java)" instead of JavaHL as the SVN interface.

---

### Post by jesterfred on 2008-07-08
I have the exact same problem (Ubuntu 8.04 using Ganymede).  I can't get the JavaHL library working either so I switched to the SVNKit pure Java client library.  Be aware there is an undocumented "feature" that blesses you with its kind and benevolent presence.  As soon as you perform any local actions on a checked-out tree, it upgrades your meta data to 1.5.  (This is the info in the .svn dir).  Works flawlessly from Eclipse (Ganymede).  However, you can forget using the Ubuntu supplied svn command line tool or <oXygen/>.  They will both report:
```
svn: This client is too old to work with working copy 'src/com/dilijent/gsp/mti/util'; please get a newer Subversion client
```
The 1.5 clients will be available in Ubuntu 8.10....

I'm still trying to figure out:
[LIST]
[*]How to tell SVNKit NOT to perform this upgrade - you can do this in your own code.  I don't know how to do it within Eclipse.
[*]How to get the linker to load the javahl library
[/LIST]

---

### Post by ominolore on 2008-07-09
Thank for replying jespdj and jesterfred.
Your post have been very clarifying to me. Unfortunately using SVNKit doesn't work for my project, Eclipse hangs on every SVN operation attempt.

Anyway I've read ([click here]("http://beerholder.blogspot.com/2008/06/eclipse-34-ganymede-and-subclipse-14.html")) that there are chances to succeed with JavaHL + Ganymede using an older version of Subclipse. I haven't had the time to try it out yet, but setting an old update mirror for Subclipse should be a workaround.

Try:
```
http://subclipse.tigris.org/update_1.2.x
```

Hope it helps, let me know if it's working for you.

L.

---

### Post by peterdm on 2008-08-02
This is how I got JavaHL to work:

I presume you've installed Eclipse Ganymede by hand, since it's not in the Ubuntu repos. The problem comes from the fact that the subclipse plugin *requires* subversion 1.5.x installed, while Ubuntu 8.04 comes with subversino 1.4.x. So if we want it to work, we'll have to uninstall subversion from the Ubuntu repos and compile subversion ourselves.

Let's assume you have Eclipse Ganymede installed in /usr/share/eclipse, and that you're using a JDK installed in /usr/lib/jvm/java-6-openjdk.

[LIST=1]
[*]In order to be able to compile subversion, you need to make sure the following packages installed: libapr-1, libapr1-dev, libaprutil1, libaprutil1-dev
```
sudo apt-get install libapr-1 libapr1-dev libaprutil1 libaprutil1-dev
```
[*]Make sure the Ubuntu package libsvn-java is not installed, this is the one we're about to compile for ourselves in the following steps
[*]Now download the [subclipse]("http://subversion.tigris.org/downloads/subversion-1.5.1.tar.bz2") sources and untar them (e.g. in your user's home)
```
tar -xvjf subversion-1.5.1.tar.bz2
```
[*]Enter the directory, configure and build javahl (as normal user) and install (as super user)
```

cd subversion-1.5.1
./configure --enable-javahl --with-jdk=/usr/lib/jvm/java-6-openjdk/
make javahl
sudo make install-javahl

```
[*]Now the javahl libraries are installed in /usr/local/lib but you probably want them in /usr/lib/jni.
```

sudo cp /usr/local/lib/libsvnjavahl-1.* /usr/lib/jni/
sudo cp /usr/local/lib/svn-javahl/svn-javahl.jar /usr/share/java/

```
The first command has not copied the symbolic links correctly, it has replaced them by copies of the actual files. This works, but you may want fix the links.
[*]For some reason Eclipse still doesn't pick them up now, so we'll have to be a bit more persuasive. You should add a line -Djava.library.path=/usr/lib/jni to the file /usr/share/eclipse/eclipse.ini (edit as super user) after the -vmargs line
[*]Install [http://subclipse.tigris.org/update_1.4.x]("http://subclipse.tigris.org/update_1.4.x") as Eclipse update site, and install subclipse with the javahl adapter
[/LIST]

Now you should have JavaHL working in Eclipse Ganymede! Double-check by opening Window->Preferences->Team->SVN, and select JavaHL under "SVN Interface" section. It should say "JavaHL (JNI) 1.5.1..." instead of the dreaded "JavaHL(JNI) Not Available"!

Hope this helps,

Peter

---

### Post by simon roadkill on 2008-08-03
> **jespdj said:**
> I have Eclipse 3.4 (Ganymede) and Subclipse here on my 64-bit Ubuntu 8.04 laptop.

As far as I know, the JavaHL stuff (native library for SVN access) is not absolutely required. Subclipse can either use JavaHL or a pure Java interface.

In Eclipse, go to Window / Preferences / Team / SVN. Select "SVNKit (Pure Java)" instead of JavaHL as the SVN interface.

This seems to be working nicely for me, too.

---

### Post by peterdm on 2008-08-12
Yet another alternative is to install subversion from the Intrepid repos. That will work with JavaHL as well.

---

### Post by Mwiti on 2008-08-15
> **peterdm said:**
> 

Now you should have JavaHL working in Eclipse Ganymede! Double-check by opening Window->Preferences->Team->SVN, and select JavaHL under "SVN Interface" section. It should say "JavaHL (JNI) 1.5.1..." instead of the dreaded "JavaHL(JNI) Not Available"!

Hope this helps,

Peter

I've still JavaHL(JNI) Not Available. The procedure is ok, even if I had to install also libsvn-dev for a relink error during make install.

also svnadmin command has no effect in the shell and give me this:

```

$ svnadmin
The program 'svnadmin' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svnadmin: command not found

```

is it subversion 1.5.1 not installed?

Thank you!

---

### Post by Mwiti on 2008-08-15
I've finally installed Subversion 1.5.1 with "make install" only command. Now svnadmin works fine.

But Eclipse still not find JavaHL.

I'm using:
- Ubuntu Hardy
- Eclipse 3.4
- Subversion 1.5.1
- Subclipse 1.4.3
- Subversion Client Adapter 1.5.1
- Subversion Native Library Adapter (JavaHL) 1.5.1.1



SVNKit works fine as a client but is not able to find repository

- repository "svnadmin create ~/SVN"... ok
- location "svn://localhost"

---

### Post by Jæd on 2008-08-26
> **ominolore said:**
> Hello everybody.
I'm a JavaEE developer, currently using Ubuntu Hardy + Eclipse Europa. I'd like to upgrade to Eclipse Ganymede but I really can't get Subclipse to work.

I have problems with the installation of JavaHL libraries I really can go through, that's why I really need your help, Ubuntu community!):P

In order to operate, Subclipse needs to use an SVN interface (JavaHL), but I can't find a way to set it up in Ganymede. First I tried to install the JavaHL libraries from the Sublipse update, with no success.
Then I tried to use JavaHL binding in Ubuntu repositories installing the libsvn-javahl package. Again, with no success.

Anytime I try to configure the Subclipse plugin it tells that the JavaHL interface cannot be found. Anybody succeeded in such an upgrade? I really can't find how to get through it. 

Any help would be appreciated.
Thanks,
L.

I found it easier to use the Subversive plugin instead. See : [http://blog.punchbarrel.com/2008/06/30/using-the-new-subversion-integration-in-eclipse-ganymede/](http://blog.punchbarrel.com/2008/06/30/using-the-new-subversion-integration-in-eclipse-ganymede/) In the comments there's an approach that works on Ubuntu...

---

### Post by hoc on 2008-08-27
[B]UPDATE: I found an easier solution to the problem (described in my forum post following this one).
I'll leave this post for the more adventurous users out there. :)[/B]

> **peterdm said:**
> This is how I got JavaHL to work:

I presume you've installed Eclipse Ganymede by hand, since it's not in the Ubuntu repos. The problem comes from the fact that the subclipse plugin *requires* subversion 1.5.x installed, while Ubuntu 8.04 comes with subversino 1.4.x. So if we want it to work, we'll have to uninstall subversion from the Ubuntu repos and compile subversion ourselves.

Let's assume you have Eclipse Ganymede installed in /usr/share/eclipse, and that you're using a JDK installed in /usr/lib/jvm/java-6-openjdk.

[LIST=1]
[*]In order to be able to compile subversion, you need to make sure the following packages installed: libapr-1, libapr1-dev, libaprutil1, libaprutil1-dev
```
sudo apt-get install libapr-1 libapr1-dev libaprutil1 libaprutil1-dev
```
[*]Make sure the Ubuntu package libsvn-java is not installed, this is the one we're about to compile for ourselves in the following steps
[*]Now download the [subclipse]("http://subversion.tigris.org/downloads/subversion-1.5.1.tar.bz2") sources and untar them (e.g. in your user's home)
```
tar -xvjf subversion-1.5.1.tar.bz2
```
[*]Enter the directory, configure and build javahl (as normal user) and install (as super user)
```

cd subversion-1.5.1
./configure --enable-javahl --with-jdk=/usr/lib/jvm/java-6-openjdk/
make javahl
sudo make install-javahl

```
[*]Now the javahl libraries are installed in /usr/local/lib but you probably want them in /usr/lib/jni.
```

sudo cp /usr/local/lib/libsvnjavahl-1.* /usr/lib/jni/
sudo cp /usr/local/lib/svn-javahl/svn-javahl.jar /usr/share/java/

```
The first command has not copied the symbolic links correctly, it has replaced them by copies of the actual files. This works, but you may want fix the links.
[*]For some reason Eclipse still doesn't pick them up now, so we'll have to be a bit more persuasive. You should add a line -Djava.library.path=/usr/lib/jni to the file /usr/share/eclipse/eclipse.ini (edit as super user) after the -vmargs line
[*]Install [http://subclipse.tigris.org/update_1.4.x]("http://subclipse.tigris.org/update_1.4.x") as Eclipse update site, and install subclipse with the javahl adapter
[/LIST]

Now you should have JavaHL working in Eclipse Ganymede! Double-check by opening Window->Preferences->Team->SVN, and select JavaHL under "SVN Interface" section. It should say "JavaHL (JNI) 1.5.1..." instead of the dreaded "JavaHL(JNI) Not Available"!

Hope this helps,

Peter

Thx for the info Peter. This has worked for me with some differences:

I did one more install through apt-get, as noted by Mwiti (thx!):

```
sudo apt-get install libsvn-dev
```

As i didn't have any jni-libraries installed I had to create the jni directory before I did make install

```
sudo mkdir /usr/lib/jni
sudo make install-javahl
```

(To be complete, I actually executed the normal target instead: sudo make install, but target install-javahl should be sufficient.)

Afterwards I didn't have to edit the eclipse.ini (I actually did add this but without the desired result.), but instead create links in /usr/lib to every file in the /usr/lib/jni directory.
```
cd /usr/lib
sudo ln -s jni/libsvnjavahl-1.a
sudo ln -s jni/libsvnjavahl-1.la
sudo ln -s jni/libsvnjavahl-1.so.0.0.0
sudo ln -s libsvnjavahl-1.so.0.0.0 libsvnjavahl-1.so
sudo ln -s libsvnjavahl-1.so.0.0.0 libsvnjavahl-1.so.0
```

After the linking Subclipse picked up JavaHl.

Installed on:
Kubuntu Hardy 8.04 amd64
Eclipse 3.4 Ganymedes

---

### Post by hoc on 2008-08-29
Okok, after i ran a full 'make install' and did all the stuff mentioned above, subclipse was happy with it's javahl, but subversion had trouble accessing repositories through webdav (from commandline, etc.). I tried resolving this by recompiling subversion with the correct parameters, but without some serious changes to the makefile and compiling other libraries because of missing libraryfiles, this was impossible. Too much work and maintenance afterwards, so I just searched for the intrepid packages, as Peter rightfully suggested.

Much easier, i admit, but the packages are not yet officially declared stable, so install at your own risk. :)

So ... solution 2. Basically download relevant packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them. An alternative is to add the intrepid repository to your apt-get installation, but then you have some pinning/priority management to do, otherwise you end up with intrepid instead of hardy.

The packages you need are:

[http://packages.ubuntu.com/intrepid/libsqlite3-0](http://packages.ubuntu.com/intrepid/libsqlite3-0)
[http://packages.ubuntu.com/intrepid/libsvn1](http://packages.ubuntu.com/intrepid/libsvn1)
[http://packages.ubuntu.com/intrepid/libneon27-gnutls](http://packages.ubuntu.com/intrepid/libneon27-gnutls)
[http://packages.ubuntu.com/intrepid/libsvn-java](http://packages.ubuntu.com/intrepid/libsvn-java)
[http://packages.ubuntu.com/intrepid/subversion](http://packages.ubuntu.com/intrepid/subversion)

Download them to a separate folder, cd to the folder and run:
```
sudo dpkg -i *
```

Afterwards for subclipse to find the shared libraries you still need to create some links in /usr/lib
```
cd /usr/lib
sudo ln -s jni/libsvnjavahl-1.so.0.0.0
sudo ln -s libsvnjavahl-1.so.0.0.0 libsvnjavahl-1.so.0.0
sudo ln -s libsvnjavahl-1.so.0.0.0 libsvnjavahl-1.so.0
sudo ln -s libsvnjavahl-1.so.0.0.0 libsvnjavahl-1.so
```

Now subclipse works and the command line client as well. At least for repository-access over http.

And of course thx to the ubuntu package maintainers and to the helpfull forum people for making life a bit easier. :)

---

### Post by danigb on 2008-10-14
i've installed solution 2 at my own risk... and i've messed everything up! i could install the packages because some dependencies missing. after i could remove the installed packages and some conflicts in apt-get appeared!!

oohhohh! now i cant install svn1.5 using sourcecode because some version conflicts!! how can i remove the hand-installed deb packages and downgrade to the prev version?

thanks!!

---

### Post by peterdm on 2008-11-14
Intrepid contains the correct subversion library version 1.5.*.
So for intrepid, the solution becomes slightly easier:

1. Make sure libsvn1 and libsvn-java are installed from the repos.
2. Edit the file /usr/share/eclipse/eclipse.ini] as superuser and add a line -Djava.library.path=/usr/lib/jni after the -vmargs line.
3. Add [http://subclipse.tigris.org/update_1.4.x](http://subclipse.tigris.org/update_1.4.x) as an eclipse update site and install the plugin.
4. After eclipse restarts, you can double-check in Preferences->Team->SVN that the SVN Interface Client says "JavaHL (JNI) 1.5.*".

Peter

---

### Post by ognum on 2008-12-16
I used to have the same problem. The cause, in my case, was that I was using the subclipse 1.2 update site. When I changed to the supclipse 1.4 update site everything worked fine.

Follow the instructions on the following page:
[http://subclipse.tigris.org/install.html](http://subclipse.tigris.org/install.html)

---

### Post by kehan on 2008-12-31
I too was racking my brains - ubuntu 8.10, subclipse 1.4, ganymede, libsvn-java 1.5.1. The only other thing I needed to do was add:
-Djava.library.path=/usr/lib/jni
to eclipse.ini and hey presto working again.

---

### Post by ptvnga on 2009-02-18
Hi all 
I am new on Ubuntu Hardy...

I have to work with my laptop on ganymede with subclipse (1.4)
I have install Ubuntu Hardy cause my thinkpad got some trouble 
with intrepid (audio)

That's why I read this thread.
I install some libs :libapr ....
I dowload subversion1.5.1 
I configure it
I compile it
But unfortunately I got this error
cannot find the library `/usr/lib/libneon.la'

can you help me?
Thanks

---

### Post by kehan on 2009-02-18
I did it without compiling anything, just do the following
```
sudo apt-get install subversion libsvn-java
```Then edit eclipse.ini in your eclipse folder (mine's at ~/eclipse/eclipse.ini) and add the following line:
```
-Djava.library.path=/usr/lib/jni
```But I seem to recall that when I was using hardy (which you seem to be on) I just had to have libsvn-java installed - I didn't have to edit the eclipse.ini file at all.

---

### Post by willou on 2009-07-19
Hi 

I still have the problem with the new configuration.
Here's element of my configuraton : 

```
$ dpkg -l |grep libsvn-java
ii  libsvn-java                                1.5.4dfsg1-1ubuntu2                       Java bindings for Subversion
$ dpkg -l |grep subversion
ii  subversion                                 1.5.4dfsg1-1ubuntu2                       Advanced version control system
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
$ grep '<p>Release' ~/bin/eclipse/readme/readme_eclipse.html 
<p>Release 3.4.2<br>

```

See joined screenshots.

Thans for your support.
David «Willou»

---

