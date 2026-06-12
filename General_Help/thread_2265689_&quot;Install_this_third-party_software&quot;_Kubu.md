---
title: "&quot;Install this third-party software&quot;? Kubuntu mini.iso?"
date: 2015-02-17
forum: General Help
---

### Post by garycheng12 on 2015-02-17
I am trying to understand Linux, testing how dependencies and certain commands for the console work. I use Kubuntu on my laptop for general use and I don't want to possibly mess the system up so I created virtual machine with Kubuntu installed. Two questions to start off (may have more depending on replies):

1. How can I install only certain things from the "install this third-party software" that I'm presented when I install Kubuntu? For example, I want MP3, wifi/graphics drivers, but maybe not Flash (do I really need Flash now that Firefox/Youtube supports or are going to support HTML5 soon)? I googled and found this page: [http://packages.ubuntu.com/utopic/kubuntu-restricted-extras](http://packages.ubuntu.com/utopic/kubuntu-restricted-extras). So basically, checking this option during Kubuntu installation only installs kubuntu-restricted-extras? Is everything listed as "depends", "recommends", "suggests", and "enhances" going to be installed or just "depends"? What is the difference between all 4 descriptions and if only "depends" is required, how do I specify that I only want the minimal requirement for only features I need (for example, install everything that is identified as "depends" but not "recommends, suggests, enhances")? I suspect I might need to come back to the page so understanding these 4 attributes will help me in terms of knowing what I really need and what I don't need.

2. Ubuntu has a mini.iso and from what I understand, it is like Ubuntu without default applications installed. Is it even more stripped down than that? Is there a mini.iso for Kubuntu? I rather build up from the "bare essentials" rather than strip down the default Kubuntu of its extras (certain pre-installed applications) if it's not too much of a hassle. I did a brief search online and found kde-full and kubuntu-desktop. What's the difference between them and kubuntu-desktop the equivalent of downloading Kubuntu 14.10 from the website and kubuntu-desktop the mini.iso for Kubuntu? 

Also, any tips/advice on how I should approach learning Linux in an efficient manner (like what to learn and how to learn it aside from dependencies/commands on the console)? 

Thanks.

On an unrelated note, if someone can explain/tell me the specific steps to setting up the Java environment (ex. JDK path) for running a Java IDE from a fresh Kubuntu install, that would be helpful. I found many sites recommending you to put the directory paths of JDK_HOME, JAVA, etc. at various files (ex. bash_rc profile, profile.d, etc.) and I don't know which is most ideal. I don't want to set it up incorrectly and encounter problems in the future. Since I'm specifying the path of JDK, what happens when I update the JDK to a new version--will I have to change the path to the newer version of the JDK manually? I am new to Java programming as well and I was wondering why a programmer may not want to use the latest JDK version (IDE gives the option to change to previous versions). I don't really understand what Java/JDK/JRE is, why users have to set up so much "environment variables" manually, and why users may want multiple JDK versions to switch between them--why isn't it as simple as apt-get install JDK, apt-get install IDE, and then being able to run the IDE?

---

### Post by sudodus on 2015-02-17
> **garycheng12 said:**
> I am trying to understand Linux, testing how dependencies and certain commands for the console work. I use Kubuntu on my laptop for general use and I don't want to possibly mess the system up so I created virtual machine with Kubuntu installed. Two questions to start off (may have more depending on replies):

1. How can I install only certain things from the "install this third-party software" that I'm presented when I install Kubuntu? For example, I want MP3, wifi/graphics drivers, but maybe not Flash (do I really need Flash now that Firefox/Youtube supports or are going to support HTML5 soon)? I googled and found this page: [http://packages.ubuntu.com/utopic/kubuntu-restricted-extras](http://packages.ubuntu.com/utopic/kubuntu-restricted-extras). So basically, checking this option during Kubuntu installation only installs kubuntu-restricted-extras? Is everything listed as "depends", "recommends", "suggests", and "enhances" going to be installed or just "depends"? What is the difference between all 4 descriptions and if only "depends" is required, how do I specify that I only want the minimal requirement for only features I need (for example, install everything that is identified as "depends" but not "recommends, suggests, enhances")? I suspect I might need to come back to the page so understanding these 4 attributes will help me in terms of knowing what I really need and what I don't need.

I think other people are better explaining what packages you should select ...
> 
2. Ubuntu has a mini.iso and from what I understand, it is like Ubuntu without default applications installed. Is it even more stripped down than that? Is there a mini.iso for Kubuntu? I rather build up from the "bare essentials" rather than strip down the default Kubuntu of its extras (certain pre-installed applications) if it's not too much of a hassle. I did a brief search online and found kde-full and kubuntu-desktop. What's the difference between them and kubuntu-desktop the equivalent of downloading Kubuntu 14.10 from the website and kubuntu-desktop the mini.iso for Kubuntu? 

Also, any tips/advice on how I should approach learning Linux (like what to learn and how to learn it?)? 

Thanks.

There is only one Ubuntu mini.iso for each version (12.04 LTS, 14.04 LTS, 14.10 ...). It is very small and grabs most packages via the internet during the installation. This is why it is also called 'netboot'. See the following link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it - post #3]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

And for the not yet released version Vivid Vervet [http://iso.qa.ubuntu.com/qatracker/milestones/326/builds](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds)

You can install all flavours of Ubuntu using the mini.iso (for example Kubuntu), but it does not work in UEFI mode. If you need to run Kubuntu in UEFI mode, you should install from the Kubuntu 64-bit desktop iso file.

---

### Post by v3.xx on 2015-02-17
> What's the difference between them and kubuntu-desktop
[http://packages.ubuntu.com/trusty/kubuntu-desktop](http://packages.ubuntu.com/trusty/kubuntu-desktop)
The red dots are must have packages, the green dots are optional (recommends).

So one way to do a mini install with the mini.iso is to leave off the recommends.
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```

---

### Post by grahammechanical on 2015-02-17
It is better if you have a thread for each question. It is less confusing.

The restricted extras package in the software centre is a simple method of installing many useful third party audio and visual codecs and other stuff. We may not need or want all the stuff that comes with restricted extras but that is the way things work and many of us find that useful in contrast to installing these things one at a time. Especially if we do not know what we are missing and so cannot know what we need to install.

But all this is completely separate from "depends" and "recommends" and that other stuff that you ask about.

Regards.

---

