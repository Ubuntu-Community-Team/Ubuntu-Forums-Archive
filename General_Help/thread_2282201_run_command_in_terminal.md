---
title: "run command in terminal"
date: 2015-06-12
forum: General Help
---

### Post by choochoousmc on 2015-06-12
newbie using comands in terminal   following online directions not working need syntax help.
Wanting to install truecrpyt and freenet and some other security programs to play with and learn.

I went to software  center and installed java.
Now need to install freenet. it is in a jar folder, but also been unpacked can't find a way to actually install

.jar folder     /Home/Downloads/ new_installer_offline_1467.jar

the extracted location        /Home/Downloads/new_installer_offline_1467

in there is several folders and files, but don't know what is what.

would somebody please  type out the command line for a terminal window of what to type and how.
Directions o line say double clicking the install jar will install, all it appears to do is extracct

thanks

---

### Post by Holger_Gehrke on 2015-06-12
```

java -jar ~/Downloads/new_installer_offline_1467.jar

```

should run the installer directly from the java-archive. jar-files are just zip-archives with a specific structure containing the class-files (and various other resources) of a java application. On your system the fact that it's an archive takes precedence over the specific kind of archive it is.

Since I do most everything from the cli anyway, I can't even recall whether I've ever tried to start a jar by double clicking it ...

---

### Post by oldos2er on 2015-06-13
I'm not sure it's safe to run truecrypt any more since support for it was dropped awhile back.

---

### Post by choochoousmc on 2015-06-13
thanks.  tried that it did not work      but will try it again

---

### Post by choochoousmc on 2015-06-13
I been running it for a few years on another machine. While official support has dropped there are still some fresh articles on it, and since I do have container files under another system, would still need access here on Ubuntu.
But one thing at a time.
thanks for your response

---

### Post by choochoousmc on 2015-06-13
tried the new syntax code. still won't run.  first time said to try sudo apt-get        then ithat returned
E: Command line option 'j' [from -jar~/Downloads/new_installer_offline_1467.jar] is not known.

any other ideas how to install the freenet program?

---

### Post by QDR06VV9 on 2015-06-13
I Don't use it but there is new information now.
> **[Yes&#8230; TrueCrypt is still safe to use.]("http://steve.grc.com/2014/05/30/yes-virginia-truecrypt-is-still-safe-to-use/")**

                                                                                              Posted on [May 30, 2014]("http://steve.grc.com/2014/05/30/yes-virginia-truecrypt-is-still-safe-to-use/")                            by [Steve Gibson]("http://steve.grc.com/author/agilesynapse/")                                             
                                               So opens the short editorial I wrote this morning and placed at the top of [GRC&#8217;s new TrueCrypt Final Version Repository page]("https://www.grc.com/misc/truecrypt/truecrypt.htm").
 [IMG]https://www.GRC.com/misc/truecrypt/tc-logo.png[/IMG]
 The impetus for the editorial was the continual influx of questions  from people asking whether TrueCrypt was still safe to use, and if not,  what they should switch to, and so on. By this time, one of the  TrueCrypt developers, identified as David, had been heard from, and his  interchange confirmed the essential points of my conjectured theory of  the events surrounding the self-takedown of TrueCrypt.org, etc.
 Rather than repeating that entire editorial here, I&#8217;m posting this as [a pointer to it]("https://www.grc.com/misc/truecrypt/truecrypt.htm")  since folks here have thanked me for maintaining a blog and not relying  solely upon Twitter.  And also, this venue supports feedback and  interaction which GRC&#8217;s current read-only format can not.
 Peace.
 /Steve.
From Here [http://steve.grc.com/2014/05/30/yes-virginia-truecrypt-is-still-safe-to-use/](http://steve.grc.com/2014/05/30/yes-virginia-truecrypt-is-still-safe-to-use/)
And This Please dont kill the Messenger
> The mistake these developers made was in believing that
they still &#8220;owned&#8221; TrueCrypt, and that it was theirs to kill.
There Now Clear as Mud.lol
You had 2 new posts by the time I posted.
But have you tried this method
> [h=3]Linux and other Unix-like systems[/h]  	 	  Try the [Java Web Start installer]("https://freenetproject.org/jnlp/freenet.jnlp").
	  If it doesn't work: 	
 	 	  You need to have a recent **Java Runtime Environment** 	  (JRE). We have experienced best results with Oracle's Java 	  Runtime Environment which can be obtained via 	  your [package 	    manager]("https://en.wikipedia.org/wiki/Package_manager") or 	  from [http://www.java.com/](http://www.java.com/).
  	
 	       Java version 1.6 or higher is required, and 1.7 or higher is strongly       recommended. You should keep Java up to date to avoid problems and for       better performance.     
  	 	  Open a terminal and run: 	
 	 	  		  wget '[https://freenetproject.org/jnlp/freenet_installer.jar](https://freenetproject.org/jnlp/freenet_installer.jar)' -O new_installer_offline.jar
	  java -jar new_installer_offline.jar 	 	 	  Alternatively, 	  downloading [the 	    installer]("https://freenetproject.org/jnlp/freenet_installer.jar") 	  ([gpg 	    signature]("https://downloads.freenetproject.org/alpha/installer/new_installer_offline_1467.jar.sig")) and then clicking on the file may work on 	  some systems, but if there are problems we recommend the 	  above command lines. If wget is not installed, it can be installed with a package manager, such as 	  sudo apt-get install wget on Debian or Ubuntu. 	
 	 	If the link above is blocked, you could download it from our server [here]("https://downloads.freenetproject.org/latest/new_installer_offline.jar"). 	But please use the other link if you can.
       **Note:** Many Linux distributions no longer ship with Java Web Start enabled. We would like to make distribution packages for easier installation, and have an in-development (and not maintained) [Debian package]("https://github.com/freenet/debian"), but haven't gotten it stable or made official ones for other distributions. If you are a developer and would like to join us and help it would be much appreciated!     
   	If this doesn't work on a headless server, try "java -jar new_installer_offline.jar -console", and  	follow the prompts to tell it where to install Freenet etc.
Kind Regards

---

### Post by choochoousmc on 2015-06-15
yes I followed all those directions and it refuses to install.
'I installed java from the software center.
Now I want to install Freenet first       Nothing seems to work.
Any other ideas?

I'll worry about truecrypt after I get freenet installed.  One at a time

---

### Post by QDR06VV9 on 2015-06-15
> **choochoousmc said:**
> yes I followed all those directions and it refuses to install.
'I installed java from the software center.
Now I want to install Freenet first       Nothing seems to work.
Any other ideas?

I'll worry about truecrypt after I get freenet installed.  One at a time
if you have installed open-jre or ice-tea from syanptic or software center you may want to try.
You can use [WebUpd8 PPA]("https://launchpad.net/%7Ewebupd8team/+archive/ubuntu/java") (this will download the required files from Oracle and install JDK 8):

```
sudo apt-add-repository ppa:webupd8team/java
sudo apt-get update 
sudo apt-get install oracle-java8-installer
```
And Just to Avoid confusion with the installer install "oracle-java8-set-default"
> We have experienced best results with Oracle's Java       Runtime Environment
Then Try again to install freenet.
Fingers Crossed
Other Possible Resources.
Installing Freenet on Ubuntu server (command line)
[http://notepad.patheticcockroach.com/2519/installing-freenet-on-ubuntu-server-command-line/](http://notepad.patheticcockroach.com/2519/installing-freenet-on-ubuntu-server-command-line/)

Freenet Installation and Administration
Issue 84
[http://www.linuxjournal.com/article/4565](http://www.linuxjournal.com/article/4565)
From Issue #84
April 2001
Apr 01, 2001  By Peter Todd

---

