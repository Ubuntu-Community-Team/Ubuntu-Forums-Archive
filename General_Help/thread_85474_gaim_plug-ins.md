---
title: "gaim plug-ins"
date: 2005-11-02
forum: General Help
---

### Post by eyebrowman92 on 2005-11-02
On The Sourceforge Website For Gaim Are A List Of Available Plug-ins, But I Dont Know How To Download And Install Them. Can Someone Walk Me Through This Please?

---

### Post by eyebrowman92 on 2005-11-02
Please Someone Help!!!

---

### Post by eyebrowman92 on 2005-11-02
Any Ideas Anyone?

---

### Post by metwo on 2005-11-02
Which plugins were you after?

Some, like gaim-encryption, can be installed through apt, others you need to compile from source.

---

### Post by eyebrowman92 on 2005-11-02
these two plug-ins,  [http://sourceforge.net/tracker/index.php?func=detail&aid=1286042&group_id=235&atid=390395](http://sourceforge.net/tracker/index.php?func=detail&aid=1286042&group_id=235&atid=390395)        

[http://sourceforge.net/tracker/index.php?func=detail&aid=1152896&group_id=235&atid=390395](http://sourceforge.net/tracker/index.php?func=detail&aid=1152896&group_id=235&atid=390395)

---

### Post by ecobuntu on 2005-11-02
[QUOTE=eyebrowman92]these two plug-ins,  [http://sourceforge.net/tracker/index.php?func=detail&aid=1286042&group_id=235&atid=390395](http://sourceforge.net/tracker/index.php?func=detail&aid=1286042&group_id=235&atid=390395)        

[http://sourceforge.net/tracker/index.php?func=detail&aid=1152896&group_id=235&atid=390395](http://sourceforge.net/tracker/index.php?func=detail&aid=1152896&group_id=235&atid=390395)[/QUOTE]

d/l the tarball
[http://sourceforge.net/tracker/download.php?group_id=235&atid=390395&file_id=148578&aid=1286042](http://sourceforge.net/tracker/download.php?group_id=235&atid=390395&file_id=148578&aid=1286042)

Then...
tar xvzf filename.tar.gz
cd filename
./configure
make
sudo make install

viola!

---

### Post by eyebrowman92 on 2005-11-02
whats d/l mean?

---

### Post by djdennie on 2005-11-02
d/l = download

---

### Post by eyebrowman92 on 2005-11-02
im sorry ecobuntu, but im new to linux and i dont really know what you're directions mean. can you help me?

---

### Post by eyebrowman92 on 2005-11-02
Please Help!

---

### Post by eyebrowman92 on 2005-11-02
some

---

### Post by eyebrowman92 on 2005-11-02
one

---

### Post by eyebrowman92 on 2005-11-02
help

---

### Post by endersshadow on 2005-11-02
[QUOTE=eyebrowman92]Please Help![/QUOTE]

First thing to do: Breathe :-D

Secondly, download the file and put it in your home folder

Thirdly, open up your terminal (Applications Menu>Accesories>Terminal).  
The next code box is what your are to type, line by line (type a line, hit enter):

```
cd
tar xzf filename.tar.gz
cd filename
sudo ./configure  **you will need to put your password in here**
sudo make
sudo make install
```

Then, open up GAIM, go to Tools>Preferences, click on Plug-ins on the left, check the plugin you installed, and then select it from the left hand menu and click the options you want!

---

### Post by ecobuntu on 2005-11-02
[QUOTE=endersshadow]First thing to do: Breathe :-D

Secondly, download the file and put it in your home folder

Thirdly, open up your terminal (Applications Menu>Accesories>Terminal).  
The next code box is what your are to type, line by line (type a line, hit enter):

```
cd
tar xzf filename.tar.gz
cd filename
sudo ./configure  **you will need to put your password in here**
sudo make
sudo make install
```

Then, open up GAIM, go to Tools>Preferences, click on Plug-ins on the left, check the plugin you installed, and then select it from the left hand menu and click the options you want![/QUOTE]

Sorry...I should have mentioned that it need to be done at the terminal.  I don't think you need to sudo though until make install...but it's up to you.  If I recall you can also convert a tarball to a deb file...no i lied it's a slackware package (.tgz) that i was thinking of.

---

### Post by ecobuntu on 2005-11-02
You've got a great strategy to increase your number of posts Eyebrowman!

---

### Post by endersshadow on 2005-11-02
[QUOTE=ecobuntu]Sorry...I should have mentioned that it need to be done at the terminal.  I don't think you need to sudo though until make install...but it's up to you.  If I recall you can also convert a tarball to a deb file...no i lied it's a slackware package (.tgz) that i was thinking of.[/QUOTE]

I've found that it's about 50/50 w/ the sudo needed with the configure, so I just do it all the time just to make sure :)

---

### Post by guoweiok on 2005-11-03
just follow ecobuntu's instruction, everything should be done! 
what kind of further help do you need?

---

### Post by guoweiok on 2005-11-03
when i first started to reply this thread, there were only  9 replies, but when i finished my first reply, there were almost 20 replies already.....

---

### Post by eyebrowman92 on 2005-11-03
> @ubuntu:~$ cd
@ubuntu:~$ sudo @ubuntu:~$ tar xzf filename.tar.gz
sudo: @ubuntu:~$: command not found
@ubuntu:~$ tar: filename.tar.gz: Cannot open: No such file or directory
bash: tar:: command not found
@ubuntu:~$ tar: Error is not recoverable: exiting now
bash: tar:: command not found
@ubuntu:~$ tar: Child returned status 2
bash: tar:: command not found
@ubuntu:~$ tar: Error exit delayed from previous errors
bash: tar:: command not found
@ubuntu:~$ sudo ./configure
sudo: ./configure: command not found
@ubuntu:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
@ubuntu:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
@ubuntu:~$ i got these errors while typing in the commands into the terminal. what should i do?:confused:

---

### Post by eyebrowman92 on 2005-11-03
im not trying to increase my number of posts by doing this i just want someoneto answer please!

---

### Post by ecobuntu on 2005-11-03
[QUOTE=eyebrowman92]i got these errors while typing in the commands into the terminal. what should i do?:confused:[/QUOTE]


Replace filename with the name of the file you are trying to install.
Let's say I am trying to install gaim.tar.gz

I would do this in a terminal

tar xvzf gaim.tar.gz
cd gaim
sudo ./configure
sudo make 
sudo make install

Then you're done.  
If your file is called joe.tar.gz...just replace gaim with joe and so on.

---

### Post by eyebrowman92 on 2005-11-03
i've tried and it still claims theres no file or directory. ive moved the tar file into my home folder and tried but still nothing. i made the file name tar xvzf warnback.tar.gz and when i type that into a term it says it doesnt exist. what do i do?

---

### Post by metwo on 2005-11-03
[QUOTE=eyebrowman92]i've tried and it still claims theres no file or directory. ive moved the tar file into my home folder and tried but still nothing. i made the file name tar xvzf warnback.tar.gz and when i type that into a term it says it doesnt exist. what do i do?[/QUOTE]

You called the file tar xvzf warnback.tar.gz or just warnback.tar.gz? Calling it the first one is just going to confuse things!

---

### Post by eyebrowman92 on 2005-11-03
ok so i got the first one right but now when i type in cd warnback it gives me an error saying the file doesnt exist. what now?

---

### Post by metwo on 2005-11-03
you should probably check what the directory is called by using

```
ls
```

---

### Post by eyebrowman92 on 2005-11-03
@ubuntu:~$ ls
Desktop                Internet Explorer  OperaDownloads  warnback.tar.gz
gaim-plugin-send-some  Limewire           Pictures

---

### Post by metwo on 2005-11-03
[QUOTE=eyebrowman92]@ubuntu:~$ ls
Desktop                Internet Explorer  OperaDownloads  warnback.tar.gz
gaim-plugin-send-some  Limewire           Pictures[/QUOTE]

It looks like you haven't untarred it yet, so I would try typing

```
tar -xvzf warnback.tar.gz
```

and see what happens.

---

### Post by metwo on 2005-11-03
actually, where did you get warnback.tar.gz from? I can't find the download link for it. Are you sure you haven't just renamed gaim-plugin-send-some.tgz from ecobuntu's link on page one of this thread? If so the thats actaully the send to some plugin you've downloaded.

However, the tar.gz file just contains a patch to the gaim source code, so you need to read the README file in the gaim-plugin-send-some directory for further instructions.

---

### Post by BIGtrouble77 on 2005-11-03
eyebrowman92,
Sorry to stray a little, but I suggest reading through [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

I think you'll start to notice a pattern for installing and configuring programs.  The site is for the Ubuntu Hoary release, but much of it still applies to Breezy.  

There's basically 3 ways to install a program (listed from easiest to most difficult).
1. Through the repositories (with apt and synaptic)
2. Installing a deb file with dpkg
3. Compiling the source

You should get familiar with installing basic apps before you jump into compiling source as it's much more difficult to do, and much more difficult to uninstall.

-BT

---

### Post by ecobuntu on 2005-11-03
[QUOTE=BIGtrouble77]eyebrowman92,
Sorry to stray a little, but I suggest reading through [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

I think you'll start to notice a pattern for installing and configuring programs.  The site is for the Ubuntu Hoary release, but much of it still applies to Breezy.  

There's basically 3 ways to install a program (listed from easiest to most difficult).
1. Through the repositories (with apt and synaptic)
2. Installing a deb file with dpkg
3. Compiling the source

You should get familiar with installing basic apps before you jump into compiling source as it's much more difficult to do, and much more difficult to uninstall.

-BT[/QUOTE]

I second this!

---

### Post by eyebrowman92 on 2005-11-03
how do i reconfigure gaim . is there a code fr the terminal?

---

