---
title: "[SOLVED] firefox running very slowly on Ubuntu"
date: 2007-07-18
forum: General Help
---

### Post by MacDuff on 2007-07-18
On a new installation of Ubuntu Feisty I notice that FireFox runs extremely slowly compared to when this box had Windows XP.  Two other XP boxes run firefox at a reasonable speed.

I enquired in the Firefox forums and was told that Firfox from Ubuntu repositories is optimised for languages other than English and that causes the problem.

I find it hard to believe that language optimization could account for the huge difference in speed between Ubuntu and Windows.

Can anyone offer any advice

---

### Post by merlinus on 2007-07-18
Run a speed check on your Internet connection under ubuntu, and compare it with  gatesware.

Mine is faster with ubuntu -- even amazed the comcast techie, although he kept looking for the Start button.

:):):)

[http://performance.toast.net/](http://performance.toast.net/)

-merlin

---

### Post by Flashgordon20 on 2007-07-18
You may want to try Swiftfox ([http://getswiftfox.com/](http://getswiftfox.com/)) It's an optimized build of Firefox that works well under Ubuntu.

---

### Post by MacDuff on 2007-07-18
Speed test indicates that the upload/download speeds are identical to the Windows boxes.

The problem seems to be within the Ubuntu box.  Very slow load, scrolling etc.

Any thoughts

---

### Post by RedSquirrel on 2007-07-18
My Firefox is fine (even on a 7 year-old computer).

Is Firefox the only application that seems slow? What are the specs of your machine? I wonder if it might be a video driver issue, or maybe you don't have enough RAM (?).

---

### Post by OzzyFrank on 2007-07-18
Yeah, that's weird. Some things in Ubuntu run faster, but generally my apps perform the same in Windows and Ubuntu. Firefox is identical, as is Opera (which is actually my preferred browser coz it can save and view MHT web page archives).

I gather you haven't installed any extensions/widgets in Firefox in Ubuntu, as you would have already thought of that. They can really slow down Firefox to a crawl (depending on the plugin of course). Maybe that Swiftfox is worh alook. Best of luck!

---

### Post by dougfractal on 2007-07-18
check out

[http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)
Feisty performance - Fly like a butterfly.

> 1. Disable IPv6
Edit /etc/modprobe.d/aliases and change the line:

alias net-pf-10 ipv6

to

alias net-pf-10 off #ipv6


3. Aliasing hostname to localhost
Modify /etc/hosts's first two line as follows:

127.0.0.1 localhost yourhost
127.0.1.1 yourhost

where yourhost, is your chosen hostname. This will fasten up applications load.

---

### Post by ubanchaos on 2007-07-18
well i use firefox but i might need swiftfox try that

---

### Post by MacDuff on 2007-07-18
Thanks for the good information folks.  

I called my friendly hardware techie and described the problem to him.  He does not know a heck of a lot about Linux ( Nobody in my circle knows much about it, they are all waiting to see what kind of experience I have) but he thinks it may just be a problem with the video card.  Anyway I took the box to his shop and he is going to run some diagnostics, that I don't have and see if it is an electronic/mechanical problem.

If it is not, I will come back here and try the ideas offered.  From what I have seen so far of Linux I just cannot believe it would be that much slower, we are talking a factor of about 20x.  There has to be some major problem somewhere.  This is very important because the Linux box is supposed to replace a windows box for our communications and my wife went wild when she tried to open 6 windows on Firefox in Ubuntu and it was so slow she literally  had time to go to another part of the building, pour a cup of coffee and when she got back it only had four pages loaded.

As I said in response to Merlins comment,  the network is delivering the data at high speed, Ubuntu/Firefox just cannot deliver it to the screen.

---

### Post by UK-Wobbie on 2007-07-18
> **MacDuff said:**
> On a new installation of Ubuntu Feisty I notice that FireFox runs extremely slowly compared to when this box had Windows XP.  Two other XP boxes run firefox at a reasonable speed.

I enquired in the Firefox forums and was told that Firfox from Ubuntu repositories is optimised for languages other than English and that causes the problem.

I find it hard to believe that language optimization could account for the huge difference in speed between Ubuntu and Windows.

Can anyone offer any advice

Get fasterfox [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) that will speed things up! :)

---

### Post by MacDuff on 2007-07-19
Thanks UK.Wobbie.  That may help some but I think the problem is more serious than just needing a better caching arrangement.  

I may give fasterfox a try after I have found the real problem.

---

### Post by MacDuff on 2007-07-21
Got my Ubuntu box back from the shop.  My techie said there is nothing he could find wrong with the hardware.  He did not have any answer.

The processer is an Intel Celeron 2.00 Ghz and it has 512 mb of memory.

I cannot find any reference to the Video card on Ubuntu's Device Manager.
Can anyone point me to some software that will give me details on the installed hardware similar to what Lavaley Everest will do with the  Winoows OS?

The machine is running Ubuntu Feisty and does not have any other system installed.  I am comparing it to a 1.6 Ghz laptop running dual booted with Feisty, which is some but not a great deal better  and Windows XP and against a 2.6Ghz machine running XP only which absolutely flys.   All are using FireFox.  All use the same Internet source and all show the same download/upload rate.

When I load only one web page, performance is not too bad but scrolling is jerky, definately not smooth.  When I load 6 web pages, nobody could stand to watch it work, (or NOT work actually)

If I can't solve this problem I will have to write off Linux as a replacement for Windows as my wife needs multiple web pages loaded and this will not work.

By the way, I tried to use dougfractal's suggestion but when I tried to edit /etc/modprobe.d/aliases  I got a file not found message.  As I am very new to Linux I was probably doing something wrong.  Perhaps I have to change directories or something.

Any suggestions are welcome and would be much appreciated.

---

### Post by xarmian on 2007-07-21
Unfortunately Firefox 2.0 and all of its derivatives (Swiftfox, Swiftweasel, etc.) are simply horrible on Ubuntu.. I don't know exactly where the problem stems from (may be gnome, may be the linux port in general, it may be something about the way it interacts with the environment).. On top of that, the Flash implementation for linux is very poor and will cause an additional headache, so pages which use flash run particularly bad or can cause the browser to crash.

Opera handles the page rendering (scrolling, for example) much better, but it's not perfect.  It's what I've started using.  Unfortunately I like Firefox a lot more, and Opera has its own problems, so I find myself switching between them.

Fortunately the future's outlook is better.  The new engine used in Firefox 3.0 (Gran Paradiso) has resolved the scrolling/rendering issues (at least in the 3.0 alpha 5 release) so it runs a lot more like Opera.  It's still in Alpha though, and has its own pluthera of bugs and issues which are still being worked on.  Also most plugins don't work with it yet so I don't use it regularly.  Additionally, that can't fix the problems with Flash (for example it's impossible to log in to the Verizon wireless website if you're using Linux because the login link gets covered by flash, this happens no matter what browser you use)

In fact, because of the problems I've had getting a working web browser and a useful Usenet binary reader (for some reason all of the Usenet readers in linux are poor), I've resorted to running a VMWare server setup with WinXP.  Firefox 2.0.x actually runs much better through VMWare on WinXP than it does natively in Unbuntu/Gnome/Linux.  In fact this was my first time trying vmware and I am amazed at how cleanly it runs.. it may be a good solution to your problem, at least temporarily. (Edit: it also allows you to avoid dual boot, which I've never been a fan of, and it's free)

-Dave

---

### Post by MacDuff on 2007-07-21
Very Interesting!

Actually, I just took some time off to install Faster Fox as recommended by another poster.   It actually made things worse,  much worse.  In fact it completely killed FireFox on one test and I had to force quit.

Before I re-format this machine and go back to Windows, I will try your suggestion Dave, and will install VM Ware Server.    Actually I intended to install it anyway because I have some Windows applications that I simply must have.

I have been looking at Virtual Box as an alternative to VM Ware because I was told that it runs faster.  I also considered the purchase Version of VM Ware but I don't want to spend money on a system that I may have to dump.  Have you had any experiences with  Virtual Box or the commercial version of VM Ware?

Mac

---

### Post by xarmian on 2007-07-21
Unfortunately I have never tried either (commercial VM or virtualbox), and have only just begun experimenting with virtualization with vmware server, but I've been impressed with it.  I used Automatix2 to do the install, which made it quick and painless (automatix2 also has virtualbox) and allocated 384 megs of memory to winxp (which is the same amount it had on this laptop before, 512 megs with 128 dedicated to video, then i upgraded the memory to 1.25gig total after switching to ubuntu).  I also installed it on my roommate's desktop, he only has 512 meg total and I allocated 256 to the WinXP VM and it still runs well.

I like how the virtual machine can be modified after creation.. you can add, remove, or temporarily disable devices, or even set up a cdrom which points to a specific ISO file instead of an actual drive.  The only downside I have found is that the free vmware server only supports USB 1.1, but I consider that to be a very minor downside for my uses, and you can kind of get around it using samba shares.

Funny thing is, the installation of Windows XP went faster through the VM than it did as a regular installation, and you can continue to use the computer like normal as it installs.  Plus you can network the machines so you can access it remotely or from another setup, and/or share the desktop (much nicer than Remote Desktop).

Ok, I'm starting to sound like a commercial for virtual machines.. It just happens to be my latest toy..

-Dave

---

### Post by OzzyFrank on 2007-07-21
The only other thing I can think of is the swap file. You can check if it is working with top from the terminal. More info here:

[http://ubuntuforums.org/showthread.php?t=491757](http://ubuntuforums.org/showthread.php?t=491757)

Hope you fix this, as it isn't a common thing, and would hate for you to give up on Ubuntu because of it.

[EDIT] The more I look through your problem, the more it seems it could be the swap not working. The **top** command will show you if it is being used or not. If it isn't, then go to the bottom of the thread (above link) and the answer on how to fix it all is there.

---

### Post by MacDuff on 2007-07-21
Dave:   As I write this on one computer VM Ware Server is installing Windows XP on the problem box.

OzzyFrank:  Now that makes a lot of sense.   I had a quick look at the thread you mentioned.  I did not understand much of it because of my lack of knowledge about Linux but from what I know about Gates & Co OS it does sound like a swap problem.

When the Virtual machine is complete I will have a look at using top to find out if the swap is working. 

Thanks for all the help.  I love everything (almost) I have seen and done with Ubuntu.  I would hate to have to give it up after all the time I have invested in it, not to mention the money.  With all the time loss, travel to the computer shop and all the cost of hardware mods that did not work,  the MS product is beginning to look cheap but I am so p----d off due to a problem I had during a re-install of XP that I will do almost anything to reduce my dependence on it in future. 

Mac

---

### Post by OzzyFrank on 2007-07-21
In short, open a terminal and simply type **top** and hit enter. If it tells you you have 0 swap, that's your problem. If it shows you a number for total swap and a smaller one for swap being used, then it isn't the problem.

---

### Post by Steveway on 2007-07-21
Are you sure that you have a driver for your graphics-card installed?
Using Vesa or nv on a nvidia card can also cause the slowness.

---

### Post by xarmian on 2007-07-21
If he's having the problem that I think he's having, I don't think it has to do with swap or video drivers.. The problem seems to be specific to Firefox (and all firefox 2.0 derivatives, i don't know about earlier versions) and how they operate.  To be more descriptive, the problem is just in the way the browser functions, not how it renders a webpage or how quickly a webpage loads (which were some of the fixes suggested earlier in this thread, such as using FasterFox or adjusting ipv6 settings).  The problem can be seen easiest when you scroll certain types of websites.

Here's an example.. I'm running a processor utilization monitor in my gnome panel so I can see how much of the processor is being used as I work.  So I opened a Firefox window and went to the main ubuntuforums.org page.  After the page finished loading, the processor utilization stayed between 0% and 5%.  I then pressed the down arrow and held it to scroll to the bottom of the page.  As the page scrolled, the processor utilization jumped to 77% for the duration of scrolling.  Once I reached the bottom of the page it immediately went back to 0% and 5%.  This is consistently repeatable.

Now this is a very basic example on a very low-demand website.  If you add more images, embedded content, etc. to the page, the processor utilization will reach 100% and will cause the scrolling to be very jerky.  How much can be handled obviously depends on your processor speed.

There was a discussion about this a few weeks ago, and no resolution was reached.  There was an example webpage put up which made the issue very obvious (if you used Firefox in Ubuntu on the page it was nearly impossible to scroll, whereas Firefox in Windows handled the page without any problems).  Unfortunately that website has been modified to not cause the problem anymore, but for those interested the thread is here:

[http://ubuntuforums.org/showthread.php?t=494942]("http://ubuntuforums.org/showthread.php?t=494942")

-Dave

---

### Post by MacDuff on 2007-07-21
I don't know what happened to my last post but it disappeared somewhere between my computer and the forum, so here it is again as well as I can remember it.

The idea of possibly a bad video driver has been raised but I have no idea how to find a better one so that will have to be set aside because Dave's idea to install VM server and install Windows XP worked.  It is incredible how much faster FireFox runs in Virtual Windows.  It is almost as fast as on a dedicated Windows XP box.

I will have to see how my wife feels about it but it would suite me OK.  But then I REALLY want to get rid of MS Windows as soon as I can find replacements for all the software I depend on that seems to be written only for Windows.   She does not care.  She just was performance and ease of use.  I get to fix the d----d system every time windows crashes or screws up a file.

Thank you Xarmian for the information you provided regarding this problem.  I was beginning to doubt myself;  thought it was something I had done, or had not done, that was causing my grief.  Now at least I know it is bigger than me.   It is a bitter pill to swallow to hear (and see) how much better FireFox runs under Windows than under Linux or at least Ubuntu Linux another FOSS application.   I certainly hope that situation is corrected soon.

Thanks to all of you who responded with suggestions.  Even if they did not solve the problem, I learn a little more with each posting.  The user support is excellent and in this case Dave gets the prize for best suggestion.  It is a good workaround until the FireFox developers get the problems sorted out.

Mac

---

### Post by xarmian on 2007-07-22
I'm glad to hear it's working out for you.  I too would prefer to use an All-linux environment, but sometimes our needs simply necessitate a custom mixture to achieve what we're looking for.  I know exactly how you feel right now, only a few days ago I said "woah" as I saw how much better Firefox was running in what you would think would be a much worse environment.

I think the problem is that a lot of Linux followers turn anti-Windows.  The reality is that Windows isn't really bad, it's just commercial.  There are good things about Windows, and good things about Linux, and if you put them together you can get the best of both worlds.  People try to do this with dual-boot, but it ends up failing because if it takes a minute to switch operating systems just to run one program (not to mention having to close all your other applications) you'll never bother, you'll eventually settle on one operating system.  With virtual machines you can run two operating systems side-by-side, sharing the same disk space (or a portion of it, or none, it's up to you), you can copy-and-paste seamlessly between them, and you can run applications simultaneously that you never could before.  It gives one single machine the greatest amount of functionality possible.

Again, sounding like a commercial or a philosophical psycho, but it's true.  As a P.S. make sure you install the VMWare tools if you haven't already (boot up your XP virtual machine, select VM->Install VMWare Tools from the Virtual Machine menu).  This will correct the mouse from acting really jerky in Windows.

-Dave

---

### Post by stchman on 2007-07-22
> **MacDuff said:**
> On a new installation of Ubuntu Feisty I notice that FireFox runs extremely slowly compared to when this box had Windows XP.  Two other XP boxes run firefox at a reasonable speed.

I enquired in the Firefox forums and was told that Firfox from Ubuntu repositories is optimised for languages other than English and that causes the problem.

I find it hard to believe that language optimization could account for the huge difference in speed between Ubuntu and Windows.

Can anyone offer any advice

You may have cr@ppy DNS.  Try OpenDNS and see if it helps.  Also fixing your hosts and hostname could not hurt.

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

They helped my system.

---

### Post by MacDuff on 2007-07-22
Hi Stchman:
I tried your suggestion but I really could not see any increase in speed so I have returned to the original DNS settings.

At the time I tried it I was fighting with another new problem that occurred when I tried to plug in a 250 GB USB hard drive.  For some reason that trampled on an internal 200 GB drive and caused Nautilus to lose the internal drive, although when I viewed the drive through the terminal, it was still mounted.

Things like that are confusing, and being so new to Ubuntu, I have no idea where to look to solve the problem.  Obviously I must be trying to progress too fast and I expect too much.  Eventually when I re-started Ubuntu everything fell back into place and I have since re-mounted the USB drive with no problem.

When I was testing your suggestion to try OpenDNS, I lost my network entirely but I may have a flaky Linksys router.  Eventually everything came back.

There is so much to love about Ubuntu and I have suggested that one of my friends try it because he has very limited needs and knows nothing about computers having only been exposed to Windows for a few months.

But for someone who has many years experience with Windows, and wants to do the same, out of the ordinary,  things with Ubuntu that could be accomplished  with Windows,  it is a bit of a challenge.

I am learning though and one of the most impressive things about Ubuntu is that it has only locked up on me once and that may have not been a true freeze but I got very impatient with a process that was taking a long time and was not showing any progress.   I could never have messed around with Windows in the same way without having to give it the three finger salute dozens of times.  Ubuntu (Linux) is very forgiving which offsets much of the frustration of learning some of the obscure (to me anyway) ways of doing things in Linux.   I will soldier on with the kind help of the people who reside in the forum community.:)

Thanks to all

---

### Post by dougfractal on 2007-08-09
Have you tried opera
```
sudo apt-get install opera
opera
```

```
lspci -nn     #   list hardware
lspci | grep "VGA"  #   list graphic card.
free -m       # display memory

ls -l /etc/modprobe.d/        # list files in /etc/modprobe.d


```

although the the aliases fix is only going to give a slight speed up, It's like your pc is having a memory problem.


So how well does firefox run from the LiveCD?

---

### Post by MacDuff on 2007-08-09
Hi Dougfractal:

I had a look at Opera and indeed it runs much faster than Firefox.  However my wife has come to love some of the features in FireFox that are not available in Opera and I don't think I want to deprive her of them right now when I am fighting to get Ubuntu working satisfactorily.

I did not try to run FireFox from the live CD.  I would have thought that it would run even slower if it had to access the CD at all.  Perhaps not but I cannot imagine it running faster than a hard drive installation.

At the moment I have other more important problems to solve with Ubuntu and if I cannot work them out, I will, regretfully, have to return to Windows.  The time it is taking to iron out all the glitches is frustrating to say nothing of how much my self esteem is suffering:( 

I suppose I could subscribe to the paid support and get problems solved more quickly but I can purchase a copy of MS Windows for less money than the cost of paid support for Ubuntu.    The books I have purchased and the time I have invested in Ubuntu would have paid for more than one Windows license, sad to say.

---

### Post by stchman on 2007-08-09
> **MacDuff said:**
> On a new installation of Ubuntu Feisty I notice that FireFox runs extremely slowly compared to when this box had Windows XP.  Two other XP boxes run firefox at a reasonable speed.

I enquired in the Firefox forums and was told that Firfox from Ubuntu repositories is optimised for languages other than English and that causes the problem.

I find it hard to believe that language optimization could account for the huge difference in speed between Ubuntu and Windows.

Can anyone offer any advice

When I first started using Ubuntu my internet was really slow.  I have Charter high spped and turns out they had lousy DNS.  I use the OpenDNS.  I also re-did my hosts and hostname file.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

Give these a try.

---

### Post by MacDuff on 2007-08-09
Hi Stechman:

You mentioned those suggestions a week or two back.  I tried them and did not find any noticeable difference in performance.  Apparently Mozilla has a new version of FireFox due for release this fall that is purported to solve the slow performance problem with Linux.... or so I was told by someone, somewhere, sometime.

---

### Post by dougfractal on 2007-08-09
Hi MacDuff

I'm sorry you getting such a bum deal at the momment. 
> I would have thought that it would run even slower if it had to access the CD at all. True it would launch slower but once running it wouldn't have to read the CD anymore and should be as fast as HD.  The reason of trying this is to see if there is an error from the installation. As having only 6 FF windows open causing freezing, means something is badly wrong.  
It's also not fully a FF issus, although FF with Flash can bring Feisty down. I had logout. Then login and "resume session" several times in the past . I'm not finding this in Gusty which seems quite stable, but there are ~40MB updates per day..

I would like to help you but I need to know what you system is.

```

cd ~                     #  goto myhome
touch mylatop.info # create file
lsb_release -d > mylatop.info   # version
uname -r >> mylatop.info   # kernel
uptime >> mylatop.info    # time on
ps --no-headers -A -o "%cpu sz ucomm" | sort +0r | head  >>  mylatop.info  # condensed version **top**
lspci -nn >> mylatop.info   #   list hardware
free -m >>   mylatop.info    # display memory
cat /etc/X11/xorg.conf >>   mylatop.info   #  graphics file
```

please attach  "mylatop.info" to your post as it will be quite long


stchman I really feel it not a DNS issue as other web apps would also suffer eg. IE on windows.

---

### Post by OzzyFrank on 2007-08-09
Did you try sussing out the swap file? That is, opening a terminal and typing** top**? You never mentioned any results.

Sorry you're having hassles... but I personally wouldn't keep paying for windows just so my wife could play with the widgets in Firefox (I assume they are the features you mention... Opera has billions of widgets too). But then I admit I much prefer Opera to Firefox, so I am being biased (Opera's "Magic wand" for storing passwrds is great!).

So can you please try **top** and let us know what it says (feel free to copy and paste the results).

---

### Post by OzzyFrank on 2007-08-09
> **xarmian said:**
> The problem seems to be specific to Firefox (and all firefox 2.0 derivatives, i don't know about earlier versions) and how they operat

But the vast majority of us aren't having any problems with it whatsoever. Firefox flies along on my PC... I just much prefer Opera. I still reckon **top** should be used to see if any swap problem is happening, as my browsing in Opera died when my swap went.

---

### Post by MacDuff on 2007-08-10
Here is the top section of "TOP".  It does not seem to be possible to copy the data below the titles because it is constantly changing.   It appears to be a list of running processes.

top - 09:50:31 up  1:49,  2 users,  load average: 0.12, 0.11, 0.04
Tasks: 111 total,   1 running, 109 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.7%us,  0.7%sy,  0.0%ni, 97.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    515984k total,   444120k used,    71864k free,    14732k buffers
Swap:  1510068k total,        0k used,  1510068k free,   267788k cached

 When I tried to enter the code suggested by Dougfractall,  I just received an error rather than output.   I am not sure if he intended me to enter this as he wrote it or if he overestimated my degree of knowledge and thought that I would not take the instructions literally.   Anyway, the terminal objected as soon as I entered "cd~"  "CD~ command not found"

Code:
cd ~                     #  goto myhome
touch mylatop.info # create file
lsb_release -d > mylatop.info   # version
uname -r >> mylatop.info   # kernel
uptime >> mylatop.info    # time on
ps --no-headers -A -o "%cpu sz ucomm" | sort +0r | head  >>  mylatop.info  # condensed version top
lspci -nn >> mylatop.info   #   list hardware
free -m >>   mylatop.info    # display memory
cat /etc/X11/xorg.conf >>   mylatop.info   #  graphics file

I hope that what I did manage to capture sheds light on the problem.

---

### Post by dougfractal on 2007-08-10
> "cd~" "CD~ command not found"

"cd~" is not "cd ~"

please try again and attach laptopinfo.txt . You can just copy and paste the code into terminal (no typing required!))
```

cd ~ # goto myhome
touch mylatop.info # create file
lsb_release -d > mylatop.info # version
uname -r >> mylatop.info # kernel
uptime >> mylatop.info # time on
ps --no-headers -A -o "%cpu sz ucomm" | sort +0r | head >> mylatop.info # condensed version top
lspci -nn >> mylatop.info # list hardware
free -m >> mylatop.info # display memory
cat /etc/X11/xorg.conf >> mylatop.info # graphics file
mv  mylatop.info  laptopinfo.txt   #    rename file
```

---

### Post by MacDuff on 2007-08-10
Here is what the terminal shows when I did the paste of the commands:

mac@ubu-comm:~$ cd ~ # goto myhome
mac@ubu-comm:~$ touch mylatop.info # create file
mac@ubu-comm:~$ lsb_release -d > mylatop.info # version
mac@ubu-comm:~$ uname -r >> mylatop.info # kernel
mac@ubu-comm:~$ uptime >> mylatop.info # time on
mac@ubu-comm:~$ ps --no-headers -A -o "%cpu sz ucomm" | sort +0r | head >> mylatop.info # condensed version top
sort: Warning: "+number" syntax is deprecated, please use "-k number"
mac@ubu-comm:~$ lspci -nn >> mylatop.info # list hardware
mac@ubu-comm:~$ free -m >> mylatop.info # display memory
mac@ubu-comm:~$ cat /etc/X11/xorg.conf >> mylatop.info # graphics file
mac@ubu-comm:~$ mv  mylatop.info  laptopinfo.txt   #    rename file

---

### Post by dougfractal on 2007-08-10
and the file laptopinfo.txt in your home folder ?

cd ~
cat laptopinfo.txt  #   cat is "display to console"
or
less laptopinfo.txt    # q to quit    # less is more
or 
gedit laptopinfo.txt     #   

but please click "go Advance" and then the "attach icon" and post. It's too long to quote.

---

### Post by MacDuff on 2007-08-10
Sorry, here it is

Description:	Ubuntu 7.04
2.6.20-16-generic
 10:39:26 up 17 min,  2 users,  load average: 0.77, 0.30, 0.18
 6.2  1380 bash
 5.1 19410 gnome-terminal
25.9 38260 firefox-bin
 1.1  5286 Xorg
 0.3  2609 hald
 0.2 20085 tomboy
 0.1   727 init
 0.1 24452 nautilus
 0.1 15752 gnome-panel
 0.0  9930 bonobo-activati
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
             total       used       free     shared    buffers     cached
Mem:           503        420         83          0         12        252
-/+ buffers/cache:        155        348
Swap:         1474          0       1474
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Mac

---

### Post by dougfractal on 2007-08-10
I can't see anything really odd, but I can improve your graphics.

Things can always go wrong but I am doing my best to make this a pleasant experience.
Always have a rescue disk ready.

here goes. don't be afraid!

Note: Radeon 9200/9250 (RV280) and DVI : [https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI)  there is a bug if you use DVI.

```
sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
sudo modprobe -r fglrx
```


```
sudo gedit /etc/X11/xorg.conf.radeon
```paste in  code and save
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

#Section "Device"
#Identifier "ATI Technologies Inc RV280 [Radeon 9200 SE]"
#Driver "ati"
#BusID "PCI:1:0:0"
#EndSection

Section "Device"
        Identifier        "ATI Technologies Inc Radeon R280 [Radeon 9200 SE]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
      #  Option "BusType" "PCI"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV280 [Radeon 9200 SE]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout" 
Option          "AIGLX"         "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

** FINISHED **

```
wget -O testx http://redballoonlearner.co.uk/doug/ubuntu/testx.sh
chmod a+x testx
sudo ./testx xorg.conf.radeon
```

When run and new X is open; `less /var/log/Xorg.2.log` is displayed.
press "q" to quit and return to gnome.

---

### Post by MacDuff on 2007-08-10
OK just so I am clear about this:

I must copy and paste into a terminal window,  the code that you have kindly provided, exactly like it appears, right?

This would be three separate steps, is that correct?

You mention a "Rescue Disk".  By that do you mean the original Ubuntu install disk or is there a routine to create a "Rescue Disk" that I should know about?

Sorry I have not been on top of this but between all this mucking about with Ubuntu, I am trying to finish an application for a client which must be done if I want to stay in business.  Yes, I am ashamed to admit it  but I am an application developer.  You would not know it from the stupid questions I ask but I really can write applications  that run brilliantly under windows and DOS.  However I find the Linux world to be very confusing, probably because you use many of the same words as I use but they have a different meaning in your world.  Then too, the shortcuts I would take as a matter of course REALLY don't work in Linux, in fact they screw things up royally.  That is why I need very detailed instructions, something like I provide to my associates.  I assume they don't know anything. By telling them about every I to dot and every "T" to cross, nothing is left to chance.

---

### Post by dougfractal on 2007-08-10
I had to finnish a script for the next part of the instructions.

Rescue Disk === LiveCD (just in case althought I think you wont need it)
> I must copy and paste into a terminal window, the code that you have kindly provided, exactly like it appears, right?
Yes , but I have an easier way :-

copy and paste into a terminal window
```
sudo echo "Activate sudo"   # so it doesn't ask again for next 5 mins
```

```

wget http://redballoonlearner.co.uk/doug/ubuntu/xorg.conf.radeon
sudo mv xorg.conf.radeon /etc/X11/xorg.conf.radeon
wget -O testx http://redballoonlearner.co.uk/doug/ubuntu/testx.sh
chmod a+x testx
./testx xorg.conf.radeon
```

When run and new X is open; `less /var/log/Xorg.2.log` is displayed.
press "q" to quit and return to gnome.

[SIZE="1"]

[I]files also at.
[http://ubuntuforums.org/attachment.php?attachmentid=40359&d=1186792733](http://ubuntuforums.org/attachment.php?attachmentid=40359&d=1186792733)
and 
[http://ubuntuforums.org/attachment.php?attachmentid=40358&d=1186792324](http://ubuntuforums.org/attachment.php?attachmentid=40358&d=1186792324)
[/I][/SIZE]

---

### Post by OzzyFrank on 2007-08-11
Weird as hell... your swap seems OK (I assume none was being used as you had just booted in or hadn't been doing much?)... or at least it's recognised, which I assume means it is getting used properly. And yes, trying to copy the rest of the "top" output is fun, hehe.

Sorry this is turning you off Ubuntu, but I'd even suggest contacting the Firefox guys at Mozilla and seeing what they think. Just remember to tell them the rest of us have Firefox flying along in the same OS. They might even know a workaround, or at least become aware of a bug that affects some using Ubuntu. Best of luck, and hope you get some progress soon! (And remember, you can always migrate to Opera, like all of us have at one point decided to give up on Internet Explorer and try another, like Firefox and Opera... so it's a pain, but not THAT much).

---

### Post by MacDuff on 2007-08-11
Ozzyfrank:

Thanks for the reply.  I appreciate all the suggestions but NO this particular problem is not turning me off Ubuntu.  It is an annoyance but I know that somehow, sometime, it will be addressed (even if I have to purchase new hardware that fully supports Linux, Yes I want to use Linux that much).  

What is getting me really frustrated are all the other problems that crop up whenever I try something out of the ordinary. I have a number of posts concerning two other BIG pains in the butt that have not received any responses, or at least none that solve the problems.   Since part of this exercise was to check out Linux for a client who expressed a desire to try it but did not want to waste the time himself, I volunteered to install it on at least one computer to check it out.   

While I REALLY LOVE much of what I have discovered about Ubuntu, there is no way that I can recommend it yet to any of my clients because the lack of support would drive them over the edge.  Yes they could purchase commercial support but they can purchase Windows for less that it would cost for Ubuntu commercial support and though Windows is far from perfect, when you compare costs, it is not THAT BAD.  It is no trick to deal with all the problems that attend Windows Operating Systems but Linux is a new world and the learning curve appears to be pretty steep unless one is prepared to accept just what is included in the live CD.

Until I get more answers or have time to study Linux in more depth, I will just leave it on one computer and play with it when I have time.  The time I am loosing by trying to get a Ubuntu system doing real work in concert with my Windows boxes is driving me wild.  I am getting too old to fight this hard.  

Hopefully I will get time later today or tomorrow to install the scripts created for me by dougfractal and see if the graphics are better after that.   I was not too concerned about the graphic because I am aware of the problems with my particular Video card and Linux, however if dougfractal's work makes the graphics better, that will be a plus.

By the way I REALLY do appreciate the help and encouragement offered by Ubuntu users.  Unfortunately for me, many of them reply in terms that are well understood by the Linux fraternity but which mean very little to those of us who are new to Linux.  In a past life I had a bit of contact with Unix but that smattering of knowledge, obviously does not help me either because as Linus Torvalds said "Linux is not Unix"

Cheers

---

### Post by OzzyFrank on 2007-08-11
OK, I've yet to check out your other "pains" but I just have to say one thing about Ubuntu/Windows/Support: Windows users pay for their OS, and don't get free support past installation problems (beyond that, they really want you to pay for it). I know you can't be suggesting Windows doesn't need support, as their huge helpdesk that rakes in millions a year wouldn't exist if this were the case (OK, I know you're saying those users are familiar with Windows so won't need any support, but see a lot of people trying to tell us Microsoft help is free, when I know years back I was forced to pay for something that ended up not being my fault, and they stood by that).

If you have a problem your best bet is sites and forums, which doesn't differ for Ubuntu. One thing that does, and I personally have noticed a VAST difference, is the speed and quality of forum posts for Ubuntu. Actually, I've still got quite a few unanswered posts in various Microsoft forums, though I ended up sussing most of those issues out myself.

Personally, I'm recommending Ubuntu to everyone, and in fact helped a good friend yesterday to buy his first PC... he was slightly annoyed he had to fork out an additional $95 for Vista Basic, and only did so because he wants to run the software for the TV card. He'll be doing everything else in Ubuntu with free software, and definitely surfing the web and doing his netbanking from there (we both saw the current affair show where a guy lost $138,000 over a couple of days via spyware sending his details out from his "protected" Windows machine!). So you can always tell friends and clients this:

[COLOR="Purple"]Ubuntu is great, but SOME people have problems with their particular hardware configs.This is no different from Windows, except that you don't get free helpdesk support on the installation (though if it seems to be the hardware, Microsoft can't really help... but will try and charge you to do so anyway). There are people who could barely use Windows who have successfully migrated totally to Ubuntu, knowing they won't need to keep paying for antivirus software, firewalls and anti-spyware suites. Lastly, while learning any Linux is going to require some patience, for totally new computer users Ubuntu seems more user-friendly, and definitely more "intuitive" and has standard features that even Vista hasn't addressed yet. That said, some will find it a steep learning curve for anything but a standard install (or even that), though others will happily keep adding to and expanding their systems without issue and only minimal brain-aches (if any).[/COLOR]

Anyway Mac, keep at it, don't pull too much hair out... as you said, your Windows machine is going, and you can slowly get the Ubuntu one up to speed on the side. This really is the best way for ANYONE to go at first... then later you can surprise yourself how little you go into Windows.

As for getting answers way over your head, yeah some think the rest of us have been using Linux for the last decade, and express their answers accordingly. Compliant hardware? Well, good to know you like Linux/Ubuntu enough to get new hardware, but I reckon if you got anything other than what you have now, you'd be OK (I've got Ubuntu onto old PIIs through to my P4). I'd perhaps suggest not an ATI card, though mine works fine, and can handle Beryl easy enough with the help of a script (the actual fglrx drivers crash upon boot).

---

### Post by DavidFourer on 2007-08-11
Not an expert here, but when firefox loaded super-sluggish for me, I went to the menu bar: System>System Monitor>Resources.  This monitors your CPU utilization and network traffic.  If you are doing nothing, the CPU utilization is around 3%.  When my software was not loading fast, something was utilizing the CPU 50% or 90% and hogging the system.  I booted the previous kernel version (very easy if it's already installed, reboot and hit escape early in the start-up) and all worked fine.  So I ran Ubuntu on a slightly older kernel until the next kernel upgrade fixed it.  No problems since then.

---

### Post by Blindraven on 2007-08-11
If firefox is a problem try the new opera.

---

### Post by OzzyFrank on 2007-08-11
Installing Opera doesn't seem to be an option, due to personal preference. Some of us obviously think Opera is superior anyway, but this is irrelevent, and certainly doesn't do anything to satify the geek in us that wants to know what the hell is going on here, hehe! Booting to an earlier kernel (which is easy nowadays with the options for them in the GRUB menu) seems like something worth trying.

---

### Post by OzzyFrank on 2007-08-11
Hey, don't think this has been suggested: try some "boot options" when at the GRUB menu. I had problems with a Compiz update ([http://ubuntuforums.org/showthread.php?t=489206](http://ubuntuforums.org/showthread.php?t=489206)) and couldn't boot into Gnome "properly" (details in that post). While I could log into any other desktop, like KDE/Kubuntu, I wanted to solve the issue in Gnome. While it ended up solving itself with the next update, the way i ended up getting into Gnome without issue till then was using 2 boot options:

**noapictimer irqpoll**

When you get to the GRUB menu you'll see at the bottom it says you can hit the "e" key to edit the boot process. Hit "e" and then select the 2nd line (which has the actual boot commands), then hit "e" to edit that. It will take you to the end of that line, which is where you type the options (should be after something like "ro quiet vga=771 splash" or "ro single"). Hit Enter when finished then "b" to boot.

See if Firefox behaves any differently after booting into Ubuntu with those 2 options.

(PS: The reason I mention this, if you're wondering why I am mentioning a workaround for a Gnome startup problem, is that I have seen many varied uses of boot options - those in particular - being applied to get various programs to behave. It's worth a try, and only takes a minute, and you never know)

---

### Post by EXCiD3 on 2007-08-11
You could always go with Swiftweasel, based off of Iceweasel, but enhanced for your specific processor. It seems to run a hell of a lot faster than Firefox.

---

### Post by HarmonicaGoldfish on 2007-08-12
I had the same frustratingly slow browser problem and found a solution that worked wonders for me. 

It has to do with  ipv6. 

Someone else mentioned a fix for that on page one of this thread. That particular fix did not work for my system, but the following did.

Here was my process:

> Disable Firefox IPV6:
1. Open Firefox and type "about:config".
2. Type "ipv6" in the "Filter" box.
3. You will see an option to disable ipv6. Click on it to set the value to true.
4. Close and restart all Firefox browsers.

That helped for a bit, but the problem seemed to come back. So then I tried this. Method A did not work but Method B worked like a charm. I run a system that has 1.8ghz with 256 ram and still have very fast Internet speed since doing this.

> Disable IPV6 System Wide:
There are actually many ways to do this, but the following two are the easiest and most compatible I have found. You should try Method A first. The first thing is to see if IPV6 is running at all though.

Check if IPV6 is running by typing this line into your terminal:
ip a | grep inet6

If there is any output from this command then IPV6 is running. If there isn't any output then don't continue, there's nothing to disable.

IPV6 Disable Method A -
For Gnome users:
sudo gedit /etc/modprobe.d/bad_list

For KDE users:
sudo kwrite /etc/modprobe.d/bad_list

Add this line to the file:

alias net-pf-10 off

Save the file and exit, and reboot. Check if IPV6 is running after reboot. Remove the line from bad_list and try Method B if it is.

IPV6 Disable Method B -
For Gnome users:
sudo gedit /etc/modprobe.d/aliases

For KDE users:
sudo kwrite /etc/modprobe.d/aliases

Change this line in the file:

"alias net-pf-10 ipv6" To "alias net-pf-10 off ipv6"

Save the file and exit, and reboot. Check if IPV6 is running after reboot. If it is you will have to look for other solutions beyond the scope of this instruction.

I got this information from this forum post, in section 4 of the post (it is a long post :) )
[http://mepislovers.org/forums/archive/index.php/t-6750.html](http://mepislovers.org/forums/archive/index.php/t-6750.html)

I hope it is as helpful to you as it was for me.

I began using ubuntu about 1/2 a year ago and have had a few issues to work through but, even as a complete un-know it all about computers and operating systems have managed to solve problems and learn a lot by searching through forums like this one. The ubuntu community is incredibly giving and helpful. 
Ever since I have had a few issues ironed out (Internet and a camera detect issue) I have never been happier with my computer performance.
Really.

Cheers and good luck with this!

---

### Post by MacDuff on 2007-09-18
Well the problem is SOLVED!

I have spend months learning Ubuntu.  It has been interesting and EXTREMELY frustrating!

I will indulge myself by suggesting that a foray into a new operating system can be a minefield, particularly when there is no real person nearby to whom one can turn for advice.  The underlaying problem is that someone new to an OS does not know what looks right and what looks wrong when trying to solve a problem.  It requires experience to know if a situation is improving or just moving sideways.

I purchased four books on Linux and Ubuntu to deal with problems of various kinds from getting a network to run ( I still have problems with some permissions) to running virtual windows applications to finding substitutes for essential Windows applications to dealing with dozens of seemingly minor problems like the slow/jerky operation of Firefox, which was the subject of this thread.  And of course I posted help wanted messages to forums such as this.  Some of the problems were solved but it was such a long drawn out process that I began to feel that I would die before I had a fully functioning Ubuntu system.  

Twice I nearly threw in the towel and returned to Windows.  Then one of my friends purchased a new laptop with Windows Vista on it.  His litany of woes was enough to convince me that I should press on with Ubuntu, hoping that the next version due out in October would solve yet more problems and hoping that it would not cause other problems, such as those posed by Vista.

I decided to replace the chipset and processor of the computer I had designated as being the Linux box.   That was frustrating!  My computer shop installed Intel hardware that they had been told would work great with Ubuntu. It worked fine with Ubuntu 6.04 but would not run longer than five minutes with Ver 7.04.   After a week of trying everything we could  do to make that hardware work, we finally replaced it with a Gigabyte S series board and an AMD processor.

I am happy to report that everything works great!   Well....almost.  I still have to sort out some networking problems but I think that is just a matter of editing some settings when I find them.

Firefox, the subject of this post, flies along as fast as it does on my Windows XP machines and I have successfully installed Ubuntu 7.04 as a second system on an Acer laptop ant it  runs FF as fast as with Ubuntu as it does with XP.  

To those who tried to help in this matter, I extend my thanks and apologize if, in my frustration, I offended anyone.  

Hopefully in the months to come, I will be able to contribute something to the Ubuntu community because it is primarily because of the encouragement of its members that I kept on with the project.

Thanks to you all
Mac

---

### Post by Ubuntiac on 2007-09-29
> **MacDuff said:**
> dealing with dozens of seemingly minor problems like the slow/jerky operation of Firefox

[...]

After a week of trying everything we could  do to make that hardware work, we finally replaced it with a Gigabyte S series board and an AMD processor.

I am happy to report that everything works great!   Well....almost.  I still have to sort out some networking problems but I think that is just a matter of editing some settings when I find them.

Firefox, the subject of this post, flies along as fast as it does on my Windows XP machines and I have successfully installed Ubuntu 7.04 as a second system on an Acer laptop ant it  runs FF as fast as with Ubuntu as it does with XP.  


Interesting... so if I can just confirm:
You were having the slow jerky firefox thing. Your computer store just changed the motherboard and CPU and your firefox issue dissapeared?

As someone trying to bugfix a similar issue (interestingly also with Intel motherboard and CPU) I'm fascinated to hear your reply.

Glad it's working well for you! (Hope you're wife's happy with her spiffy FF also :) )

---

### Post by irieken on 2007-10-14
[SOLUTION]  --> Well, at least it works.

This sounds like the same problem I was having.

My temporary solution is to install gnome-compiz-manager and disable "GL Desktop" in the GL Desktop preferences panel. Now, everything is nice and responsive.

I guess that my video card isn't up to the demands of Compiz, but at least my Linuxing experience is very pleasant now:)

---

### Post by MarilenCorciovei on 2007-12-10
Indeed disabling ipv6 has [helped me too]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/what-was-killing-my-gutsy/") after lots of other unsuccesfull tries.

---

