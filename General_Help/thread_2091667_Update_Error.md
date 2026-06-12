---
title: "Update Error"
date: 2012-12-05
forum: General Help
---

### Post by RocketPenguin on 2012-12-05
Recently i have tried to update my laptop running ubuntu 12.04, and when i hit 'install updates' it gave me this error:
> Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

And the details where:
> E:Method  has died unexpectedly!, E:Sub-process  returned an error code (100), E:Method /usr/lib/apt/methods/ did not start correctly
Last i remember, nothing bad happened the last time i updated it, so i have no clue what happened. How would i fix this problem???
And, what caused it?
SOLVED.

---

### Post by madhater on 2012-12-05
It sounds like you have broken dependencies on your system. If your problem is what I think it is, the following command should solve your problem. 
```

sudo apt-get install -f

```
 This command will resolve broken dependencies on your system. 

James

---

### Post by ibjsb4 on 2012-12-05
You can also try:

```
sudo apt-get update
```

---

### Post by RocketPenguin on 2012-12-05
> **madhater said:**
> It sounds like you have broken dependencies on your system. If your problem is what I think it is, the following command should solve your problem. 
```

sudo apt-get install -f

```
 This command will resolve broken dependencies on your system. 

James

All this did was:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

---

### Post by RocketPenguin on 2012-12-05
> **ibjsb4 said:**
> You can also try:

```
sudo apt-get update
```

[http://pastebin.com/PCUaZax0](http://pastebin.com/PCUaZax0)

---

### Post by madhater on 2012-12-05
The error (I think) is to do with your system authenticating (or not, as the case may be)  a secure connection with the package servers. I am afraid to say that’s all I know apt-get wise. Hope I have helped.

James

---

### Post by ibjsb4 on 2012-12-05
I have not encountered this before and have been searching here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Method+has+died+unexpectedly+Sub-process+returned+an+error+code+%28100%29&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Method+has+died+unexpectedly+Sub-process+returned+an+error+code+%28100%29&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[https://www.google.com/search?client=ubuntu&channel=fs&q=Method+has+died+unexpectedly+Sub-process+returned+an+error+code+%28100%29&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Method+has+died+unexpectedly+Sub-process+returned+an+error+code+%28100%29&ie=utf-8&oe=utf-8)

And have not hit on a good answer yet.

---

### Post by ivotkl on 2012-12-05
I know this may sound pretty obvious, but... Did you have internet at the time of the upgrade?
 
And, by the way, have you tried changing server? Apparently all connections failed.

---

### Post by RocketPenguin on 2012-12-05
> **ivotkl said:**
> I know this may sound pretty obvious, but... Did you have internet at the time of the upgrade?
 
And, by the way, have you tried changing server? Apparently all connections failed.

I had internet, but it was being buggy, not loading pages at times. And what do you mean, "changing server"?

---

### Post by ivotkl on 2012-12-09
Sorry, I' ll explain better.
 
What I meant to say is what happens if you change server you download the packages from (software sources) to another one.
However, I think the problem may rely on the faulty service given by your ISP at that time. Have you tried again since?

---

### Post by ibjsb4 on 2012-12-09
This may be a result of third party repos.

```
grep ^ /etc/apt/sources.list.d/*
```

Please post the output of that.

---

