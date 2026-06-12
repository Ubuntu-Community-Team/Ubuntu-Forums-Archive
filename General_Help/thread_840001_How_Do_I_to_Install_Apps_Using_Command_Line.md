---
title: "How Do I to Install Apps Using Command Line"
date: 2008-06-25
forum: General Help
---

### Post by jaydub868 on 2008-06-25
I want to install the xawtv television viewing application, but not from add/remove.  I downloaded the relevant tar.gz file from the site that hosts it, decompressed it, and the contents are currently sitting on my desktop (/home/jon/Desktop) in the default folder named "xawtv-3.95" which contains 16 subfolders and 323 files. 

The install instructions from the ReadMe file read verbatim (in bold):

[B]	$ ./configure [ options ]
	$ make

should compile xawtv, v4l-conf, fbtv and a few other utilities.  You can
also simply type "make" if you don't want to pass any options to
configure.

You can install the programs (as root) with:

	# make install[/B]

So my question is, how do I pull this off?  I know how to get to the terminal window, but that's about it.

Any help would be really appreciated.

---

### Post by badfish591 on 2008-06-25
well first you have to get build-essentials so in terminal run
```
sudo apt-get install build-essentials [enter]
```
then cd into the folder that you have downloaded.
and then run those commands you saw in the readme i would do it like this
```
./configure [enter] and wait
make && make install [enter] root password [enter] and wait
```

---

### Post by DirtDawg on 2008-06-25
There is a great guide called [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing"). It is perfect for just such occasion.

EDIT: Being new at compiling, you should be warned that you will likely get a lot of errors. Usually, the errors are basically telling you what packages you need to install. But it can be frustrating if you are inexperienced at deciphering the errors.

---

### Post by jaydub868 on 2008-06-25
OK, so I tried badfish's instructions, and I get two errors:

[B]jon@ubuntu:~$ sudo apt-get install build-essentials
[sudo] password for jon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
jon@ubuntu:~$ cd /home/jon/Desktop/xawtv-3.95
jon@ubuntu:~/Desktop/xawtv-3.95$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
jon@ubuntu:~/Desktop/xawtv-3.95$ [/B]

And so it begins.  Any suggestions?

---

### Post by kevdog on 2008-06-25
To add to the post above:

sudo aptitude install build-essential linux-headers-`uname -r`

That will install prerequisite packages so you can install

cd ~/Desktop/xawtv-3.95
./configure
make
sudo make install

Executable should be located within /usr/local/bin

---

### Post by badfish591 on 2008-06-25
oops i ment to type 

```
sudo apt-get install build-essential
```
there is no "s" on the end of that package......heh

---

### Post by jaydub868 on 2008-06-25
Well, we're half way there, kevdog.  The first part works.  Using the code:

**sudo aptitude install build-essential linux-headers-`uname -r`**

seems to work fine.  It sets up a bunch of stuff, taking about a minute to do so.  However, the ./configure part fails, as follows:

[B]jon@ubuntu:~/Desktop/xawtv-3.95$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/B]

So what now?

---

### Post by kuja on 2008-06-25
Try looking here: [http://ubuntuforums.org/showthread.php?t=17033](http://ubuntuforums.org/showthread.php?t=17033)

It seems to be a solution to "C compiler cannot create executables" Problem

---

### Post by cariboo on 2008-06-25
Use Tvtime it's a much better app:)

Jim

---

### Post by badfish591 on 2008-06-25
> **jaydub868 said:**
> Well, we're half way there, kevdog.  The first part works.  Using the code:

**sudo aptitude install build-essential linux-headers-`uname -r`**

seems to work fine.  It sets up a bunch of stuff, taking about a minute to do so.  However, the ./configure part fails, as follows:

[B]jon@ubuntu:~/Desktop/xawtv-3.95$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/B]

So what now?

you might be able to skip the ./configure command and just run 
```
make && make install
```
and just get the standard install.

---

