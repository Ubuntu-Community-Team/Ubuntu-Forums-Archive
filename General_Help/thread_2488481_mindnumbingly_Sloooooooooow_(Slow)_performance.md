---
title: "mindnumbingly Sloooooooooow (Slow) performance"
date: 2023-07-05
forum: General Help
---

### Post by pjstock on 2023-07-05
I just installed 22.04 LTS on an admittedly older system (Dell Optiplex 3020 with 4GB memory Intel® Core™ i5-4590 CPU @ 3.30GHz × 4)

since it is just a Ubuntu system I didn't do any clever partitioning. I am just using the entire 500 gb for Ubuntu.

but the system is still mindcrushingly slow.
5-10s delays between responses to keystrokes or cursor movements.
frequent applications and devices "not responding. Force quit or Wait"

could using the entire HDD for the install be the problem?

I've read that there are sippier options - Slackware, OpenBSD?? - but I am really not up for learning my way around a completely new system (plus I cannot figure out how to even download a Slackware ISO)

suggestions?

---

### Post by pjstock on 2023-07-05
though I expect the first test would be to run Ubuntu from a USB Stick and see if it is still slow.
If so, the problem would be the system being too aged.
but if it runs well from the stick but not from an actual install, then maybe there was something wrong with the install

---

### Post by Autodave on 2023-07-05
The 4G of RAM isn't helping, but that is not the problem.  I have Xubuntu running on lesser machines than yours with no problems like you are describing.  I would follow your own advice and boot from a USB stick and see what happens.  If that at least has a USB 2 port, make sure that you use that.....or USB 3 if it has it.

---

### Post by guiverc on 2023-07-05
I still spend hours of each day on a c2q-9400 CPU, ie. core2quad that pre-dated the i-series of CPUs from intel (*I'd expect to be slower than your i5-4590 or 5th gen i5*)

To me the significant detail you listed was the 4GB of RAM as already mentioned, but you gave no clues as to how you use your system; which to me would be very significant.

I perform QA-testing on c2d, c2q & even some i5 hardware, with as little RAM as 2GB, but when using a low-RAM device I think ahead before I start *apps.*

Ubuntu 22.04 LTS uses GNOME 42 which uses an early GTK4, so will be most efficient if you're using GTK4 apps; are you?   Given how early in the GTK4 cycle it is, it won't be too bad if using GTK3 apps, but it'll be inefficient if using Qt5 apps for example unless you've plenty of RAM; in my view >5GB which you don't have.

ie.  on a system with low resources (esp. RAM), I consider first what apps I'll use, then select a desktop that will share resources with those apps (ie. not forcing two sets of libraries/toolkits into RAM that do the same thing, but one required by your desktop & another for the apps you'll use), thus don't just consider the *distribution* you'll use, as they'll have all have the same issues. 

Consider instead what you'll be putting in your limited RAM; ie. the software stack you'll use as a whole in what will be efficient. Same rules apply for any GNU/Linux, BSD, windows or macOS system.. With windows & apple they don't mention toolkits/libraries (*except in the small print technical section*) and just say you need 8GB of RAM for example that will mean the user doesn't have to *mentally guesstimate  *what RAM they usage will actually require.

I haven't used BSD in awhile, but I'm using Ubuntu *mantic* now, use Debian 3+ hours per day, have a OpenSuSE *tumbleweed* system here, plus Fedora - and to me they'll all identical (*I can't recall BSD being any different except you build your setup more yourself thus it'll be efficient or resource-wasteful depending on decisions you make!*).  To me the *distribution* or OS isn't the issue.

*This will be too technical for you, but my point is you're not looking at the correct places.  I still use hardware from 2003 & newer, perform QA installs of Ubuntu desktop (esp. flavors) on hardware from 2005 & it works well when you use it appropriately for the machine. On older  (resource limited) *[I]hardware you just need to plan a little more. Up to end last year my primary desktop PC was a 2009 dell desktop anyway, alas it finally died (forcing me to replace it)


[/I]Your alternative is hardware issues.. Have you explored logs? looking for clues.  Disk issues are pretty easy *generally* to spot; and diagnostics is pretty much the same for any OS too. You can use a drive's SMART capability to see health ([https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)) but I'd just explore system logs first.

 You weren't specific as to what Ubuntu 22.04 LTS product (Server? thus text UI only? or Desktop? thus GUI) so I've tried to be generic, but have mostly spoken about desktops anyway (*where RAM is wasted by users; server users tend to consider it during setup in my experience*)

---

### Post by MAFoElffen on 2023-07-06
I'm very surprised that guiverc didn't mention trying Lubuntu. It really does run well on limited resources.

You mentioned BSD. I have a few variants running. Of them, FreeBSD probably tops my list.  
```

mafoelffen@freebsd13-2-01:~ $ dmesg | grep memory
real memory = 214747483648 (2048)
avail memory = 2034827264 (1940 MB)

```
That is while running Gnome Desktop... It doesn't use much resources, and it runs well on old hardware. Though... BSD is not for the faint of heart nor unskilled. It has a very steep learning curve.

You rack your brains remembering it's flavor of Unix commands versus Linux commands... and everything is installed manually. Everything. For example, you install the OS. To get a desktop, you install and configure the graphics engine. Then install and configure the Desktop Environment. Then install and configure the Desktop Manager so you can boot to  Graphical Login screen. Then install and configure each application. There is no default installed applications suite. Each piece, you pick, install, configure: browser, word processor, email client, etc.

I still do not really recommend it... LOL. No. Ubuntu and it's flavors are a world more "user friendly".

---

### Post by Rubi1200 on 2023-07-06
If I can throw my tuppence worth in the bucket, I recommend giving Bodhi Linux a try. I run it on a 1GB Intel Atom netbook and it is well put together and fast. It uses a different desktop environment than you would be used to but package management is based on Ubuntu/Debian so all the familiar packages are available and can be added using apt or the in-built software manager.

---

### Post by HermanAB on 2023-07-06
In my experience Xubuntu and Lubuntu will work OK on that machine.  However, OpenBSD or Slackware will be screaming fast by comparison.  There are multiple reasons why - too much to delve into now.

---

### Post by oldfred on 2023-07-06
I have newer machine with lots of RAM, but still like Kubuntu which is a mid-weight flavor, and only using 1.3GB with Firefox (not snap version, but ppa version) running.
> fred@dell-5310:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:            15Gi       1.3Gi        11Gi       603Mi       3.1Gi        13Gi
Swap:          4.0Gi          0B       4.0Gi



You can down load various flavors and see what you like using live installer.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

