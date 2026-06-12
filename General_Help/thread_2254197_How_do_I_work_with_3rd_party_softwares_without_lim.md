---
title: "How do I work with 3rd party softwares without limitations"
date: 2014-11-25
forum: General Help
---

### Post by wert2 on 2014-11-25
&#65279;Hi! I am used to designing websites in Windows 7 using wampp server, however my pc is 32bit pentium4 with 2.4ghz, 1.2gb ram and on-board video and thus slow in Windows 7. So recently I&#8217;ve tried Ubuntu and Linux Mint but they were problematic with graphics so I found one that works which is Xubuntu 14 and found it extremely fast on my PC and it has GIMP, Abi Word and an HTML editor built in so all I needed was a local server and since Xubuntu matches my hardware very well I want to use it. 

So i have installed in to a partition in one of my my hard drives and now I dual boot it with Windows 7. Since I found installing php, apache & mysql separately donkey work and time consuming, I decided to use Xampp server 1.8 which I am familiar with more and is a single installation of a full sever. So I downloaded in to my flash drive and installed it in Xubuntu using this tutorial: [http://computernetworkingnotes.com/ubuntu-12-04-tips-and-tricks/how-to-install-xampp-1-8-2-in-ubuntu.html](http://computernetworkingnotes.com/ubuntu-12-04-tips-and-tricks/how-to-install-xampp-1-8-2-in-ubuntu.html). 

On the first run after installation Xampp opened a graphical control panel where it had an FTP and it was working fine just like I&#8217;m used to in wamp on windows. Now after restarting my PC, I cannot open Xampp&#8217;s graphical control panel. The only options I have is starting the server with "sudo /opt/lampp/lampp start". 

I am having a problem making folders and moving website files in /opt/lampp/htdocs/ using Xubuntu file manager because the create folder, create document and paste options are not active it's like their blocked or something. 

So I spent countless hours researching in forums and reading the Xampp docs for Linux and finally I was able to actually load Xampp&#8217;s graphical control panel and use the Xampp FTP to make folders and move in one of my php sites. However this was just wasting my time and helping me very slightly because the website was not working properly since it couldn&#8217;t modify it&#8217;s settings and php files when it runs and php websites need to change code in .php files in order to do something.

What can I do now? please tell me straight forward if small fixes are just a waste of time and if I need to properly learn Linux. What free book or what process can you recommend for me to do or learn in order for me to work flawlessly like I am used to in windows and how long can it take me. Please don&#8217;t help me with small sudo fixes or codes that will just stress me more rather just advice me on the best idea to do since I have to work on alot of websites, plus I am using this servers softwares for business not just fun or learning. By the way I am amazed by the lightning speed of this OS.

My complete PC specs can be seen here on this table: [http://www.mss.net/Links/DellDocs/OptiGX260/UserGuide/specs.htm](http://www.mss.net/Links/DellDocs/OptiGX260/UserGuide/specs.htm). My specific PC is the&#65279; small desktop computer(SD). :-k

---

### Post by ian-weisser on 2015-02-25
> **wert2 said:**
> &#65279;please tell me straight forward if small fixes are just a waste of time and if I need to properly learn Linux. What free book or what process can you recommend for me to do or learn in order for me to work flawlessly like I am used to in windows and how long can it take me.

Consider yourself gently told.
Actually, I'm proud of you. It's *really hard* to realize that your years of experience on one platform might actually be holding you back on another platform.
Your willingness to keep your Windows skills, and to learn new Linux skills alongside, is highly commendable and may greatly increase your earning power.

The specific problem of can't create-files or can't-paste-files seems like a permission problem. If the install created an xampp group, add your user to that group. But that's a patch on unsupported software installed inappropriately. There may be more problems that you can't get support on.

My recommendation:
1) Do a fresh install of _buntu of your choice.
2) Install the fully-supported LAMP stack ( [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) )
3) The best framework for you depends upon what you do and how you do it. There are several PHP frameworks in Software Center. Since I don't use wamp, I can't tell you which is most like it. Try them all. You might discover one you like better...or at least one you can be happy with.

Honestly, "It doesn't work" is a critical bug. It may have several causes. If the software were in Debian/Ubuntu, which has a pretty low barrier to entry (it's reasonably open, it compiles, it works, it doesn't break the system), we could do a lot to help troubleshoot the problem. But it's not.

---

### Post by coldraven on 2015-02-26
> I am having a problem making folders and moving website files in  /opt/lampp/htdocs/ using Xubuntu file manager because the create folder,  create document and paste options are not active it's like their  blocked or something.

This is probably a permissions problem. The advice in your link said to install XAMPP as root so those folders will belong to root and not you as a user.
I'm not sure what is the best solution because you don't really want to be logged in as root all the time for security reasons.
If XAMPP creates a group you could add yourself to that group (This is just a guess)
To find out the list of groups
```
cut -d: -f1 /etc/group
```

Hopefully someone with more knowledge than me will respond.

---

### Post by tgalati4 on 2015-02-26
Rather than fight with *xampp*, install *tasksel* and run it and select LAMP.  Then create a simple website that you can use for learning.  Then bring your websites over one-by-one.  There are too many differences between how Windows and Linux handles web pages to describe in a forum post.

---

