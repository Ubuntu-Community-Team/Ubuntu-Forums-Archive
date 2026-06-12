---
title: "Uninstall a app compiled from source"
date: 2023-06-11
forum: General Help
---

### Post by a-k-i-r-a on 2023-06-11
Hello everyone o/

I've complied an application from source for the first time, so i would appreciate some help on how to reverse the alterations made. Google says that is only a matter of reversing the steps returned by the following command:
```
make -n install
``` 
Which i already have in a convenient text file. But, my issue is i'm having trouble to understand these commands. Here are the first lines of the text file:
```
for d in libsent libjulius julius mkbingram mkbinhmm adinrec adintool mkgshmm mkss jcontrol gramtools generate-ngram jclient-perl man; do \
  (cd $d; make install); \
done
make[1]: Entering directory '/home/pedro/julius/julius-4.3.1/libsent'
/usr/bin/install -c -d /usr/local/lib
/usr/bin/install -c -m 644 libsent.a /usr/local/lib
/usr/bin/install -c -d /usr/local/include/sent
/usr/bin/install -c -m 644 include/sent/*.h /usr/local/include/sent
/usr/bin/install -c -d /usr/local/bin
/usr/bin/install -c libsent-config-dist /usr/local/bin/libsent-config
make[1]: Leaving directory '/home/pedro/julius/julius-4.3.1/libsent'
make[1]: Entering directory '/home/pedro/julius/julius-4.3.1/libjulius'
```
So if a go to /usr/local/bin for example there is no file (apparently) related to the app itself. But under ~/julius/lib the file libsent.a is there. i don't understand exactly how any substitution taked place in this case, i indeed forced the app to be compiled on ~/julius but the steps returned by make -n install are not making sense to me. Can i just delete the entire ~/julius folder or is not that simple?

---

### Post by ajgreeny on 2023-06-12
Have you searched the folder containing all the source code files?

I believe there is often some help there, either in the form of an uninstall script, or maybe as a **readme** file with all instructions of installing and uninstalling.

Your problem is, I think, a very good reason for you to check out the use of ***checkinstall*** when you get to that point in a source installation; this means a .deb package is created in the source folder and used for the installation and apt commands can be used to uninstall that package.

---

### Post by a-k-i-r-a on 2023-06-14
Sadly no, there is no sign of how to manually uninstall the app in the readme file or in the other source code files. i guess i should have used checkinstall to create a package, at least i know that now XD

---

### Post by philhughes on 2023-06-14
Disclaimer: I am not at all familiar with the use of make, so anything you do is at your own risk :) However, I have used make to install and uninstall a network driver before it was supported by the kernel, by following instructions supplied with the driver.

I think you can remove the software by running the command you originally used to install the software with, but instead of using "install", you use "clean". However, I think this depends upon the software's Makefile including "clean" as a target.

So for example, if you installed the software with

```
make -C src/ install
```

you would run

```
make -C src/ clean
```

From the make manual page, using the -n option does a dry-run, so you should first do:

```
make -n -C src /clean
```

and closely examine what it is going to do.

Reading the Makefile may give you some further clues. Good luck.

---

### Post by MAFoElffen on 2023-06-14
Try
```

make uninstall
# or if installed as root, then
sudo make uninstall

```
If that does not work, then do
```

make -n install

```
Which will do a dry run. listing the steps, which you will need to reverse.

Last ditch effort, delete the executable and do
```

make clean

```
Did you know that 'julius' has a deb package in the Ubuntu repo's?

EDIT-- Sniped with same answer. LOL

---

### Post by TheFu on 2023-06-14
So, if you manually compile and install the files for a program, then I'd look for a de-install guide.  If one doesn't exist, I'd reverse the install steps manually.

I know make (gnumake).  There's usually an install (i.e. **make install**) target.

**make clean** and **make cleanall** are common targets too, but those wouldn't touch any files that were "installed". They would clean up old libraries and objects and perhaps preprocessor files from the make process.

From the output above, seems like the **make install** target placed the files under /usr/local/  which is a best practice.  If you don't have any other manually installed files there, you could just remove everything under /usr/local/* ... be certain you check every file under there first.  The **make install** has a list of files it copied under /usr/local/, so you know those need to be removed.

Heck, it took me longer to write this post than it would to look at the makefile, get the list of files and remove them.

---

### Post by MAFoElffen on 2023-06-14
Oh dang. I checked the site, github, sourceforge, etc. I didn't see any uninstall script. I too didn't get a clear picture of things from the make -n ouput... So I downloaded the .deb package and looked where it installs what, and where:
```

/usr/bin/
 |_ accept_check
 |_ adinrec
 |_ adintool
 |_ dfa_determinize
 |_ dfa_minimize
 |_ jclient
 |_ jcontrol
 |_ julius
 |_ julius-generate
 |_ julius-generate-ngram
 |_ mkbingram
 |_ mkbinhmm
 |_ mkbinhmmlist
 |_ mkfa
 |_ mkgshmm
 |_ mkss
 |_ nextword
 |_ yomi2voca

/usr/share/doc/julius/
 |_ examples
  |_ gram2sapixml.gz
  |_Sample.jconf.gz
 |_ changelog.Debian.gz
 |_ copyright
 |_ README.gz

/usr/share/man/man1/
 |_accept_check.1.gz
 |_ adinrec.1.gz
 |_ adintool.1.gz
 |_ dfa_determinize.1.gz
 |_ jclient.1.gz
 |_ jcontrol.1.gz
 |_ julius.1.gz
 |_ julius-generate.1.gz
 |_ julius-generate-ngram.1.gz
 |_ mkbingram.1.gz
 |_ mkbinhmm.1.gz
 |_ mkbinhmmlist.1.gz
 |_ mkdfa.1.gz
 |_ mkss.1.gz
 |_ nextword.1.gz

```
I hope that helps...

---

### Post by a-k-i-r-a on 2023-06-14
Thank you everyone for the replies, i had tried 'make uninstall' before and it failed. So i looked the directories manually to see if there was any sign of the app files and didn't find anything. i just installed the package using apt as mentioned above and deleted the folder containing the manually compiled files. julius is working normally now :)

---

