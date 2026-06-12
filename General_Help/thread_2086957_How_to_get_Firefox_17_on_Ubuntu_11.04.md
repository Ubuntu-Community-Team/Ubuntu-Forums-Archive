---
title: "How to get Firefox 17 on Ubuntu 11.04"
date: 2012-11-22
forum: General Help
---

### Post by javagreen on 2012-11-22
As Ubuntu 11.04 no longer receives official updates, how do you get the latest Firefox 17 on Ubuntu x64?

I can't seem to find a .deb installer and the update hasn't landed in the repos either :/

If I must manually update it, how do I do that?

---

### Post by snowpine on 2012-11-22
You can get it from [http://firefox.com](http://firefox.com)

The reason there are no updates in the repos is that **11.04 is end-of-life, obsolete, and completely unsupported!**

[http://fridge.ubuntu.com/2012/10/28/ubuntu-11-04-natty-narwhal-end-of-life-reached-on-october-28-2012/](http://fridge.ubuntu.com/2012/10/28/ubuntu-11-04-natty-narwhal-end-of-life-reached-on-october-28-2012/)

---

### Post by javagreen on 2012-11-22
> **snowpine said:**
> You can get it from [http://firefox.com](http://firefox.com)

The reason there are no updates in the repos is that **11.04 is end-of-life, obsolete, and completely unsupported!**

[http://fridge.ubuntu.com/2012/10/28/ubuntu-11-04-natty-narwhal-end-of-life-reached-on-october-28-2012/](http://fridge.ubuntu.com/2012/10/28/ubuntu-11-04-natty-narwhal-end-of-life-reached-on-october-28-2012/)

Yes I know it's EOL, I said in the very first line of my post that i know it won't get any updates now, although I had thought basic apps like the browser etc would continue to be pushed to the repos. 

Anyway, the Firefox site gives me a .tar download, how do I overwrite my current FF 16.02 install with this one? 

Any help on this appreciated :)

---

### Post by snowpine on 2012-11-22
You extract the .tar and double-click the firefox icon inside, there is no need to "install" firefox from the .tar.

Beyond that I cannot Support you with something that is Unsupported as I'm sure you can appreciate. :)

---

### Post by sdowney717 on 2012-11-22
try this, simply goto help - about 

firefox should download an upgrade, then hit the button to upgrade.
I went from 14 to 16 to 17 using that
Oh sorry, It is only for Firefox running under wine.

---

### Post by javagreen on 2012-11-22
> **snowpine said:**
> You extract the .tar and double-click the firefox icon inside, there is no need to "install" firefox from the .tar.

Beyond that I cannot Support you with something that is Unsupported as I'm sure you can appreciate. :)

lol ofcourse I appreciate any help, but I have just one concern. 

Won't doing the above result in me having 2 Firefox installs on my system? The already installed 16.02, and now the new 17.0? :D 

Could I not overwrite the 16.02 with 17.0, and I just needed some tips on how to do that.

---

### Post by javagreen on 2012-11-22
> **sdowney717 said:**
> try this, simply goto help - about 

firefox should download an upgrade, then hit the button to upgrade.

Just did that, but It didn't do anything :D

Actually, I don't think that's how FF handles updates, atleast on Ubuntu, you need to either update from the repos (synaptic/Software center) or do it manually.

---

### Post by sdowney717 on 2012-11-22
[https://launchpad.net/~mozillateam/+archive/ppa](https://launchpad.net/~mozillateam/+archive/ppa)

using terminal simply
add the ppa
do the upgrade

commands are
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt-get update
sudo apt-get upgrade

---

### Post by sdowney717 on 2012-11-22
screen showing 17, I just did this after I read your post.

For me it always overwrites the install, so you only get the latest version

---

### Post by james_mcl on 2012-11-22
> 
Won't doing the above result in me having 2 Firefox installs on my system?


Why can't you just mark FF16 for removal in Synaptic (but not complete removal), and apply the change? This should remove FF16 but leave your profile in place (though back up ~/.mozilla just to be sure) ready for you to now install FF17.

---

### Post by snowpine on 2012-11-22
> **javagreen said:**
> lol ofcourse I appreciate any help, but I have just one concern. 

Won't doing the above result in me having 2 Firefox installs on my system? The already installed 16.02, and now the new 17.0? :D 

Could I not overwrite the 16.02 with 17.0, and I just needed some tips on how to do that.

It's analagous to a .zip archive with an .exe executable in Windows.
It won't touch your installed FF 16.

---

### Post by javagreen on 2012-11-22
> **sdowney717 said:**
> [https://launchpad.net/~mozillateam/+archive/ppa](https://launchpad.net/~mozillateam/+archive/ppa)

using terminal simply
add the ppa
do the upgrade

commands are
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt-get update
sudo apt-get upgrade

I added the PPA, but it gives a 404 for /natty

> **sdowney717 said:**
> screen showing 17, I just did this after I read your post.

For me it always overwrites the install, so you only get the latest version

Hmm, I did check like you adviced, but it didn't DL any update. I guess they won't push it for 11.04 after all.

---

### Post by javagreen on 2012-11-22
> **james_mcl said:**
> Why can't you just mark FF16 for removal in Synaptic (but not complete removal), and apply the change? This should remove FF16 but leave your profile in place (though back up ~/.mozilla just to be sure) ready for you to now install FF17.

I could try this, but it now seems there isn't a FF 1.7 for Natty users anymore :(

So even if I remove the installed 16.02 and run FF via the .tar method, I'll have to do this for *every* FF release hereafter.

I did find a 64 bit .deb for FF 17 build 2, but it's for 11.10

---

### Post by javagreen on 2012-11-22
> **snowpine said:**
> It's analagous to a .zip archive with an .exe executable in Windows.
It won't touch your installed FF 16.

Okay I see, does it pick up the existing profile, or would I need to reconfigure everything from scratch?

---

### Post by snowpine on 2012-11-22
> **javagreen said:**
> So even if I remove the installed 16.02 and run FF via the .tar method, I'll have to do this for *every* FF release hereafter.

Yes, that is the meaning of "end of life." If you choose to use an obsolete release then **you** are in charge of tracking down and applying security updates for your kernel, browser, and other apps (nobody else will do it for you).

---

### Post by javagreen on 2012-11-22
> **snowpine said:**
> Yes, that is the meaning of "end of life." If you choose to use an obsolete release then **you** are in charge of tracking down and applying updates (nobody else will do it for you).

:(

Okay okay, but please check my question on the post above yours. I guess I'll do it the tarball way, but would it pick up my existing profile? 

Any way to get it to use the 16.02 profile so that I don't have to reconfigure each release from scratch every time.

---

### Post by snowpine on 2012-11-22
> **javagreen said:**
> :(

Okay okay, but please check my question on the post above yours. I guess I'll do it the tarball way, but would it pick up my existing profile? 

Any way to get it to use the 16.02 profile so that I don't have to reconfigure each release from scratch every time.

Try it and see... I am not going to install an obsolete release and test this just to answer your question (sorry).

---

### Post by javagreen on 2012-11-22
> **snowpine said:**
> Try it and see... I am not going to install an obsolete release and test this just to answer your question (sorry).

It was a general question, I'm not asking or expecting you to install 11.04 so you can check it and let me know, that's ridiculous :P

---

### Post by evilsoup on 2012-11-22
Why do you want to stick with 11.04? Just upgrade to a supported version, it's surely much easier than this byzantine workaround, and you'll be safer -EOL means that it won't even get patches for any security holes found in the software!

---

### Post by javagreen on 2012-11-22
> **evilsoup said:**
> Why do you want to stick with 11.04? Just upgrade to a supported version, it's surely much easier than this byzantine workaround, and you'll be safer -EOL means that it won't even get patches for any security holes found in the software!

The machine I want to get FF 17 on is just a machine for browsing and light gaming. I'm not too concerned about security updates because I have an iptables firewall in place and also I'm behind a hardened router. 

This is an old machine and I want to keep Gnome 2x, I can move to 12.10, but it's not worth it as it'll slow the machine down. It does what it's supposed to do, just browse the web and play some light games :D

It's just me trying to move to the newer FF release, regardless of whether it brings any improvements or not.

---

### Post by claracc on 2012-11-22
[QUOTE

It's just me trying to move to the newer FF release, regardless of whether it brings any improvements or not.[/QUOTE]

I think the only way to do is to do it from the tar package provided for mozilla for linux ubuntu, as it has been addressed previouly by snowpine, you have to untar the .tar file and then click on the firefox icon.

Anycase, I don't understand your point to update browser in an obsolete release,I think you probably will find more problems than advantages in doing it.  I think it would be better to use a lighter and fully updated ubuntu as lubuntu or xubuntu (very near to gnome classic desktop), since you have an old machine, I would recommend lubuntu 12.04.

---

### Post by javagreen on 2012-11-22
> **claracc said:**
> 

I think the only way to do is to do it from the tar package provided for mozilla for linux ubuntu, as it has been addressed previouly by snowpine, you have to untar the .tar file and then click on the firefox icon.

Anycase, I don't understand your point to update browser in an obsolete release,I think you probably will find more problems than advantages in doing it.  I think it would be better to use a lighter and fully updated ubuntu as lubuntu or xubuntu (very near to gnome classic desktop), since you have an old machine, I would recommend lubuntu 12.04.

As I said, it's just me trying to move to the next released build regardless. The current 16.02 version of FF does the job just fine ;)

I guess that's what I'll eventually end up doing, move to a new release but with a light WM :)

---

### Post by SuperFreak on 2012-11-23
My 12.04 machine just updated automatically to Firefox 17. I am having major problems with it now (can't scroll down pages,resizing window doesn't work right, roboform no longer works...), Suggest you hold off on updating for the sake of updating until the bugs are worked out of the new Firefox release

---

### Post by vasa1 on 2012-11-23
> **SuperFreak said:**
> My 12.04 machine just updated automatically to Firefox 17. I am having major problems with it now (can't scroll down pages,resizing window doesn't work right, roboform no longer works...), Suggest you hold off on updating for the sake of updating until the bugs are worked out of the new Firefox release
I'm on the beta channel which means I've been using Firefox 17 for nearly six weeks. I haven't seen the issues you describe (but can't comment on roboform since I don't use that).

---

### Post by NikTh on 2012-11-23
> **javagreen said:**
> The machine I want to get FF 17 on is just a machine for browsing and light gaming. I'm not too concerned about security updates because I have an iptables firewall in place and also I'm behind a hardened router. 

This is an old machine and I want to keep Gnome 2x, I can move to 12.10, but it's not worth it as it'll slow the machine down. It does what it's supposed to do, just browse the web and play some light games 
Hi , 
Other environments (except Unity plugin in Gnome) exits. Have you tried other Environments ? I suggest Ubuntu 12.04 LTS (supported until April 2017). 

This way with .tar ball is only for testing Firefox without install it. I didn't test it , but try to load firefox (from bin inside tarball) with the profile switch and see if you can load your current Firefox profile.
```
man firefox
```
for more info. 

Thanks

---

### Post by SuperFreak on 2012-11-23
I reset Firefox and it seems to be working now. It may have been a plugin that wasn't compatible

---

