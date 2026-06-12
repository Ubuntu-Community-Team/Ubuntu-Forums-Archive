---
title: "Trouble installing programs in Ubuntu"
date: 2007-06-23
forum: General Help
---

### Post by NuNn DaDdY on 2007-06-23
I'm stuck in the windows world and cannot figure out how to install a program when I download it for linux.  After downloading I extract the files to the Desktop so I know where they are and then I bring them up in my command prompt but when I view them on there I'm unsure how to run the installation because I see no installation file to begin with.  For example I'm trying to install Jedit righ now if anyone has an idea on how to do this.  thanks

---

### Post by Keisad on 2007-06-23
Run the synaptic package manager. See if you can find what you are looking for in their.
Go to system>administration>synaptic package manager.
Click on search, mark the packages you like for installation, and then click apply. All should be well.

What you have downloaded requires you to learn how to compile a program from source. But it is much easier to find it through synaptic. Post if having trouble.

---

### Post by NuNn DaDdY on 2007-06-23
Thank you I was wondering though if I can run it with "make" or the "./" command

---

### Post by nutz on 2007-06-23
[http://www.google.com/search?q=how+to+install+anything+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+install+anything+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Maxtorm on 2007-06-23
With Jedit, you also have the option of using the deb file (I don't think it is available via the repos).  Try downloading the deb from here: [http://sourceforge.net/project/showfiles.php?group_id=588&package_id=48232](http://sourceforge.net/project/showfiles.php?group_id=588&package_id=48232)
and then double-clicking on it to invoke the package installer.

---

### Post by Keisad on 2007-06-24
Hey, that's really useful....

Thanks for the link.

---

### Post by logos34 on 2007-06-24
> **NuNn DaDdY said:**
> I'm stuck in the windows world and cannot figure out how to install a program when I download it for linux.  After downloading I extract the files to the Desktop so I know where they are and then I bring them up in my command prompt but when I view them on there I'm unsure how to run the installation because I see no installation file to begin with.  For example I'm trying to install Jedit righ now if anyone has an idea on how to do this.  thanks

Speaking in general, after you untar/extract the downloaded package and cd over to the directory, look for a file 'INSTALL.txt' or "README.txt'--that's where the install instructions should be.  Usually, though, it's simply 
[B]./configure
make
sudo make install[/B]

But either text file will have details on additional flags/options you can specify.  Be sure any dependencies are satisfied before attmepting to install.

.deb files are the easiest to install--just a couple of clicks using the deb installer.

---

### Post by jpbefx on 2007-06-24
I've been trying to install beryl for two days now, and I've found alot of different ways to do it.  Almost all of the ways tell of a .deb file to look for, I've untared the 0.2.0, and the 0.2.1 files twice now and only find the 'install sh' file.  In the install.txt, and readme.txt I don't really understand the "basic" installation sequence.  new to the Linux world any ideas? I might be missing something.  all programs I try to install using 'sudo apt-get install ...' it tells me it can't find the package.  WTH.  Thanks for the help. jpb.

---

### Post by logos34 on 2007-06-24
> **jpbefx said:**
> I've been trying to install beryl for two days now, and I've found alot of different ways to do it.  Almost all of the ways tell of a .deb file to look for, I've untared the 0.2.0, and the 0.2.1 files twice now and only find the 'install sh' file.  In the install.txt, and readme.txt I don't really understand the "basic" installation sequence.  new to the Linux world any ideas? I might be missing something.  all programs I try to install using 'sudo apt-get install ...' it tells me it can't find the package.  WTH.  Thanks for the help. jpb.

Here's the INSTALL file:

> The simplest way to compile this package is:

  1. **`cd' to the directory** containing the package's source code and type
     `**./configure**' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `**make**' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `**make install**' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

That's just a generic instructions.  You can add options if you want (read the rest).

so, open a terminal and type:

**cd /path/to/dir/aquamarine-0.2.1**  or whatever the extracted beryl folder is called
[B]
./configure
make 
sudo make install[/B]

So, they're a are .debs for this?  I didn't see any on the repos

---

### Post by jpbefx on 2007-06-24
Thank you logos for the advice I typed that cd /path/to/dir/beryl-core-0.2.0 into my terminal since the untared folder is called beryl-core-0.2.0, and it displayed this 
[COLOR="Blue"]jpbefx@jpbefx-laptop:~$ cd /path/to/dir/beryl-core-0.2.0
bash: cd: /path/to/dir/beryl-core-0.2.0: No such file or directory[/COLOR]
I feel like an idiot here am I still doing something wrong.
Thanks again

---

### Post by logos34 on 2007-06-24
> jpbefx@jpbefx-laptop:~$ cd /path/to/dir/beryl-core-0.2.0
bash: cd: /path/to/dir/beryl-core-0.2.0: No such file or directory

sorry.   'path/to/dir...' means you fill it in with your actual path.  So if you have the folder waiting in your home folder, you're already in your home folder (your're in the working directory 'jpbefx@jpbefx-laptop:~$), 'your might try simply 

cd beryl-core-0.2.0

or if its on your desktop:

cd Desktop/beryl-core-0.2.0

or if in your home dir inside 'download/eycandy', then

cd download/eyecandy/beryl-core-0.2.0

See?

---

### Post by jpbefx on 2007-06-28
cool thanks again

---

