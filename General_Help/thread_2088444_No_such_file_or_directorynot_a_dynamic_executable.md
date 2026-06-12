---
title: "No such file or directory/not a dynamic executable"
date: 2012-11-26
forum: General Help
---

### Post by HeidiJTP on 2012-11-26
Hi, I would appreciate some help with getting the program meme ([ftp://ftp.ebi.edu.au/pub/software/MEME/](ftp://ftp.ebi.edu.au/pub/software/MEME/)) working on 32-bit Ubuntu 11.10. For the record, I have been able to get it working on 64-bit Ubuntu, so it's likely an issue between 32 vs 64.

When I try to run the program, I get the message:

$ meme
/meme/etc/meme.doc: No such file or directory


The file is present, I checked the permissions and for required libraries:

$ ls -l
-rwxrwxrwx 1 root root    1273 2012-11-26 12:22 meme

$ file meme
meme: C shell script text executable

$ ldd meme
    not a dynamic executable

I understand that there is a fix available for this problem when using a 64-bit program on a 32-bit machine . It looks like I have the opposite (program works on 64-bit but not 32-bit machine). Is there a simple fix for this?

Thanks!

---

### Post by papibe on 2012-11-26
Hi HeidiJTP. Welcome to the forums ):P

I'm not familiar with the program you are trying to run, but according to this:
> **HeidiJTP said:**
> $ file meme
meme: C shell script text executable
it is a C shell script, that is, an text file with instructions for an interpreter called 'csh'.

You can confirm this by seeing the content of the file on a regular text editor, or just checking the first lines by running:
```
head meme
```
The file should start with this line:
```
#!/bin/csh
```
Ubuntu uses bash as default shell, and 'csh' is not installed by default.

If you want to install it, do this:
```
sudo apt-get install csh
```
After that you will be able to run the script by either doing this:
```
./meme
```
or this:
```
csh ./meme
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by HeidiJTP on 2012-11-26
papibe,

Thanks for the suggestion, you're definitely right about the csh pre-requisite - however, that was an error that I had already gone through. When I originally tried to run meme, I had the message:
bash: /home/heidi/meme/bin/meme: /bin/csh: bad interpreter: No such file or directory

I already performed 
sudo apt-get install csh
This took of the bad interpreter error, but now I get the errors detailed in my initial post.

I tried running the command as:
csh ./meme
However, I still am told "No such file or directory"

---

### Post by HeidiJTP on 2012-11-26
I think it is maybe having trouble finding a file with the same name but another extension:
/meme/etc/meme.doc: No such file or directory

meme.doc is a separate file than the executable (meme)

The executable meme is in /home/meme/bin
The meme.doc is in /home/meme/etc

I checked the code in meme and found the following regarding meme.doc:
[INDENT]# Describe MEME and its output format:
usage:
set usage = /meme/etc/meme.doc
tty -s                        # see if stdin is a terminal
if ($status == 0) then
  more $usage
else
  cat $usage
endif
goto cleanup
[/INDENT]
I'm not sure why it needs to even locate meme.doc - it's just a document explaining the usage, options, and examples.

---

### Post by pkadeel on 2012-11-26
> **HeidiJTP said:**
> I understand that there is a fix available for this problem when using a 64-bit program on a 32-bit machine . It looks like I have the opposite (program works on 64-bit but not 32-bit machine). Is there a simple fix for this?

Thanks!
32bit application can be run on 64bit OS but I don't think there will be a fix or something like that to run a 64bit application on a 32bit OS because you can put a small bowl inside a bigger bowl but not the other way round.

---

### Post by steeldriver on 2012-11-26
How did you build / install meme?

I just managed to get it to build and run on a 32-bit machine, from the gzipped tarball in the link you provided, using the instructions in the included INSTALL file [there was 1 unmet dependency not detected by the ./configure (zlib.h) which went away after I installed the zlib development package]

Were you able to run the post-install tests ('make test') successfully?

It seems to need that doc file in order to print the usage message - I initially just did a 'make' not a 'make install' and I got the same error although since I configured with

```
./configure --prefix=$HOME/meme --with-url="http://meme.nbcr.net/meme"
```it looks in my home dir not /etc:

```
./scripts/meme
/home/steeldriver/meme/etc/meme.doc: No such file or directory
```That went away after I did the 'make install' - so I wonder whether the prefix got screwed up in your case? (maybe a different prefix used for the make versus install stages?)

---

### Post by HeidiJTP on 2012-11-26
> **pkadeel said:**
> 32bit application can be run on 64bit OS but I don't think there will be a fix or something like that to run a 64bit application on a 32bit OS because you can put a small bowl inside a bigger bowl but not the other way round.

Thanks pkadeel. I'm not certain that it was a 64-bit application because it was not specified, so I hoped it would work with 32 or 64 (probably not a safe assumption, I'm not very experienced with this!). 

What you're saying makes sense, although I see someone else has suggested a problem with the prefix configuration step. I'll look into that before I scrap the idea of using it on the 32-bit OS.

---

### Post by HeidiJTP on 2012-11-26
steeldriver,

I also installed the zlib package. I uninstalled meme and then went back and redid everything with no error messages and successful post-install tests:

[INDENT]$ sudo make uninstall
$ sudo ./configure --prefix=$HOME/meme --with-url=http://meme.nbcr.net/meme
$ sudo make
$ make test
$ sudo make install
$ export PATH=/home/hpagan/meme/bin:$PATH
$ sudo chmod 777 -R /home/hpagan/meme
[/INDENT]
I still have the error message:
/meme/etc/meme.doc: No such file or directory

---

### Post by steeldriver on 2012-11-26
**[B]EDIT: **[/B]I think that sudo / chmod is unnecessary (since you are installing everything within your home dir) and **might** cause some problems - **however** I have just redone everything, using 'sudo' everywhere like you did - and it still works for me... sorry I am out of ideas :(

---

### Post by steeldriver on 2012-11-26
unless... one more thought: is it possible your $HOME variable is not set when you do the ./configure? that might explain why the error says

```
[COLOR=Red]**/**[/COLOR]meme/etc/meme.doc: No such file or directory 	
```

instead of

```
[COLOR=Red]**/home/hpagan/**[/COLOR]meme/etc/meme.doc: No such file or directory
```

which is where it *should* be looking given that ./configure prefix, I think...

---

### Post by mc4man on 2012-11-26
> **HeidiJTP said:**
> I think it is maybe having trouble finding a file with the same name but another extension:
/meme/etc/meme.doc: No such file or directory

meme.doc is a separate file than the executable (meme)

The executable meme is in /home/meme/bin
The meme.doc is in /home/meme/etc

I checked the code in meme and found the following regarding meme.doc:
[INDENT]# Describe MEME and its output format:
usage:
set usage = /meme/etc/meme.doc
tty -s                        # see if stdin is a terminal
if ($status == 0) then
  more $usage
else
  cat $usage
endif
goto cleanup
[/INDENT]
I'm not sure why it needs to even locate meme.doc - it's just a document explaining the usage, options, and examples.
Try altering the meme script to point to actual location, maybe as shown in post 10, ie.,
set usage = /home/hpagan/meme/etc/meme.doc

---

### Post by HeidiJTP on 2012-11-27
> **mc4man said:**
> Try altering the meme script to point to actual location, maybe as shown in post 10, ie.,
set usage = /home/hpagan/meme/etc/meme.doc


steeldriver and mc4man, you're both geniuses!

Works perfectly now after changing the set usage line as well as another line for the bin folder in the meme script.

Thanks to everyone who responded, I greatly appreciate the help!!

---

