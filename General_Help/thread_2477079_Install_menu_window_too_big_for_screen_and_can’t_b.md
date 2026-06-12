---
title: "Install menu window too big for screen and can’t be resized"
date: 2022-07-14
forum: General Help
---

### Post by werdna55521 on 2022-07-14
I’m trying to install Ubuntu on an old Toshiba satalite with a desktop environment to run an octoprint server and I went into safe graphics because that’s the only way I could get the external monitor to display using the live cd as the built in one is probably in a dump somewhere. After selecting a language the next button is at the bottom of the window but the screen doesn’t go down far enough to click the next button and I don’t know how to proceed with the install. There is only a minimize and exit button but no full screen and when I right click the resize options are greyed out.

---

### Post by guiverc on 2022-07-14
Summary 
- does your machine meet the minimum requirements? for your [I]unstated product/unstated release
- [/I]what Ubuntu product, release & choices did you make/try and install?


You've provided no product or release details; but the [minimum requirements for Ubuntu's desktop installer]("https://help.ubuntu.com/community/Installation/SystemRequirements") is 

> VGA capable of 1024x768 screen resolution

which I'm guessing you've not provided. 

Ubuntu provide many products; 
- Ubuntu Core,
- Ubuntu Server,
- Ubuntu Desktop
- & many other [I][flavors]("https://ubuntu.com/download/flavours")
[/I]
with releases using the *year.month* format (*though specialist products use the year format as they come out only once per even year*), but I wonder if you're using an appropriate product/release for your *unstated* Toshiba satellite device. 

You may not have noted *five* installers are available; with them selected by the product/ISO you download & try to install, but you gave no clues as to what you actually tried.  Do your machine meet the minimum requirements for your *unstated* Ubuntu product, if it doesn't you maybe better opting for a *lighter* flavor, alternate ISO *(some old ISOs use text installer so you can get it installed & fix issues post-install though I'd recommend other solutions over that*). 

Also if you're talking a LTS release, different kernel stack options exist (GA, HWE, OEM) and being careful as to which ISO you download/install can have different results (*when compared to the same release but different ISO*).  Being specific with details may allow us to better understand & provide you with options *(eg. some really old IBM Thinkpads didn't like 18.04.5 ISOs with the 5.4 HWE kernel, but installation with older 18.04 ISOs were easy & perfect; you just defaulted to an ISO that used the GA kernel stack (4.15 for 18.04)* *and the system was perfect, or installed with an older ISO, eg. 18.04.4 which used 5.3, add the GA kernel stack & thus avoid the 5.4 HWE kernel the box didn't do well with... ie. easy workarounds  yet you stayed on the same 18.04 release...*)[I]. If you use an ISO with `subiquity` installer you can select the kernel stack during installation, but for most the ISO you download dictates the default stack.

FYI:  If you device lacks resources; use a lighter flavor.  I use devices as old as from 2005 in QA-test (Quality Assurance testing) all current releases; but used older devices up to 19.04 (2019-April release)
[/I]

---

### Post by Paddy Landau on 2022-07-14
> **werdna55521 said:**
> … the screen doesn’t go down far enough to click the next button
I have had this problem before. You might be able to move the window around by pressing the Super key (that's usually the Windows key) while using your mouse to drag the window.
> **guiverc said:**
> … you maybe better opting for a *lighter* flavor…
The lightest official flavour of Ubuntu is Lubuntu. The lightest unofficial flavour that I know of is [Bodhi]("https://www.bodhilinux.com/").

If you try Lubuntu, please note that the top result in an internet search is an unofficial, unapproved website with old software, without guarantee that it's malware-free. The correct, official website is [https://lubuntu.me/](https://lubuntu.me/)

---

### Post by ajgreeny on 2022-07-14
I think it's the left Alt key, not the Win/Super key, you need to hold and then move the window with the mouse.

---

### Post by Paddy Landau on 2022-07-14
> **ajgreeny said:**
> I think it's the left Alt key, not the Win/Super key, you need to hold and then move the window with the mouse.
Thanks. It's the Super key on my computer; maybe I changed the default a long time ago?

EDIT: It is the Super key, according to [the documentation]("https://help.ubuntu.com/stable/ubuntu-help/shell-windows-states.html.en").

---

### Post by ajgreeny on 2022-07-14
> **Paddy Landau said:**
> Thanks. It's the Super key on my computer; maybe I changed the default a long time ago?

EDIT: It is the Super key, according to [the documentation]("https://help.ubuntu.com/stable/ubuntu-help/shell-windows-states.html.en").
I think it must therefore depend on either hardware or the DE; I use Xfce (Xubuntu) and have just tried on my system where the Win/Super key does nothing but left Alt works as I thought.

---

### Post by Paddy Landau on 2022-07-14
> **ajgreeny said:**
> I think it must therefore depend on either hardware or the DE; I use Xfce (Xubuntu)…
The DE. The OP said that they used Ubuntu, not Xubuntu, so there's the difference.

---

### Post by ajgreeny on 2022-07-14
> **Paddy Landau said:**
> The DE. The OP said that they used Ubuntu, not Xubuntu, so there's the difference.
I have been using Xubuntu now for over 10 years but I thought the "Move window" keys were the same in gnome when I last used it, ie gnome-2.
Things have obviously moved on since then and changes been made, or (more likely) my memory is just wrong.

---

