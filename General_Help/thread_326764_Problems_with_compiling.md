---
title: "Problems with compiling"
date: 2006-12-28
forum: General Help
---

### Post by rogerdrange on 2006-12-28
Hello! I have a huge problem with compiling.

> 
checking for gtk-config... no
checking for GTK - version >= 1.2.6... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK2 failed. See the file 'INSTALL' for help.


But I tought that I had gtk installed? I am a bit new to ubuntu, so I don't know what to do. Can anybody please help me? 

Happy New Year!

---

### Post by xopher on 2006-12-28
You might have gtk installed yes, but for compiling you need the -dev versions of the applications.

The easiest way to get build dependencies for a program is to enable deb-src's in /etc/apt/sources.list and do a:

```
sudo apt-get build-dep appname
```

---

### Post by scrooge_74 on 2006-12-28
> **xopher said:**
> You might have gtk installed yes, but for compiling you need the -dev versions of the applications.

The easiest way to get build dependencies for a program is to enable deb-src's in /etc/apt/sources.list and do a:

```
sudo apt-get build-dep appname
```

Xopher is probably right, the package you have install is for using the program, but the .dev version is for development or in this case for  compiling stuff

---

### Post by rogerdrange on 2006-12-28
> **xopher said:**
> You might have gtk installed yes, but for compiling you need the -dev versions of the applications.

The easiest way to get build dependencies for a program is to enable deb-src's in /etc/apt/sources.list and do a:

```
sudo apt-get build-dep appname
```

Thank you! I am sorry for my stupidity, but exactly what sources shall I add? I've tried to search a bit around, but can't find anything...

---

### Post by shrimphead on 2006-12-28
there should be a tickbox in the Synaptic options page that enables source repositories.

either that or edit your sources.list using
```
sudo gedit /etc/apt/sources.list
```
and uncomment (remove the # from the beginning of the line) any line that has deb-src in it.

then you can issue the command sudo apt-get build-dep appname as xopher mentioned. 

this will automatically install everything you need to compile that particular application yourself.


BTW have you installed build-essential too?

EDIT: check this link for details about your sources.list
[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)
but bear in mind that that is meant for breezy and not edgy

---

### Post by rogerdrange on 2006-12-28
Okay. Say that I for excample am going to install dguitar.

I will then type:
> 
sudo apt-get build-deb dguitar


But when thats done, what shall I do next? When I using the comfigure file, the same message as I wrote in my first post in this thread appears. 

Thanks to everyone that have tried to help me!

---

### Post by scrooge_74 on 2006-12-29
When you install those packages try compiling again, if it then says you need something else you  will have to install those other packages also

As an example I was using the open source nvidia drivers, but now I decided to try a few games that need 3D acceleration.

So I had to follow instructions to change drivers and I have to install a few packages needed.

The other day I was compiling brutalchess a game I saw here at the forum, and I had to install a couple of packages in order to be able to compile the game correctly..

---

### Post by mohdridha on 2006-12-31
Ok, i might have similar case with roger. and Sorry for hijacking your thread :)

I tried to install gkrellm on my Dapper. 

When i type
```
 apt-get install gkrellm 
```

The gkrellm installed without a problem. But when i try to install another version like GKrellMEris
at [http://starforge.co.uk/gkrellm/gkrellmeris.shtml](http://starforge.co.uk/gkrellm/gkrellmeris.shtml), I got the same error message as Roger have. What i have tried was download the tarball of the application, and extract it. When i type 'make' it said that cant find GTK+2.. 

By reading to earlier post on this thread, it seems that i apt-get build-dep <package name> might be the solution. But in my case, what name should i put on the <package name>?
Is it

apt-get build-dep GKrellMEris
or
apt-get build-dep GTK+2

and how if i want to install and configure GTK+2 manually?

---

