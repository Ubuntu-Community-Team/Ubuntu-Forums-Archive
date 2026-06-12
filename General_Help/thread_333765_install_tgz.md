---
title: "install tgz"
date: 2007-01-07
forum: General Help
---

### Post by kievking on 2007-01-07
I want to install qgeo in Edgy, the National Geographic interactive viewer. I followed the installation instructions and got an Error 127 message after entering the make command. Has anyone installed this 7 year old program?

---

### Post by po0f on 2007-01-07
kievking,

Error output would be nice.  I don't feel like googling what error 127 is; and even if I did, I'd still like to see your error output.  The last 10 lines or so should be fine.  It just makes it easier to help you.  :)

---

### Post by kievking on 2007-01-08
I should have been more specific. The following info is from the Install instructions:

[I]This is a brief description on how to install QGEO, I will assume
that you use SuSE 6.x Linux, and mention the basic requirements.

Install the development tools, including qt1.44 libs and devel
packages. In addition to just Qt, you will also require tmake
available from ftp.troll.no

unpack the source archive with "tar -zxf qgeo-0.0.1.tgz
then run the following commands ..

   make clean
   make
   su -c "make install"
[/I]

I googled qtl.44 and got zero results. I think I already have qt3, and I installed tmake.

Here's the make clean output:

[I]/usr/local/tmake/bin/tmake -o qgeo.make qgeo.pro
make: /usr/local/tmake/bin/tmake: Command not found
make: *** [qgeo.make] Error 127
[/I]

There is no tmake directory in /usr/local?

I've installed recently written tarballs without any major snags. Unfortunately, this program was last updated in Jan 2000. Is there any hope..........Thanks.

---

### Post by taurus on 2007-01-08
What if you link tmake to make?

```
sudo ln -s /usr/bin/make  /usr/bin/tmake
```

---

### Post by kievking on 2007-01-08
> **taurus said:**
> What if you link tmake to make?

```
sudo ln -s /usr/bin/make  /usr/bin/tmake
```

Thanks.. I entered that command with no luck. Here's the output:

*ln: creating symbolic link `/usr/bin/tmake' to `/usr/bin/make': File exists*

---

### Post by taurus on 2007-01-08
> **kievking said:**
> Thanks.. I entered that command with no luck. Here's the output:

*ln: creating symbolic link `/usr/bin/tmake' to `/usr/bin/make': File exists*

Can you also paste the actual command that you ran to get that output from above?

---

### Post by po0f on 2007-01-08
kievking,

Do you have [tmake](http://packages.ubuntu.com/edgy/devel/tmake) installed?  If not, install it.  If so, create a symlink to where the installer thinks it is and where it actually is:
```
[FONT="Courier New"]$ sudo ln -s /usr/bin/tmake /usr/local/tmake/bin/tmake[/FONT]
```

(Notice in the error where it looks for the `tmake` command.)

If this works for you, I don't know if you'll be able to build this anyway.  I'm sure a lot has changed coming from Qt 1.33 to Qt 3.x (at least, I hope a lot has changed).  It's not unusual for library APIs to be broken between major releases, and here you're looking at two major version from the one qgeo wants.

---

### Post by kievking on 2007-01-09
> **po0f said:**
> kievking,

Do you have [tmake](http://packages.ubuntu.com/edgy/devel/tmake) installed?  If not, install it.  If so, create a symlink to where the installer thinks it is and where it actually is:
```
[FONT="Courier New"]$ sudo ln -s /usr/bin/tmake /usr/local/tmake/bin/tmake[/FONT]
```

(Notice in the error where it looks for the `tmake` command.)

 
command output:
 [I]sudo ln -s /usr/bin/tmake /usr/local/tmake/bin/tmake
ln: creating symbolic link `/usr/local/tmake/bin/tmake' to `/usr/bin/tmake': No such file or directory[/I]

tmake is installed:

[I]whereis tmake
tmake: /usr/bin/tmake /etc/tmake /usr/X11R6/bin/tmake /usr/bin/X11/tmake /usr/share/tmake /usr/share/man/man1/tmake.1.gz

[/I]

Thanks - - - gqview actually displays the NG thumbnails and pages very nicely, but I would
like to have the search tool as well without having to use the NG website.

---

### Post by kievking on 2007-01-09
> **taurus said:**
> Can you also paste the actual command that you ran to get that output from above?

[I]sudo ln -s /usr/bin/make  /usr/bin/tmake
ln: creating symbolic link `/usr/bin/tmake' to `/usr/bin/make': File exists[/I]

Thanks

---

### Post by Topsiho on 2007-01-09
The latest version number is 0.0.2, and is released in 2000, almost 7 years ago. On the site of National Geographic is stated that "this product is no longer available". So I am afraid that this ducky is dead and buried. I can see that you'll be very disappointed with this.

Only thing I may suggest (unwisely) is installing a Linuxversion which was current in 2000, and installing this app on that.

Problem of course is that using such an old Linux version on the internet of today is not advisable at all. But on a standalone computer, away from the internet, why not?

Topsiho

---

### Post by kievking on 2007-01-09
> **Topsiho said:**
> 
Only thing I may suggest (unwisely) is installing a Linuxversion which was current in 2000, and installing this app on that.

Problem of course is that using such an old Linux version on the internet of today is not advisable at all. But on a standalone computer, away from the internet, why not?

Topsiho

Good Idea. I have an empty partition on my laptop and one on my desktop. It might be
fun to play with an old distro.

---

