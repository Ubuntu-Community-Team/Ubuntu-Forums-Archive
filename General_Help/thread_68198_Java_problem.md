---
title: "Java problem"
date: 2005-09-22
forum: General Help
---

### Post by andlinux on 2005-09-22
Hi

I installed Java and I made a symbolic link for firefox but when I enter a website that has some java apllets then I see the java sun logo with the star and a loading bar in it and nothing happens.

I installed java with fakeroot...

What can be the problem ?

---

### Post by papangul on 2005-09-22
[QUOTE=andlinux]I installed java with fakeroot...[/QUOTE]
Did you download java from sun's site and installed it?

---

### Post by andlinux on 2005-09-23
[QUOTE=papangul]Did you download java from sun's site and installed it?[/QUOTE]
ofcourse

---

### Post by phex on 2005-09-23
what have you typed in? if you you type "ls" in the <firefox dir>/plugins directory, is the libjavaplugin_oji.so or how you named it colored red or green?

---

### Post by rjwood on 2005-09-23
I have not been able to install java via apt-get so I downloaded the self-extracting file from sun to my home folder, I am trying to follow the instructions but, am not quite understanding them. Is there someone who could help me with the install please. Thank you!

---

### Post by phex on 2005-09-23
what is not clear?

At the beginning if you start the jdk1....bin script you should browse to the end (100%) and type in yes. then a jdk1... directory is created and all the jdk files are extracted into this directory. then you should type "su" and enter your "root" password and copy this jdk directory to usr: 
cp -R jdk1... /usr/java

-> so you have the java directory in /usr/java where in the bin directory the java script can be found. you can try it out if you type: 
cd /usr/java/bin
java -version

if you have done this you should set the PATH variable to that:
PATH=/usr/java/bin:$PATH (simple type this in the console)
-> from now on you can type java in any directory and the command is found.

but this is only temporary. if you close the terminal and open a new terminal, you can not use the java command again because the PATH variable will be fogotten by each terminal instance if it is closed.

So to make it permanent do that:
cd /etc/X11/Xsession.d
touch 90environement
vi 90environement
<press the "i" button>
<type>
PATH=/usr/java/bin:$PATH<press Enter button>
export PATH
<press the "ESC" button>
<press the ":" button and the "x" button>
<press the "Enter" button>

-> thats it ;)

---

### Post by rjwood on 2005-09-23
thanks phex. Sorry to be so thick-headed! I did everything you said and still no java 

rob@ubuntu:~$ cd /usr/java/bin
rob@ubuntu:/usr/java/bin$ ls -a
.             java     keytool  ktab     policytool   servertool
..            java_vm  kinit    orbd     rmid         tnameserv
ControlPanel  javaws   klist    pack200  rmiregistry  unpack200
rob@ubuntu:/usr/java/bin$

ob@ubuntu:/usr/java/bin$ java -version
bash: java: command not found
rob@ubuntu:/usr/java/bin$

not sure what I did wrong. Would you mind taking a look :grin: ??

---

### Post by phex on 2005-09-23
oh. my fault. try:

2)
cd /usr/java/bin
./java -version 
->(relative path: "./" means that the command is in the same directory where you are at the moment)

OR

2)
/usr/java/bin/java -version
->(absolute path from the root directory "/")

Since you have not set the PATH variable, you must specify the absolute path or rather the relative directory where to find the command. See the 2 examples above.

---

### Post by facefur on 2005-09-24
I have the same problem, but all I get is Firefox asking me to install the plug-in.  I have done the following:
1.  Downloaded the java jre1_5_0_04-linux.i586.bin package from Sun's web site.
2.  Dowloaded the Sun instructions for installation, and followed them, using a /usr/java directory for the target.  I had to use "sudo" commands to get it to the point where I could accept the license.  

After that all I get are error messages telling me "permission denied" when it tries to create directories, then error messages telling me it can't find the directories I apparently idn't have permission to create.

The result - no Java installed.  Same result twice.  I'm not insane so I thought I'd ask.

---

### Post by andlinux on 2005-09-24
[QUOTE=phex]what have you typed in? if you you type "ls" in the <firefox dir>/plugins directory, is the libjavaplugin_oji.so or how you named it colored red or green?[/QUOTE]

[COLOR=MediumTurquoise]**It's this color, not green or red**[/COLOR]

I couldn't find the website where they explained how to install java, but I found this on the Ubuntu forums and it's (almost) the same.

sudo apt-get install fakeroot java-package
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named).

---

### Post by facefur on 2005-09-24
Following up on my request above, I tried installing Java while logged in as myself and in my home directory, where the downloaded self-extracting file is located.  This time, it appeared to install.

Now I don't know where it installed itself, and Mozilla still cannot see it.  I'm sure this has something to do with PATH variables and the like, but I am lost here.

---

### Post by phex on 2005-09-24
[COLOR=MediumTurquoise]It's this color, not green or red[/COLOR]

so the links are ok. its really strange. sry. cannot help you then. must be a problem with your firefox. with version 1.04 it functioned in my case. :(

------------------------------------------------
After that all I get are error messages telling me "permission denied" when it tries to create directories, then error messages telling me it can't find the directories I apparently idn't have permission to create.

you must be the root user to copy directories to /usr, etc...
sudo normally does the trick for you. but type in "su" and type in your root password if it is prompted. then you have enough permissions to create directories, etc...
To be honest I dont really know which directories cannot be created? I assume that the directories are the java directories.

---

### Post by Blue1k on 2005-09-24
What you can do is link the java directory with /usr/bin.

You need to find where you installed java to. Find that folder and its bin folder and then type this in console:

 **ln -s /usr/java/jre1.5.0_04/bin/java /usr/bin/java**

In my system I installed jre to a directory I made: /usr/java

---

### Post by phex on 2005-09-24
if you used the self extracting file (....bin) then the java directory is in your home directory! You simple have to copy it then to /usr/java as root or to another directory you want it to be.

be aware that you have to set the PATH variable to your java bin directory to use the java command!!
for example:
PATH=/usr/java/bin:$PATH under assmption that there lies your java directory

---

### Post by andlinux on 2005-09-25
[QUOTE=Blue1k]What you can do is link the java directory with /usr/bin.

You need to find where you installed java to. Find that folder and its bin folder and then type this in console:

 **ln -s /usr/java/jre1.5.0_04/bin/java /usr/bin/java**

In my system I installed jre to a directory I made: /usr/java[/QUOTE]

Mine is standing in /usr/lib/j2re1.5-sun/bin and if I want to create a symbolic link to /usr/bin/java then it tells me that it already exist.
[QUOTE=phex]
if you used the self extracting file (....bin) then the java directory is in your home directory! You simple have to copy it then to /usr/java as root or to another directory you want it to be.

be aware that you have to set the PATH variable to your java bin directory to use the java command!!
for example:
PATH=/usr/java/bin:$PATH under assmption that there lies your java directory[/QUOTE]
I only find one directory from java and it's a hidden one (.java) but that's has nothing to do with the java from sun (I think).

This is standing in the .java directory:
[email]and@Linux-laptop:~/.java[/email]$ cd deployment/
[email]and@Linux-laptop:~/.java[/email]/deployment$ ls
cache  deployment.properties  ext  log  security
[email]and@Linux-laptop:~/.java[/email]/deployment$

---

### Post by papangul on 2005-09-25
Did you try this? it worked for me:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by andlinux on 2005-09-25
[QUOTE=papangul]Did you try this? it worked for me:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)[/QUOTE]
Yes, that was the first thing that I tried, it was installed but I had the same problem with firefox.

Strange problem now, Ubuntu had some updates including firefox (version 1.0.7).
I installed it but it gave me an error output, so I removed firefox (there he had some problems) and I installed the new version of firefox but when I want to start firefox nothing happens. :(

Edit2: It works again, searched on this forum and there were people with the same problem.

---

