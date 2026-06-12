---
title: "All is ruined because of a bad installation of Mono"
date: 2014-09-04
forum: General Help
---

### Post by offir on 2014-09-04
i tay to install mono

i use this link

[http://blog.bekijkhet.com/2014/06/install-mono-340-in-ubuntu-1404-lts.html]("http://blog.bekijkhet.com/2014/06/install-mono-340-in-ubuntu-1404-lts.html")

and it didnt work 

so i try this link 
[http://www.rocko.me/install-mono-3-4-ubuntu/]("http://www.rocko.me/install-mono-3-4-ubuntu/")

after the The first command
Everything went to hell

All display was destroyed

Icons are shown as a blue circle with a question mark inside

The rest of the icons are shown as black frame
Or purple square standing on its edge

Right now I want to fix the display
More than install mono

How I do it
What I did not do good

---

### Post by Impavidus on 2014-09-04
That second link is really a complicated way to install mono. The tutorial is not very good either.

When I run that first command as simulation I get this:```
$ apt-get purge -s mono-*
REMARK: This is a simulation!

(lots of lines about selected packages and packages that are currently not installed)

The following packages will be REMOVED:
  fonts-thai-tlwg* fonts-tlwg-mono* light-themes* ubuntu-mono*
0 packages upgraded, 0 packages newly installed, 4 to remove and 0 not upgraded.
Purg fonts-thai-tlwg [1:0.5.1-3]
Purg fonts-tlwg-mono [1:0.5.1-3]
Purg light-themes [14.04+14.04.20140410-0ubuntu1]
Purg ubuntu-mono [14.04+14.04.20140410-0ubuntu1]
```Closer inspection reveals these packages have nothing to do with mono (which I don't have installed). The first and second are thai fonts (which you may or may not need, but are irrelevant here), the others are default themes, which provide the icons on your desktop. I guess they were uninstalled by the command in that tutorial. You may be able to get them back with```
sudo apt-get install light-themes ubuntu-mono
```You may have to log out and log in to make it work.

The common way to install mono would be installing the package **mono-devel**, **mono-runtime** or **mono-complete**, whichever you need. On 14.04 this will get you mono 3.2. If you need the latest version, the best thing to do is find a PPA. This is the approach taken by the first link you gave. It's best to find out why that didn't work.

---

### Post by offir on 2014-09-04
Thank you thank you thank you

I thought I destroyed it all

Another thing it does not work ubuntu tweak
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

I tried reinstalling it does not help






How do I install the Mono
This time without me destroying the system

---

### Post by ian-weisser on 2014-09-04
> **offir said:**
> How do I install the Mono
This time without me destroying the system

Impavidus answered that question already.
It was an excellent answer, too.

---

### Post by offir on 2014-09-04
I acted according to the instructions of the first link again
And something was installed

But there is still a problem on sites that require mono


How do I know if Mono is installed on a computer or not

---

### Post by QIII on 2014-09-04
offir --

Please keep this thread limited to Mono to keep it on topic and keep it from getting confusing.

It is best to limit each thread to one topic.

Please feel free to start another thread for assistance with ubuntu-tweak.

Thanks.

May I ask why, when given advice about how to install mono from the Ubuntu repo, you went back to the other tutorial?  These people are trying to help make this easy for you.  Random tutorials on the web are not always trustworthy.

If you want to make sure you have the most up-to-date copy, why not follow the instructions given in Mono Project's own instructions:  [http://www.mono-project.com/docs/getting-started/install/linux/](http://www.mono-project.com/docs/getting-started/install/linux/)

---

### Post by offir on 2014-09-05
Sorry

Just attempt to install mono destroyed some other things

But you're right
Post subject is mono


I got the link that you give through Google for the first time

[http://www.mono-project.com/docs/getting-started/install/linux/]("http://www.mono-project.com/docs/getting-started/install/linux/")


I always install something I first going to the original site

I could not act according to the instructions
The first instruction to download the file

I clicked on the link of the download I get a screen is not clear (to me at least)

I added a picture of what I get


Do i need to open a New Topic (How to install mono ?)
About all this or to stay if this message ?

---

