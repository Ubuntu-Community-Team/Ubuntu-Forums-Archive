---
title: "Firefox got clumsy..."
date: 2017-08-26
forum: General Help
---

### Post by Innernet on 2017-08-26
Hi. 
Running Ubuntu 14.04.  Had not updated **anything at all** since 2014, and everything ran normally fine.

A couple of weeks ago did updating.  Now browsing is clumsy, freezes while typing, or slow, really jumpy scrolling, sometimes shows libavcodec as not working near the top of screen. How do I delete such that I never needed before and will never want ?

How to determine if it is a Ubuntu thing, a Firefox thing, both or what ?  Which forum should I address?  This or the browser ?

The updated Firefox browser shows as 55.0.2 -32bit.  Visiting the Firefox site, the splash screen shows that my browser is not current, 'click here to update to 55.0.2. '  Someone is goofing there.  
Any guidance, please ?.

---

### Post by walts48 on 2017-08-26
Well, Mozilla did release version 55.0.3 yesterday.

I suggest you try refreshing your profile.

Use Help > Troubleshooting Information and click the Refresh Firefox button.

---

### Post by Innernet on 2017-08-26
Thank you, Walts48.

Still scratching my head...[ATTACH=CONFIG]276513[/ATTACH]

---

### Post by vasa1 on 2017-08-26
> **Innernet said:**
> Thank you, Walts48.

Still scratching my head...
About what?

---

### Post by Innernet on 2017-08-26
Hi.
About 'refreshing profile' and if it is a Ubuntu thing or a Firefox thing.  
Tried to get rid of 'libavcodec and is not found :

[ATTACH=CONFIG]276514[/ATTACH]

---

### Post by vasa1 on 2017-08-26
Please open a terminal and run```
sudo apt-get update
```Copy the entire output and post it here.


Then, please open a terminal and run```
sudo apt-get upgrade
```Copy the entire output and post it here.

Then please run```
uname -a
```Copy the entire output and post it here.

The refresh profile is "a firefox thing".

---

### Post by Innernet on 2017-08-26
Thanks.

sudo apt-get update
[sudo] password for externet: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [960 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                    
Fetched 1,026 kB in 4s (244 kB/s)                    
Reading package lists... Done
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ 

----> Is the next step 'upgrade' for the latest release of of Ubuntu or for the latest version of Firefox ?

(To be continued)

---

### Post by vasa1 on 2017-08-26
> **Innernet said:**
> ...
----> Is the next step 'upgrade' for the latest release of of Ubuntu or for the latest version of Firefox ?
...
It is for upgrading your existing software. You'll see that when you run the command. If you have doubts, press "n" when you see the "Y/n" prompt.

But post the entire output here! And the output of```
uname -a
```

---

### Post by Innernet on 2017-08-27
Thanks again.
No Y/N prompted.  ¿? 
If that is to upgrade Ubuntu to 17.04; prefer not to at this time, and stay with 14.04.

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get upgrade
[sudo] password for externet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ uname -a
Linux externet-Compaq-Presario-CQ60-Notebook-PC 3.13.0-128-generic #177-Ubuntu SMP Tue Aug 8 11:41:08 UTC 2017 i686 athlon i686 GNU/Linux
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$

---

### Post by mörgæs on 2017-08-29
If you haven't updated software for years I suggest that you at least change all passwords which have been entered using the breached operative system. 

In addition to that, if it were my computer I would also do a fresh install of a recent 64 bit Buntu. A CQ60 does not need a 32 bit install.

---

### Post by Innernet on 2017-08-29
Thank you.

The software **_was_** not updated in years as on post #1.  Three weeks ago, was updated and is current onto 14.04LTS

If the processor is 64 bit; it has worked fine and smooth for many years with 32 bit operative system.  After the update, the symptoms started.
Can you explain how is the OS  "breached", please ?  
Will proceed to backup data and install a fresh current 64 bit version as suggested.

---

### Post by Innernet on 2017-08-29
Hi.
I have the habit of 'never' upgrading operative systems.  Instead, I **always** buy a new hard drive; load the latest version and archive the old drive untouched.  That way I have a real backup, and has served me very well since Ubuntu 5.10.

Well, just removed my misbehaving 14.04 LTS (from this thread above)  Reinstalled the Ubuntu 10.10 old hard drive from behind the spider webs and it is like a rocket fast, clean and neat.

Am typing from the running 10.10 hard drive on the same crappy laptop.
Did the same a few moths ago looking for a file with my 7.04 hard drive and all the real superb beauty of Ubuntu was there, performing great.  I mean, GREAT  !  With the temptation of going back.

By the way, checked "About Firefox "  shows am now with version 3.6.10.  :biggrin:
Soooo nice, smooth and fast.  Even more pleasant !

---

### Post by sudodus on 2017-08-29
Smooth and fast :-) but wide open for attacks via the network connection :-(

I would recommend that you use a version, that is supported. Otherwise you get no security updates, and if you have bad luck, some malware gets into your computer. It can cause serious problems for you.

See this link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by Innernet on 2017-08-29
Thank you.
Am back, inserted the 14.04 fully updated hard drive again.

Typed "250 gb hard drive ebay" in the search window to start 'my process' of upgrading this laptop, and it showed "2" ;   three seconds later showed "250 gb hard dr" ;  seven second later finished the text.
So am buying a new hard drive to install 17.10 whenever comes out.  This one with 14.04 will go behind the spiders webs, to give company to the wonderful 10.10 ; even better 7.04; and the humble 5.10 hard drives there.

Can the "breached operative system" be explained ?  Will do as suggested, upgrade Ubuntu on 64 bit.  Been years working just fine and smooth on 32 bit with zero updates until the three week ago update brought the symptoms of post #1.

---

### Post by sudodus on 2017-08-30
The version 17.10 will be supported for only 9 months until its end of life. The versions that are released in April even years (2014, 2016, 2018 ...) are supported for longer time, 5 years for standard Ubuntu, 3 years for the Ubuntu community flavours; they have LTS (long time support).

I would recommend that, when you receive the new hard disk drive, you try 16.04.1 LTS first live (booted from the install drive), and then, if it works well, install it. It is the version with the longest support time until end of life right now, when this is written.

If standard Ubuntu is laggy in your computer, you can download and try an Ubuntu community flavour with a lighter desktop environment, Lubuntu, Ubuntu MATE or Xubuntu (of the same version, 16.04.1 LTS, which is well debugged and polished by now, and should work well in most computers). See the link in my previous post.

After that I suggest that you stay with 16.04.1 LTS until the first point release of the next long time supported version, 18.04.1 LTS will be available, maybe in August 2018. And I suggest that you keep your operating system up to date every week with the following command lines

```
sudo apt update
sudo apt full-upgrade
```

It is a good idea to keep the two newest working kernels, and to remove the older kernels to 'house-clean' the hard disk drive.

If you think it is complicated with command lines, you can [install and] use the Synaptic Package Manager for this purpose.

---

### Post by mörgæs on 2017-08-30
Breached refers to the fact that no security updates have been applied for years. I am aware that the updates are OK now. 

Here is a list of the bugs which should have been fixed by the updates. Read if you dare.
[https://usn.ubuntu.com/usn/](https://usn.ubuntu.com/usn/)

Since there have been countless of security holes present for a long time best is to take the approach that someone besides you has had access and might know your passwords. The operative system is up to date now but if you haven't changed passwords since then you are still not safe.

---

### Post by Innernet on 2017-08-30
Thank you.
> **mörgæs said:**
>  ... take the approach that someone besides you has had access and might know your passwords. The operative system is up to date now but if you haven't changed passwords since then you are still not safe.

Are you referring about passwords to access files in my laptop or passwords used from my laptop to access sites/accounts on the internet, or both ?
 
Understood a fraction of the first (August only!) of 79 pages of vulnerabilities fixed.  What a task by the developers !  =d>  Interestingly, in 12 years using Ubuntu, never had a security or virus related problem.

Typing this post, characters showed with considerable delay onto the screen -at some moments-.  Something is kaput.  No brain left to diagnose.:redface:

---

### Post by mörgæs on 2017-08-31
> **Innernet said:**
> 
Are you referring about passwords to access files in my laptop or passwords used from my laptop to access sites/accounts on the internet, or both ?

Both.

> **Innernet said:**
> 
Interestingly, in 12 years using Ubuntu, never had a security or virus related problem.


How do you know? How would you detect that someone had your passwords? 

I suggest that you take backup of your user files but not of the old operative systems. They are best deleted.

---

