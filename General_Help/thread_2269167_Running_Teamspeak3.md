---
title: "Running Teamspeak3"
date: 2015-03-13
forum: General Help
---

### Post by devdlp on 2015-03-13
I've did what I think is installed Teamspeak3 on my pc. But my problem is running it how do I run the program I've tried the .sh file and all i dont know where to start.

---

### Post by slickymaster on 2015-03-13
Quick google:
For 32bit OS```

wget dl.4players.de/ts/releases/3.0.15/TeamSpeak3-Client-linux_x86-3.0.15.run
sudo chmod +x TeamSpeak3-Client-linux_x86-3.0.15.run
./TeamSpeak3-Client-linux_x86-3.0.15.run
cd TeamSpeak3-Client-linux_x86/
./ts3client_runscript.sh
```
For 64bit OS```

wget dl.4players.de/ts/releases/3.0.15/TeamSpeak3-Client-linux_amd64-3.0.15.run
sudo chmod +x TeamSpeak3-Client-linux_amd64-3.0.15.run
./TeamSpeak3-Client-linux_amd64-3.0.15.run
cd TeamSpeak3-Client-linux_amd64/
./ts3client_runscript.sh
```

Follow on screen display to enter a nickname and log into one of the servers.

---

### Post by devdlp on 2015-03-14
Thank you

---

### Post by slickymaster on 2015-03-14
You're welcome. Happy *buntuing.

---

### Post by devdlp on 2015-03-14
im sorry this is not solved. When i closed the program cuz it was running slow i cant open it again and i did 
cd TeamSpeak3-Client-linux_amd64/
./ts3client_runscript.sh
to bring it back up and also saved it to my launcher and it still dissappeared so what do i do to open the already installed program?

can i get help with this please??

---

### Post by slickymaster on 2015-03-16
Can you please post back here what the terminal outputs when you run the command:```
./ts3client_runscript.sh
```

---

### Post by devdlp on 2015-03-27
it worked the first time but now it wont work.
it shows:  deven@deven-Satellite-L455:~/Desktop/TeamSpeak3-Client-linux_amd64$ ./ts3client_runscript.sh
bash: ./ts3client_runscript.sh: Permission denied

---

### Post by slickymaster on 2015-03-27
Please try```
sudo ./ts3client_runscript.sh
```

---

### Post by devdlp on 2015-03-27
it shows command not found

---

### Post by slickymaster on 2015-03-27
Can you please post back the output of```
ls -l ~/Desktop/TeamSpeak3-Client-linux_amd64/
```

---

### Post by devdlp on 2015-03-28
deven@deven-Satellite-L455:~$ ls -l ~/Desktop/TeamSpeak3-Client-linux_amd64/
total 30900
drwx------ 2 deven deven     4096 Aug  4  2014 accessible
-rw------- 1 deven deven   152840 Aug  4  2014 CHANGELOG
-rwx------ 1 deven deven   117302 Aug  4  2014 error_report
drwx------ 2 deven deven     4096 Aug  4  2014 gfx
drwx------ 2 deven deven     4096 Aug  4  2014 imageformats
-rwx------ 1 deven deven  5372056 Aug  4  2014 libQt5Core.so.5
-rwx------ 1 deven deven  3847824 Aug  4  2014 libQt5Gui.so.5
-rwx------ 1 deven deven  1273040 Aug  4  2014 libQt5Network.so.5
-rwx------ 1 deven deven   250296 Aug  4  2014 libQt5Sql.so.5
-rwx------ 1 deven deven  6241232 Aug  4  2014 libQt5Widgets.so.5
-rwx------ 1 deven deven   200552 Aug  4  2014 libquazip.so.1
-rw------- 1 deven deven    36708 Aug  4  2014 LICENSE
drwx------ 6 deven deven     4096 Aug  4  2014 news
-rwx------ 1 deven deven   151266 Aug  4  2014 package_inst
-rw-rw-r-- 1 deven deven        0 Mar 13 19:39 ?PII@0??@8
drwx------ 2 deven deven     4096 Aug  4  2014 platforms
drwx------ 6 deven deven     4096 Aug  4  2014 plugins
-rw------- 1 deven deven      313 Aug  4  2014 plugin_sdk.html
-rw------- 1 deven deven       26 Aug  4  2014 qt.conf
drwx------ 6 deven deven     4096 Aug  4  2014 sound
drwx------ 2 deven deven     4096 Aug  4  2014 soundbackends
drwx------ 2 deven deven     4096 Aug  4  2014 sqldrivers
drwx------ 6 deven deven     4096 Aug  4  2014 styles
drwx------ 2 deven deven     4096 Aug  4  2014 translations
-rwx--x--x 1 deven deven 12834736 Aug  4  2014 ts3client_linux_amd64
-rw------- 1 deven deven      283 Aug  4  2014 ts3client_runscript.sh
-rwx------ 1 deven deven  1088128 Aug  4  2014 update
deven@deven-Satellite-L455:~$

anything?

---

### Post by slickymaster on 2015-03-28
In the terminal please run```
sudo chmod +x ~/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
```and afterwards```
cd Desktop/TeamSpeak3-Client-linux_amd64
./ts3client_runscript.sh
```

---

### Post by devdlp on 2015-03-29
deven@deven-Satellite-L455:~$ sudo chmod +x ~/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
[sudo] password for deven: 
deven@deven-Satellite-L455:~$ cd Desktop/TeamSpeak3-Client-linux_amd64
deven@deven-Satellite-L455:~/Desktop/TeamSpeak3-Client-linux_amd64$ ./ts3client_runscript.sh/
bash: ./ts3client_runscript.sh/: Not a directory
deven@deven-Satellite-L455:~/Desktop/TeamSpeak3-Client-linux_amd64$ ./ts3client_runscript.sh
./ts3client_runscript.sh: line 16: ./ts3client_linux_amd64: cannot execute binary file: Exec format error
deven@deven-Satellite-L455:~/Desktop/TeamSpeak3-Client-linux_amd64$

---

### Post by slickymaster on 2015-03-29
Sorry, I mistype my last command. The correct one is ```
./ts3client_runscript.sh
```

I've edited my last post to also correct it there.

---

### Post by devdlp on 2015-05-06
iTS STILL NOT WORKING

---

### Post by slickymaster on 2015-05-06
> **devdlp said:**
> iTS STILL NOT WORKING
Using all capital letters in electronic communication is like shouting at someone in person and that is not acceptable in these forums.

That said, just stating that it isn't working isn't enough. What are the error messages you get, if any, when you run the command you were provided?

---

### Post by devdlp on 2015-05-06
I apologize for that.
Im gonna go back to the beginning i cant even get this to work.
 sudo chmod +x ~/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
[sudo] password for deven: 
chmod: cannot access &#8216;/home/deven/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh&#8217;: No such file or directory
deven@deven-Satellite-L455:~$ cd Desktop
deven@deven-Satellite-L455:~/Desktop$ cd TeamSpeak3-Client-linux_amd64
bash: cd: TeamSpeak3-Client-linux_amd64: No such file or directory
deven@deven-Satellite-L455:~/Desktop$ sudo chmod +x ~/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
chmod: cannot access &#8216;/home/deven/Desktop/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh&#8217;: No such file or directory
deven@deven-Satellite-L455:~/Desktop$

---

### Post by slickymaster on 2015-05-06
> **devdlp said:**
> deven@deven-Satellite-L455:~$ ls -l ~/Desktop/TeamSpeak3-Client-linux_amd64/
total 30900
drwx------ 2 deven deven     4096 Aug  4  2014 accessible
-rw------- 1 deven deven   152840 Aug  4  2014 CHANGELOG
-rwx------ 1 deven deven   117302 Aug  4  2014 error_report
drwx------ 2 deven deven     4096 Aug  4  2014 gfx
drwx------ 2 deven deven     4096 Aug  4  2014 imageformats
-rwx------ 1 deven deven  5372056 Aug  4  2014 libQt5Core.so.5
-rwx------ 1 deven deven  3847824 Aug  4  2014 libQt5Gui.so.5
-rwx------ 1 deven deven  1273040 Aug  4  2014 libQt5Network.so.5
-rwx------ 1 deven deven   250296 Aug  4  2014 libQt5Sql.so.5
-rwx------ 1 deven deven  6241232 Aug  4  2014 libQt5Widgets.so.5
-rwx------ 1 deven deven   200552 Aug  4  2014 libquazip.so.1
-rw------- 1 deven deven    36708 Aug  4  2014 LICENSE
drwx------ 6 deven deven     4096 Aug  4  2014 news
-rwx------ 1 deven deven   151266 Aug  4  2014 package_inst
-rw-rw-r-- 1 deven deven        0 Mar 13 19:39 ?PII@0??@8
drwx------ 2 deven deven     4096 Aug  4  2014 platforms
drwx------ 6 deven deven     4096 Aug  4  2014 plugins
-rw------- 1 deven deven      313 Aug  4  2014 plugin_sdk.html
-rw------- 1 deven deven       26 Aug  4  2014 qt.conf
drwx------ 6 deven deven     4096 Aug  4  2014 sound
drwx------ 2 deven deven     4096 Aug  4  2014 soundbackends
drwx------ 2 deven deven     4096 Aug  4  2014 sqldrivers
drwx------ 6 deven deven     4096 Aug  4  2014 styles
drwx------ 2 deven deven     4096 Aug  4  2014 translations
-rwx--x--x 1 deven deven 12834736 Aug  4  2014 ts3client_linux_amd64
-rw------- 1 deven deven      283 Aug  4  2014 ts3client_runscript.sh
-rwx------ 1 deven deven  1088128 Aug  4  2014 update
deven@deven-Satellite-L455:~$
Is this still true, currently?^^^

---

### Post by devdlp on 2015-05-06
deven@deven-Satellite-L455:~/Desktop$ ls -l ~/Desktop/TeamSpeak3-Client-linux_amd64/
ls: cannot access /home/deven/Desktop/TeamSpeak3-Client-linux_amd64/: No such file or directory
deven@deven-Satellite-L455:~/Desktop$ total 30900
30900: cannot open
deven@deven-Satellite-L455:~/Desktop$

---

### Post by slickymaster on 2015-05-06
Can you please post back the output of
```
ls -l ~/Desktop/
```

---

### Post by devdlp on 2015-05-06
deven@deven-Satellite-L455:~$ ls -l ~/Desktop/
total 21480
-rwxr-xr-x 1 deven deven      299 Feb 23 16:15 Aion.desktop
-rwxr-xr-x 1 deven deven      366 Feb 17 09:59 ASIO4ALL v2 Instruction Manual.desktop
-rw-rw-r-- 1 deven deven      794 Feb 17 09:59 ASIO4ALL v2 Instruction Manual.lnk
-rwxr-xr-x 1 deven deven      256 May  6 10:15 Dxtory.desktop
-rw-rw-r-- 1 deven deven      761 May  6 10:15 Dxtory.lnk
-rwxr-xr-x 1 deven deven      323 Feb 17 09:59 FL Studio 11.desktop
-rw-rw-r-- 1 deven deven      890 Feb 17 09:59 FL Studio 11.lnk
-rwxrwxr-x 1 deven deven  3379447 Feb 23 07:44 forge-1.8-11.14.1.1328-installer.jar
drwxrwxr-x 6 deven deven     4096 Mar  1 18:08 Intruments
drwxrwxr-x 2 deven deven     4096 Feb  7 23:12 League of Legends
-rwxrwxr-x 1 deven deven      323 Feb 25 11:17 League of Legends.desktop
-rwxr-xr-x 1 deven deven      293 Feb 15 10:35 Minecraft 1.7.5.desktop
-rw-rw-r-- 1 deven deven      865 Feb 15 10:35 Minecraft 1.7.5.lnk
-rwxrwxr-x 1 deven deven   280212 Feb  6 03:47 Minecraft.jar
-rwxrwxr-x 1 deven deven  1673860 Feb 15 07:32 Minecraft Launcher.jar
-rwxr-x--x 1 deven deven 15363384 Oct 27  2009 Nexus 2 Setup.exe
-rwxrwxr-x 1 deven deven   894141 Feb 16 02:31 OptiFine_1.8.1_HD_U_C7.jar
-rwxr-xr-x 1 deven deven      336 Feb  9 05:27 secondlife-viewer.desktop
-rwxrwxr-x 1 deven deven    58876 Feb  7 01:58 strife
drwxr-xr-x 6 deven deven     4096 Apr 23 17:24 Strife
-rw-rw-r-- 1 deven deven      137 Feb 21 16:51 swappiness
-rw-rw-r-- 1 deven deven        0 Feb 21 16:49 swappiness~
-rw-rw-r-- 1 deven deven       98 Mar 14 12:14 TeamSpeak
-rw-rw-r-- 1 deven deven        0 Mar 14 12:13 TeamSpeak~
drwxrwxr-x 3 deven deven     4096 May  2 12:06 Untitled Folder
drwxrwxr-x 4 deven deven     4096 Feb 21 13:18 UrbanTerror42
drwxrwxr-x 4 deven deven     4096 Mar  1 16:51 VST's
-rwxrwxr-x 1 deven deven   125637 Mar 30 18:54 XRay-1.7.10-v2.15.2.jar
-rwxrwxr-x 1 deven deven   125138 Feb 14 17:30 XRay-1.8.1-v2.15.2.jar
deven@deven-Satellite-L455:~$

---

### Post by slickymaster on 2015-05-06
Can you please post back the output of```
ls -l ~/Desktop/TeamSpeak
```and```
ls -l ~/Desktop/TeamSpeak~
```

---

### Post by devdlp on 2015-05-06
deven@deven-Satellite-L455:~$ ls -l ~/Desktop/TeamSpeak
-rw-rw-r-- 1 deven deven 98 Mar 14 12:14 /home/deven/Desktop/TeamSpeak
deven@deven-Satellite-L455:~$ ls -l ~/Desktop/TeamSpeak~
-rw-rw-r-- 1 deven deven 0 Mar 14 12:13 /home/deven/Desktop/TeamSpeak~
deven@deven-Satellite-L455:~$

---

### Post by slickymaster on 2015-05-06
I'm at loss here. Apparently **~/Desktop/TeamSpeak3-Client-linux_amd64/** (and all its contents) is completely wiped out from your system. I even thought you may had renamed it to **~/Desktop/TeamSpeak** but that doesn't seem to be the case, since that folder is also empty.

At this point my advise would be to completely remove all traces of TeamSpeak left behind from your previous attempt and start again from scratch.

---

### Post by devdlp on 2015-05-06
im on it, ill come back if i need help

Thank sir. I started fresh and got it to work lets hope it stays that way. Thanks again man

---

### Post by slickymaster on 2015-05-06
Sure, no problem. Just glad you got it fixed.

Please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---

