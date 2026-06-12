---
title: "gyach webcam problems"
date: 2008-02-11
forum: General Help
---

### Post by eul0gy on 2008-02-11
i just got gyachE installed and im trying to send my cam. i can see that it's reading it but all people can see if a white screen. what do i do??

---

### Post by spiderbatdad on 2008-02-11
You have to select the broadcasting button in the camera window...you probably know, Have you tried the connection tab in the camera window, then properties to manually adjust some of the settings? Though it should be automatic. Maybe turn the brightness down.

---

### Post by lingnoi on 2008-02-11
Check your webcam settings by clicking setup->general tab. Make sure enable web cam features is ticked and your webcam device is "/dev/video0"

What kind of web cam are you using? Make and model?

If Gyachi doesn't work you could give the Skype beta ago..

---

### Post by eul0gy on 2008-02-12
My Cam Is A Labtec Easy Cam I Believe

---

### Post by alecz20 on 2008-04-08
When I try to use my webcam, I click "start my webcam" and I get three messages:

1) Gyachi (webcam broadcaster):
An error occurred at 'ioctl VIDIOCSPICT'.
Could not set camera proprieties.

2) Gyachi (webcam broadcaster):
Error while querying mmap-buffers.

3) Gyachi (webcam broadcaster):
An error occurred at 'ioctl VIDIOCSPICT'.
Could not set camera proprieties.

then I click ok on message 1) or 3) and it closes.

I can however see someone elses webcam.

The webcam device is /dev/video0

Also the webcam works perfectly in aMSN, and with Cheese.

Any ideas?

---

### Post by alecz20 on 2008-04-08
How do I subscribe to a thread without posting a new message?:confused:

---

### Post by loell on 2008-04-08
do a  

```
lsusb
```  

copy and paste the output here.

also, does your webcam work with other webcam based applications?

you can subscribe, through **thread tools** menu.

---

### Post by Sef on 2008-04-08
> How do I subscribe to a thread without posting a new message?


Read [Post #9 in Tutorials on Forum Basics]("http://ubuntuforums.org/showthread.php?t=726150").

---

### Post by alecz20 on 2008-04-09
this is the output:

alex@alex-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:09b0 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

Also, as I said in my previous post, the webcam works perfectly with aMSN and Cheese (the program that allows you to take pictures and have effects on the image)

Now I saw that my webcam is actually a Logitech one (I might have forgotten to mention that it's build in the laptop)

So what do you think about this?

Thanks!

---

### Post by alecz20 on 2008-04-09
> **Sef said:**
> Read [Post #9 in Tutorials on Forum Basics]("http://ubuntuforums.org/showthread.php?t=726150").

Thanks! Nice thread!

---

### Post by loell on 2008-04-09
the driver of your webcam is uvc/v4l2 , in which case gyachi could not detect it by default without a bit of a complex tweak ,

if you are in the mood for tweaking and compiling then this one might help, 
[http://ubuntuforums.org/showthread.php?t=431290]("http://ubuntuforums.org/showthread.php?t=431290")

if you just like something that works for now,   kopete would be a good one too.

---

### Post by alecz20 on 2008-04-09
I might give a try to compiling gyachi, but I have a question. Would kopete work with Yahoo nmessenger clients and provide text chat, webcam and "pc-to-pc calls" ?

---

### Post by loell on 2008-04-09
yes definitely, with text chat and webcam :)

but pc to pc call, it couldn't. i'd still recommend gizmo, to call your yahoo contact.

---

### Post by eul0gy on 2008-04-10
I've downloaded all the files i believe, but when i try to find in in the terminal it says no such file or directory

---

### Post by spiderbatdad on 2008-04-10
gyache has a deb for Gutsy on sourceforge.
[http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)

---

### Post by eul0gy on 2008-04-10
LoL i downloaded the file from sourceforge. what now??

---

### Post by eul0gy on 2008-04-10
LoL i downloaded the file from sourceforge. what now??

---

### Post by eul0gy on 2008-04-10
Can someone guide me step by step through instalation??  It'd be greatly appreciated

---

### Post by Oldsoldier2003 on 2008-04-10
> **eul0gy said:**
> LoL i downloaded the file from sourceforge. what now??

right click, open with GDebi installer

---

### Post by spiderbatdad on 2008-04-10
Linked the Gusty deb in previous post...just click on it.

---

### Post by eul0gy on 2008-04-10
I'm trying to install Gyachi Enhanced. i've downloaded the packages, deleted the packages, reinstalled them, I've done everything on these forums i've searched for and nothing seems to work. Should I get automatix? Some step by step help would be the best thing ever!!!  HELP!!!!

---

### Post by eul0gy on 2008-04-10
I right click, all i can do is open with archive manager

---

### Post by spiderbatdad on 2008-04-10
You already have a post running on this. Why would you start another?
I have linked you to a deb package for gyache. All you do is download the package to your desktop and click on it. IT self-installs.

---

### Post by Tatty on 2008-04-10
I am not familar with this software.  Could you provice a link to the site you are trying to get it from.

**Edit:** Late posting... follow Spiderbatdad's advice

---

### Post by eul0gy on 2008-04-10
which one do i download???  im running 7.04 feisty

---

### Post by eul0gy on 2008-04-10
[http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)

Do I need to download gdebi??

---

### Post by loell on 2008-04-10
the one for ubuntu edgy, it should be there.

---

### Post by Tatty on 2008-04-10
> **eul0gy said:**
> I right click, all i can do is open with archive manager


Try double-clicking, this should open Gdebi which will install the .deb for you.  If not, try to install gdebi with:

```
sudo apt-get install gdebi
```

---

### Post by eul0gy on 2008-04-10
I downloaded the file, it automatically opens in gdebi. here's what I get:

Error: Dependency is not satisfiable.: libasound2

???

---

### Post by eul0gy on 2008-04-10
i've been trying to install gyache for like an hour and no luck. help??

---

### Post by eul0gy on 2008-04-10
Installing gyache

---

### Post by loell on 2008-04-10
double posting doesn't really help, its also an abuse 

[http://ubuntuforums.org/showthread.php?t=748906&highlight=gyachi](http://ubuntuforums.org/showthread.php?t=748906&highlight=gyachi)

[http://ubuntuforums.org/showthread.php?t=751701&highlight=gyachi](http://ubuntuforums.org/showthread.php?t=751701&highlight=gyachi)


stop it..

---

### Post by p_quarles on 2008-04-10
Cross-posted threads merged.

---

### Post by alecz20 on 2008-04-11
Hello,

I installed kopete and gizmo and they look very promising, and do at least as much as ghyaci, and also look neater.

Now I want to remove ghyaci, but I can't find it in apt-get so I think i installed it with a deb package. How can I remove it? or do I need the deb package to remove it?

Thanks!

---

### Post by loell on 2008-04-11
in the command line,

```
sudo apt-get remove gyachi
```

---

### Post by alecz20 on 2008-04-11
Thanks, 

This worked, however only after re-installing using the package you posted a few messages above.

I think I might have installed gyachi from source long time ago, so first time i tried "sudo aptitude remove gyachi, I got error (package not found or something)

Now it's removed, thanks for the help.

On the other hand I have a question. I just tried to re-compile from source to make a package, so I can remove it, but I got errors on ./configure, saying there were some problems in the code (like undeclared functions)... in the end I couldn't compile.

My question is: Why in the Linux world so many programs need to be compiled by the end-users? Why aren't packages made by the developers for all major Linux distros?

Compiling for the average person is really not the easiest thing to do: you need all dependencies, all libraries, all dev-tools, and alos admin rights.

So... what is the reason programs are released with source code which can sometimes be compiled in three steps, why aren't the developers finishing their product?

Thanks again!

---

### Post by loell on 2008-04-11
compiling is not intended for new users, packages are made by packagers ,but they are not paid to do packaging, they just volunteered.  

if time allows them to package then they will, mostly.  

btw, gyachi have binary packages deb and rpm are  at their site.

[http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by p_quarles on 2008-04-11
I would also point out that there are numerous tools for relatively effortless packaging of compiled programs. The easiest of all is checkinstall. 

I use checkinstall to package many programs for myself, but its ease of use is a tradeoff: the packages it creates are not going to meet Debian packaging guidelines, and thus aren't really suitable for distribution.

---

### Post by alecz20 on 2008-04-12
I was about to say that I would like to become a package maintainer mostly because I figured how to make my own packages from source code using checkinstall. But if you say checkinstall is not really suitable for debian distribution, then what should I use?

---

### Post by loell on 2008-04-12
[http://www.debian.org/doc/maint-guide/]("http://www.debian.org/doc/maint-guide/")

---

