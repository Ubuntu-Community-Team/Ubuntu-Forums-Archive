---
title: "Ubuntu ./configure command not found"
date: 2007-04-17
forum: General Help
---

### Post by Vanaheim on 2007-04-17
Hi all ^^ first time poster, user and a newbie to Nix* in general.

First of a brief intro, iv been a windows user basicaly since my beginning on the computer world, like 15 years ago or so. Well, to put this really short and simple, windows isnt 100% required right now for my work and entertainment so i decided it was time to move on to the next step, Linux.

I choose Ubuntu for many reasons but mostly because for someone without experience in the Nix world it should have an easier learning curve, and so far im loving it ^^

Iv been able to configure almost everything that i need to in order to work and have a multimedia experience just like i always had with windows, being the only thing i "miss" are the games, but well, since im a retro fan emulation plays a big part in my life as a gamer so, i want to install some emus  but im having a bit of a harsh time.

I downloaded Gens and extracted it to Home/Emulators/Gens/GensForLinux and tried to compile it but without success.

I read the readme file and i followed the steps as described, 

sudo ./configure 

on the dir were i have the files, the files on the dir aren't missing, it as everything but the following message appears when i try to execute that command

./configure command not found

I dont know what I'm missing here, so far iv been able to install programs with synaptic and even with commands using the shell, so far not one single problem until i tried to install gens.

I tried to find more information about it but i couldnt, i dont know if its a specific problem related to "Gens" or if something is missing.

Compiling tools, libraries etc..

If so, could anyone point me the way to what i need to install to prevent this and future similar cases with ./configure command?

By the way, im using Ubuntu Drapper LTS

I'm sorry if this question is too obvious or so, but for me it isn't ^^

Thank you in advance, any help would be very apreciated!

Cheers

---

### Post by srhlefty on 2007-04-17
I'm not sure I understand:  I went to the gens official homepage, and it looks like all the downloads they offer are for windows, not linux.  Where did you get the package?

---

### Post by bruenig on 2007-04-17
Ok first thing you need to know is that ./configure is not a command. ./configure runs an executable script. I don't know why the tutorials never explain this and just sort of throw out this mysterious ./configure will fix it for you, I guess it is too much trouble to explain it is a script.
The ./ indicates the current directory and "configure" is the name of the script. So if your current directory does not have a script in it called configure it won't work.

With that said, things needed for compilation can be installed with
```
sudo apt-get install build-essential
```

You should not need to use sudo when you run ./configure. Make sure you are in the correct directory when you issue the ./configure, that is likely the problem.

---

### Post by WiseElben on 2007-04-17
Hi, welcome to the Ubuntu community!

First, make sure you have build-essential installed:

```

$ sudo apt-get install build-essential

```

Then check to see that you have the proper permissions to read/write/execute in the folder. You can give full allowance by doing:

```

$ sudo chmod -R 777 folder_name

```

EDIT: Bah, bruenig posted seconds before me. Noob you are Matt.

---

### Post by srhlefty on 2007-04-17
My fault, sorry.  The linux package is inside the source archive deceptively named "gens-win32-src"

---

### Post by srhlefty on 2007-04-17
Now this is interesting, I have those packages already installed, and I get similar errors:
> srhlefty@srhlefty-edgy:~/gens/GensForLinux$ ls
aclocal.m4      config.sub                  history.txt    pixmaps
AUTHORS         configure                   INSTALL        README
autom4te.cache  configure.in                install-sh     src
BUGS            COPYING                     Makefile.am    stamp-h.in
compile         depcomp                     Makefile.in
config.guess    GENS-DEVS-README-FIRST.txt  missing
config.h.in     gens.txt                    mkinstalldirs

srhlefty@srhlefty-edgy:~/gens/GensForLinux$ sudo ./configure
sudo: unable to execute ./configure: No such file or directory

srhlefty@srhlefty-edgy:~/gens/GensForLinux$ sudo sh configure
: not found11: 
configure: 19: Syntax error: "elif" unexpected (expecting "then")
 

I've compiled programs before, and haven't encountered this sort of problem.  Now I'm interested to see its cause.:)

---

### Post by Vanaheim on 2007-04-18
Hi srhlefty, you can find the Nix versions of some emulators at linuxemu.retrofaction.com

bruenig, i do have build essential installed and updated, just checked it again to make sure and thank you for the explanation ^^ i apreciate it.

here is a screenshot..speaks alot more than words..

[http://www.zshare.net/image/798798-jpg.html](http://www.zshare.net/image/798798-jpg.html)
	
WiseElben, thank you for your reply ^^

as you guys can see, im in the correct dir, with permission and in the dir there are the correct files, configure, make..etc

I have the tools i just..dont get what im doing wrong or what im missing..

Cheers

---

### Post by Vanaheim on 2007-04-18
Hi guys ^^

Hows it going?

Well, i found two solutions for my problem, an easy one and a tricky one.

The easy one is that while searching this forums i found a post writing by megamaced in which he provides a debian re-package for Gens, get it here

[http://ubuntuforums.org/showthread.php?t=290008&highlight=gens](http://ubuntuforums.org/showthread.php?t=290008&highlight=gens)

Now, its all nice and all but it didn't actualy "solve" my problem because i wanted to know why i wasn't able to use ./configure to execute the script.

After some hours messing around, i decided to mess with the libs, so i decided to change libc6 to the latest unstable, 2.5.2..well, this gave errors behind errors and i decided to uninstall it..another headache.

I used sudo apt-get install -f to remove all packages, after that more errors in synaptic.

Well, i then tried to revert libc6 back to the latest update for drapper which also was failing, until i decided to reboot..just one of those "windows old feelings"

After that i went and choose to force to the old version, which for my surprise worked, so after the rollback i just had to 

sudo apt-get install build-essential

and voilá, ./configure executes perfectly and i was able to compile Gens from the start without the debian package.

I actualy "don't" know exactly every detail in question, but im assuming something was wrong with the compiling files installed, so a clean build-essential did the trick

But, once more, thanks for the replying and its good to be part of the Ubuntu comunity ^^

Cheers

---

### Post by hotweiss on 2007-09-25
Thanks. I've been using Ubuntu for a week now and I could not follow some of the instructions posted because I didn't have build-essential installed, grrrr.

---

### Post by simonnance on 2007-10-10
I'm having this problem at the moment, trying to install Thunderbird 2, have installed build-essential, but still get a "bash: ./configure: No such file or directory" when trying to run the ./configure line to allow me to continue installation.

the readme.txt. sends me to the [http://getthunderbird.com/releases/](http://getthunderbird.com/releases/) which tells me nothing of any use.


Help?

---

### Post by 3rdalbum on 2007-10-10
There are four things you have to be sure of when you're compiling:

1. Be sure you have *build-essential* installed. (sudo apt-get install build-essential)
2. Make sure your terminal is opened in the correct directory. The terminal needs to be navigated to the directory that contains the "configure" file that came with the source code you are trying to compile.

If you don't know how to navigate your filesystem in the terminal, install the nautilus-open-terminal package. Log out, log back in again, open a file browser and go to the source code's directory, then right-click and choose "Open in Terminal". Then try ./configure

3. It's:

```
./configure
```

DO NOT use sudo at this point; it won't work. The only part you should use sudo on is:

```
sudo make install
```

Or even better:

```
sudo apt-get install checkinstall
sudo checkinstall
```

4. That the source code does actually come with a configure script. If it doesn't, then consult the INSTALL file that comes with the program. Some programs don't require a configure step, some use other build systems (like Jam or Scons; yeah I know, jam and scones haha), or you might actually have a precompiled binary inside that gzip archive!

---

### Post by simonnance on 2007-10-10
hmm... i cant seem to FIND a configure  file in the extracted folder..... however it appears to run the program from the  thunderbird.exe ok, however the installer.exe  DOESNT work. Weird.

It also doesnt have an install file, or a particularly relevant README.

Prob is, i'd kind like to be able to install it properly so i can access it through the menu, rather than going into the dir with the .exe every time!

---

### Post by ed1ct on 2007-12-27
some help for the people hit by this problem:

execute one of the following commands: 
`bash configure` 
`sh configure` 
`csh configure` 

depending on the flavor of shell / shell scripting you're up against. Not sure if the scripts have differences between them or not, but I installed the zsnes 1.5.1 package on linux using `bash configure` and using apt-get to resolve any dependencies it complained about.

the error you're getting about syntax "elif found where 'else' expected" means the script was written for either a different shell or different supported distro...probably distro. I would check the link provided by another poster regarding a repackage for debian.

~Matt

---

