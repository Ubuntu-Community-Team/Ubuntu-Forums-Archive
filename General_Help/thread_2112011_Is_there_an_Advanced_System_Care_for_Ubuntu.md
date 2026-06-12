---
title: "Is there an Advanced System Care for Ubuntu"
date: 2013-02-03
forum: General Help
---

### Post by cwblanch on 2013-02-03
Hi,[INDENT]Just wondering if there is an Advanced System Care like program for Ubuntu like there is in Windows, or if an ASC is even needed for Ubuntu.

Thanks
[/INDENT]

---

### Post by sudodus on 2013-02-03
I don't know ASC for Windows, but there is Ubuntu Tweak, that you can install according to the following link

[[COLOR="Red"]http://ubuntu-tweak.com/downloads/[/COLOR]]("http://ubuntu-tweak.com/downloads/")

I suggest you add the source 'tualatrix' the easy way.
```
sudo add-apt-repository ppa:tualatrix/ppa
```
Then
```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
And you have Ubuntu Tweak :-)

---

### Post by Yellow Pasque on 2013-02-03
Not all of us are familiar with Windows, so please explains what "ASC" does...

---

### Post by SeijiSensei on 2013-02-03
Looks like he is talking about [this](http://www.iobit.com/advancedsystemcareper.html).

There is no such beast that I know of in the Linux menagerie.  The Unix philosophy is lots of individual specialized programs rather than large integrated ones.  There also isn't anything like a registry to clean, and malware is a minor issue for most users, especially desktop users.  You can still encounter things like Javascripts with evil intent, but if you are concerned about those sorts of threats you're better off with browser plugins like NoScript and FlashBlock.

You might want to read the [security "sticky"](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by cwblanch on 2013-02-03
> **sudodus said:**
> I don't know ASC for Windows, but there is Ubuntu Tweak, that you can install according to the following link

[[COLOR=Red]http://ubuntu-tweak.com/downloads/[/COLOR]]("http://ubuntu-tweak.com/downloads/")

I suggest you add the source 'tualatrix' the easy way.
```
sudo add-apt-repository ppa:tualatrix/ppa
```Then
```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```And you have Ubuntu Tweak :-)
Thank you. I will definitely play around with that! 


> **Temüjin said:**
> Not all of us are familiar with Windows, so please explains what "ASC" does...
Sorry about that, I'm newish to it so I didn't think about explaining what it does, it is the program that SeijiSensei link off to.

> **SeijiSensei said:**
> Looks like he is talking about [this]("http://www.iobit.com/advancedsystemcareper.html").

There is no such beast that I know of in the Linux menagerie.  The Unix philosophy is lots of individual specialized programs rather than large integrated ones.  There also isn't anything like a registry to clean, and malware is a minor issue for most users, especially desktop users.  You can still encounter things like Javascripts with evil intent, but if you are concerned about those sorts of threats you're better off with browser plugins like NoScript and FlashBlock.

You might want to read the [security "sticky"]("http://ubuntuforums.org/showthread.php?t=510812").
I didn't think there would be anything like it for Ubuntu, but it doesn't hurt to make sure.

Thanks for your help :)

---

### Post by ibjsb4 on 2013-02-03
There is also BleachBit, its in the software center.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by oldos2er on 2013-02-03
I've read a bit of the page linked to ([http://www.iobit.com/advancedsystemcareper.html);](http://www.iobit.com/advancedsystemcareper.html);) some of it is very vague, i.e. "Optimizes, cleans, and fixes all kinds of PC problems with just 1 click" and "giving your computer a boost to optimize your PC experience." I would say running Linux in itself is a "boost", for what it's worth.  :)

If you choose to run one of the Linux "cleaners" such as Computer Janitor or Bleachbit, make sure you know exactly what you're deleting or "cleaning"; there's no shame in asking first if you aren't sure.

---

### Post by Max Blyss on 2013-02-03
Also, if the forums will permit a little sacrilege, ASC on Windows is a bit jenky...  Try [Ccleaner]("http://www.piriform.com/ccleaner")...  I found it to be lighter and less buggy than ASC when I was still using Winduhs.

---

### Post by cwblanch on 2013-02-08
> **oldos2er said:**
> I've read a bit of the page linked to ([http://www.iobit.com/advancedsystemcareper.html);](http://www.iobit.com/advancedsystemcareper.html);) some of it is very vague, i.e. "Optimizes, cleans, and fixes all kinds of PC problems with just 1 click" and "giving your computer a boost to optimize your PC experience." I would say running Linux in itself is a "boost", for what it's worth.  :)

If you choose to run one of the Linux "cleaners" such as Computer Janitor or Bleachbit, make sure you know exactly what you're deleting or "cleaning"; there's no shame in asking first if you aren't sure.

I completely agree that Linux is a boost! I probably will end up asking what needs the upkeep. :D
Thanks

> **ibjsb4 said:**
> There is also BleachBit, its in the software center.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

I found it in the software center.
Thank you very much!

---

### Post by wildmanne39 on 2013-02-08
Please know that if you just let bleachbit remove things it recommends it will most likely remove applications that you need, I used it not knowing and it broke my system so it will definitely remove things you need.

It is best to use the auto remove command. 
```
sudo apt-get autoremove
```
Thanks

---

### Post by pompel9 on 2013-02-09
> **Max Blyss said:**
> Also, if the forums will permit a little sacrilege, ASC on Windows is a bit jenky...  Try [Ccleaner]("http://www.piriform.com/ccleaner")...  I found it to be lighter and less buggy than ASC when I was still using Winduhs.

I would advise against that. CCleaner is known for deleting registry that is not empty or are used by vital software (such as windows itself). Leaving the OS bricked.

---

### Post by kurt18947 on 2013-02-09
I guess this is a 'YMMV' case.  I've used both bleachbit as root and CCleaner with no known ill effects.  I run Windows *very* infrequently - mostly hardware updates and formatting flash drives - so my experience database is pretty small.

---

### Post by ibjsb4 on 2013-02-09
> **Wild Man said:**
> Please know that if you just let bleachbit remove things it recommends it will most likely remove applications that you need, I used it not knowing and it broke my system so it will definitely remove things you need.

Guess everyones experience is different, but I have used BB since 8o4 and not experience this.  I have had this problem in the pass when using computer-janitor and would stay away from it.

---

