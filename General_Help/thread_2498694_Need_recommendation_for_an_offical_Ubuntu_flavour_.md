---
title: "Need recommendation for an offical Ubuntu flavour for my machine config"
date: 2024-06-24
forum: General Help
---

### Post by j.gohel on 2024-06-24
I have a 11.6 inch Asus laptop with following configuration

```
    OS: Windows 10 Home
    Processor: Intel Celeron N4500 Processor 1.1 Ghz (4M Cache, upto 2.8 GHz, 2 cores)
    Memory: 4GB DDR4 onboard, Memory Max upto 4 GB
    Storage: 128 GB M.2 NVMe PCIe 3.0 2280 SSD (Supports upgrade upto  2 TB M.2 NVMe SSD)
```

I want to install Ubuntu on it. 

Reading about latest (24.04) **Ubuntu Desktop** edition at [https://ubuntu.com/download/desktop#system-requirements](https://ubuntu.com/download/desktop#system-requirements) found that it is not suitable for my machine and exploring on web I found that for machines with lower configurations official Ubuntu flavours ([https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)) should be used. 

Checking out the websites of **Xubuntu, Kubuntu and Lubuntu** it is only on **xubuntu** website I could find the system requirements page at [https://xubuntu.org/requirements/](https://xubuntu.org/requirements/) and looking at the recommended specs I came to conclusion it is not suitable for my machine.

Checking the website of **Kubuntu** at [https://kubuntu.org/](https://kubuntu.org/) and **Lubuntu** at [https://lubuntu.me/](https://lubuntu.me/) I couldn't find the system requirements for installing them.

So my first question is: Are there any official pages which mentions them so that one can go through them and decide whether they are suitable for a particular machine or not?

Checking out website of **Ubuntu Budgie** at [https://ubuntubudgie.org/downloads/](https://ubuntubudgie.org/downloads/) following is mentioned at the time of writing this

```
Ideal for computers with: 4GB or more of RAM, 64-bit capable Intel and
AMD processors, UEFI PCs booting in CSM mode, Modern Intel-based Apple
Macs
```

Checking out **Edubuntu** at [https://www.edubuntu.org](https://www.edubuntu.org) no system requirements information available.

Checking out **Ubuntu Cinnamon** at [https://ubuntucinnamon.org/](https://ubuntucinnamon.org/) no system requirements information available.

Checking out **Ubuntu Mate** I could find System Requirements information at [https://ubuntu-mate.org/about/requirements/](https://ubuntu-mate.org/about/requirements/).

All that said and shared, my last question is which of the available flavours would one recommend for my machine config? I want to primarily use my machine for note-taking purpose and doing some scripting using a simple text-editor in Ruby language. 

Thank you.

---

### Post by phatton1 on 2024-06-24
I run Ubuntu Cinnamon on both of my machines. One is 2 years old with 8gb ram and the other at least 8 years old and on both machines it runs really fast

---

### Post by j.gohel on 2024-06-24
**[COLOR=#000000]@[/COLOR]**[**[COLOR=#000000]phatton1[/COLOR]**]("https://ubuntuforums.org/member.php?u=2185660") Thanks for your response. Do you mind sharing whether your machines share similar configuration like mine? If you notice I have a **Intel Celeron N4500 Processor 1.1 Ghz processor and max 4GB memory **support**.**

---

### Post by tea for one on 2024-06-24
> **j.gohel said:**
> I have a 11.6 inch Asus laptop with following configuration
```
    OS: Windows 10 Home
    Processor: Intel Celeron N4500 Processor 1.1 Ghz (4M Cache, upto 2.8 GHz, 2 cores)
    Memory: 4GB DDR4 onboard, Memory Max upto 4 GB
    Storage: 128 GB M.2 NVMe PCIe 3.0 2280 SSD (Supports upgrade upto  2 TB M.2 NVMe SSD)
```
Checking out the websites of **Xubuntu, Kubuntu and Lubuntu** it is only on **xubuntu** website I could find the system requirements page at [https://xubuntu.org/requirements/](https://xubuntu.org/requirements/) and looking at the recommended specs I came to conclusion it is not suitable for my machine.
I'm sure that your PC is more than capable of running Xubuntu.
I use Xubuntu 24.04 daily on a Lenovo 11.6" Netbook (2021 vintage)
It has a slightly older processer Intel Celeron 4020

How did you conclude that Xubuntu was not suitable?

---

### Post by guiverc on 2024-06-24
Lubuntu hasn't provided minimum specifications since 2018 (specifically Lubuntu 18.04 LTS).

The Lubuntu team wrote the reason in this doc - [https://lubuntu.me/taking-a-new-direction/](https://lubuntu.me/taking-a-new-direction/)

[I]I've already written about this on your prior question [here]("https://askubuntu.com/questions/1518545/official-pages-mentioning-system-requirements-for-official-ubuntu-flavours"), but I'll answer here so others don't see any need to.
[/I]
Whilst I wasn't part of Lubuntu team when they made that decision, I sure can understand it.

I still use single-core/single-thread devices with 1 (& 1.5) GB of RAM, and what matters most is how the machine is used. Those old *pentium M *devices were used in QA of Lubuntu up to the 19.04 release (*the last providing support for **i386; they run Debian now*), and still use core2duo machines with as little as 2GB of RAM running current releases in QA. Whilst the machines will run all software, I'm using such low resource hardware rather differently to this 2017 machine, or even my secondary 2008 *core2quad* machine.

On a machine with LOW ram (*and generally I see a device with <6GB of RAM low-ram, but it'll really depend what you use the machine for*) you want to ensure the apps you'll use share RAM with your desktop, rather than needing different resources (ie. *libraries or toolkits*) that do the same thing differently...   ie. I'd pick your apps first, then choose a desktop/WM that will share resources with the apps you'll run.

You mentioned

> [LEFT][COLOR=#0C0D0E][FONT=-apple-system]my primary goal with this machine is note-taking and secondary doing general Ruby scripting.[/FONT][/COLOR][/LEFT]

which is generic, but not specific.   How do you wish to take notes; do you want to use just a simple text editor?  do you care what text editor?  maybe you're happy with just using `vi` or `vim`, `nano` or `emacs` and using the same tools I used back in the mid-1980s.

Likewise how to you do your ruby scripting??   No IDE but a simple text editor running in terminal that won't use resources...  How will you run that code?  These details do matter... as a text based TEXT EDITOR will be very light on resources.. but GUI Text editors will use more resources.... and they thus they impact the desktop choice!

The lightest system will be just installing Ubuntu Server, if you want a GUI of sorts; then add a simple WINDOW MANAGER and forget a more complex (*and thus resource intensive*) desktop...

The *lightest* flavor *out of the box* is Lubuntu... however as that desktop is Qt5 based (*up to 24.04 anyway*), if using GTK3/4 apps you'll do better with Xubuntu in my opinion, as apps will share resources with the Xfce desktop....

FYI:   On this machine (2017 optiplex), thru to a really old

> ibm thinkpad t43 (pentium m, 1.5gb ram, radeon x300)

I have multiple desktops installed, and on that really old IBM THINKPAD with limited resources its most useful too!  That box has at most a 60GB *spinning rust* drive, thus I can happily lose a *few hundred MB* of disk space by having multiple desktops installed.. and I select which I'll use based on what I'll do in that session, thus I may choose to use a WM alone, Xfce, MATE, LXDE, LXQt  .. based on what I'll consider is most efficient with what I intend to do on the session... On that really ancient thing, its the 1.5GB of RAM that matters to me, not the extra bloat of maybe 450MB of having multiple desktops installed.... ie. I care about RUNTIME performance, and don't care about the larger footprint on disk, more bandwidth used by updates (*as I get updates for all desktops/packages I have installed*)  etc... 

My point is I don't think the *flavor* choice is something to really concern yourself with.

FYI:  If you don't know what I mean by effect of flavors/libraries/toolkits... the old IBM Thinkpad I'm using as EXAMPLE will offer you many text editors... from VIM, NANO..., to PLUMA (MATE text editor), MOUSEPAD (Xfce text editor), FeatherPad (LXQt text editor), Leafpad (LXDE text editor).... ie. multiple tools that all do the same thing, but do so efficiently when running the desktop that they're intended for; as they'll share resources with that DE...  On my current 16GB machine I don't worry about resources; but when using a low-resource machine I do consider that (*and tend to ignore disk space unless the box has <32GB of disk*).

For note-taking... are you wanting to just type??  do you want/need formatting?? want to include pictures/diagrams etc??  ie. app or type of app & note-taking matters..

For coding... text editor & runtime compile/interpret or execute just at terminal??  or a IDE/*integrated development environment* have rather different requirements... If you want an IDE, which IDE??  as that is a question that does matter on limited resource machines.

Note:  I know almost nothing about RUBY coding, so have no idea as to the resources required to develop & execute your code, nor know nothing about the datasets you'll process, and how many MB/GB of data you'll be using, thus what resources are required to execute the code etc..

Does your device have touch screen??   I tend to prefer a different DE if the box has a touchscreen to not having it.. 

I'd work out those details first... 

This doesn't answer your question though, but is my 2c (*as someone who uses low-resource devices from 2008 & older on a daily basis*)  **but** you can likely get away with a number of choices..

---

### Post by j.gohel on 2024-06-24
> **tea for one said:**
> 
I use Xubuntu 24.04 daily on a Lenovo 11.6" Netbook (2021 vintage)
It has a slightly older processer Intel Celeron 4020

How did you conclude that Xubuntu was not suitable?

**@tea for one** It was based on following recommendation at [https://xubuntu.org/requirements/](https://xubuntu.org/requirements/)

> To get a smooth experience when running multiple applications parallel  on the desktop, it is recommended to have a 1.5Ghz Dual Core processor  with at least **2 GB** of memory.

In my config I mentioned 1.1 Ghz Dual Core processor. So based on this I assumed that Xubuntu is not suitable for my machine.

Do you mind sharing your use-cases with the machine? As I said 

> I want to primarily use my machine for note-taking purpose and doing  some scripting using a simple text-editor in Ruby language. 

Do you do use it for similar purpose or you can smoothly perform fairly advance tasks as well?

Thanks.

---

### Post by tea for one on 2024-06-24
> **j.gohel said:**
> I want to primarily use my machine for note-taking purpose and doing some scripting using a simple text-editor in Ruby language 
I have zero experience of Ruby, so I am unable to answer your question.

Why not try a live session see if it is suitable for you?

---

### Post by coley9225 on 2024-06-24
j.gohel, Hello.
My daily driver is a 15 inch Lenovo laptop. When I got it,(upgraded a little since), it had a celeron, 1.1Ghz, 2 core 2 thread processor, and 4 GB of ddr3 memory, and a 1TB 5400rpm hdd. I run Lubuntu with zero issues. I always have 2 instances of Firefox, 1 google chrome, and Thunderbird email client running, many times with multiple tabs open. On top of that, I run vscodium to write code( bash scripts, python, html), listen to pandora in the chrome browser, and still have no hicups or lags. The integrated graphic work well. I use the laptop screen and a 43 inch 1080p tv, I stream video, etc., all with out issue. I believe Lubuntu would be a great choice for that machine. My advice is to make a live usb and test it out first, along with a couple of others, and find the desktop environment you like best. I prefer the lxqt, but you may be happier with kde plasma or cinnamon. That's the joy of linux, do what fits your style and taste. Best of luck to you.

---

### Post by j.gohel on 2024-06-24
> **guiverc said:**
> 
On a machine with LOW ram (*and generally I see a device with <6GB of RAM low-ram, but it'll really depend what you use the machine for*) you want to ensure the apps you'll use share RAM with your desktop, rather than needing different resources (ie. *libraries or toolkits*) that do the same thing differently...   ie. I'd pick your apps first, then choose a desktop/WM that will share resources with the apps you'll run.

You mentioned

```
[COLOR=#0C0D0E][FONT=-apple-system]my primary goal with this machine is note-taking and secondary doing general Ruby scripting.[/FONT][/COLOR]
```

which is generic, but not specific.   


> How do you wish to take notes; do you want to use just a simple text editor?  do you care what text editor?  maybe you're happy with just using `vi` or `vim`, `nano` or `emacs` and using the same tools I used back in the mid-1980s.

I regularly use Geany ([https://www.geany.org/](https://www.geany.org/)) on my Ubuntu Desktop machine and would prefer to use it on the current machine under discussion. But I have a thought for using a markdown editor also like Abricotine ([https://github.com/brrd/abricotine](https://github.com/brrd/abricotine)).


> Likewise how to you do your ruby scripting??   No IDE but a simple text editor running in terminal that won't use resources...  

Using Geany for writing the code should be fine.

> How will you run that code?  

From terminal.

> These details do matter... as a text based TEXT EDITOR will be very light on resources.. but GUI Text editors will use more resources.... and they thus they impact the desktop choice!

Agreed and thanks for sparing time to make me realize about the need for sharing such specific things because in my original question I took it for granted, so sorry about that.

> The *lightest* flavor *out of the box* is Lubuntu... however as that desktop is Qt5 based (*up to 24.04 anyway*), if using GTK3/4 apps you'll do better with Xubuntu in my opinion, as apps will share resources with the Xfce desktop....


> My point is I don't think the *flavor* choice is something to really concern yourself with.
I am getting your point but since I haven't use any of the available flavours I really don't knew which one to start with and thus I sought the community's help. And also I am not a Linux expert so I don't know many of things/terminologies you mention about, for e.g. *Qt5 based* , *GTK3/4 apps, etc.*

> FYI:  If you don't know what I mean by effect of flavors/libraries/toolkits... the old IBM Thinkpad I'm using as EXAMPLE will offer you many text editors... from VIM, NANO..., to PLUMA (MATE text editor), MOUSEPAD (Xfce text editor), FeatherPad (LXQt text editor), Leafpad (LXDE text editor).... ie. multiple tools that all do the same thing, but do so efficiently when running the desktop that they're intended for; as they'll share resources with that DE...  On my current 16GB machine I don't worry about resources; but when using a low-resource machine I do consider that (*and tend to ignore disk space unless the box has <32GB of disk*).

Thanks for being proactive on clarifying that. I am not an expert with Linux systems so I am unaware about all the text editors you have mentioned. I have got a chance to use only NANO. And whenever possible I prefer to work with GUI-based editors like I have mentioned that I regularly use Geany.

> For note-taking... are you wanting to just type??  do you want/need formatting?? want to include pictures/diagrams etc??  ie. app or type of app & note-taking matters..

For now I just know that I want to type and probably in markdown syntax. As of now I am not sure whether I will need pictures/diagrams to be included with my notes but doing that would definitely be an advantage.

> For coding... text editor & runtime compile/interpret or execute just at terminal??  or a IDE/*integrated development environment* have rather different requirements... If you want an IDE, which IDE??  as that is a question that does matter on limited resource machines.

For coding I would type the code in Geany and run it from terminal. On the Ubuntu Desktop I use on my PC I code using Eclipse editor but that should prove too heavy on the machine under discussion.

> Note:  I know almost nothing about RUBY coding, so have no idea as to the resources required to develop & execute your code, nor know nothing about the datasets you'll process, and how many MB/GB of data you'll be using, thus what resources are required to execute the code etc..

I will need to install Ruby and configure it to use its interpreter from the terminal. I don't have any plans to do complex programming tasks with this machine. The idea is to have the capability to use it for developing simple scripts as and when needed, and run them from terminal. I am not looking at using the machine for crunching/processing large-data sets.

> Does your device have touch screen??   I tend to prefer a different DE if the box has a touchscreen to not having it.. 

Yes the device has touch screen and the pre-installed Windows works with touch gestures as well. As a matter of fact a stylus is also provided which works with Windows but with Windows the machine shows lags in processing within few mins of constant usage and anyways I have never been a fan of Windows. For my regular programming I prefer Ubuntu.

Considering the fact that device support touch-screen is there any option to leverage the touch features?

@**guiverc **I hope this time I have been elaborate and specific enough (and for that big Thanks to you for asking questions related to which things were actually supposed to be mentioned by me) to help you get into a position to help me kick-start with an appropriate flavour in my context.

Thank you so much again.

---

### Post by oldfred on 2024-06-24
[FONT=arial]I use Kubuntu on my desktop from 2017 with [/FONT][FONT=monospace][FONT=arial][COLOR=#000000]Intel Core i5-6500[/COLOR] but have lots of RAM.
 I also installed Kubuntu on an external SSD and found it worked reasonably well with old 2006 retired laptop with 1.5GB of RAM.
When using it from HDD I learned to only load one larger app and several small apps at once. Only a few Firefox tabs. When I loaded more it when to swap on HDD which was slow an up to 2 sec of grey screen.
With external SSD I still tried to only load a few apps, but swap was so fast I barely noticed it.

Or with your NVMe drives & 4GB of RAM, you can run any of the light weight flavors.

I just loaded Zim, geany & have Firefox with 2 tabs. shows 3GB used with my Kubuntu 24.04.
```
[/FONT][/FONT][FONT=arial][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ free -h [/COLOR]
               total        used        free      shared  buff/cache   available 
Mem:            15Gi       3.1Gi       9.4Gi       853Mi       4.2Gi        12Gi 
Swap:          511Mi          0B       511Mi
[/FONT][FONT=monospace][FONT=arial]
```[/FONT]
[/FONT]

---

### Post by guiverc on 2024-06-24
I'll answer, but I'm in a hurry so I won't quote and just give some points...

Geany is an app I don't know, but a quick look on my system (ie. 

```

guiverc@d7050-next:~$   apt depends geany
geany
  Depends: libatk1.0-0t64 (>= 1.12.4)
  Depends: libc6 (>= 2.38)
  Depends: libcairo2 (>= 1.8.0)
  Depends: libgcc-s1 (>= 3.3.1)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0t64 (>= 2.79.0)
  Depends: libgtk-3-0t64 (>= 3.21.5)
..

```

I stopped at LIBGTK-3 as that is an indication that the app is intended for a GTK3 environment, ie. that app I'd expect would be more efficient on a Xfce (Xubuntu) or even GNOME (Ubuntu Desktop) environment that a LXQt (Qt5) setup.... 

Looking up details on something you compile would of course need to be done differently.

But does this matter??

To me, my current system is a Ubuntu system....

The desktop (or really *session*) I logged in is using a Lubuntu one, so I'm using a LXQt desktop with Lubuntu configs  (*though I've swapped out Lubuntu's WM with xfwm4 from Xfce for reasons*)...    but I still see the install as a Ubuntu one.

If it was me, and I wanted Ubuntu or a *flavor*, I'd just install one.. and then decide for yourself which is best..  Personally, I see the *release* as more critical, ie. do you want a LTS or *long term support* release, or need newer software??   Currently the *latest* release is also a LTS, so maybe that implies 24.04 LTS is maybe a winner, as it'll be supported until 2029-April !!

I mentioned multi-desktops in that I find on *low-resource* hardware its actually helpful.  On that *ancient* thinkpad I mentioned, the RAM is so minimal (1.5GB) that I decide which DE or WM I'll used at login... 

Have you tried Xfce?  LXQt?  do you have a preference for one or the other??  Have you tried MATE? or other DEs  (Xfce the lightest GTK, LXQt the lightest Qt5, MATE probably next lightest GTK etc)

Geany is one app you stated, and I suspect that app would perform better on Xubuntu.. so maybe Xubuntu.   Most of what you describe though is very light, as you appear to not be fussy with your requirements at all (ie. almost any text editor would do I suspect...) and no mention of any special development environment.

I rarely use touch devices, but personally I do like GNOME best when using touch...

Your requirements are *light* as I see it, so I'd try some and see which you think you'll be happiest with..   But if you make a wrong decision, if you've installed Xubuntu, Lubuntu, Ubuntu-MATE, Kubuntu, Ubuntu-Budgie, Ubuntu-.... etc. you can rather easily convert one into another... via package changes OR just a *non-destructive *re-install (*see end*)...

What GPU does your box have... Another benefit of Xfce or Xubuntu.. is I have found it has fewer issues than other desktops with really old graphics cards  (even better than Lubuntu of late too!)  If you try some out (ie. write them to a thumb-drive, even using a tool like Ventoy to write multiple ISOs to a thumb-drive and just use them *live* on your hardware without install) you may decide some you like, others you don't.. thus have fewer to choose from anyway. 

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)   (*which applies to all Ubuntu Desktop flavors too !* )

I'll add I did keep some older hardware on older releases, as I get better performance.. I also find the older hardware can perform better on the older kernel stacks (ie. Ubuntu LTS has kernel stack choice; GA being better for older hardware often, HWE usually best for newer hardware of course)...  but this can usually easily be changed post-install

-----

I'll go off on another *tangent*.... but you can also change *flavors* rather easily too for releases up to 23.10... I talk about it over on the prior site ([https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533))...

ie.. the final comment talks about a problem I encountered in 24.04 or *noble* QA testing...  ie. Some testing I perform includes the following

- install a system (say Lubuntu)... makes changes to desktop (eg. change wallpaper); add additional packages/apps & data files to make it my own system...   looks good now ..
- install *non-destructively* a Xubuntu system... & reboot... On login I expect the LXQt desktop to be replaced by Xfce, all Lubuntu/LXQt apps to now be Xfce apps, but my additional apps I expect to still be there (re-installed actually!) & my data files to survive....
- install *non-destructively *a Ubuntu Desktop system & reboot... On login I now expect to see GNOME apps & GNOME desktop, but still have my have data files intact, plus my non-standard music play continue the same playlist I created back on the first Lubuntu install... 
- now *non-destructively re-install Lubuntu*, and reboot... I now expect to have returned back to where I started with the altered wallpaper I selected on the first step, my non-standard music app still there progressing through my music playlist, and my data files there  etc...

This is an QA type of install test I've done on many releases... on 24.04 it discovered a problem, thus this has been *prevented* on *flavors* using `ubuntu-desktop-installer` ... so maybe making the correct choice matters.. but personally I still don't think it does...  This is still possible for some *flavors* (*those using calamares for starters*) but my attempted point is I don't think you need to stress over which *flavor*...   I consider them all Ubuntu, and you can turn one into another by just changing packages...

You do realize all Ubuntu *flavors* are created by the same tools, on the same infrastructure etc...   ie. the *seed* files just alter which packages get included..., for 24.04 or *noble* two such *seed *files are 
- [https://ubuntu-archive-team.ubuntu.com/seeds/xubuntu.noble/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/xubuntu.noble/desktop)
- [https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.noble/desktop](https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.noble/desktop)

A quick explore from those and you'll find links to other *flavors*, or even Ubuntu Desktop, Ubuntu Server etc...

I do really just see them all as Ubuntu systems... with different packages, and we can install/remove packages rather easily...  

Release maybe consider too, what kernel stack works well with your GPU etc..  Have you tried any?  on the intended hardware?

---

### Post by phatton1 on 2024-06-24
> **j.gohel said:**
> **[COLOR=#000000]@[/COLOR]**[**[COLOR=#000000]phatton1[/COLOR]**]("https://ubuntuforums.org/member.php?u=2185660") Thanks for your response. Do you mind sharing whether your machines share similar configuration like mine? If you notice I have a **Intel Celeron N4500 Processor 1.1 Ghz processor and max 4GB memory **support**.**

Totally different pcs by different companies. One is an old hp, the other more modern one is from novatech

---

### Post by j.gohel on 2024-06-24
> **guiverc said:**
> 

I stopped at LIBGTK-3 as that is an indication that the app is intended for a GTK3 environment, ie. that app I'd expect would be more efficient on a Xfce (Xubuntu) or even GNOME (Ubuntu Desktop) environment that a LXQt (Qt5) setup.... 


Ok.

> If it was me, and I wanted Ubuntu or a *flavor*, I'd just install one.. and then decide for yourself which is best..  Personally, I see the *release* as more critical, ie. do you want a LTS or *long term support* release, or need newer software??   Currently the *latest* release is also a LTS, so maybe that implies 24.04 LTS is maybe a winner, as it'll be supported until 2029-April !!


Yes LTS is preferred.

> I mentioned multi-desktops in that I find on *low-resource* hardware its actually helpful.  On that *ancient* thinkpad I mentioned, the RAM is so minimal (1.5GB) that I decide which DE or WM I'll used at login... 

Have you tried Xfce?  LXQt?  do you have a preference for one or the other??  Have you tried MATE? or other DEs  (Xfce the lightest GTK, LXQt the lightest Qt5, MATE probably next lightest GTK etc)


Sorry cannot answer that I as am unaware about those technical things. As I said I know bare-minimum linux with which I can achieve my daily programming job. But yes, based on your first quote in this answer I think Xfce indicates Xubuntu and based on that what I understand is that you are asking me have I tried Xubuntu? If yes, then no I haven't.


```
Geany is one app you stated, and I suspect that app would perform better on Xubuntu.. so maybe Xubuntu.   Most of what you describe though is very light, as you appear to not be fussy with your requirements at all (ie. almost any text editor would do I suspect...) and no mention of any special development environment.
```

Yes. Geany is just a preference because I am used to it for so many years. But no rigidity regarding it.

> I rarely use touch devices, but personally I do like GNOME best when using touch..

Sorry couldn't get you on that. Is there any flavour available which supports touch features and which I can try?

> 
Your requirements are *light* as I see it, so I'd try some and see which you think you'll be happiest with..   But if you make a wrong decision, if you've installed Xubuntu, Lubuntu, Ubuntu-MATE, Kubuntu, Ubuntu-Budgie, Ubuntu-.... etc. you can rather easily convert one into another... via package changes OR just a *non-destructive *re-install (*see end*)...

Ok.

>  What GPU does your box have... 

```
Graphics:  Intel® UHD Graphics
Display:29.46cm  (11.6), 16:9 HD (1366 x 768), 250nits,  NTSC: 50%  , Screen-to-body  ratio:63 &#65285;, MPP2.0 Stylus input,  360-degree Flip hinges | Garaged Stylus with inboard Charging





```

> 
Another benefit of Xfce or Xubuntu.. is I have found it has fewer issues than other desktops with really old graphics cards  (even better than Lubuntu of late too!)  If you try some out (ie. write them to a thumb-drive, even using a tool like Ventoy to write multiple ISOs to a thumb-drive and just use them *live* on your hardware without install) you may decide some you like, others you don't.. thus have fewer to choose from anyway. 

Thanks for letting me know about Ventoy. I will definitely download ISOs of multiple flavours on my pen-drive and try them without installing.

> I'll go off on another *tangent*.... but you can also change *flavors* rather easily too for releases up to 23.10... I talk about it over on the prior site ([https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533))...

Thanks for sharing this. I will bookmark it just in case I needed to perform such changes with my installation.

Thank you so much again for sparing your precious time for such elaborate answers and guidance.

---

### Post by Impavidus on 2024-06-24
[Your processor](https://www.intel.com/content/www/us/en/products/sku/212326/intel-celeron-processor-n4500-4m-cache-up-to-2-80-ghz/specifications.html) has 1.1 GHz base frequency, 2.8 GHz burst frequency. What that means is explained by intel [here](https://www.intel.com/content/www/us/en/support/articles/000098324/processors.html). Your operating system does nothing most of the time, so the burst frequency is more relevant. 2.8 is more than 1.5, so it's fine. Anyway, processor speed isn't the most critical. If slow, your system will become slow, not unusable.

De base speed is more relevant for processes that run at high load for a long time. Real-time simulations and things like that.

4 GiB isn't a lot of memory, but you should be fine, as long as you don't run a web browser with 26 open tabs.

---

### Post by dragonfly41 on 2024-06-24
Post #1

[COLOR=#000000]> I want to install Ubuntu on it.
There is another option which I use daily.
Subject to host PC having USB 3.0 port (for speed) you can quite happily run Ubuntu in an external SSD. I have two in a powered dual docking bay from StarTech. The SSD's sit in caddies which plug into the powered dual docking bay.

P.S. for note editing I suggest CherryTree.[/COLOR]

---

### Post by j.gohel on 2024-06-28
Finally I installed **Ubuntu Cinnamon** after trying  following flavours (using Ventoy) before installing them on my low-config machine for  which I sought recommendation for a particular flavour. Following are  the observations I noticed.

```
Xubuntu
   UX I found ok on my screen.
   Touchpad not working.
   Touchscreen working.

 Cinnamon
   UX I found rich on my screen.
   Touchscreen working
   Installing Ruby hanged. Probably it was because I was trying it live with Windows already on the machine. But later when I actually decided to install it everything went smooth.
 
  Kubuntu
   UX I found ok on my screen.
   Touchpad not working.
   Touchscreen working.
 

Lubuntu
   UX I found ok on my screen.
   Touchpad not working.
   Touchscreen working.
 
Ubuntu Budgie
   Hanged after logged-in saying preparing it.
 
Ubuntu Mate
   UX I found ok on my screen.
   Touchpad detected.
   Slight delay while preparing. After few mins it worked.
```

Hope this would help someone else like me who might end up finding this discussion.

And Thank you again to all of you who spared time to share their recommendations and a big thanks to @**guiverc **for his elaborate guidance.

---

