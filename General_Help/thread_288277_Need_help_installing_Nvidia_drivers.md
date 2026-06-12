---
title: "Need help installing Nvidia drivers"
date: 2006-10-28
forum: General Help
---

### Post by brad1138 on 2006-10-28
Every couple years, since about 1998, I try Linux, I have tried Mandrake 8 & 10 RedHat 6 & 8 and now Ubuntu 6.10. I want very much to use Linux. I am not a comp. noob. I have been building computers for over 10 years, and I know more about them than anyone I know. 

I installed Ubuntu last night and have spent the last 5 hours on the 1st thing I tried, updating the Nvidia drivers. This is ridiculously hard. I could copy and paste pages of instruction on how to do this, but I wont fill this post with all that. A lot of the instructions are very cryptic if you don't know Linux real well, you end up having to look explanations for every explanation you find. Every time I figure out the next step in the instructions a new problem pops up and I have to search for what  to about this new issue. WHY can't Linux(Ubuntu) just have a button to click on "Update driver" and have the OS take care of all of it, or just click the downloaded file and have it take care of it? If Linux EVER wants to be a mainstream desktop alternative to M$ or Mac (don't get me wrong I'm no M$ fan) it CAN NOT be this complicated. 

I guess I don't have a question, just venting a bit. I love the look feel of Linux and what Linux & Open Source is all about but I am having basically the same probs I have had EVERY time I try Linux, Guess I'll try it again in a couple more years.

---

### Post by ~LoKe on 2006-10-28
I think you're putting too much pressure on yourself so early on, then.

I mean, for the latest nvidia driver, you just have to download the .run file, go into the virtual console, then type...
```
sudo sh NV*.run
```
And the installer will run.

---

### Post by Blutack on 2006-10-28
Loke has a point.  Maybe you found a really bad howto.  As a total nube I managed to install the nvidia drivers in about 10 min.  Most of that was working out how to get a terminal.  If you are learning maybe 6.10 is a bad idea...it is edgy which means it is the beta version, and still slightly unstable I believe.  You would be much better with 6.06, dapper drake.  Then once 6.10 goes general you can update with a few mouse clicks...try that with xp and vista.  In ubuntu go applications --> terminal by the way...

---

### Post by jurgnn on 2006-10-28
Don't give up, search forums, google, etc for help.

I had same problems with linux before, it was so simple to boot windows instead of fixing linux, but that way you will stay with windows.

Few months ago I installed ubuntu and had problems with fglrx, wacom and tv-out, took maybe few days to get them working, but now they work perfectly and I gained lots of experience to get through future problems.

---

### Post by 23meg on 2006-10-28
Use Automatix.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by brad1138 on 2006-10-28
*I think you're putting too much pressure on yourself so early on, then.*

Loke, I know, I was thinking the same thing as when I posted that but I'll just outline what I have gone though. 

Nvidia driver site says to run "sh NVIDIA-Linux-x86-1.0-7184-pkg1.run" and then edit xconf. So I hit alt-F2 paste that line and click run..... Nothing happens except the terminal window disappears, did it run and do what it needed? I still cant access anything higher than 1024x768(my first prob)

After searching a while I find I should open a terminal first(not alt-F2) Tried that, no difference. Then I found I need to cd to proper dir (should have thought of that earlier) Ok so now I run line... "You do not have permission, must be logged in as root" O...K... I log out and try to log in as root, it asks for a password (I never created a root password during setup) I tried no password and the password I created for my main login, no luck. I logged back in and created a password for root and logged back out. I then tried to log in as root again and get "The system administrator is not allowed to log in from this screen" GGGGRRRRRRRRRRR!!!!

After logging back in and googling for a while I learned (a little) about sudo. Sudo gives you admin priv. if you know what to type to active the prog. you want to run, you type sudo before it and there you go. 

So now I "Sudo Terminal" enter the root password I created and...nothing :( tried password for main acct and it worked(?) :) cd to desktop (where my file is) run "sh NVIDIA-Linux-x86-1.0-7184-pkg1.run" It starts :) .....error unable to find system utility 'ld' you need to install ldxxxsomething... GGGGGGGGGRRRRRRRRRRRRRRRRR!!!!!!!!!!!!!!!!!

That is where I am stuck now, during all this I also looked into xconf at what I might need to edit (Nvidia just said edit it w/o instruction). Looking in, there is a lot of stuff in there, I see a few things that might need to be changed. Graphic modes were listed up to 1024x768, maybe I just need to add 1280x1024 in line? I tried that and ran into the permission problem as above when I tried to save and so never did change that(good thing, I found later the changes I am supposed to make)

As I am looking though web page after web page trying to find answers to each problem of the driver install I see a lot of "you will need to edit this file" and not much info beyond that, assuming you will just know how to edit files.

I know I need to give it more time, but it is darn frustrating that I have had to go through all this just to update a driver.

---

### Post by iovar on 2006-10-28
brad1138:

You ask how to install the drivers and 7 hours later, instead of bumping
the thread you make a new one saying linux is #$%^&* complicated!!!!! ? 

First things first:
1:
Alt-F2 is only good for launcing programs. Commands, installers, etc are 
always to be run on a terminal, since you probably have to interact with
them, somehow.

2:
Why not automatix? Do you really want to start using linux 
with compiling kernel modules?

In any case this is a fast how-to:

Open a terminal and run this:

```
sudo apt-get install linux-kernel-headers build-essential
```

When finished logout and hit alt-ctrl-f1 .
Enter login and passw on the terminal screen(you can go back to graphical mode with alt-f7)

Now run ```
sudo /etc/rc2.d/S13gdm stop
```.
If you use kdm it's S13kdm, if you are on dapper I think the number is S99.
In any case you can write up to /etc/rc2.d/S and then hit tab. 
This will list possible suggestions.

Next, cd to the directory where you have the driver.Run:
```
sudo sh NVIDIA*.run
```
( again writting sudo sh NV and hitting tab will autocomplete for you or list any possible combinations).

And now you are running the installer. If it asks to compile the module
(very likely) and then says it didn't find the headers, do the following:

```
sudo ln -s /usr/src/linux-headers(press TAB here) /usr/src/linux 
```
(most probably it's linux-headers-2.6.17-10)

Now rerun the installer and everything should go fine.

To go back to graphical mode run

```
sudo /etc/rc2.d/S13gdm start
```
and then hit alt-f7
To logout from the console session hit ctrl-d



[B]Or instead of all that:


[http://www.getautomatix.com/]("http://www.getautomatix.com/")


Linux is different and if you go the way you knew in windows
(go to nvidia site, download driver ,run it) it can be very complicated.
If you ask first (and wait for an answer), it can be very easy.[/B]

Plus, Ubuntu is a linux distro but linux is not ubuntu. If you find this distro
too hard, go with Mepis, or Mandriva, or Sabayon, or Slackware(just kidding :-) about the last one, but it will teach you a lot)

---

### Post by maniacmusician on 2006-10-28
wow, iovar! now that's some dedication. awesome job on that quick howto.

---

### Post by Reshin on 2006-10-29
Can you really say with a serious face that the instructions that iovar wrote are **not complicated**?

Simple is: you download the file and run it. That's it. Now compare that to what you really have to do...

---

### Post by aysiu on 2006-10-29
> **Reshin said:**
> Can you really say with a serious face that the instructions that iovar wrote are **not complicated**?

Simple is: you download the file and run it. That's it. Now compare that to what you really have to do...
So use these instead:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Reshin on 2006-10-29
> **aysiu said:**
> So use these instead:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

I know, but I was tying to make point there...

---

### Post by awakatanka on 2006-10-29
> **Reshin said:**
> Can you really say with a serious face that the instructions that iovar wrote are **not complicated**?

Simple is: you download the file and run it. That's it. Now compare that to what you really have to do...
That is the choise someone makes. In Mepis you can install it with simply one button. That goes for nvidia and ati. Is (k)ubuntu a starting distro for users that don't have much experience?i don't think its the right distro to start with. I found Mepis much easier for people that wanna start witj KDE linux. There is also a Gnome distro that is much easier.

(k)ubuntu wanna stay a free and free from ... distro then you can run in this kind of troubles.

---

### Post by Reshin on 2006-10-29
> **3rdalbum said:**
> Hey. If you hate the installation procedure for the Nvidia driver, then don't complain to us! Complain to Nvidia, who actually wrote the driver and created the installer.

Blame anything/anyone you want, that still doesn't change the fact. Whoever wrote it, it's still part of the whole.

---

### Post by slimdog360 on 2006-10-29
> **Reshin said:**
> Blame anything/anyone you want, that still doesn't change the fact. Whoever wrote it, it's still part of the whole.

which is why anyone can install it very easily through synaptic, automatix, easyubuntu and probably about 50 other similar programs.

---

### Post by aysiu on 2006-10-29
> **slimdog360 said:**
> which is why anyone can install it very easily through synaptic, automatix, easyubuntu and probably about 50 other similar programs.
Or, as awakatanka pointed out, you can install it during the OS installation process in Mepis by just choosing to use Nvidia drivers.

Mepis, unlike Ubuntu, has no qualms about including proprietary software in its default installation.

---

### Post by brad1138 on 2006-10-29
OK I installed Automatix (here's a link to the simple install instructions for that :mrgreen: [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29) 

But I did install it, the install worked as the instructions outlined. I found nvidia driver and clicked update and it started working. when it was done it said "error report" If Xwindows should crash on restart please enter this line "sudo cp/etc/x11/xorg./conf_backup_200610291209/etc/x11/xorg.conf". Luckily it did not crash on reboot, but..... I still don't have access to 1280x1024 (my original problem). I looked in xconf and it does list driver as nvidia. I know it works with 1280x1024 because before I installed Ubuntu I ran it just from the cd and had it.

So now what???

Brad

---

### Post by Reshin on 2006-10-29
> **brad1138 said:**
> OK I installed Automatix...

Basically, automatix/easy ubuntu just does apt-get install nvidia-glx and does nvidia-glx-nvidia. It trusts that ubuntu found correct settings for your monitor at install and just changes few lines to make the driver work.

I can't make this accurate because I'm on windows right now, but...find about your monitors horizontal and vertical frequencies. They should be on monitors manual or manufacturer's homepage on monitors specs. Open /etc/X11/xorg.conf and find lines with HorizFreq and VertFreq or something like that. Replace the values with your monitors' and find lines with resolutions. Find the one that lists resos for 24 depth and type the reso you want as the the first value on that list. Save and restart x. Might not make sense. Use at your own risk.

---

### Post by brad1138 on 2006-10-29
This just gets better all the time :???: No matter what I do there is another problem waiting. I will try what Reshin said, But my monitor is used and old, have no manual for it. I ran it at 60 Hz 1280x1024 in XP. If this doesn't work I am not sure how many more hoops I am going to jump threw b4 I say forget it and go back to Windows again.

Brad

---

### Post by Reshin on 2006-10-29
> **brad1138 said:**
> This just gets better all the time :???: No matter what I do there is another problem waiting. I will try what Reshin said, But my monitor is used and old, have no manual for it. I ran it at 60 Hz 1280x1024 in XP. If this doesn't work I am not sure how many more hoops I am going to jump threw b4 I say forget it and go back to Windows again.

Brad

Old monitors are usually recognized well. Just do the reso-adding part

---

### Post by brad1138 on 2006-10-29
Ok, I opened terminal, cd to etc/X11/, type "sudo gedit xorg.conf", and entered password.

I then changed:

SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection

to look like this:

SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

I did this for Depth 16 also. 

the default depth is 24.

Saved, closed and rebooted.

Anyone want to guess if it worked........... NO! 

Still have no 1280x1024. I do have a nice nvidia utility under App. Sys. tools, so I know the drivers where installed correctly, unfortunately resolution isn't in the util. 

next hoop please

Brad

---

### Post by John.Michael.Kane on 2006-10-29
brad1138 heres an example xorg conf

Section "Monitor"
	Identifier	"DELL M782"
	Option		"DPMS"
        [B]HorizSync       30.0-85.0 [COLOR="Red"]this needs to match your monitor specs[/COLOR]
        VertRefresh     50.0-160.0
      # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"DELL M782"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		**1280x1024_60.00"** "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

brad1138 also instead of highjacking this thread for help post a thread with your issues next time.

---

### Post by aysiu on 2006-10-29
> **SD-Plissken said:**
> brad1138 also instead of highjacking this thread for help post a thread with your issues next time. Partially brad1138's fault, partially mine.

brad1138 started a thread with a ranting subject title that made me think it was another "Linux is not ready for the desktop" thread, so I merged it with the other active one.

Then, it turns out that was just a way to draw attention to what essentially ends up being a support request, so now it's a support thread--I've extracted all the relevant posts into this new thread.

---

### Post by brad1138 on 2006-10-29
Here is what my file looks like

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


The only difference form the original is the addition of "1280x1024"

I have NO WAY of knowing what my old used monitors V H Sync are. If Ubuntu/Linux can't figure it out a guess I am screwed, I am sure not going to go out and buy a new monitor for this "free" OS so I can find out the sync. When I first burned the iso and booted the comp off the cd w/o installing, it gave me 1280x1024x60, I guess it has forgotten how to figure out all the info it needs. 

next hoop please,

Brad

---

### Post by nardis_Miles1 on 2006-10-29
First, Brad, congratulations on sticking with this. Second, it is a little disingenuous to say that one can simply download the nvidia package and run it to be successful. Third, there are both good and bad reasons that Linux has not come to grips with commercial binary drivers. There seem to be a couple of ways to go.

1. Debian/Ubuntu has a set of nvidia kernel modules that I have not figured out yet. Good luck with those. They should have the advantage of automatic upgrading.
2.Using the drivers from the nvidia website. 

I assume you have done the latter. Do you know that running the NVIDIA-Linux-x86... package was successful? I have done this a few times with decent success. The package will tell you that it has finished successfully. Every time I have installed the nvidia driver I was required to have the kernel source installed on the machine. Was that the case for you? Part of the installation involves a query about letting the NVIDIA package update your xorg.conf file, so I don't think you should have problems with that. 

You mentioned a need to know your terminal settings. I have had great success google-ing the exact terminal name with the keyword specifications or specs.

---

### Post by iovar on 2006-10-29
I've skimmed throught the thread and I'm not if someone recommended it but did you try this?
```
sudo dpkg-reconfigure xserver-xorg
```

That's the way to get more resolutions, since you'll go through
a simple procedure, that will prompt you with simple checkboxes.

I was under the impression that you wanted 3d accel or something.

[Here, is that simple enough? :mrgreen: ]("http://johnvarouhakis.googlepages.com/out.ogg")

---

### Post by brad1138 on 2006-10-29
iovar, someone in a separate tread did post that, I tried it and it isn't check boxes per say more of a "dos" looking prog. It started asking question I didn't know the answer to or even understand. so I exited out. 

I'll start it again

ex: 

Whats your video cards bus identifier  (?)

How many kbs of memory does your card use (prob 32x1024 but ?)

should I Use kernel framebuffer device interface? :confused: 

Now its asking a lot of keyboard q's, what the heck do they have to do with  Video???

what X.Org server modules that should be loaded by default: :confused: :confused: 

Now it's asking mouse question, I am stopping here, this is a simple point and click ??? (actually you can't click on anything in this window)

Brad

---

### Post by iovar on 2006-10-29
How about defaults on most of them?
> 
Whats your video cards bus identifier  (?)

Doesn't it have a value?

> 
How many kbs of memory does your card use (prob 32x1024 but ?)

You did read the message saying "This parameter should be left blank..."
didn't you?

> 
should I Use kernel framebuffer device interface? :confused: 

Similarly: "Enabling this option is the safe bet, but feel free to turn it off..."

> 
Now its asking a lot of keyboard q's, what the heck do they have to do with  Video???


You are reconfiguring the xserver, which includes the input devices.

> 
what X.Org server modules that should be loaded by default: :confused: :confused: 

How about, whatever is already checked?

> 
Now it's asking mouse question, I am stopping here, this is a simple point and click ??? (actually you can't click on anything in this window)


Point and click or mindless next, next...???

I mean, if you don't even bother to read ten lines of text, why should I
or anyone else go on helping you? 

This is simply annoying. Linux is not ready for left-click zombies.

---

### Post by brad1138 on 2006-10-29
I had read the "10 lines" along with about 100,000 lines this weekend. They were helpful but still left parts of it were you had to assume what would be right, for all I knew one wrong assumption would crash everything. 

Ex:

Use kernel framebuffer device interface? 
Enabling this option is the safe bet, but feel free to turn it off... 

It also says commonly one way works the other doesn't, It seems to recommend "yes" but "no" is highlighted by default.

I have read so many instructions and posts with "try this" or "try that", my brain is frazzled.

That being said, I went through the entire setup, finished and rebooted and.....:D :D :D  I have 1280x1024!!

Thank you everyone for all you help and sorry for sounding testy, This wasn't what I was expecting to spend my weekend doing.

Thanks Again,
Brad

---

### Post by iovar on 2006-10-29
Well, I'm glad you made it, really.

But all this wasn't needed. If you've just posted a question on
how to get more resolutions, instead of going around on your own,
trying to install drivers, you would have needed a lot less time.

Anyway, if that finishes your installation, welcome!
Now you can start answering questions, too!:)

---

