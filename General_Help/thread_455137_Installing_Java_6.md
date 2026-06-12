---
title: "Installing Java 6"
date: 2007-05-26
forum: General Help
---

### Post by moljac024 on 2007-05-26
Hi, i hava a simple question:

I have installed java 5 with synaptic but i  see that java 6 is also available....can i install that too ? Do i need to have java 5 or should i delete it before installing java 6 ? or maybe after ?

---

### Post by taurus on 2007-05-26
You can install java6 and configure your system to use it or you can uninstall java5 first and then install java6.

---

### Post by swv on 2007-05-26
Has anyone successfully downloaded java 6 sdk for AMD 64 platform? All I ever get is an error message at Sun's site when I try to download it..... what's going on? :(

---

### Post by taurus on 2007-05-26
What command did you run and what was the exact error message?  Which release are you running anyway?

---

### Post by swv on 2007-05-26
I can't downliad any java from sun's site... can anyone else do this? Mozilla- latest amd64 fiesty

---

### Post by taurus on 2007-05-26
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by swv on 2007-05-26
I have no idea if this is directed to me or not. 

Code:

sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version


If it is, I have no idea what it means. If it's not, I have no way to tell that.

Does anyone else hav ea problem of not bing able to download java from sun's site? I just get taken ot a page that says FATAL ERROR....

---

### Post by taurus on 2007-05-26
> **swv said:**
> 
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version


I was showing you how to install java, plugin, and font from a terminal (the easy way) but I guess you want to do it the hard way then.

---

### Post by swv on 2007-05-26
Not really... I don't know what the code means, that's all.. is that something I type somewhere... can't I just use the install manager... oh yeah, and why are not .bin files which I downloaded directly executable on Linux/ Fiesty? 

Anyway for anyone who has followed this thread, here is what I learned:

1) Sun supports the combo of Linux AMD 64 bit java except for 
a) the browser plug-in
and 
b) webstart

neither of which have ever been supported so it's not just a java 6.0 issue (the latest version of java as of this posting end of may 2007)

2) Sun's download site for java just HAPPENS to be down along with their download manager site... the same day I happened to try to download java for the  first time on my first day of my first installation of Linux ever, so it's all just a big coincidence and nothing to do with Feisty Faun or Linux of Sun not supporting Linux or anything else....

3) downloading and installing Java on Linux is apparently not as straight forward as the click and  run  installation to be had on Windows. In no way did the add/remove programs of Feisty Faun give me any indication that it even KNEW what the SDK was nor did it know anything about 6.0, even under the programming  subcategory, which is where I would think to look for it. 

I will try again tomorrow to download and install java SDK 6.0 . I will post how it goes to this thread, if I am able to get it off Sun's site.

---

### Post by taurus on 2007-05-26
Okay, let's try this again.

You have two options to install java on your feisty.

1.  Download the .bin from Sun's and install and config it by hand.

or

2.  Open a terminal, Applications -> Accessories -> Terminal, and install it by running those commands since java 1.6 is available from the repos.  Otherwise, open synaptic and Search for **sun-java6** if you want to install it from a GUI.

Again, there is a hard way and an easy way to install things in Ubuntu and somehow you are looking for a hard way.

---

### Post by swv on 2007-05-26
what is synaptic?

---

### Post by swv on 2007-05-26
Synaptic is a package manager under the menu system-->administration.. it "manages packages"... a package is a clearly defined unit of functionality in Linux, about. Why is java a package and not a software program that you add/ remove? Who knows !

---

### Post by taurus on 2007-05-26
Maybe you need to read this, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

### Post by swv on 2007-05-26
OK under synaptic you have to search for "java"... what that returns is everything that mentions java (apparently) which is better than looking through everything...

Then to find java 6 you have to scroll past java 5, way pat and down away from the J entries down to the S entries, as in Sun and there you'll find all things java 1.6ish including documentation the source the sdk etc etc... I checked install or reinstall everything to do with Java 6

It seems that this synaptic is not being  bothered by the downed Sun site because it's downloading all of this as I write, which is great.

---

### Post by swv on 2007-05-26
Ahh spoke too soon, it is not able to download from the Sun site either... a lottle terminal screen pops up to tell me that it has failed (to download from Sun's site) and I can press return to try again or abort.So I know the site is down and I choose abort (type "no" and hit return)

What you see (the UI for this process)  is a lot of stuff scrolling by in the terminal window, which itself is pretty hard to read....

THen it finally tells me that such and such has failed.. so that's how you can set up Java on your Feisty.... if Sun ever fixes their site....

---

### Post by DocHoliday52090 on 2007-05-27
It should be working now (at least, it does so for me). 

Trust me on this one - the terminal is in many ways a whole lot easier than using synaptic. 

GUI (The window, the nice little buttons, etc etc) doesn't neccesarily mean simpler. In this case, a GUI brings on unneccesary steps. 

Open up terminal through APPLICATION -> ACCESSORIES -> TERMINAL

Copy the entire contents of the following box: 

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

and paste it into terminal with Shift+Control+V

It's gonna bring on a nice list of updated repositories and do everything else by itself. Enter your password and/or enter a 'Y' for agreement if/when asked. Enter again. When it's done downloading and installing, it'll go back into a ready state, displaying "Username"@"Computer Name".  

Done. Presto. Hooha.

That's it.

---

### Post by swv on 2007-05-27
Thank you !

I have to disagree with respect to the relative level of worth of command line vs GUI. 
With a command line, you never gain knowledge, you only execute commands. However, with a GUI, you get a richer and enriching experience, while downloading (or whatever).

For instance, when I used synaptic package manager, I was able to purview all the many things that are considered packages by Linux. I gained knowledge about what a package could be; what it meant t BE a package in the eyes of Linux. I gained the specific knowledge that there existed a package called Sunclock, whose existence I never would have imagined. It's description follows, and maybe it's someting I am interested in and maybe it's not, but the point it, by being "efficient" you're depriving yourself of the acquiring new knowledge through happenstance. It's rather as if you decided not to look out the window as your friends drove you about a new town, because you don't "need" to.  Over time, the person who permits his or herself to be exposed to accidental knowledge has more happy finds, has better intuition and a broader   understanding of things...

sunclock vector graphic maps
sunclock is an X11 application that displays a map of the Earth and
indicates the illuminated portion of the globe by drawing sunlit
areas dark on light, night areas as light on dark.  In addition to
providing local time for the default timezone, it also displays GMT
time, legal and solar time of major cities, their latitude and
longitude, and the mutual distances of arbitrary locations on Earth.

This package contains the vector graphic earthmaps.

 Homepage: [http://frmas.free.fr/li_1.htm](http://frmas.free.fr/li_1.htm)

---

