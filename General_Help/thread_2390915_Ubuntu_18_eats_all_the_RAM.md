---
title: "Ubuntu 18 eats all the RAM"
date: 2018-05-03
forum: General Help
---

### Post by waffen on 2018-05-03
Hi,

I have this PC: Core I5-6400, 2.70Ghzx4, Intel HD Graphics 530 (Skylake GT2) 4GB RAM and 1 TB HD, now I just start session open Firefox and the OS eats 80% of the RAM, almost 3GB I need to work with Eclipse IDE and thats almost impossible now.. in Ubuntu 16.04 the memory consumption was very low..  I have LAMP installed too. 

any tips for improve the memory usage?

---

### Post by Claus7 on 2018-05-03
Hello,

I noticed almost the same thing with chromium yet:
the open tabs are ~ 20
system alone takes approximately 1.2GB RAM
and with chromium 3.0GB RAM

I would advice you to:
i) use alternative browser, e.g. opera
ii) increase your memory
iii) use firefox with a lower version

Regards!

---

### Post by waffen on 2018-05-03
> **Claus7 said:**
> Hello,

I noticed almost the same thing with chromium yet:
the open tabs are ~ 20
system alone takes approximately 1.2GB RAM
and with chromium 3.0GB RAM

I would advice you to:
i) use alternative browser, e.g. opera
ii) increase your memory
iii) use firefox with a lower version

Regards!

Thanks for the reply! Im a web dev so I need both tools at least... so for 
1. Firefox is the best for my job
2. So 4GB is not enough for ubuntu? in the same PC dual boot I have windows 10 installed and no memory issue running the same software....
3. So you mean dont use the latest Firefox version?

---

### Post by monkeybrain20122 on 2018-05-03
Maybe this? [https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed)

---

### Post by Claus7 on 2018-05-03
Hello,

> **waffen said:**
> Thanks for the reply! Im a web dev so I need both tools at least... so for 
1. Firefox is the best for my job
2. So 4GB is not enough for ubuntu? in the same PC dual boot I have windows 10 installed and no memory issue running the same software....
3. So you mean dont use the latest Firefox version?

for example using firefox 47.0.2 the extra RAM is 0.2GB. I have not used the latest version, yet you were able to see the comparison with chromium.

> **monkeybrain20122 said:**
> Maybe this? [https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed)

Just to mention that I can see this performance using gnome-flashback. The link provided is about the garbage collector, which seems not be an issue in this situation, if I'm not mistaken.

Regards!

---

### Post by waffen on 2018-05-03
> **monkeybrain20122 said:**
> Maybe this? [https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed)

I just make some tests and nope...

---

### Post by waffen on 2018-05-03
What about use another desk? which one do you recommended?

---

### Post by monkeybrain20122 on 2018-05-03
> **Claus7 said:**
> 

Just to mention that I can see this performance using gnome-flashback. The link provided is about the garbage collector, which seems not be an issue in this situation, if I'm not mistak.



Beats me then. I use unity on 18.04, doesn't have any problem with many tabs open on FF and even running vbox. I have 4 G of ram on this machine.

---

### Post by monkeybrain20122 on 2018-05-03
> **waffen said:**
> What about use another desk? which one do you recommended?
  
IMO 4 Gs or ram is more than enough for any Linux DE so there are probably some issues with your hardware or gnome, hence a "light desktop" us not really necessary unless you have an aesthetic prefetence for something like LXDE or xfce. But either of which would pull in a lot of duplicated stuffs like fie manager, editors etc so it is not clean. 


I am using  good old unity here. it is fast and smooth and doesn't have many duplicates since it uses a lot of gnome stuffs anyway.

If want to give it a try just do
```
sudo apt install  ubuntu-unity-desktop
```

choose lightdm as your default

reboot, log into unity session in the login greeter screen

That's it

If you are using a labtop for certain touchpad functions you need to install the package xserver-xorg-input-synaptics

i have added the [unity7 maintainer ppa]("https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop") but I think it is optional.

The package ubuntu-unity-desktop package pulls in some recommended pkgs like mpv, gnome-mpv and youtube-dl. You can uninstall them later if you don't need them. ( I have tried "sudo apt install --no-install-recommends ubuntu-unity-desktop" but somehow something didn't work, maybe it was my set up, or may be some recommended pkgs are actually needed, so installl the recommends on the safe side)

If all work you can uninstall gnome-shell (or keep it if you wish)

---

### Post by waffen on 2018-05-03
I just discover this: change the display manager to lightdm will reduce the RAM consumption in almost +1GB, looks like gdm is not working well in this version....

---

### Post by Claus7 on 2018-05-04
Hello,

> **waffen said:**
> I just discover this: change the display manager to lightdm will reduce the RAM consumption in almost +1GB, looks like gdm is not working well in this version....

haven't checked that! After upgrade to 18.04 the default was gdm3. Yet, due to loop problems and due to the fact that I like the brighter lightdm and its faster boot time I changed to that without in-between checking the ram consumption. The values I have reported are all using lightdm and ubuntu-flashback.

Nice that you solved your problem. Just to mention that one desktop environment that all these years is light concerning the ram usage and I'm aware of is xubuntu.

Regards!

---

### Post by waffen on 2018-05-06
Well, like I said -1GB of RAM now I changed to lightdm, but now Firefox is eating almost 2GB with only 2 tabs opened, is this a bug? I cant found info about it

---

### Post by nameinuse on 2018-05-06
Same problem here with Gnome - changed to Unity and everything working normally again. Gnome was unusable as mouse was laggy and Firefox, Thunderbird, Gnome Web etc were dreadfully slow. On the system monitor Gnome was using 98% of memory and the four CPU graph lines looked like someone was seriously ill!

---

### Post by QIII on 2018-05-06
Hello!

Do you have any help to offer the OP with GNOME?

---

### Post by waffen on 2018-05-06
> **nameinuse said:**
> Same problem here with Gnome - changed to Unity and everything working normally again. Gnome was unusable as mouse was laggy and Firefox, Thunderbird, Gnome Web etc were dreadfully slow. On the system monitor Gnome was using 98% of memory and the four CPU graph lines looked like someone was seriously ill!

Yes I was in 16.04 with Unity with the latest Firefox and no issues at all with memory, its the same machine, Win10 no issues too (dual boot) if I cant found a fix I''ll need to install unity again...

---

### Post by waffen on 2018-05-06
> **QIII said:**
> Hello!

Do you have any help to offer the OP with GNOME?

Yes please! I was tunning FF so I gain almost 1.2GB of RAM, still not even close than the performance in 16.04

---

### Post by monkeybrain20122 on 2018-05-06
> **QIII said:**
> Hello!

Do you have any help to offer the OP with GNOME?

Well suggesting an alternative DE is a kind of help, OP never says he won't use any DE other than Gnome. People routinely recommend alternative DE liks xfce, mate, etc if things don't work. This is Linux and there are many DEs , there is no reason to commit to the default even if it is working poorly, and hacking gnome may be beyond the ability of most of us here.

---

### Post by QIII on 2018-05-06
The user did not ask for an alternative DE.  The question is about GNOME.  Please stay on topic.

---

### Post by waffen on 2018-05-17
After one week, the problem is still there, but Firefox is the app eating all the RAM, if its opened too much time FF will eat your memory, now I dont see any difference between it and Chrome... hope this will be fixed soon. Any ideas?

---

### Post by scottm75 on 2018-05-17
My laptop is a Dell Inspiron 1720.  It's over 8 years old now.  So there's a few old computer stats there.  Only just a short while ago.  I upgraded the ram to 4 Gigs.  I have swap set at 4 Gigs also.  I chose the upgrade option from Ubuntu  16.04 to 18.04.  Every time I look.  The computer is using just over half the ram.  Swap is barely touched.  Firefox and other programs are hardly increasing Ram and CPU.  Also temperature seems good.  In fact the computer is operating the best it has ever been.  

Before I used the tested Nvidia driver.  This time I'm using the X.Org.  I have done a couple of swaps between the two.  X.Org seems more stable for me.  I had trouble getting a couple of things to run.  So a couple of switch overs seemed to fix things for me.

---

### Post by waffen on 2018-05-18
I dont have NVidia, my PC have intel graphics inside.. it have 4GB RAM. 10GB Swap, at this moment I have open only Firefox, and memory consumption is 80% thats very bad...

---

### Post by techguru30 on 2018-05-19
> **waffen said:**
> Hi,

I have this PC: Core I5-6400, 2.70Ghzx4, Intel HD Graphics 530 (Skylake GT2) 4GB RAM and 1 TB HD, now I just start session open Firefox and the OS eats 80% of the RAM, almost 3GB I need to work with Eclipse IDE and thats almost impossible now.. in Ubuntu 16.04 the memory consumption was very low..  I have LAMP installed too. 

any tips for improve the memory usage?

This issue has to be hardware specific. I am currently running Ubuntu 18.04 LTS Bionic Beaver in UEFI mode on a Dell Latitude E4310. The most memory my computer uses is 2.8 GB with multiple tabs opened in Google Chrome. My computer does have 8GB of ram but only 7.6 GB is available due to it being shared with the Intel integrated HD Graphics card but I am not using 4GB of ram.

---

### Post by waffen on 2018-05-24
> **techguru30 said:**
> This issue has to be hardware specific. I am currently running Ubuntu 18.04 LTS Bionic Beaver in UEFI mode on a Dell Latitude E4310. The most memory my computer uses is 2.8 GB with multiple tabs opened in Google Chrome. My computer does have 8GB of ram but only 7.6 GB is available due to it being shared with the Intel integrated HD Graphics card but I am not using 4GB of ram.

Hardware?? which hardware can eat RAM?? 
I just test in my laptop CI5 4th generation 8MB RAM and the same issue, Firefox is eating all the memory, 2 tabs opened and 2GB of RAM for it, thats crazy... any idea how to fix it?

---

### Post by deadflowr on 2018-05-24
How "vanilla" is your Firefox setup?
Do you have any extensions/add-ons installed/added?

If you run Firefox in safe mode, does it eat everything?
(In Firefox go to Help > and click on Restart with add-ons disabled)

What happens if you create a new Firefox Profile?
(In Firefox either go to
```
about:profiles
```
or go to help again and Troubleshooting then scroll down to the About:profiles and click.
You'll enter a page and at the top will be create new profile.)

---

### Post by waffen on 2018-05-24
I have the same addons like in Ubuntu 16.04 a few weeks ago, in that version over the same machine no issues with memory.... I'll make some tests with new profiles but I dont think thats the issue, I read a lot of reports about FF eating all the memory in ubuntu.

---

### Post by waffen on 2018-05-24
I just test FF with new profile, the same result! start with 1.6 GB RAM consumption, only open gmail, this page and a third one tab where I browse differents pages, after 30 minutes FF eats almost 3GB of RAM +

---

### Post by deadflowr on 2018-05-24
Have you tried other browsers yet?
To see if there is something more to it?
(Whether or not it's not Firefox per se, but just something wrong in general, or whatnot)

(i feel this is somewhat a nuclear option...)

---

### Post by waffen on 2018-05-24
Im working now with Chromium, I'll post here an update.... but I know Chrome/Chromium eat more memory than FF ...

---

### Post by kazakore on 2018-05-25
> **QIII said:**
> The user did not ask for an alternative DE.  The question is about GNOME.  Please stay on topic.


I suggest you try reading the title of the thread and the OP again. Gnome is not mentioned once! He only asks for help on how to solve his issue. So stop bitching at people who are trying to do this for no good no reason!

To the OP:
Browsers are often huge memory sinks, especially when perusing sites with advanced advert content using Java, JS or Flash. This includes the likes of Facebook, Twitter and most online mail providers such as Hotmail and Gmail. One of the most simple things you can do to improve browser performance and save memory if to use a decent ad-blocker. Personally I would recommend installing uBlock Origin for such purposes. It can make a huge difference to RAM used by browsers.

---

### Post by waffen on 2018-05-25
Thanks for the reply! To be honest I was using Ubuntu Unity 16.04 with no issues in my both machines, using the same config and the same software, mostly for my work I need to have opened FF and Eclipse IDE (setting up with 1GB memory) all the time, I have installed LAMP and PostgreSQL too, just in case but as far I can see in the System Monitor no issues with memory for both apps. 

Like I said in Unity 16.04 I dont have issues just upgrade to Ubuntu Gnome 18.04 and the PC start with the memory problems (it have "only" 4GB of RAM) my laptop with Nvidia card and 6GB RAM run pretty well but off course it have +2GB RAM.. 

Yesterday I was testing others browsers: Chromium, Epiphany Midori(this cant load gmail) and the same problem, Im using lightgdm (in my laptop gnome default) and the same problem.. so looks like Gnome eats a lot of more memory than Unity.

This weekend I'll try installing Unity desktop...

---

### Post by HermanAB on 2018-05-25
Well, the desktop is an application same as any other.  There is nothing magical about it.  If it doesn't work properly, use another one.  FOSS provides many choices, from the super simple like Blackbox to the super fancy like KDE - the rest are somewhere in the middle.  

If you need to conserve RAM and processing cycles, then XFCE is a good choice: 
$ sudo apt install xfce4

Log out and log in.  

La voila.

---

### Post by lisati on 2018-05-25
> **waffen said:**
> Hardware?? which hardware can eat RAM?? 
I just test in my laptop CI5 4th generation 8MB RAM and the same issue, Firefox is eating all the memory, 2 tabs opened and 2GB of RAM for it, thats crazy... any idea how to fix it?

I don't know if there's a hardware issue or not. Sometimes it matters, sometimes it doesn't matter. I recently discarded two older android based smartphones that weren't being used. The hardware was perfectly adequate when the phones were new, but the software environment has evolved over the years, making the phones little better than dumb phones.

---

### Post by waffen on 2018-05-28
After 2 days of testings I need to post an update:for my work like I said I need to run Firefox and Eclipse IDE at the same time at least, in Gnome I cant run both because 4GB RAM is not enough for it, so I installed Xubuntu desktop (really good job with it, I dont use xfce in a lot of time) and all is working fine... FF is not eating memory I check his RAM consumption and actually he eats 1.2 GB, in gnome 2GB and increase a lot till block the entire system, now I can open all my others common programs with no issues at all.

So my conclusion: Gnome or/and Firefox dont works very well, but I think is Gnome in this case, I save some money because I planed to buy a new 4GB RAM card tomorrow... I really dont understand the change unity->gnome

Hope this thread help to another user with the same issue.... thanks to all for your comments!

---

### Post by leonardo-buffa on 2019-01-22
Hello I want to confirm I had the same problem, desperate about a machine hang due to 100% ram usage mainly using FF. I tried to install lightdm as suggested and the problem is solved: memory usage without FF or TB: 28%, with TB and a lot of FF tabs: 65%.
Before reading this I was really stuck! Thanks a lot to everybody

---

### Post by dick13d on 2019-01-23
I have a laptop 4gb ram, slow wifi, ssd with pentium performing excellent. 20 tabs in firefox or chromium is still performing great.
The new machine feels much slower and starts kswapd0 quickly. This while cpu is 4 times faster.
Differences:
laptop has swap partion and uses swap 200mb (some do not advice that with a ssd). New machine has no dedicated swappartition. much faster ssd, faster memory.
New machine has 4k monitor at 50hz.
New machine uses ext4. Laptop xfs filesystem + swap partition.

Both xubuntu 18.10 installed.

I do not know how to monitor swapfile (does it have swapfile?) at new machine. 

Is there an easy method to compare those machines to monitor their swap behaviour and memory usage?

Just ordered extra 4gb ram, but it would be nice to be able to explain the difference in behaviour and get better performance at new machine.

---

### Post by dick13d on 2019-01-23
The swapfile of the new machine was full. 1.5gb.

I added an extra swapfile 4gb and I guess it is solved. 40 tabs open in Chromium is no problem with 4gb ram and ssd.

Nevertheless is the investment in (4gb or more) extra ram recommended. 
Extra RAM will extend the life of harddisk and ssd and saves you probably a few extra recovery actions.

For monitoring swap:
[https://www.tecmint.com/commands-to-monitor-swap-space-usage-in-linux/](https://www.tecmint.com/commands-to-monitor-swap-space-usage-in-linux/)

For adding space to your swapfile: 
[https://askubuntu.com/questions/1009404/how-to-expand-existing-swap-file](https://askubuntu.com/questions/1009404/how-to-expand-existing-swap-file)

---

### Post by leonardo-buffa on 2019-01-23
> **dick13d said:**
> I have a laptop 4gb ram, slow wifi, ssd with pentium performing excellent. 20 tabs in firefox or chromium is still performing great.


I do not know how to monitor swapfile (does it have swapfile?) at new machine. 

hello, if I understood your doubt, you can easily see the swapfile usage with command: top

---

### Post by dick13d on 2019-01-29
Thx. The command: free

Gives also information about memory usage and swap memory.

---

### Post by oldrocker99 on 2019-01-29
It is possible that the disk cache may be taking up RAM. It is the lowest priority memory, and deletes itself if a program needs it.

---

### Post by Arthur King on 2019-02-24
I also had this problem after updating from 16.04.  The solution was to change the display manager to light DM. sudo dpkg-reconfigure lightdm  Then reboot possibly twice if you have multiple users.  Some posts advise the installation of slick-greeter, but that isn't actually essential.
Before changing to light DM I had tried using Cinnamon DE and Unity without changing the display manager, which did not solve the problem.  Now I find that the default Ubuntu DE works fine with light DM.

---

### Post by usernamoi on 2019-02-24
i know someone must have written this before, but have you tried using a  lightweight distro focused in very low specs like puppy linux or lubuntu, or xubuntu?

In my experience, Firefox and chrome will always consume around 1.5 or 2 gb of ram after having more than one tab open, and ubuntu usually consumes around 500mb or more. IMO 4gb is a bit low if you like to use or have many tabs opened, or browse and do something else.

Also, something i think can improve a bit speed is to use addons like addblock plus, cookie auto-delete, freeze tabs, and similar, so you can reduce the amount of things that are loaded in each page; the addons might consume a good amount of ram, but not as much as many tabs open with all their ads and other unnecessary things (like social buttons or some comment areas; in yt, for example, the live comments consume a lot of ram, and you could remove it with addblock plus).
[https://addons.mozilla.org/en-US/firefox/addon/ff-tab-suspender/?src=search](https://addons.mozilla.org/en-US/firefox/addon/ff-tab-suspender/?src=search)

Also, in firefox preferences you can experiment with the performance section: turn off "use recommended settings" and then you could reduce or increase the number of processors used by firefox; that could make it run faster or slower. But, firefox with 2 to 4gb wont offer a very good experience, so, if theres a way to get more ram, you should go for that if you really need to use it a lot, and with many tabs opened.
[https://support.mozilla.org/en-US/kb/performance-settings](https://support.mozilla.org/en-US/kb/performance-settings)

You could also remove or disable all telemetry related options in firefox. You have to use "about:config". Not sure how much it would affect ram, but if its one thing less firefox must do, it might help a bit.
[URL="https://superuser.com/questions/1003201/how-do-i-stop-mozilla-telemetry/1003208"]https://superuser.com/questions/1003201/how-do-i-stop-mozilla-telemetry/1003208
[/URL][https://www.reddit.com/r/firefox/comments/9hmiau/to_unsuspecting_admins_firefox_continues_to_send/](https://www.reddit.com/r/firefox/comments/9hmiau/to_unsuspecting_admins_firefox_continues_to_send/)

Another thing you could try to reduce ram consumption, if you only need the browser to check online articles, or videos, you could try using a lightweight browser. 

Qupzilla (now Falkon) consumes very little ram, but it used to crash or fail if you open many tabs, so if you could work with less than 10, the risk of crashing the browser was low. Im not sure how good is falkon currently; probably more stable and maybe it can handle 20 or tabs. 
[https://www.falkon.org/download/](https://www.falkon.org/download/)

Midori
Also might fail, but is still very light.
[https://www.midori-browser.org/download/](https://www.midori-browser.org/download/)

Qutebrowser
I have never used this one, but i just discovered it. It claims to be extremely lightweight, but it can be used only with keyboard.
[https://qutebrowser.org/](https://qutebrowser.org/)

---

