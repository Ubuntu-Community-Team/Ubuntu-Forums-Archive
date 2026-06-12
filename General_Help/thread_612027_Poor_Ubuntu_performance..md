---
title: "Poor Ubuntu performance."
date: 2007-11-13
forum: General Help
---

### Post by jkarma on 2007-11-13
My laptop's stock specs are

1.6GHz Intel T2300 dual-core processo
1GB DDR RAM
120GB hard drive
(some sort of integrated intel graphics)

I am getting all sorts of crashes/ "not responding" errors. I've got it set up and really like it except for the fact that I cannot listen to a song without it locking up, or watch a video without it freezing every few seconds. Conky draws over my icons when I run it (looked for a fix, came up empty). I'm getting AWFUL download speeds regardless of my connection as well. Although I set up a static IP in Network Manager I only pull around 10kpbs with torrent files. My windows box normally runs steadily at 450kbps. And I'd like to switch it to linux as well. 

I'd appreciate any help you might have to offer. Thanks. I'll provide any info I can.

---

### Post by jfinkels on 2007-11-13
Your best bet is going to be to present each problem one at a time to the community by creating a new thread describing your problem, but I'll do what I can from here.> **jkarma said:**
> 
 I've got it set up and really like it except for the fact that I cannot listen to a song without it locking up, or watch a video without it freezing every few seconds.

What program are you using? What kind of output do you get when it crashes when you run the program from the terminal?

> Conky draws over my icons when I run it (looked for a fix, came up empty).
Move conky so that it's on an empty part of your desktop :). Conky is just a window, without borders, I believe.
> I'm getting AWFUL download speeds regardless of my connection as well. Although I set up a static IP in Network Manager I only pull around 10kpbs with torrent files.

Are you behind a firewall? A router? Does your ISP allow static IP addresses? Is there any packet loss when you try to ping an external address, like 'google.com'? You may have a problem with NAT if you're behind a router, or you may need to mess with port forwarding or something.

---

### Post by jkarma on 2007-11-14
I honestly feel like its more of a hardware configuration problem than a software problem. I see my CPU spike frequently when things lock up. I understand ubuntu has issues with dual core processors. How can I address this. What other hardware problems could be causing it. I think its much more general than software failures. Although if you can help me figure out how to install from an executable file that would be sweet as well.

---

### Post by jfinkels on 2007-11-14
> **jkarma said:**
> I honestly feel like its more of a hardware configuration problem than a software problem. I see my CPU spike frequently when things lock up. I understand ubuntu has issues with dual core processors. How can I address this. I wasn't aware that Ubuntu had "issues with dual core processors". Are you using the 32-bit or 64-bit version of Ubuntu? Search around to see if anyone else had any problems with your particular processor, or make a new thread.



> What other hardware problems could be causing it. I think its much more general than software failures.
Well it *could* be software problems, so if you want help in diagnosing the problems about which you asked, answer the questions which I asked of you in my above post.

If you don't want to, check bug reports at [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
> Although if you can help me figure out how to install from an executable file that would be sweet as well.
To run an executable file, first make sure that it is executable by typing in the terminal:```
chmod +x *nameoffile*
``` and then type the following in the terminal:```
./*nameoffile*
```

Read the links in my signature for more information, *especially* the first one about installing software, as well as psychocats.net

Let me know if you have any more questions.

---

### Post by jkarma on 2007-11-15
root@Dahlia:/home/joshua# rmdir /usr/local/bin/nview
root@Dahlia:/home/joshua# rmdir /usr/local/bin/nconvert
root@Dahlia:/home/joshua# rmdir /usr/local/bin/xnview
root@Dahlia:/home/joshua# ./ Desktop/Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4/install
bash: ./: is a directory
root@Dahlia:/home/joshua# Desktop/XnView-1.70-x86-unknown-linux2.x-static-fc4/install
  OS  : Linux, version 2.6.22-14-generic
This script will install nview/nconvert/xnview in the /usr/local/bin directory
cp: cannot stat `bin/nview': No such file or directory
cp: cannot stat `bin/nconvert': No such file or directory
cp: cannot stat `bin/xnview': No such file or directory
chmod: cannot access `/usr/local/bin/nview': No such file or directory
chmod: cannot access `/usr/local/bin/nconvert': No such file or directory
chmod: cannot access `/usr/local/bin/xnview': No such file or directory
cp: cannot stat `app-defaults/XnView.ad': No such file or directory
cp: cannot stat `man/nview.1': No such file or directory
cp: cannot stat `man/xnview.1': No such file or directory
chmod: cannot access `/usr/local/man/man1/nview.1': No such file or directory
chmod: cannot access `/usr/local/man/man1/xnview.1': No such file or directory

Done!

This is what happened following the install. I read your link but came up with jnothing for installing thes programs.

and say in terminal i run amarok. it launches the gui. then closes both the term and gui.

I really do appreciate all the help you're giving me though. Thank you.

---

### Post by jfinkels on 2007-11-15
If it is installed, then you should be able to run the program from the terminal. To run the program, type:```
xnview
```(I assume this is the name of the program).

If you are still having problems installing xnview, take a look at the following thread: [http://ubuntuforums.org/archive/index.php/t-86306.html](http://ubuntuforums.org/archive/index.php/t-86306.html)

As for amarok...you open the terminal, type 'amarok', and then they *both* close? That's odd...open another terminal after that happens and see if the process 'amarok' is still running by typing the following:```
ps ax | grep amarok
```This checks the list of running processes to see if amarok is in it.

---

### Post by jkarma on 2007-11-15
joshua@Dahlia:~$ ps ax | grep amarok
 6603 pts/0    S+     0:00 grep amarok

is what I get after both windows close. Watching the term as it starts it gets repeated error messages before shutting them down.

And xnview will not start. I'm going to go read that link now.

---

### Post by njparton on 2007-11-15
Check your computer's not overheating, check heat sinks, thermal grease stuff like that?

Also consider runing memtest from a bootable CD to check that you've not got any dodgy RAM.

---

### Post by jkarma on 2007-11-15
I have fixed Xnview and have it up and running right. 

It's my laptop so Theres no good way for me to go check the thermal grease or anything internal. 

I'll try checking my ram and see what comes up.

---

### Post by jkarma on 2007-11-16
<a href="http://photobucket.com" target="_blank"><img src="http://img.photobucket.com/albums/v181/Jkarma/Screenshot-4.png" border="0" alt="Photo Sharing and Video Hosting at Photobucket"></a>

WHAT THE HELL.

---

### Post by jfinkels on 2007-11-16
XnView was created with a different distribution in mind (a distribution that uses the .rpm package as opposed to the .deb package), and people have had a lot of trouble with xnview on Ubuntu. May I suggest another program, like 'gqview' for example, or some other program that is in the Ubuntu repositories, so that you can install it easily:```
sudo aptitude install gqview
```

---

