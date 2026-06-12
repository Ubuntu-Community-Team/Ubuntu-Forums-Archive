---
title: "How to retreive yahoo mails like pop3 in yahoopops?"
date: 2005-06-01
forum: General Help
---

### Post by eizo on 2005-06-01
Hi all,

Ubuntu's great. Been converting 90% of work to Ubuntu since I installed it a week ago, now I am facing a problem of retreiving yahoo mails like pop3. There's a small program called yahoopops for windows, it works flawlessly. However, the linux version is source code only and I have no idea of compiling at all. Can anyone here help give me some hints and howtos? Thanks a lot.

God bless.

---

### Post by Dromio on 2005-06-01
[QUOTE=eizo]Hi all,

Ubuntu's great. Been converting 90% of work to Ubuntu since I installed it a week ago, now I am facing a problem of retreiving yahoo mails like pop3. There's a small program called yahoopops for windows, it works flawlessly. However, the linux version is source code only and I have no idea of compiling at all. Can anyone here help give me some hints and howtos? Thanks a lot.

God bless.[/QUOTE]
 I use fetchyahoo on my debian box, so I think that means the package is in Universe.

---

### Post by astronerd on 2005-06-01
How do you get this to work with Evolution?  I have tried to look at the freepops website, but I cant get anything to work.....  I got freepops from synaptic, and when I enter freepops in the command line nothing happens, how do I get it started and configure evolution to accept yahoo mail?

---

### Post by rider343 on 2005-06-01
pop.mail.yahoo.com.br
smtp.mail.yahoo.com.br

I use the pop and smtp yahoo with evolucion and thunderbird... 

Ps.: the pop and smpt above are a Yahoo brazilian server... :)

---

### Post by arnieboy on 2005-06-02
I thought pop access (in email clients) to yahoo mail servers doesnt come free of charge and u gotta pay for it

---

### Post by Dromio on 2005-06-02
[QUOTE=astronerd]How do you get this to work with Evolution?  I have tried to look at the freepops website, but I cant get anything to work.....  I got freepops from synaptic, and when I enter freepops in the command line nothing happens, how do I get it started and configure evolution to accept yahoo mail?[/QUOTE]
 fetchyahoo is a command-line script will pull scrape the Yahoo website for emails and forward them to your local unix mailbox.  I have it set to run on my system every 15 minutes.  Then you just set up Evolution to read the local mailbox and you are all set.

---

### Post by dbloom on 2005-06-02
fetchyahoo works fairly well.   

last night, i decided to compile ypops for ubuntu and although i got working, i got banned from my yahoo account for a little while...  perhaps i set up evolution incorrectly -- i'll have to look into it.

otherwise, i've been using fetchyahoo for about a month and it works rather nicely.  my only issue is that you can't respond to email via the yahoo server, which is why i attempted compiling ypops in the first place.

if you want to compile ypops.  see this [link](http://yahoopops.sourceforge.net/index.php?name=PNphpBB2&file=viewtopic&t=1959&POSTNUKESID=51fd354ea013bd939a01160b98fba77b)  to get the source code with mime++. 

read the README file.  you'll have to apt-get curl and ssl dev packages and then set the correct directories in the makefile (they are different). then, when you edit the config file, be sure to set the ports to 5058 (for pop), 5059 (for smtp) so you don't have to be root to run it.  

this worked for me.

---

### Post by rider343 on 2005-06-02
[QUOTE=arnieboy]I thought pop access (in email clients) to yahoo mail servers doesnt come free of charge and u gotta pay for it[/QUOTE]

Here in Brazil is free of charge  \\:D/

---

### Post by AmandaKerik on 2007-02-01
Thunderbird has an add-on called webmail - [http://webmail.mozdev.org/](http://webmail.mozdev.org/)
It works like a dream, doesn't rely on OS folders, easy to tinker with.
I, personally, find it a lot easier to use than ypops!

---

### Post by holyowned on 2007-02-12
> **AmandaKerik said:**
> Thunderbird has an add-on called webmail - [http://webmail.mozdev.org/](http://webmail.mozdev.org/)
It works like a dream, doesn't rely on OS folders, easy to tinker with.
I, personally, find it a lot easier to use than ypops!

The Yahoo Webmail extension is invalid.  Any ideas/clues where I can get it.  Alternatively, I have ypops,  but I'm a noob, and don't know how to install it.

---

### Post by tskariah on 2007-04-08
YPOPS! for Ubuntu is available here: [ypops_0.8.8-1_i386.deb]("http://www.geocities.com/t_skariah/ypops/")

---

### Post by Gustave on 2007-04-17
> **tskariah said:**
> YPOPS! for Ubuntu is available here: [ypops_0.8.8-1_i386.deb]("http://www.geocities.com/t_skariah/ypops/")

WOW!  thanks!  I've been goin nuts for the past hour!  I tried several different means of getting my yahoo mail, including another version of ypops (couldn't install right, or even at all), the webmail extention (which I use on my XP box, but here it just kept giving me errors), and a couple other things which slip the mind (oh, yosucker, was one of them).

I'm a newbie to linux and I just wanted it to work!  I could actually follow these instructions and got it all working in about 2 minutes, so um, what I'm getting at is thanks for posting that link. :D

---

### Post by tskariah on 2007-05-11
> **Gustave said:**
> WOW!  thanks!  I've been goin nuts for the past hour!  I tried several different means of getting my yahoo mail, including another version of ypops (couldn't install right, or even at all), the webmail extention (which I use on my XP box, but here it just kept giving me errors), and a couple other things which slip the mind (oh, yosucker, was one of them).

I'm a newbie to linux and I just wanted it to work!  I could actually follow these instructions and got it all working in about 2 minutes, so um, what I'm getting at is thanks for posting that link. :D

Glad to be of help.

---

