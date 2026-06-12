---
title: "Installing Skype"
date: 2016-07-18
forum: General Help
---

### Post by 4kh3RAm on 2016-07-18
[h=2]Followed this, but can find Skype.
```

Installing Skype[/h] Users of 64-bit Ubuntu, should enable [MultiArch]("https://help.ubuntu.com/community/MultiArch") if it isn't already enabled by running the command 
sudo dpkg --add-architecture i386Since Ubuntu 10.04 (Lucid Lynx), Skype is part of the Canonical partner repository. To install Skype add the [Canonical Partner Repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories"). You can do this by running the command 
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"Then install Skype via the [Software-Center]("https://help.ubuntu.com/community/SoftwareCenterFAQ") or via the Terminal. 
sudo apt-get update && sudo apt-get install skype
```

---

### Post by Frogs Hair on 2016-07-18
Open software & updates , navigate to the other software tab and check the box for Canonical Partners . Close software and updates and open the terminal and run the following.

```
sudo apt-get update && sudo apt-get install skype
```

I see skype in synaptic , but not in ubuntu software. ??

---

### Post by 4kh3RAm on 2016-07-18
> **Frogs Hair said:**
> Open software & updates , navigate to the other software tab and check the box for Canonical Partners . Close software and updates and open the terminal and run the following.

```
sudo apt-get update && sudo apt-get install skype
```

I see skype in synaptic , but not in ubuntu software. ??

Followed your directions.
> 
W: The repository 'http://ppa.launchpad.net/bneijt/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/bneijt/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/bneijt/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.



Still no Skype.

---

### Post by kostkon on 2016-07-18
There's also [the alpha version of the new Skype client for Linux]("http://www.omgubuntu.co.uk/2016/07/skype-linux-alpha") you could try.

---

### Post by 4kh3RAm on 2016-07-18
Before I try that I need to uninstall the 2 versions of Skype that are already installed that do not work.

Package manager is not showing it installed.

That is disturbing. :-)

---

### Post by danbosse1 on 2016-07-18
The new skype client works great!

---

### Post by 4kh3RAm on 2016-07-18
Great. :-)

But I still need to cleanup after some bad installations of Skype.

---

### Post by Frogs Hair on 2016-07-18
The errors look to be from an un-supported/un-related ppa. I would suggest installing the synaptic package manger as tool for cleanup and installation if not already. ```
sudo apt-get install synaptic   
```

---

### Post by 4kh3RAm on 2016-07-18
I already have it.

"Package manager is short for 'synaptic package manger.'

I try to minimize typing whenever possible. :-)

---

### Post by Bucky Ball on 2016-07-18
I have provided the answer for this already on [your other thread]("https://ubuntuforums.org/showthread.php?t=2331107&p=13519368#post13519368") ...

It helps to make it clear why you are wanting to do what you are doing when posting a support thread. You do not need Skype to test a video camera and if that is the only reason you are installing, it's killing a mosquito with an elephant gun. :) Use Cheese. In the repos. Take two seconds to install.

Installing Skype from anywhere other than the official repositories is unnecessary and done at your own risk. It can also cause a mess as you've discovered by creating one. There is no need to do so. Installing Skype is (or should be) very simple.

Enable Canonical Partners repository in Software and Updates> Other Software> update> install Skype. Done. Consulting a search engine may have told you all you need to know in a few minutes.

Good luck with it.

---

### Post by 4kh3RAm on 2016-07-18
My post was about a CCTV camera connected to a TV card that had a RCA input.

Not the same as a video camera.

I am human and I make mistakes.

I will gladly provide more details.

Have a nice day.

---

### Post by Bucky Ball on 2016-07-19
No mistakes means no learning, so human is good! But do you need Skype if you only want to check the camera or do you actually want to use Skype? That is my question. If the former, there are much easier ways of checking a video camera. Skype is certainly not the 'go to' option for that, but if you have it already installed, it would be a way.

If you only want to check the camera, all I'm saying is you can install Cheese from the repositories (whatever package manager you are using) in less than a minute. Skype is a rather larger beast for such things and not specifically designed for video. It can do it, but it is a VOIP app, not a video one. Cheese is specifically designed for purpose. It is one of others but probably one of the lightest in the repos. :)

If you only want to check the camera, Skype will drag in a ton of stuff that you don't need, won't use and is unrelated to testing cameras, or cameras at all.

[QUOTE=4kh3RAm]My post was about a CCTV camera connected to a TV card that had a RCA input.

Not the same as a video camera.[/QUOTE]

Well, one doesn't record to itself, but without going there, Cheese will use either device if its working and available on your system in one way or another: RCA, Firewire, USB, whatever you're using. ;)

---

### Post by 4kh3RAm on 2016-07-19
Cheese is not seeing the camera.

I will see if there is some other way that my computer can see the CCTV camera.

---

