---
title: "in over my head i was told"
date: 2007-05-12
forum: General Help
---

### Post by collieman on 2007-05-12
Just an update .  I posted a question on how to install the program "XnView" here in the forum.  I got some help but nothing worked.  Been reading and trying for 3 weeks now with no success.  So I went to the Linux shop today where I bought my Ubuntu CD hoping that they could give me a demo on to install software in Linux.  They told me I was in over my head trying to install .rpm's in a Dedian system.   Since XnView is an .rpm I couldn't install it in a Debian system without a lot of difficulty.  They told me NOT to download .rpm's for Ubuntu just stick with what's available or get .deb's.  They  also said NOT to use Alien or Red Hat package manager as it leads to more problems.  They said they could install it for me at a price by compiling the source or something like that but it surely wouldn't be worth it and to use Picasa instead of XnView.   They also said not to use NDISwrapper just use what's on the list of supported hardware for Ubuntu.  I tried hard.  Did a lot of reading.  I have Ubuntu installed.  Wireless works.  Got a good MP3 player installed...XMMS.  I think it sounds better than Win AMP.  So maybe the shop was right in telling me to be happy with Ubuntu the way it is even though it's not even close to what I have in XP.  So to the guys that gave me some help I thank you.  All I can say is you guys have to be pretty damn smart  to learn this Linux.    Collieman

---

### Post by jfinkels on 2007-05-12
> **collieman said:**
> Just an update .  I posted a question on how to install the program "XnView" here in the forum.  I got some help but nothing worked.  Been reading and trying for 3 weeks now with no success.  So I went to the Linux shop today where I bought my Ubuntu CD hoping that they could give me a demo on to install software in Linux.  They told me I was in over my head trying to install .rpm's in a Dedian system.   Since XnView is an .rpm I couldn't install it in a Debian system without a lot of difficulty.  They told me NOT to download .rpm's for Ubuntu just stick with what's available or get .deb's.  They  also said NOT to use Alien or Red Hat package manager as it leads to more problems.  They said they could install it for me at a price by compiling the source or something like that but it surely wouldn't be worth it and to use Picasa instead of XnView.   They also said not to use NDISwrapper just use what's on the list of supported hardware for Ubuntu.  I tried hard.  Did a lot of reading.  I have Ubuntu installed.  Wireless works.  Got a good MP3 player installed...XMMS.  I think it sounds better than Win AMP.  So maybe the shop was right in telling me to be happy with Ubuntu the way it is even though it's not even close to what I have in XP.  So to the guys that gave me some help I thank you.  All I can say is you guys have to be pretty damn smart  to learn this Linux.    Collieman

See here for more info on installing: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

I looked for XnView to see if I could help you out.

I tried to convert the RPMs on this page Download the Linux x86 TAR GZ version of XnView from their website here: [http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html](http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html) using alien, but that just wasn't meant to be (lots of errors):
```

error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
chmod: invalid option -- /
Try `chmod --help' for more information.
error: open of <html> failed: No such file or directory
error: open of <html> failed: No such file or directory
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'

```

 I also tried to download the source, but extracting it with tar gives this error:
```

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

It looks like whoever made these packages made them poorly.

These errors are very unusual. I'm afraid this isn't going to work for you. I advise you to look through Synaptic (System > Administration > Synaptic Package Manager) for some other image managers. Avoid installing software that can't be installed using Synaptic! If you absolutely must have this program, I suppose you could try to install wine and download their Windows version...but that seems like a lot of extra work.

Use Synaptic to install software first before trying anything else!

---

### Post by Subban on 2007-05-12
I had installed Xnview from an alien converted rpm on dapper, so just had another look at it and it worked just dandy on Feisty too.

Download the RPM
[http://download.xnview.com/XnView-static-fc4.i386.rpm]("http://download.xnview.com/XnView-static-fc4.i386.rpm")

```
sudo apt-get install alien
```

CD to the folder with XnView-static-fc4.i386.rpm in and paste/type:

```
sudo alien XnView-static-fc4.i386.rpm
```

Then install it with:

```
sudo dpkg -i xnview_1.70-2_i386.deb
```

Hopefully that will help you out.

---

### Post by jfinkels on 2007-05-12
> **Subban said:**
> I had installed Xnview from an alien converted rpm on dapper, so just had another look at it and it worked just dandy on Feisty too.

Download the RPM
[http://download.xnview.com/XnView-static-fc4.i386.rpm]("http://download.xnview.com/XnView-static-fc4.i386.rpm")

```
sudo apt-get install alien
```

CD to the folder with XnView-static-fc4.i386.rpm in and paste/type:

```
sudo alien XnView-static-fc4.i386.rpm
```

Then install it with:

```
sudo dpkg -i xnview_1.70-2_i386.deb
```

Hopefully that will help you out.

Hmm, doesn't work on my computer! But if there's a chance that it'll work on the original poster's, then that's fabulous.

---

### Post by collieman on 2007-05-13
Guys,  I sure appreciate your help with instaling XnView.   The file that you've suggested is different  than the one I downloaded.........XnView-static.i386.rpm.   There's still  some hope.   I will download and follow your instructions later this afternoon when I get back and post the results.  I don't HAVE to have XnView but it works nicely in Windows and I thought I could use it here in Ubuntu.  If it doesn't work I'll use what Ubuntu has to offer.  It was just a challenge for me.  Later,  Collieman

---

### Post by rillip on 2007-05-13
One thing to keep in mind is that .rpm is not a format supported directly by Ubuntu.  I know Fedora Core, for example, supports RPM directly.

Imagine trying to install a .deb on Windows... same kind of idea.  It's not that it's impossible, just a lot more difficult than the average user is willing to do.  TTTthe few RPM's I've tried to install seemed to work, but then I could neverr find them, or they wouldn't actually run after install, etc.  With some work, I found .debs or a repository for them on these particular two.

When all else fails, very politely ask the developer if they've ever considered releasing a .deb.  Gently point out to them that there are tons of Debian based OS's in the Linux community right now; in fact, many of the really popular distros are Debian based, like Ubuntu, MEPIS, Knoppix, Debian; that's 4 of the top 10 on distrowatch).

---

### Post by Talon2 on 2007-05-13
Don't worry about being in over your head.  You aren't the only one.

The good news is, given the popularity of Ubuntu, packaging in .deb format will become more popular.  I've found that a little patience is required but given time most problems can be solved.  Good luck.

---

### Post by collieman on 2007-05-13
I'm not sure I'm doing this right so I'll tell you what I did.  I downloaded the XnView-static-fc4.i386.rpm file to desktop.  Then I right clicked on the file and then chose "extract here".  That put a folder on the desktop with the extracted files.  Then I opened "terminal" and copied and pasted the first set of codes that  jfinkles gave me into it and pressed enter at the blinking black cursor.  Then entered my password.  Then did the next set of codes and then again... but it didn't work.  Here is what came up in terminal:

curt@Junk:~$ sudo apt-get install alien
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
curt@Junk:~$ sudo alien XnView-static-fc4.i386.rpm
File "XnView-static-fc4.i386.rpm" not found.
curt@Junk:~$ sudo dpkg -i xnview_1.70-2_i386.deb
dpkg: error processing xnview_1.70-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xnview_1.70-2_i386.deb
curt@Junk:~$ 

Hope I did it right.  If it's not going to work I'll use what Ubuntu has to offer and be happy with that.  At least I'm not supporting Microsoft anymore.

---

### Post by jfinkels on 2007-05-13
> **collieman said:**
> I'm not sure I'm doing this right so I'll tell you what I did.  I downloaded the XnView-static-fc4.i386.rpm file to desktop.  Then I right clicked on the file and then chose "extract here".  That put a folder on the desktop with the extracted files.  Then I opened "terminal" and copied and pasted the first set of codes that  jfinkles gave me into it and pressed enter at the blinking black cursor.  Then entered my password.  Then did the next set of codes and then again... but it didn't work.  Here is what came up in terminal:

curt@Junk:~$ sudo apt-get install alien
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
curt@Junk:~$ sudo alien XnView-static-fc4.i386.rpm
File "XnView-static-fc4.i386.rpm" not found.
curt@Junk:~$ sudo dpkg -i xnview_1.70-2_i386.deb
dpkg: error processing xnview_1.70-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xnview_1.70-2_i386.deb
curt@Junk:~$ 

Hope I did it right.  If it's not going to work I'll use what Ubuntu has to offer and be happy with that.  At least I'm not supporting Microsoft anymore.

When using the terminal, first you have to change the directory that you are in to the directory where the file is. So if the file is in /home/curt/Desktop/XnView-static-fc4.i386 (that may not be the actually directory, you have to figure that out on your own), then do this:```
cd /home/curt/Desktop/XnView-static-fc4.i386
```
'cd' stands for 'Change Directory'. Now that you are in the directory that contains the .rpm file, convert it to a .deb file using alien:
```
sudo alien XnView-static-fc4.i386.rpm
```
Again, replace what I wrote with the actual name of the file if I gave the wrong filename!

After you convert it, try to install it like this:
```
sudo dpkg -i XnView-static-fc4-i386.deb
```
Again, replacing the filename I have here with the actual filename. Let us know how this goes.

You may want to search using Google or something for "Linux terminal howto" or something similar that will give you introductory information on using the terminal.

---

### Post by twodogs on 2007-05-13
i followed directions exactly and it works for me.  even created the link in the applications>graphics menu.  

unfortunately i don't like this program.  could someone please help me remove it.  i tried rm -r xnview but did not work.  thanks for help.

TwoDogS out!

---

### Post by collieman on 2007-05-13
jfinkles,  I tried the directory change but got this error messge:

curt@Junk:~$ cd /home/curt/Desktop/XnView-static-fc4.i386
bash: cd: /home/curt/Desktop/XnView-static-fc4.i386: No such file or directory
curt@Junk:~$

---

### Post by collieman on 2007-05-13
twodogs,  You are a lucky "dog".  Wish i could get mine to work.  It has to be me.  I'm doing something wrong like jfinkles said about me not changing my directory.   I did a lot of reading before I asked for help.  How do you guys do it?

---

### Post by collieman on 2007-05-13
jfinkles,  I did a little experimenting with the directory change. The files are extracted to a folder called "usr" on the desktop.  I tried changing the path many times inserting "usr" but no go.  Should "usr " be in the path?

---

### Post by jfinkels on 2007-05-13
> **collieman said:**
> jfinkles,  I did a little experimenting with the directory change. The files are extracted to a folder called "usr" on the desktop.  I tried changing the path many times inserting "usr" but no go.  Should "usr " be in the path?

Yes...I think maybe you're not understanding the idea behind changing directories and a file hierarchy. Let me just do a brief overview of how to effectively use the terminal to navigate through the filesystem.

When you open a terminal, you will see
```
curt@Junk:~$
```
'curt' is your username, 'Junk' is your hostname (the nickname of the computer that you are using), and '~' is your current working directory. The tilde (~) is a shorthand notation for your own personal home directory, /home/curt. You can use the tilde wherever you would normally write /home/curt.

To view the current directory you are in type this:
```
pwd
```
To print the current working directory.

To list all the files and directories in the current directory, type this```
ls
```(that's the letter L and the letter S, both lowercase).

To change directory, type the following:
```
cd *directory*
```
where *directory* is the name of the directory that you want to change to. If you type the first few letters of the directory you want to change to, and then press the Tab button, bash (the program with which you are interacting in the terminal) will automatically complete the name of the directory, or show you multiple possible completions if there are more than one. To change to the directory above the current one, type this:
```
cd ..
```

When you run a program (alien for example), if you want to give the program the name of a file as a parameter, you must either give it the full path to the file in the filesystem hierarchy or just give the filename IF you are currently working in the same directory as the file! So, if your file is located at /home/curt/mydirectory/file, you can either do this:
```
cd /home/curt/mydirectory
alien myfile
```
or this:
```
 alien /home/curt/mydirectory/myfile
```
It is often advisable to change to the directory you want to work in FIRST, because the program may look for files inside the directory, or it may try to write output files and it's best to keep them in the directory in which the input is.

So here's what you need to do: go the terminal, list the files and directories that are currently in your working directory, change your directory to the directory that has the file you want to convert using alien, list the contents of THAT directory, use alien to convert the file (try typing part of the filename and then pressing tab for autocompletion as described above), and then come back to us and tell us how it went, okey dokey?

It takes time to get used to this...I've been working on Linux since October, so don't think it comes without time and practice :D

EDIT: Oh, and if you want to read more information on commands (which you do, I assure you) type 'man' followed by the name of the command:
```

man ls
man cd
man alien

```etc.

---

### Post by srt4play on 2007-05-13
> **collieman said:**
> jfinkles,  I did a little experimenting with the directory change. The files are extracted to a folder called "usr" on the desktop.  I tried changing the path many times inserting "usr" but no go.  Should "usr " be in the path?

Your first mistake was extracting the .rpm.

It doesn't need to be extracted, follow the instructions that have been given to you in this thread to convert the .rpm file into a .deb file using alien.

---

### Post by picpak on 2007-05-13
Where exactly did you download the rpm? If it's on the desktop, you'll need to run

```
cd Desktop/
```

first.

---

### Post by RedSquirrel on 2007-05-14
> **twodogs said:**
> i followed directions exactly and it works for me.  even created the link in the applications>graphics menu.  

unfortunately i don't like this program.  could someone please help me remove it.  i tried rm -r xnview but did not work.  thanks for help.

TwoDogS out!


```
sudo dpkg -r xnview
```

---

