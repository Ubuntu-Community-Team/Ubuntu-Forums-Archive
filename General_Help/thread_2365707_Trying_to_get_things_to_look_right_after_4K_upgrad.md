---
title: "Trying to get things to look right after 4K upgrade"
date: 2017-07-09
forum: General Help
---

### Post by hatetech on 2017-07-09
I recently got a 4K screen, and I've been trying to get everything adjusted so I can actually use Ubuntu 16.04 Mate in this resolution. I jacked up the DPI, and certain things are still tiny, and it's annoying. I can't find any place to change the size of the Min/Max/Close buttons on all the windows. I also can't find any place to set color output to ycrbr 4:4:4 instead of RGB. The AMD drivers don't appear to have any kind of UI. I'm using an rx480. quick screenshot: [http://viper.shadowflareindustries.com/temp/wtf2.png](http://viper.shadowflareindustries.com/temp/wtf2.png)

---

### Post by hatetech on 2017-07-10
Bump

---

### Post by hatetech on 2017-07-12
These tiny Min/Max/Close buttons are driving me nuts, and I still can't figure out how to change color output from RGB to YCbCr.

---

### Post by #&amp;thj^% on 2017-07-12
Some Themes will change the size of those buttons....I'm not yet on a 4K monitor but yes your buttons are very small: Yuck!
If you are using compiz...there is a little more control with Emerald window decorations.
No advice on your RGB to YCbCr problem though

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Some Themes will change the size of those buttons....I'm not yet on a 4K monitor but yes your buttons are very small: Yuck!
If you are using compiz...there is a little more control with Emerald window decorations.
No advice on your RGB to YCbCr problem though

I don't see that option in Compiz. Can you be more specific? To me, that thing is just a mess.

---

### Post by #&amp;thj^% on 2017-07-12
Have  a look here: [https://ubuntuforums.org/showthread.php?t=2321453](https://ubuntuforums.org/showthread.php?t=2321453)
If you have problems let me know here.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Have  a look here: [https://ubuntuforums.org/showthread.php?t=2321453](https://ubuntuforums.org/showthread.php?t=2321453)
If you have problems let me know here.


Uh, the link to Launchpad to download Emerald from that thread you linked is just a 404.

p.s. Why is Alt+Tab painfully slow in 4K? This is an rx480 with a 8core CPU and 32GB RAM. There's no excuse for any normal OS functions to be so sluggish.

---

### Post by #&amp;thj^% on 2017-07-12
Ooops!
This one works: [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+packages](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+packages)
You will need 3 Packages....Save them to a folder in your Home directory named emerald you will need to create that folder first, and save them in that folder.
These 3 .debs is what you need to download.
```
emerald_0.9.5-0~webupd8~vivid_amd64.deb
libemeraldengine-dev_0.9.5-0~webupd8~vivid_amd64.deb 
libemeraldengine0_0.9.5-0~webupd8~vivid_amd64.deb
```
Now open a terminal and run this...one line at a time.
```
cd emerald
sudo dpkg -i *.deb
```
Should be good to go for the install.
Now to change the window decoration, you need to enter this in the terminal.
```
emerald --replace & disown
```
If you are happy enough with that...you will need to add emerald to auto start.
You can also do the same with Compiz Manager...Under>>Effects>>Window Decoration>>Click on that and in the general window in the "command" remove or change this "exec /usr/bin/compiz-decorator" to look like "emerald --replace"
Screenshot included.
> p.s. Why is Alt+Tab painfully slow in 4K? This is an rx480 with a 8core CPU and 32GB RAM. There's no excuse for any normal OS functions to be so sluggish. 
I have no idea...Works just fine on my end.

---

### Post by hatetech on 2017-07-12
Followed all the steps, but nothing changed. Perhaps it doesn't work on Mate? I tried logging out and back in as well.

---

### Post by #&amp;thj^% on 2017-07-12
Works Perfect on mate. Works here on 16.04 thru 17.04 mate.
What didn't work? The Install? or trying to launch emerald?
Errors from the terminal are needed here.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Works Perfect on mate. Works here on 16.04 thru 17.04 mate.
What didn't work? The Install? or trying to launch emerald?
Errors from the terminal are needed here.

Didn't see any errors. Nothing changed when I did the command though. Not sure what it means, but it said "[1] 16429" when I entered "emerald --replace & disown"

---

### Post by #&amp;thj^% on 2017-07-12
> **hatetech said:**
> Didn't see any errors. Nothing changed when I did the command though. Not sure what it means, but it said "[1] 16429" when I entered "emerald --replace & disown"

I need to see all the output from the terminal...copy it and paste it back here Please!
Also can you paste back the return of this from the terminal do this first:
```
apt policy emerald libemeraldengine-dev libemeraldengine  
```

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> I need to see all the output from the terminal...copy it and paste it back here Please!
Also can you paste back the return of this from the terminal do this first:
```
apt policy emerald libemeraldengine-dev libemeraldengine  
```

viper@MateBMF:~/emerald$ sudo dpkg -i *.deb
[sudo] password for viper: 
(Reading database ... 525697 files and directories currently installed.)
Preparing to unpack emerald_0.9.5-0~webupd8~vivid_amd64.deb ...
Unpacking emerald (0.9.5-0~webupd8~vivid) over (0.9.5-0~webupd8~vivid) ...
Preparing to unpack libemeraldengine0_0.9.5-0~webupd8~vivid_amd64.deb ...
Unpacking libemeraldengine0 (0.9.5-0~webupd8~vivid) over (0.9.5-0~webupd8~vivid) ...
Preparing to unpack libemeraldengine-dev_0.9.5-0~webupd8~vivid_amd64.deb ...
Unpacking libemeraldengine-dev (0.9.5-0~webupd8~vivid) over (0.9.5-0~webupd8~vivid) ...
Setting up libemeraldengine0 (0.9.5-0~webupd8~vivid) ...
Setting up libemeraldengine-dev (0.9.5-0~webupd8~vivid) ...
Setting up emerald (0.9.5-0~webupd8~vivid) ...
update-alternatives: using /usr/bin/emerald to provide /usr/bin/x-window-decorator (x-window-decorator) in auto mode
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Warning: mailcap line not starting with a media type in emerald
Problematic line:  application/x-emerald-theme; nametemplate=%s.emerald
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
viper@MateBMF:~/emerald$ 



viper@MateBMF:~$ sudo emerald --replace & disown
[1] 16429
viper@MateBMF:~$ apt policy emerald libemeraldengine-dev libemeraldengine
emerald:
  Installed: 0.9.5-0~webupd8~vivid
  Candidate: 0.9.5-0~webupd8~vivid
  Version table:
 *** 0.9.5-0~webupd8~vivid 100
        100 /var/lib/dpkg/status
libemeraldengine-dev:
  Installed: 0.9.5-0~webupd8~vivid
  Candidate: 0.9.5-0~webupd8~vivid
  Version table:
 *** 0.9.5-0~webupd8~vivid 100
        100 /var/lib/dpkg/status
N: Unable to locate package libemeraldengine
viper@MateBMF:~$

---

### Post by #&amp;thj^% on 2017-07-12
[s]Aha your missing this package " libemeraldengine"[/s]
EDIT Just seen you edited your post.
And you don't run emerald with sudo just run this:
```
emerald --replace
```
lets take a look inside of here, again run one line at a time.
```
cd emerald
ls
```
Paste back again please.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> [s]Aha your missing this package " libemeraldengine"[/s]
EDIT Just seen you edited your post.
And you don't run emerald with sudo just run this:
```
emerald --replace
```
lets take a look inside of here, again run one line at a time.
```
cd emerald
ls
```
Paste back again please.

I have all 3 files.

viper@MateBMF:~/emerald$ ls
emerald_0.9.5-0~webupd8~vivid_amd64.deb
libemeraldengine0_0.9.5-0~webupd8~vivid_amd64.deb
libemeraldengine-dev_0.9.5-0~webupd8~vivid_amd64.deb

---

### Post by #&amp;thj^% on 2017-07-12
> **hatetech said:**
> I have all 3 files.

viper@MateBMF:~/emerald$ ls
emerald_0.9.5-0~webupd8~vivid_amd64.deb
libemeraldengine0_0.9.5-0~webupd8~vivid_amd64.deb
libemeraldengine-dev_0.9.5-0~webupd8~vivid_amd64.deb

Yes i seen that after you edited your post.
Now try just this:
```
emerald --replace
```
No **sudo** this can/will cause problems.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Yes i seen that after you edited your post.
Now try just this:
```
emerald --replace
```
No **sudo** this can/will cause problems.

It's just sitting there with the cursor blinking. Nothing happened. Terminal is stuck there now.

---

### Post by #&amp;thj^% on 2017-07-12
Hit key combo <ctrl+c>
with the focus on the terminal.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Hit key combo <ctrl+c>
with the focus on the terminal.

Well, that got it unstuck. Now what?

---

### Post by #&amp;thj^% on 2017-07-12
Do you still have window buttons? (Close, Minimize, Maximize)

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Do you still have window buttons? (Close, Minimize, Maximize)

Yeah, nothing changed.

---

### Post by #&amp;thj^% on 2017-07-12
Good! Now use synaptic package manager and uninstall those three packages you just installed.
I'm going to tweak those for you...I just noticed your card is AMD and I'm not sure the driver will handle emerald as is.
One more output from the terminal if you will:
```
inxi -G
```
Paste this one back here.
And you may have to install inxi with:
```
sudo apt install inxi
```
And is this your card: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814150782](https://www.newegg.com/Product/Product.aspx?Item=N82E16814150782)

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Good! Now use synaptic package manager and uninstall those three packages you just installed.
I'm going to tweak those for you...I just noticed your card is AMD and I'm not sure the driver will handle emerald as is.
One more output from the terminal if you will:
```
inxi -G
```
Paste this one back here.
And you may have to install inxi with:
```
sudo apt install inxi
```
And is this your card: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814150782](https://www.newegg.com/Product/Product.aspx?Item=N82E16814150782)

No, MSI rx480. 8GB. [https://www.amazon.com/dp/B01K1JTT8S](https://www.amazon.com/dp/B01K1JTT8S)

viper@MateBMF:~/emerald$ inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 67df
           Display Server: X.Org 1.18.4 drivers: ati,amdgpu (unloaded: fbdev,vesa,radeon)
           Resolution: 3840x2160@30.00hz, 3840x2160@24.00hz
           GLX Renderer: AMD Radeon RX 480 Graphics
           GLX Version: 4.5.13468 - CPC 16.60.3
viper@MateBMF:~/emerald$

Also, I don't actually see a package manager UI. Do I need to do this junk through the command line too? It's 2017. Linux should work better than this by now.

---

### Post by #&amp;thj^% on 2017-07-12
> **hatetech said:**
> 

Also, I don't actually see a package manager UI. Do I need to do this junk through the command line too? It's 2017. Linux should work better than this by now.
Instead of criticizing Linux what it should do or don't do....just embrace it...adapt to it. "When in Rome do what the Romans Do :P" you'll be a lot happier with this mindset.;)
Now if you want you can install Synaptic with:
```
sudo apt install synaptic
```
And do the uninstall of the three packages.
Now I'm not going to waste my time to help here...if you are just going to gripe at every turn.
Let me know.

---

### Post by hatetech on 2017-07-12
> **1fallen said:**
> Instead of criticizing Linux what it should do or don't do....just embrace it...adapt to it. "When in Rome do what the Romans Do :P" you'll be a lot happier with this mindset.;)
Now if you want you can install Synaptic with:
```
sudo apt install synaptic
```
And do the uninstall of the three packages.
Now I'm not going to waste my time to help here...if you are just going to gripe at every turn.
Let me know.

packages removed.

---

### Post by #&amp;thj^% on 2017-07-12
Give me some time to make the needed changes to the packages.
I will post back when done>
To be sure remove all left overs if any:
```
sudo apt autoremove
```
Kind Regards

---

### Post by #&amp;thj^% on 2017-07-14
Turns out I wasted a day unsuccessfully trying to tweak things....but on a brighter note I did manage to make the .debs with Apt-Cacher. (The first packages we used were out dated.)
They are in the attachment I uploaded.
Install the same way as before,**_ If you have not done already delete the old .debs in the emerald folder_**, and extract the new one's into that folder.
Install with:
```
cd emerald
sudo dpkg -i *.deb
```
And this time do not use SUDO when running emerald. So to be very clear here run only:
```
emerald --replace & disown
```
This is just to see if it runs on your system, and now if happy enough with that make the changes needed to auto start "Emerald" I have perviously explained.

---

### Post by hatetech on 2017-07-14
It did the same exact thing as last time. No effect.

viper@MateBMF:~/emerald$ sudo dpkg -i *.deb
[sudo] password for viper: 
Selecting previously unselected package emerald.
(Reading database ... 525938 files and directories currently installed.)
Preparing to unpack emerald_0.9.5-7~xenial_amd64.deb ...
Unpacking emerald (0.9.5-7~xenial) ...
Selecting previously unselected package libemeraldengine0.
Preparing to unpack libemeraldengine0_0.9.5-7~xenial_amd64.deb ...
Unpacking libemeraldengine0 (0.9.5-7~xenial) ...
Selecting previously unselected package libemeraldengine-dev.
Preparing to unpack libemeraldengine-dev_0.9.5-7~xenial_amd64.deb ...
Unpacking libemeraldengine-dev (0.9.5-7~xenial) ...
Setting up libemeraldengine0 (0.9.5-7~xenial) ...
Setting up libemeraldengine-dev (0.9.5-7~xenial) ...
Setting up emerald (0.9.5-7~xenial) ...
update-alternatives: using /usr/bin/emerald to provide /usr/bin/x-window-decorator (x-window-decorator) in auto mode
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
viper@MateBMF:~/emerald$ emerald --replace & disown
[1] 26085
viper@MateBMF:~/emerald$

---

### Post by #&amp;thj^% on 2017-07-14
Then it wont work for you and your card's Driver....This is new driver that was released in 16.04 for AMD Graphics.
The only solution I can suggest now is reverting back to 14.04 and using the AMD-pro Driver.
I don't have your hardware so I can not do anything on my end to help here.
I'm Strictly a Intel and Nvidia Guy. And as I have stated they work perfectly here.
Sorry but we tried.

---

### Post by hatetech on 2017-07-14
This is why I hate computers. Something as simple as resizing things like the Min/Max/Close or scrollbars is virtually impossible or takes a bunch of BS like this.

---

### Post by #&amp;thj^% on 2017-07-14
It is simple on my end...just lacking experience on your end...and a poor attitude just adds to your woe's.
And as far I know Linux is the most user friendly when it comes to Tweaking your system to personal taste's.(Comes with time and experince)
One thing to keep in mind here is That Drivers are written for windows first...biggest market share/with Hardware vendors.
I do understand your frustrations due to a lack of investigation with what works best in Linux...No OS is perfect, things are constantly changing.
I wish you luck in your endeavors though.

---

### Post by hatetech on 2017-07-14
> **1fallen said:**
> It is simple on my end...just lacking experience on your end...and a poor attitude just adds to your woe's.
And as far I know Linux is the most user friendly when it comes to Tweaking your system to personal taste's.(Comes with time and experince)
One thing to keep in mind here is That Drivers are written for windows first...biggest market share/with Hardware vendors.
I do understand your frustrations due to a lack of investigation with what works best in Linux...No OS is perfect, things are constantly changing.
I wish you luck in your endeavors though.

Been using Ubuntu since 8.04, and it still pisses me off. Still relies too heavily on command line stuff that's not easy to find out too. I tried increasing the width of scrollbars, and it ended up only working in Chrome. Nothing else.

---

