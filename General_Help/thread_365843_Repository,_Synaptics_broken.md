---
title: "Repository, Synaptics broken"
date: 2007-02-20
forum: General Help
---

### Post by flipflow on 2007-02-20
Here is the story:

I am pretty much a newB, still finding my way around Ubuntu/Linux. 

Last week I wanted to update my VLC player to 0.8.6 
I tried both ways recommended on the videolan website, manually and with Synaptics. 

1. didn't do the trick, because I couldnt edit my sources.list in /etc/apt/
2. In Synaptics: I finally understood how to add new repositories. But it didnt want to read the new source, instead it crashed and ever since, whenever I want to use Synaptics or do a regular update procedure, I get an error saying something like:

cant read line 33 in sources.list. [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper-plf free non-free

Problem now is: That repository is listed in sources.list allright, but I cannot edit it in a text editor, because I am not its owner, whatever that means. And I cannot disable it in Synaptics, because that cannot read the line and doesnt list it in the repositories. 

So, I guess, what I need is something like the terminal command line to remove an entry from the sources.list file with all the necessary bang or sudo or whatever you call god-like power here to scare the heck out of it and make that darned line go away!

Thanks for helping me!
flipflow   

B.t.w. if anyone can then give me a hint how to properly update VLC to 0.8.6, that would be much appreciated.

---

### Post by Jussi Kukkonen on 2007-02-20
First-aid first:```

gksudo gedit /etc/apt/sources.list
```
...and remove the offending lines.

Then the advice
1. Adding third party repositories should not be done lightly -- remember that the owners of any repository you use have pretty much total control of your computer...
2. VLC 0.8.6 is available in Edgy. If you are running Dapper, I'd suggest upgrading the system instead of using additional repositories -- especially if you are not an experienced user.

---

### Post by bapoumba on 2007-02-20
To edit /etc/apt/sources.list you need to be root:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

So open a terminal (> Accessories > Terminal) and run:
**sudo -B /etc/apt/sources.list**
and remove the freecontrib lines.

These repos are not maintained anymore, use [medibuntu]("http://medibuntu.sos-sts.com/") instead. Check the repository howto on their site.
If you do not understand, Please post here the output to **cat /etc/apt/sources.list**

---

### Post by Jussi Kukkonen on 2007-02-20
bapoumba, your editor command suggestion is missing something.

At the risk of sounding like a broken record, I'd like to point out that medibuntu has the same  possible problems as other third party repositories --additionally they're also relatively new and do not even list who they are on the website. I'm not claiming there's something shady there, just pointing out that one should *always* evaluate the trustworthiness of the maintainers before using a repository...

---

### Post by bapoumba on 2007-02-20
> **Jussi Kukkonen said:**
> bapoumba, your editor command suggestion is missing something.
I'm sorry. Here is the command:
**sudo -B nano /etc/apt/sources.list**

> **Jussi Kukkonen said:**
> 
At the risk of sounding like a broken record, I'd like to point out that medibuntu has the same  possible problems as other third party repositories --additionally they're also relatively new and do not even list who they are on the website. I'm not claiming there's something shady there, just pointing out that one should *always* evaluate the trustworthiness of the maintainers before using a repository...
Medibuntu project was set up by some of the former ubuntu team in PLF (they are french, I know some of them, even if that does not mean much ;)). So they are not newcomers. Packages in medibuntu repos have been checked by a MOTU, in december if I recall correctly (I can check my emails).
[https://launchpad.net/~medibuntu-maintainers]("https://launchpad.net/~medibuntu-maintainers")

These repos are also linked by some wiki pages. So I would say that the risk is the same as for any third party repo. In addition, some packages in medibuntu (like in former PLF-freecontrib) may be illegal to use in some countries.

Thanks Jussi Kukkonen :)

edit: I'll email them to ask they advertise who they are on their web site. Would you have any other suggestion ? Thanks again.

---

### Post by Jussi Kukkonen on 2007-02-20
...or even:
**sudo nano -B /etc/apt/sources.list**
(yeah, I know, bad typing days happen to everyone)


> edit: I'll email them to ask they advertise who they are on their web site. Would you have any other suggestion ? Thanks again.
If there is some kind of MOTU-review, mentioning that would be a big plus (at least in my accounting).

BTW, I think that medibuntu looks like a good idea. This is just a pet peeve of mine -- currently  Ubuntu is lightyears ahead of Windows in the package management department, but if new users learn to add any random sites to their sources.list, that advantage is quickly lost (as malware producers will no doubt start to use it as an easy attack vector)...

---

### Post by bapoumba on 2007-02-20
> **Jussi Kukkonen said:**
> ...or even:
**sudo nano -B /etc/apt/sources.list**
(yeah, I know, bad typing days happen to everyone)
/o\
/me going to hide somewhere very far away...


> **Jussi Kukkonen said:**
> 
If there is some kind of MOTU-review, mentioning that would be a big plus (at least in my accounting).
Will suggest them, thanks.

> **Jussi Kukkonen said:**
> 
BTW, I think that medibuntu looks like a good idea. This is just a pet peeve of mine -- currently  Ubuntu is lightyears ahead of Windows in the package management department, but if new users learn to add any random sites to their sources.list, that advantage is quickly lost (as malware producers will no doubt start to use it as an easy attack vector)...
I agree.
There are also problems when packages are installed or upgrades are run with non-ubuntu packages or repos. This is somewhat of a middle situation.

---

