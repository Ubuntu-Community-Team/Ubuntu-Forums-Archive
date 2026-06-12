---
title: "having problems with apt-get"
date: 2007-07-26
forum: General Help
---

### Post by OoooMatron on 2007-07-26
Ok, originally i thought this was a problem with vectorlinux distro but now the same thing is happening here.

Firstly, i can use the internet just fine with no problems and I can download using firefox with no problems.

The problem is that when i use apt-get or wget from the command (or synaptic manager) it's impossible to download any updates or packages without the download constantly timing out somewhere along the line. It's becoming very frustrating and I wonder if the kernel is not very keen on my network chipset.

I have some HP piece of **** which the hardware info has as an NVIDIA MCP61 adapter.

any ideas?

---

### Post by davidjmayo on 2007-07-26
Where are you downloading from?

Australia repos have had problems for a couple of days and also problems in Canada on and off (both sources for this are from reading the forum)

What happens if you change the mirror site?

When you say can download from firefox do you mean from any site in your sources list or other websites?

---

### Post by OoooMatron on 2007-07-26
I mean that normal webbrowing and stuff is ok but the package manager is timing out.

I am in Sweden and I think there maybe some issue with my network adapter and linux because I had the same problem on a different distro (vector linux). It's the same install on my home machine and zero problems here.

I have to keep stopping and starting the process because , fortunately, it continues from where it left off.

maybe i should take a new network card in and see what happens.

---

### Post by OoooMatron on 2007-07-30
Ok, this is extremely frustrating. I changed the network adapter but still the same crap: i just don't understand it. Here is my sources lists

```

deb http://no.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://no.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty universe

deb http://de.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty multiverse

# deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://de.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
#AUTOMATIX REPOS END

```

I seem to have the most trouble with the archive ones. I tried adding no and de infront of some of them instead of se to see if it helped but it doesn't.

I get constant time outs trying to install software and have to cancel and restart them 10 or so times just to download a few megabytes!

---

### Post by OoooMatron on 2007-07-31
upgraded the firmware on the router and the problem seems to be gone!

Very weird I only notice this in linux though.

---

