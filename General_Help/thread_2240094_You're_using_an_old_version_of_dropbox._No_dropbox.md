---
title: "You're using an old version of dropbox. No dropbox for you!"
date: 2014-08-17
forum: General Help
---

### Post by fizikz on 2014-08-17
I just got an email from dropbox saying that the version I'm using is old and will be discontinued next week (yeah, I know sounds like a phishing email right?). I checked my current version and it's 1.6.0. I got the PPA repository from [http://www.ubuntuupdates.org/ppa/dropbox](http://www.ubuntuupdates.org/ppa/dropbox) and installed the latest version (1.6.2) last updated in the PPA on 2014/04/21. So far so good. When I try to run dropbox, it will not let me sign in, saying the version is too old and that I must download a new version. The "newer" .deb version on dropbox's site is 1.6.1... But when I checked the release notes, I realized that the 1.6.x versions are almost 2 years old! The latest version is  2.10.28 from 2014/8/15. 

Why is the package in the repository so old? Do I really need to install manually to get a recent version that dropbox will actually allow to login?

---

### Post by vasa1 on 2014-08-17
> **fizikz said:**
> ...
Why is the package in the repository so old? Do I really need to install manually to get a recent version that dropbox will actually allow to login?
I've been using dropbox direct from dropbox.com and not from any repo or ppa. My version is 2.10.27. No scary e-mails about older versions. What is interesting is that very few other users have so far reported receiving such e-mails.

---

### Post by fizikz on 2014-08-17
I presume you installed manually? What's also strange is that the .deb and .rpm files directly from dropbox.com are even older... version 1.6.0. Just mouse over the different linux downloads available to see this.

And yes, I searched and was surprised nobody reported similar emails.

---

### Post by vasa1 on 2014-08-17
I go to [www.dropbox.com](www.dropbox.com), click on Download near the top-right corner, then do what is appropriate from there:
```
**Install Dropbox via command line**
The Dropbox daemon works fine on all 32-bit and 64-bit Linux servers. To install, run the following command in your Linux terminal.

32-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -
64-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
Next, run the Dropbox daemon from the newly created .dropbox-dist folder.

~/.dropbox-dist/dropboxd
```
They mention server, but this process works for a regular Lubuntu desktop as well. Note that I do not have Nautilus installed and that I have no need to integrate everything with everything else.

---

### Post by mc4man on 2014-08-17
> **fizikz said:**
> 
And yes, I searched and was surprised nobody reported similar emails.
At least here dropbox occasionally updates itself  (the  installed .deb from dropbox says 1.6.2, dropbox itself shows 2.10.27

It seems those that don't accept or successfully allow these updates will eventually get the email.
[https://www.dropbox.com/help/6252](https://www.dropbox.com/help/6252)
[https://www.dropbox.com/help/6251](https://www.dropbox.com/help/6251)

---

### Post by vasa1 on 2014-08-17
> **mc4man said:**
> At least here dropbox occasionally updates itself  (the  installed .deb from dropbox says 1.6.2, dropbox itself shows 2.10.27

It seems those that don't accept or successfully allow these updates will eventually get the email.
[https://www.dropbox.com/help/6252](https://www.dropbox.com/help/6252)
[https://www.dropbox.com/help/6251](https://www.dropbox.com/help/6251)
I think OP was referring to users who installed via the repo or via the ppa and not direct. I too get updates for the stable version direct and successfully.

---

### Post by uRock on 2014-08-18
I got the same email today. I uninstalled DropBox within minutes of installing it, so I won't bother with upgrading.

---

### Post by fizikz on 2014-08-18
I did eventually download and install manually as per the instructions on the download site. It's good if updates are obtained directly.

When I previously tried installing the .deb from dropbox's site, it would not install, saying that I had a newer version (1.6.2) installed. I still have no idea why they would label it as 1.6.0 if it's in fact 2.10.27. Out of curiosity, now I wish I had checked the dropbox reported version when I had 1.6.0 installed.

---

### Post by vasa1 on 2014-08-18
> **fizikz said:**
> I did eventually download and install manually as per the instructions on the download site. It's good if updates are obtained directly. ...
I've received two direct updates while on Lubuntu 14.04. I don't recall getting them previously even though I used the same installation method for Lubuntu 13.10. Maybe it's a new feature.

---

### Post by vasa1 on 2014-08-18
[http://askubuntu.com/questions/512779/dropbox-upgrade](http://askubuntu.com/questions/512779/dropbox-upgrade)

---

### Post by fizikz on 2014-08-18
> **vasa1 said:**
> [http://askubuntu.com/questions/512779/dropbox-upgrade](http://askubuntu.com/questions/512779/dropbox-upgrade)

Looks like uninstalling dropbox with a package manager and installing the .deb from dropbox's site is the simplest solution. I'd still like to point out that this thread pre-dates that askubuntu solution. :D

For now, I'll stick with the manual installation I've got. 

Thanks for the help, vasa1. Another problem solved.

---

### Post by uRock on 2014-08-18
> **vasa1 said:**
> [http://askubuntu.com/questions/512779/dropbox-upgrade](http://askubuntu.com/questions/512779/dropbox-upgrade)

After doing a quick search and seeing some of the security issues the latest Dropbox version may be fixing, I can't understand why the fellow on there is so adamant about telling people to wait for Canonical to update the currently supported version. 

[https://www.google.com/search?q=dropbox+targetted+attack&oq=dropbox+targetted+attack&aqs=chrome..69i57.8631j0j7&sourceid=chrome&es_sm=122&ie=UTF-8#q=dropbox+targeted+attack&safe=off&spell=1](https://www.google.com/search?q=dropbox+targetted+attack&oq=dropbox+targetted+attack&aqs=chrome..69i57.8631j0j7&sourceid=chrome&es_sm=122&ie=UTF-8#q=dropbox+targeted+attack&safe=off&spell=1)

---

### Post by vasa1 on 2014-08-18
> **uRock said:**
> After doing a quick search and seeing some of the security issues the latest Dropbox version may be fixing, I can't understand why the fellow on there is so adamant about telling people to wait for Canonical to update the currently supported version. 

[https://www.google.com/search?q=dropbox+targetted+attack&oq=dropbox+targetted+attack&aqs=chrome..69i57.8631j0j7&sourceid=chrome&es_sm=122&ie=UTF-8#q=dropbox+targeted+attack&safe=off&spell=1](https://www.google.com/search?q=dropbox+targetted+attack&oq=dropbox+targetted+attack&aqs=chrome..69i57.8631j0j7&sourceid=chrome&es_sm=122&ie=UTF-8#q=dropbox+targeted+attack&safe=off&spell=1)+1. Plus the repo version has been outdated for rather some time. It may have made sense, in a cynical way, if Canonical had a competing product but that isn't the case now. Plus, I wonder why the only offering the repos have is linked to Nautilus.

---

### Post by deadflowr on 2014-08-18
The guy in the askubuntu thread doesn't know what he/she's talking about.
The deb does add the dropbox repo.

> [FONT=UbuntuRegular][COLOR=#444444]I [/COLOR][/FONT][COLOR=#444444][FONT=UbuntuRegular] have to disagree with @DanJohansen. Downloading a [/FONT][/COLOR].deb[COLOR=#444444][FONT=UbuntuRegular] file and installing it will [/FONT][/COLOR]**most definitely notadd any repository to the system**

Simply wrong
Installing from the deb does add the repo.

similar to google chrome.

---

### Post by fizikz on 2014-08-18
I just checked my second computer that was mentioned by name in dropbox's warning email. It has version 1.6.2 installed, but dropbox reports 2.10.27. Let's see what happens in a week.

---

### Post by vasa1 on 2014-08-18
The command line instructions wget a tar:```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
``` So no deb, no repo, when done that way.

Whatever happens, happens in my home folder.

---

### Post by edantes2 on 2014-09-03
Is this topic really "Solved" as marked in the subject line?  I just installed on Ubuntu 10.04 version 1.62 off the dropbox.com repository.  This is Dropbox v2.6.31.  It won't connect when I try to log in -- it will still break and give the message the  "You're using an old version of dropbox". 
[h=2][/h]

---

### Post by deadflowr on 2014-09-03
> **edantes2 said:**
> Is this topic really "Solved" as marked in the subject line?  


Yes.
For the Op, at least.
For now...

---

### Post by Elfy on 2014-09-03
> **edantes2 said:**
> Is this topic really "Solved" as marked in the subject line?  I just installed on Ubuntu 10.04 version 1.62 off the dropbox.com repository.  This is Dropbox v2.6.31.  It won't connect when I try to log in -- it will still break and give the message the  "You're using an old version of dropbox". 
[h=2][/h]

Not only that - unless you're using the server version of 10.04 - you're using an old and out of date version of Ubuntu. Desktop version was EOL more than 12 months ago.

---

### Post by edantes2 on 2014-09-03
> **Elfy said:**
> Not only that - unless you're using the server version of 10.04 - you're using an old and out of date version of Ubuntu. Desktop version was EOL more than 12 months ago.

I have it working now.  It turns out that installing/updating the dropbox software package did not update the deamon installed in the user home directory (~/.dropbox-dist).

Here is what I did:

1. Quit dropbox 
2. mv .dropbox-dist  dropbox-dist-old
3. Start dropbox

Dropbox will guide you with the deamon download and installation in your home directory. Log on to your account and after reindexing,  it  works as usual.

Alternatively, you can download and install the deamon manually as indicated in a previous message in this thread:

[http://ubuntuforums.org/showthread.php?t=2240094&p=13101311#post13101311](http://ubuntuforums.org/showthread.php?t=2240094&p=13101311#post13101311)

---

### Post by ThatBum on 2014-09-03
I don't know about you guys, but when I installed my Dropbox package (direct from their site) it automatically added their repository linux.dropbox.com to my sources.list, like what Google Chrome does. I haven't seen it update through apt, though.

However, the daemon actually lives in the user's home directory, in .dropbox-dist, and is downloaded when Dropbox is run for the first time. The Dropbox daemon automatically updates itself without needing root or apt or any of that.

So, you have two versions: 1.6.2, the package, and 2.10.28, the daemon. Similar situation with Steam for Linux as well.

E: Oop, got ninja'd with the solving. Ah well.

---

### Post by vasa1 on 2014-09-03
> **ThatBum said:**
> I don't know about you guys, but when I installed my Dropbox package (direct from their site) it automatically added their repository linux.dropbox.com to my sources.list, like what Google Chrome does. I haven't seen it update through apt, though.

However, the daemon actually lives in the user's home directory, in .dropbox-dist, and is downloaded when Dropbox is run for the first time. The Dropbox daemon automatically updates itself without needing root or apt or any of that.

So, you have two versions: 1.6.2, the package, and 2.10.28, the daemon. ...

How do you see two versions? Which command do you run to see that? My sources.list does not have *any* dropbox-related entry. I don't have any dropbox-related ppa either. Maybe my set-up is "cleaner" because my distro is Lubuntu and not Ubuntu; also I didn't install any dropbox stuff from the repos.

As you've observed, everything is "at home" and not anywhere in /, AFAICT.

---

### Post by ThatBum on 2014-09-03
> **vasa1 said:**
> How do you see two versions?

I got 1.6.2 from [FONT=courier new]apt-cache show dropbox[/FONT], and 2.10.28 from simply mousing over the Dropbox indicator icon.

Also that apt line was automatically installed, it's in /etc/apt/sources.list.d/dropbox.list. My install is Xubuntu 14.04.1 LTS.

Perhaps it didn't do this on your machine with a different version of the package, I dunno.

---

### Post by vasa1 on 2014-09-04
> **ThatBum said:**
> ... and 2.10.28 from simply mousing over the Dropbox indicator icon.
...
I'm still on 2.10.27. Hmmm... 

I got this from [https://www.dropbox.com/release_notes](https://www.dropbox.com/release_notes) (with "stable" selected)
```
2.10.29   8/20/2014
2.10.28   8/15/2014
2.10.27   7/31/2014

```

---

### Post by ThatBum on 2014-09-04
> **vasa1 said:**
> I'm still on 2.10.27. Hmmm...
Their take on updating:
Auto-upgrades are rolled out gradually after a new update is avalible. We're very conservative about auto-updating. We never want to risk breaking a working version of Dropbox.

So, whenever it feels like it, it seems.

Try removing ~/.dropbox-dist/ to force it to get a new daemon.

---

### Post by vasa1 on 2014-09-04
> **ThatBum said:**
> ...
Try removing ~/.dropbox-dist/ to force it to get a new daemon.
No, no, I'm quite happy ;)

---

### Post by ThatBum on 2014-09-04
> **vasa1 said:**
> No, no, I'm quite happy ;)
It worked for me, I'm now running 2.10.29 quite fine. Settings are all still there. Rename it instead if you're worried about it dying on you.

---

