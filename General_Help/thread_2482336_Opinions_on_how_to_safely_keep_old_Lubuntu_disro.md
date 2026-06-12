---
title: "Opinions on how to safely keep old Lubuntu disro?"
date: 2022-12-28
forum: General Help
---

### Post by wally1960 on 2022-12-28
Hello all, I've been using Ubuntu off and on since the 1990's. I like it. If you need to just get something done with the least amount of fuss, Ubuntu is your distro. At present I'm using an old Dell Optiplex 3010. Intel core i3-3220 cpu @3.30 GHZ 1 physical processor; 2 cores; 4 threads. Ram is 8gb. 
Lubutu is stretching the abilities of this machine. I'm currently using Lubuntu 18.04. It will be awhile before I can get a new machine. So I would like some opinions on:

1. Which current Ubuntu distro would be the lightest for my old hardware?
2. How can I strip out some of the bloat?
3. How long can you keep a distro with security patches?

Oh yea, I use the machine for internet surfing and college courses. A little chess playing, that's it. Nothing heavy duty. I don't need upgrades and the newest and greatest. I like stable.
Any help would be appreciated.

Wally

---

### Post by Tadaen_Sylvermane on 2022-12-28
Stick with Lubuntu would my suggestion. That or Xubuntu. There isn't much you should need to strip out. I'm using an ivy bridge machine myself, albeit much more raw muscle. You should be able to stick with Lubuntu for the time being.

---

### Post by QIII on 2022-12-28
Hello!

I'm going to address bullet 3 first:  Lubuntu is a flavor that is supported for 3 years.  That means you are already well past the end of support.  This means that you are subject to security issues, including exposing yourself to every nefarious actor on the web.  In other words:  Don't connect to the internet  with that.  You endanger yourself.  Because an unsupported OS no longer gets updates, you also risk those same actors using your machine to attack everyone else.  

What do you mean by "bloat"?  Do you have a lot of things running that you do not intend?  Just the fact that there is software installed does not mean an OS is bloated.  What is important is what is *runninng* and consuming resources.

8GB of RAM should be just fine for nearly anything you want to do.  How much is being used?  What is the activity level of your CPU?

Vanilla Ubuntu or any of the flavors should work well with your specs -- depending on what you might have running.  Lubuntu is one of the lightest.  If you want to go lighter, jettison the DE and go with a straight WM.

But I stress this again:  Do not connect to the internet with an unsupported release of any OS -- or you may cause yourself and the rest of us significant emotional events.

---

### Post by guiverc on 2022-12-28
I perform QA-testing of Lubuntu and other Ubuntu products and *flavors*, and a *huge* percentage of my QA-testing is done on much older hardware than you mention (ie. c2d & c2q boxes that pre-date the release of i-series CPU & hardware).

Lubuntu is still the *lightest* out of the box Ubuntu *flavor*, however few of use the installed OS without adding new packages/software, thus the *lightest* installed may not be the *lightest* OS when you consider how you'll use it.

eg. you mention Lubuntu 18.04 LTS that is actually [EOL ]("https://lubuntu.me/bionic-eol/")though as Ubuntu 18.04 LTS is still supported; parts of your system still get security fixes & patches. You can confirm this using `ubuntu-support-status` and get details about your actual install. either way I'll start with your system.

Lubuntu 18.04 LTS uses the GTK2 desktop LXDE.  GTK2 is *deprecated*, with all *development* now on GTK4, and GTK3 now in maintenance mode, with GTK2 being *deprecated* for some time now. Deprecation mainly impact security, but as for *lightness* yes GTK2 was very light, and you gain benefits of that when using GTK2 software, and here is the problem with GTK2.  There are almost no GTK2 apps (*most having been upgraded to GTK3 where a GTK2 desktop will be less efficient in running them than a GTK3 desktop*).  Yes there are some, and maybe you only use `hexchat` or some of the very few remaining GTK2 apps.

If your chosen desktop uses one toolkit/libraries, but the apps you run require another, your machine RAM must load two tk/libs that do the same thing into RAM meaning you need more RAM/resources than a setup that has all wanted apps sharing the resources.  If you have plenty of RAM though you needn't worry about than (ie. with *5GB or more the RAM usage is less of an issue*)

On some hardware I use in QA (*Quality Assurance*) on very recent releases (ie. using 5.15 or later kernels) I'd *possibly* opt for Xubuntu myself having the least issues with graphics (Lubuntu didn't experience issues until 5.19 on those boxes, but Ubuntu/Kubuntu and others did much earlier). Xubuntu is a GTK3 desktop thus will be *light* if you're going to run GTK3 apps; in contrast to Lubuntu which now uses the LXQt desktop thus is Qt5.

Personally I'd ignore the *out of the box* lightness, UNLESS you're going to use the OS itself *out of the box* without adding additional packages.  If you're adding packages (ie. software) consider what its requirements are in choosing your desktop. The more resources your hardware has, the more I'd replace those resource-consideration though with your personal tastes, eg. if you have 8GB or more RAM, I'd consider 80% taste & 20% resource-efficient.

Read Ubuntu release notes for security patch notifications, or use tools like `ubuntu-support-status` to explore using your own box. I've written about it on the Lubuntu discourse & elsewhere (eg. [here]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4")).  A Ubuntu LTS release has a guarantee of support for five years for those packages found on Ubuntu Desktop, Ubuntu Server & other *official* media only (ie. those packages from the 'main' repository), but shorter for community-supported packages (from 'universe') as used by *flavors* like Lubuntu.  3 years applies to those media included packages, but do note NOT ALL packages in universe have 3 years, some only had 9 months (eg. Ubuntu Studio 18.04 was **not** a LTS release; Lubuntu Next 18.04 was also **not** a LTS release so those packages only had 9 months of supported life).  Ubuntu Studio provided *extended* support for 18.04 only via PPA, which was *dropped * in April 2021 when the 3 year support ended. If you didn't add the PPA you didn't get those fixes, but all this was documented, so I'd suggest reading the release announcements (eg. one [18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") can be found here, with no mention of Ubuntu Studio, Lubuntu next etc as they were EOL already; but note the 3 years of support applied from initial release in 2018-April thus ended 2021-April)

Some *flavors* offer a minimal install option, however not all do. For Lubuntu for example; their discourse will suggest you install using Ubuntu Server media then add the Lubuntu Desktop to your system without *recommends*, though the team does have a task on adding that function (*when possible*) to simply this further for end-users.

If you value security; *flavors* come with 3 years so I'd stay within that life-cycle (ie. 20.04 *flavors* end support in only a few months, ie. 2023-April; with 18.04 *flavor* support ending back in 2021-April meaning you're not getting security fixes for all your installed system now!)

I use boxes myself as old as from 2005 using the *latest* releases of Ubuntu (*how I actually think of my installs; eg. I'm using Lubuntu lunar (what will be released as 23.04) currently, but I still think of this install as a Ubuntu one*), and if you value *stable* I'd likely consider LTS as it's usually easier. I personally find the more regular upgrades less hassle at *release-upgrade* time (*less change that way, it's just more often, ie. 4 smaller jumps instead of 1 larger jump from the prior LTS to the next LTS*)

FYI: If not already clear; I don't think it's Lubuntu stretching the abilities of your machine, it's more you using the GTK2 desktop in ways that are inefficient (*running non-native GTK3/GTK4/Qt4/Qt5 apps on it*) having maybe made the wrong choice to begin with (*didn't consider how you'll use it in the decision of what desktop to use*).  I still use pentium M laptops (*from *2003-2004, still with 18.04) with 1GB of RAM, and on those I sure do consider the desktop I use in a session before I login, in relation to what I'll do in that session (*my installs are multi-desktop & thus I can select which DE I'll use at login*).

*FYI : prior responses didn't exist when I started this, real life calling me away a couple of times, and the opus-length of this response meant it sat on my screen awhile before I completed it.*

---

### Post by wally1960 on 2022-12-28
Thank you all for your input. I'll upgrade. Any advice on using a tiled window manager.

---

### Post by Tadaen_Sylvermane on 2022-12-29
Will take a bit of time to get used to it if you've never used one before. I still struggle when I use the i3 window manager. But the benefits make it worth it most of the time. Only reason I don't have it installed now is occasionally the wife will need to use my computer for a few minutes. Not worth logging out altogether to change the environment imho.

---

