---
title: "Compiling Issue"
date: 2007-09-10
forum: General Help
---

### Post by NuNn DaDdY on 2007-09-10
When I try to compile a c program which I have written, I try to use the gcc or g++ command.  But it appears I don't have the libraries to use such files because I recieve command not found when I try to compile the source code.  I was wondering what the apt-get command would be to download/install these files or is there another way to install these.  Thank you.

---

### Post by Andy_D on 2007-09-10
Well, for the compilers you will need to install the package called 'build-essential'
```
sudo apt-get install build-essential
```
as for any additional libraries, if it is a simpl(ish) C/C++ program you shouldn't really need anything more than that as long as you have used the '#include' preprocessor directive to include the necessary header files. I wasn't exactly sure what you meant, whether you didn't have the compilers or some of the functions in your program were not found. Please post back if my advice does not apply as I can probably still help you out!

---

### Post by smithrn on 2007-09-10
I too am having this trouble.
My 'end' state is to get PosgtreSQL configured and installed.

I did as Andy-D suggested and got a LOT farther than before.
But now I have:
E: Couldn't find package readline

Looking at the apt-get command, I didn't see an option for listing what's installed and what's 'out there' in cyberspace.

Thanks for any help!

Ralph

---

### Post by aJayRoo on 2007-09-10
Hi again (I posted previously as Andy_D because some one else logged into UF on my computer and I didn't notice before I posted)! It might be slightly off topic but while we are waiting for the OP to get back to us I might as well offer a solution for the readline problem... You simply need the readline library developer packages installed in order to compile PostgreSQL:
```
sudo apt-get install libreadline5-dev
```
That should be it, good luck!

EDIT: Sorry I think I may be confused, are you trying to install postgresql from the repositories (using synaptic or apt) or compiling it from source? Given the thread topic I assumed you were compiling, but the 'E:' and the presence of postgresql in the repos has thrown me!

---

### Post by Alex1770 on 2007-09-10
You can use Synaptic (System->Administration->Synaptic) to manipulate packages. You can see those that have been installed and others that you can install.

From the command line you can do more things. apt-cache allows you to search your local copy of the repository list for packages that you could install. E.g.,
```
apt-cache search readline
```
shows all packages with readline in their description. One of these is libreadline5-dev, which is probably the one you need (If you are compiling stuff of your own then you need -dev packages to build against.) You can read its description using
```
apt-cache show libreadline5-dev
```

apt-get installs and deinstalls packages and handles dependencies (so if you ask it to install package X and it knows that X needs package Y, then it will also install Y). apt-get and apt-cache are the command line equivalent of Synaptic (I think).

dpkg is the low-level command for dealing with packages. E.g.,
```
dpkg -l
```
lists all installed packages.
```
dpkg -p gcc
```
gives information about a specific installed package.

You can also visit [http://packages.ubuntu.com](http://packages.ubuntu.com) where you can search for any package in any recent version of Ubuntu, searching by title or searching by contents (so you name a file and it tells you which packages contain that file).

---

### Post by smithrn on 2007-09-10
I'm back!

Thanks for that info on the package, and the URL.  I got farther along.
What I'm trying to do:
I've taken the source code from postgresql.org and I'm ./configue ing it.

I ran into another error.  I did go to packages.ubuntu.com and did
apt-cache search zlib
and found I do have zlib1g and zlib1g-dev installed.  (Probably no surprise to you.)
From their description it LOOKS like what postgres is looking for, but not named so.

====
Below is contents of config.log (even the reference to look in the config.log)
====
smithrn@smithrn-ltb1:~/Desktop/postgresql-7.4.17$ cat config.log | grep zlib
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu

configure:6166: error: zlib library not found
If you have zlib already installed, see config.log for details on the
Use --without-zlib to disable zlib support.
====
The ./configure I used was a subset of what's above.  I tried modifying my ./configure
to use --with-system-zlib1g and just received the same error.

Is that lib in a different location than 'normal'?
Or better, do you know where is the header and where is the library itself?

Thank you very much.  I'm not a library kind of guy.  I script like hell, but not this stuff!

Ralph

---

### Post by Alex1770 on 2007-09-11
> **smithrn said:**
> I'm back!

Thanks for that info on the package, and the URL.  I got farther along.
What I'm trying to do:
I've taken the source code from postgresql.org and I'm ./configue ing it.

I ran into another error.  I did go to packages.ubuntu.com and did
apt-cache search zlib
and found I do have zlib1g and zlib1g-dev installed.  (Probably no surprise to you.)
From their description it LOOKS like what postgres is looking for, but not named so.

...

Ralph

"apt-cache search" checks for things you could install; it doesn't check what is installed. So you may not have the relevant zlib packages. To see whether you do, you could use synaptic from the desktop, or if you prefer the command-line you could type
```
dpkg -l '*zlib*'
```
and look at the letters (ii or un or ...) in the left column.

By the way, I suppose you know you can install postgresql immediately as a package? (In synaptic go to postgresql-8.1 or postgresql-8.2 depending on your version of Ubuntu.) Or maybe there is a reason you need to compile your own version.

---

