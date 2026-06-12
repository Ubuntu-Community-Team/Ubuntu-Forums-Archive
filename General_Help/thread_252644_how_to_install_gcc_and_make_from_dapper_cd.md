---
title: "how to install gcc and make from dapper cd"
date: 2006-09-07
forum: General Help
---

### Post by krmane on 2006-09-07
hello,
I want to use ubuntu 6.06.1 as my developer machine along with a desktop.
I realise that the development tools are not installed by default. I also saw in the pool directory of the cd that there is glib and gcc as well as g++, make etc.
but when I put the cd in and say apt-get install build-essentials, I can't get it installing gcc?
is cd not browsed for apt-get? is internet the only option?
thanks all,
Krishnakant.

---

### Post by aeiah on 2006-09-07
so is it installing the other bits when you do your apt-get and just leaving gcc out? hmm.

if that machine hasnt got internet access, you could just download the .deb file and transfer it, then open it up or do 'sudo dpkg -i filename.deb'

you'll be able to find gcc on packages.ubuntu.com

---

### Post by Lunar_Lamp on 2006-09-07
Have you added the CD to your list of repositories?

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essentials

---

### Post by taurus on 2006-09-07
> **Lunar_Lamp said:**
> Have you added the CD to your list of repositories?

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essentials
No **[COLOR="Blue"][SIZE="6"]s[/SIZE][/COLOR]** in build-essential!!!

---

