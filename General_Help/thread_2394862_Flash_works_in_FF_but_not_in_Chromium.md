---
title: "Flash works in FF but not in Chromium"
date: 2018-06-22
forum: General Help
---

### Post by Odense on 2018-06-22
Ubuntu 16.04 LTS
When I want to watch a video like this one:
[https://www.dr.dk/sporten/fifavm2018/kampen-paa-1-min-nigeriansk-trylleri-saetter-island-paa-plads](https://www.dr.dk/sporten/fifavm2018/kampen-paa-1-min-nigeriansk-trylleri-saetter-island-paa-plads)

     My Chromium browser gives me this error message:

     UPS. A MISTAKE HAPPENED...
     To play the broadcast, you must have Adobe Flash Player 10.2 or later installed and enabled in your browser settings.
     Download or Enable Flash here.

The link takes my to the page shown in the attached screenshot where I can download either a .tar.gz or a .rpm file. I have tried downloading and opening both with the software installer and it does not work.

On the other hand I can use the FF browser and play the videos with no problems (except clicking to accept that the video is played).
How can I make it work in Chromium too?

---

### Post by deadflowr on 2018-06-22
Open the program Software and Updates.
Go to Other Software and enable Canonical Partners
close Software and Updates and let it reload.
Then install adobe-flashplugin (not flashplugin-installer.)
If not found in Ubuntu Software, then try
```
sudo apt install adobe-flashplugin
```

Note that you might need to add sites you wish to allow flash to run in your chromium settings for flash;
Flash might be set to block all, so you can usually open Setting in Chromium (Should be an icon in the top right corner area) and go to Content>  Flash
or maybe go here
```
chrome://settings/content/flash
```
I'm currently on Google Chrome, so not sure if this is still the same on chromium.
It was at one point at least from what i remember.
From there you can copy the site address to add to the whitelist of allowed sites to run flash.

If I'm wrong about the whitelisting, someone might have a clearer answer on that.

Though I hope it helps.

---

### Post by bodhin2 on 2018-06-22
deadflowr - just saw this post and not sure about what you say works for chromium.  i have used chromium for 3 years or so now and it was by understanding and also techie people told me that they stopped support for flash.  maybe a couple of years ago?  i never got it to work even with the plugins installed.  i learned to live without it and never looked back.  you know so much more than i do - but that is my understanding.  if i am wrong please correct me.

---

### Post by deadflowr on 2018-06-22
Chromium requires the flash Google Chrome uses, which adobe-flashplugin provides.
It cannot use the flash that Firefox uses anymore.
Which is why you cannot install flashplugin-installer, as it does not provide the chrome flash version.

Hope it make sense though

---

### Post by bodhin2 on 2018-06-22
yes it was the correct plugin; but it never worked.  again, i know enough to be dangerous.  (not arguing - just letting you know what happens on my systems and also what the head tech guy of another distro told me too).  i probably should not have commented.  
:-)

---

### Post by deadflowr on 2018-06-22
You need to add sites to the allow list in the address I posted earlier.

Note that DRM flash is dead on linux except for a sorta workaround:
[https://ubuntuforums.org/showthread.php?t=2363550&p=13665814#post13665814]("https://ubuntuforums.org/showthread.php?t=2363550&p=13665814#post13665814")
The workaround is for getting it for Firefox, so you'd need to make changes to get it for chromium to work.

---

### Post by Dennis N on 2018-06-22
In Chromium, you can do this:
At left end of address bar is a small icon for the site (see attached image) click on that to get a menu (see attached image) which should have an entry for flash (if it's installed). Change it to 'allow'. Then the flash plugin will work.

---

### Post by deadflowr on 2018-06-22
> **Dennis N said:**
> In Chromium, you can do this:
At left end of address bar is a small icon for the site (see attached image) click on that to get a menu (see attached image) which should have an entry for flash (if it's installed). Change it to 'allow'. Then the flash plugin will work.

Thanks, I forgot about that one.
I knew there was an easier method than what I was thinking.

---

### Post by bodhin2 on 2018-06-22
yes thanks!

---

### Post by Odense on 2018-06-23
Thank you deadflowr.

I appreciate your help but apparently I need it a bit more "for dummies".
Please see attached screenshots.

As the screenshots should show I do not have any flash in the "Software shop"
When I try the ```
sudo apt install adobe-flashplugin
``` in a terminal I get an error.
I can also not find the setting you mention in my Chromium

so - who is the next thing I can try?


> **deadflowr said:**
> Open the program Software and Updates.
Go to Other Software and enable Canonical Partners
close Software and Updates and let it reload.
Then install adobe-flashplugin (not flashplugin-installer.)
If not found in Ubuntu Software, then try
```
sudo apt install adobe-flashplugin
```

Note that you might need to add sites you wish to allow flash to run in your chromium settings for flash;
Flash might be set to block all, so you can usually open Setting in Chromium (Should be an icon in the top right corner area) and go to Content>  Flash
or maybe go here
```
chrome://settings/content/flash
```
I'm currently on Google Chrome, so not sure if this is still the same on chromium.
It was at one point at least from what i remember.
From there you can copy the site address to add to the whitelist of allowed sites to run flash.

If I'm wrong about the whitelisting, someone might have a clearer answer on that.

Though I hope it helps.

---

### Post by Odense on 2018-06-23
More screenshots - but why am I limited to 4 pics this time?
And I just tried to make one more post for the remaining pics - but the manager will not let me upload any more (it was also the manager that limited me to 4 here).
So how do I get the last pics attached ?

---

### Post by deadflowr on 2018-06-23
Did you open Software and Updates go to the Other Software tab and enable  Canonical partners?

Then let it reload (it will ask and do so automatically when you close Software and Updates)

(You'll probably need to run the command instead of search the Software store for it, since the software store can be murky)

You can always run the reload manually like
```
sudo apt update
sudo apt install adobe-flashplugin
```

Also read Dennis N's post as that is the easier method to enable flash.

(Note you'll most likely need to restart Chromium if it is running before flash might be usable.)

---

### Post by Odense on 2018-06-23
I don't know where to find the "Software and Updates" or "Other Software" you mention? I only have a "System Tools" > "Software" option.
I am using the classic desktop NOT Unity.


```
morten@morten-Lenovo-B50-10:~$ sudo apt update
[sudo] password for morten: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Hit:2 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial InRelease         
Get:4 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]    
Hit:5 [http://repository.cliqz.com/dist/debian-release](http://repository.cliqz.com/dist/debian-release) stable InRelease         
Get:6 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]  
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.7 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [68.0 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [142 kB]
Get:11 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [796 kB]
Hit:12 [https://s3-us-west-2.amazonaws.com/brave-apt](https://s3-us-west-2.amazonaws.com/brave-apt) xenial InRelease           
Get:13 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [727 kB]
Get:14 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:15 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [233 kB]
Get:16 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [246 kB]
Get:17 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [331 kB]
Get:18 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Get:19 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:20 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,100 B]
Fetched 3,373 kB in 2s (1,378 kB/s) 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
morten@morten-Lenovo-B50-10:~$ sudo apt install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'adobe-flashplugin' has no installation candidate
morten@morten-Lenovo-B50-10:~$ 
```

I reread [COLOR=#000000]Dennis N's post but I don't see anywhere to click or doubleclick to get to the menu he posted a screenshot of - I will try to attach a screenshot of my screen again.

[/COLOR]

---

### Post by deadflowr on 2018-06-23
> I don't know where to find the "Software and Updates" or "Other Software" you mention? I only have a "System Tools" > "Software" option.
Alternate name might be software sources
or
run
```
software-properties-gtk
```
in a terminal and the Software and Updates will open.

Barring that you can edit sources.list file and remove the # comment from the canonical partners line near the bottom.
(I would save the option for last)

> I am using the classic desktop NOT Unity.

That would have saved a moment to know earlier.

---

### Post by Odense on 2018-06-23
Thanks again deadflowr - that solved it - there were 2 [COLOR=#000000]Canonical partners - I enabled them both.
I think "[/COLOR]Software and Updates[COLOR=#000000]" used to be called "Synaptic Package Manager" and I did wonder why they removed the link for that in the system menus.[/COLOR]

[COLOR=#000000]I must apologize for being late in saying that I am using something else than Unity desktop.[/COLOR]

---

