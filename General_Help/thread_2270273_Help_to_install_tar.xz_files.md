---
title: "Help to install tar.xz files"
date: 2015-03-21
forum: General Help
---

### Post by gabmuks on 2015-03-21
Am having trouble finding any info on installing taz.xz files.

I have Googled for an hour but can only find how to extract the file,

but doesn't say how to install.

Extracting seems easy enough using Archive Manager.

 Is that correct? If so, I have already extracted the file with Archive manager.

Does anyone here know of instructions on how to install extracted files?

Thanks for your time.

---

### Post by Lars Noodén on 2015-03-21
Tarballs usually have a file called "README" or "INSTALL" which contain the instructions.  The exact details vary greatly from program to program.  Usually the method is unique to that particular tarball.  Which package are you trying to install and where did you find it?

However, using a tarball is the hardest way to deal with a program and the way that is most likely to cause trouble.  The best possible option is to find the program in the official repository using either Synaptic or the Software Center.  The next best option would be a PPA.

---

### Post by gabmuks on 2015-03-21
> **Lars Noodén said:**
> Tarballs usually have a file called "README" or "INSTALL" which contain the instructions.  The exact details vary greatly from program to program.  Usually the method is unique to that particular tarball.  Which package are you trying to install and where did you find it?

However, using a tarball is the hardest way to deal with a program and the way that is most likely to cause trouble.  The best possible option is to find the program in the official repository using either Synaptic or the Software Center.  The next best option would be a PPA.

Thanks for reply.

Downloaded the tarball from Source Forge website.

It's just a game.

I have the game installed from Software Center already.
But it is not complete or up to date.

Guess your right. I read the readme file and even though
it gave no installation instructions, they made it sound like you're on your own
as far as this game usage. So I will mark thread solved. Thanks.

---

### Post by flaymond on 2015-03-21
Sorry, but can you give me the link of the site, please? Maybe I could try to install it, and I will post the steps in here if you want.

---

### Post by Lars Noodén on 2015-03-22
> **gabmuks said:**
> I have the game installed from Software Center already.
But it is not complete or up to date.

Then there's a fourth option.  If the versions are close enough, you can download the source package for the game using apt-get and then drop in the new source code and make a new, local package.  And install that instead.  Then you still get all the benefits of using the package manager yet have the latest version.  There are instructions for that and though they are a bit long they are not terribly hard -- the second time.

---

### Post by gabmuks on 2015-03-22
> **InterProg said:**
> Sorry, but can you give me the link of the site, please? Maybe I could try to install it, and I will post the steps in here if you want.

Here is link to Source Forge Website.  [http://sourceforge.net/projects/warzone2100/?source=directory](http://sourceforge.net/projects/warzone2100/?source=directory)

Name of game tarball is Warzone2100-3.1.2tar.xz.

Thank you

> **Lars Noodén said:**
> Then there's a fourth option.  If the versions are close enough, you can download the source package for the game using apt-get and then drop in the new source code and make a new, local package.  And install that instead.  Then you still get all the benefits of using the package manager yet have the latest version.  There are instructions for that and though they are a bit long they are not terribly hard -- the second time.

Thanks. Do you have link to those instructions?

---

### Post by Lars Noodén on 2015-03-22
You can get the code for 3.1rc2 from the repository

```

$ cd /tmp
$ apt-get source warzone2100

```

and then try dropping in the code from version 3.1.2

There aren't really any good guides (that I know of) about how to do that any more.  But here are some slides which give an overview. 

[https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf](https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf)

Sorry for the PDF.

There are also these:

[https://www.debian-administration.org/article/336/Rolling_your_own_Debian_packages_part_1](https://www.debian-administration.org/article/336/Rolling_your_own_Debian_packages_part_1)
[https://www.debian-administration.org/article/337/Rolling_your_own_Debian_packages_part_2](https://www.debian-administration.org/article/337/Rolling_your_own_Debian_packages_part_2)

Note that you'll have to read through and skip some steps, or parts of steps, because it is already packaged, you are just updating versions.

---

### Post by gabmuks on 2015-03-23
> **Lars Noodén said:**
> You can get the code for 3.1rc2 from the repository

```

$ cd /tmp
$ apt-get source warzone2100

```

and then try dropping in the code from version 3.1.2

There aren't really any good guides (that I know of) about how to do that any more.  But here are some slides which give an overview. 

[https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf](https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf)

Sorry for the PDF.

There are also these:

[https://www.debian-administration.org/article/336/Rolling_your_own_Debian_packages_part_1](https://www.debian-administration.org/article/336/Rolling_your_own_Debian_packages_part_1)
[https://www.debian-administration.org/article/337/Rolling_your_own_Debian_packages_part_2](https://www.debian-administration.org/article/337/Rolling_your_own_Debian_packages_part_2)

Note that you'll have to read through and skip some steps, or parts of steps, because it is already packaged, you are just updating versions.

Well I got all the way through the "$ ./configure" command, but then I put in "make" command and got this....  make: *** No targets specified and no makefile found.  Stop.

Any ideas?

---

### Post by anaconda on 2015-03-23
Just installed warzone from the .tar.xz file which you gave the link to.

Pretty standard.
Here is what I did step by step:

1. Extracted the tar.xz to a folder with "Archive Manager"

2. Went to the folder and ran "./configure"

3. configure didn't finish, because I hadn't installed required dependencies ...  installed everything that the ./configure complained about:  theora, qt4, fribidi, physfs, glew, openal. After installing those .configure finished  
(If you already had installed the version that is in the repos you propably already had all of them already installed..)


4.  ran "make"
and finally
5.  ran  "sudo make install"

That was all. "Warzone 2100" appeared to the games -menu and it works, (I am running xfce)


PS Dont know why the "make" didnt work for you.  Have you installed "build-essential" -packkage?, and are you sure the ./configure finished succesfully?

---

