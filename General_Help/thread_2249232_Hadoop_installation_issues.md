---
title: "Hadoop installation issues"
date: 2014-10-20
forum: General Help
---

### Post by Shamik_Biswas on 2014-10-20
Hi all,

I am using Lubuntu 14.04. I want to install Hadoop 1.0.3 on my machine. In order to do that I tried the following :

- hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ cd ~
- hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ wget [http://archive.apache.org/dist/hadoop/core/hadoop-1.0.3/hadoop-1.0.3.tar.gz](http://archive.apache.org/dist/hadoop/core/hadoop-1.0.3/hadoop-1.0.3.tar.gz)
--2014-10-20 22:43:57--  [http://archive.apache.org/dist/hadoop/core/hadoop-1.0.3/hadoop-1.0.3.tar.gz](http://archive.apache.org/dist/hadoop/core/hadoop-1.0.3/hadoop-1.0.3.tar.gz)
....output logs....
Saving to: ‘hadoop-1.0.3.tar.gz’

100%[==============================================================================================================================>] 6,24,28,860 83.8KB/s   in 9m 45s 

2014-10-20 22:53:42 (104 KB/s) - ‘hadoop-1.0.3.tar.gz’ saved [62428860/62428860]

-[COLOR=#0000cd] Hadoop 1.0.3 successfully downloaded.[/COLOR]

- Now extracted using the following :
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ gzip -d hadoop-1.0.3.tar.gz
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ tar -xf hadoop-1.0.3.tar

- Now trying to move the file to /usr/local using the following:
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ mv hadoop-1.0.3 /usr/local/

- [COLOR=#ff0000]Error:  mv: cannot move ‘hadoop-1.0.3’ to ‘/usr/local/hadoop-1.0.3’: Permission denied[/COLOR]

***Question 1 : - How to get rid of this error ???***

-----------------

***Question 2 :-***

- hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ sudo chown -R hduser:hadoop hadoop
[sudo] password for hduser: 
[COLOR=#ff0000]**chown: cannot access ‘hadoop’: No such file or directory**[/COLOR]

- ***How to get rid of this ???***

Please mention step-by-step solution as I am new to Linux environment.

Advanced thanks .

---

### Post by nerdtron on 2014-10-20
Here we go again. File hierarchy, file permissions and unzipping files, moving files.

> Please mention step-by-step solution as I am new to Linux environment.
Advanced thanks .

Are you copy and pasting commands? You are new to linux and already installing Hadoop? 

> hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ mv hadoop-1.0.3 /usr/local/

- [COLOR=#ff0000]Error:  mv: cannot move &#8216;hadoop-1.0.3&#8217; to &#8216;/usr/local/hadoop-1.0.3&#8217;: Permission denied[/COLOR]

***Question 1 : - How to get rid of this error ???***

Use "**sudo **mv [source] [destination]"  The location you want to put the folder hadoop-1.0.3 is not writable to the normal user. 

> - hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ sudo chown -R hduser:hadoop hadoop
[sudo] password for hduser: 
[COLOR=#ff0000]**chown: cannot access &#8216;hadoop&#8217;: No such file or directory**[/COLOR]

- ***How to get rid of this ???***

I guess you have a typo? Try "ls -l" to see the files and directories on the current directory. Also use the Tab key for auto completion to save some typing.
Do you see a folder hadoop? Or is it hadoop-1.0.3 folder? Or perhaps you already the move the folder that why it doesn't exist.

Perhaps you need to have a primer on the Linux Command line? Here's a free easy to read pdf [http://sourceforge.net/projects/linuxcommand/files/TLCL/13.07/TLCL-13.07.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/13.07/TLCL-13.07.pdf/download)

---

### Post by Shamik_Biswas on 2014-10-21
Thanks "[The Philippine Team]("http://ubuntuforums.org/forumdisplay.php?f=303")" for your support :D
[I]
"Are you copy and pasting commands? You are new to linux and already installing Hadoop?"[/I]
:(  Trying to explore new things in life.

*"Perhaps you need to have a primer on the Linux Command line? Here's a free easy to read pdf [http://sourceforge.net/projects/linu...7.pdf/download]("http://sourceforge.net/projects/linuxcommand/files/TLCL/13.07/TLCL-13.07.pdf/download")"*
Absolutely. Many thanks for the PDF. :D


[COLOR=#0000ff]_Suggestion 1:_ Use "**sudo **mv [source] [destination]"  The location you want to put the folder hadoop-1.0.3 is not writable to the normal user.[/COLOR]

_Steps that I followed :_

shamik@shamik-HP-Pavilion-g6-Notebook-PC:~$ su - hduser
Password: 
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ ls -l
total 183360
drwxr-xr-x 14 hduser hadoop      4096 May  9  2012 hadoop-1.0.3
-rw-r--r--  1 hduser hadoop 187750400 May  9  2012 hadoop-1.0.3.tar

hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ sudo mv hadoop-1.0.3.tar /usr/local/
[sudo] password for hduser: 
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ cd /usr/local
hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ ls -i
1312604 bin  1312605 etc  1312606 games  1060044 hadoop-1.0.3.tar  1312607 include  1312608 lib  1186679 man  1312609 sbin  1312610 share  1312611 src
[COLOR=Blue]
_Result :_ hadoop-1.0.3.tar successfully moved to /usr/local/

----------------------

Now I am trying to extract the [COLOR=Blue]"hadoop-1.0.3.tar[/COLOR]" in /usr/local/

[/COLOR]_What I did :_[COLOR=Blue]

[/COLOR]hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ ls -l
total 183388
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 bin
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 etc
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 games
-rw-r--r-- 1 hduser hadoop 187750400 May  9  2012 hadoop-1.0.3.tar
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 include
drwxr-xr-x 4 root   root        4096 Jul 23 04:33 lib
lrwxrwxrwx 1 root   root           9 Oct 19 02:58 man -> share/man
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 sbin
drwxr-xr-x 7 root   root        4096 Jul 23 04:34 share
drwxr-xr-x 2 root   root        4096 Jul 23 04:31 src

hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ sudo tar xzf hadoop-1.0.3.tar.gz
tar (child): hadoop-1.0.3.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ sudo tar xzf hadoop-1.0.3.tar

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
[I][B]
Question : How to remove these errors and successfully extract ??[/B][/I]



Thanks in advance.

---

### Post by nerdtron on 2014-10-21
> 
hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ ls -l
total 183360
**drwxr-xr-x 14 hduser hadoop      4096 May  9  2012 hadoop-1.0.3**
-rw-r--r--  1 hduser hadoop 187750400 May  9  2012 hadoop-1.0.3.tar


I see that the hadoop folder is already extracted here. Why are you moving the .tar to /usr/local?
You can just move the folder hadoop-1.0.3 into the /usr/local/ folder
```
sudo mv hadoop-1.0.3 /usr/local/
```

> hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ sudo tar xzf **hadoop-1.0.3.tar.gz**
**tar (child): hadoop-1.0.3.tar.gz: Cannot open: No such file or directory**
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


I told you already. The **filenames **should be exact. The file you want to extract is **hadoop-1.0.3.tar **and not **hadoop-1.0.3.tar.gz**. Of course you'll get the "no such file" error since the file is not named **hadoop-1.0.3.tar.gz.**

> hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local$ sudo tar xzf hadoop-1.0.3.tar

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

You clearly don't know the difference between .tar and .tar.gz files? And you also don't know the syntax of the tar command?
This file is not gzip. Therefore you need to change the options on the tar command and remove the -z since it not gzip format.
```
sudo tar xvf  **hadoop-1.0.3.tar **
```

x - extract
v - verbose
f - file

---

### Post by Shamik_Biswas on 2014-10-23
Hi [The Philippine Team]("http://ubuntuforums.org/forumdisplay.php?f=303"),

Your suggestion WORKED.  :D :D :D 

Learning these things very well with your help.

Going through further Hadoop installation steps...will post again if face further difficulty. :P

Thanks a TON for your constant support. :) :) :)
[COLOR=Blue]

[/COLOR]

---

### Post by mörgæs on 2014-10-23
If the problem is solved please mark the thread so.

---

### Post by Shamik_Biswas on 2014-10-26
..and continuing with some related probs :

-- Successfully configured all settings and hadoop XMLs (with all the suggestion and helps). Now tried the following :

hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ cd /usr/local/hadoop/bin/
hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hadoop/bin$ start-all.sh
Warning: $HADOOP_HOME is deprecated.

starting namenode, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-namenode-shamik-HP-Pavilion-g6-Notebook-PC.out
localhost: starting datanode, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-datanode-shamik-HP-Pavilion-g6-Notebook-PC.out
localhost: starting secondarynamenode, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-secondarynamenode-shamik-HP-Pavilion-g6-Notebook-PC.out
starting jobtracker, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-jobtracker-shamik-HP-Pavilion-g6-Notebook-PC.out
localhost: starting tasktracker, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-tasktracker-shamik-HP-Pavilion-g6-Notebook-PC.out


-- After that, if I submit the "jps" command, the output should show the 6 listed processes. However, I entered the "jps", and the output is like following :
[COLOR=#ff0000]
hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hadoop/bin$ jps
The program 'jps' can be found in the following packages:
 * openjdk-7-jdk
 * openjdk-6-jdk
Ask your administrator to install one of them[/COLOR]

[COLOR=#ff0000]***Question-1 : How to solve this ???***[/COLOR]

-- When I stopped the node, the output is like following :

hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hadoop/bin$ stop-all.sh
Warning: $HADOOP_HOME is deprecated.

stopping jobtracker
localhost: no tasktracker to stop
no namenode to stop
localhost: no datanode to stop
localhost: stopping secondarynamenode
[COLOR=#ff0000]
It seems like, only "jobtracker" and "secondarynamenode" were started as they were the only one to stop. [/COLOR]
[COLOR=#ff0000]***Question-2 : How to solve this ???***[/COLOR]

Thanks in advance.

---

### Post by nerdtron on 2014-10-26
> hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hadoop/bin$ jps
The program 'jps' can be found in the following packages:
* openjdk-7-jdk
* openjdk-6-jdk
Ask your administrator to install one of them


It says install the openjdk packages so does it install:
```
sudo apt-get install openjdk-7-jdk
```
or 
```
sudo apt-get install openjdk-6-jdk
```

> hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hadoop/bin$ stop-all.sh
Warning: $HADOOP_HOME is deprecated.

stopping jobtracker
localhost: no tasktracker to stop
no namenode to stop
localhost: no datanode to stop
localhost: stopping secondarynamenode

It seems like, only "jobtracker" and "secondarynamenode" were started as they were the only one to stop. 
No idea as I have not used hadoop before. Maybe it is was caused by the required openjdk packages that are not installed?

---

### Post by Shamik_Biswas on 2014-10-31
Hi,

I discovered that it was my HDFS-SITE.xml configuration prob...that is why all the daemons were not starting...
However, I am able to fix it....and all the daemons are starting right now when I use the 'jps' command. 

Now the problem is somewhere else...

hduser@s.....: $ cd /usr/local/hadoop/bin
hduser@s.....: /usr/local/hadoop/bin$ **hadoop fs -ls**

Warning: $HADOOP_HOME is deprecated

[COLOR=#ff0000]**ls: Cannot access.:No such file or directory.**[/COLOR]
[COLOR=#0000ff]
***_Question:_ How to get rid of this ???***[/COLOR]

---

