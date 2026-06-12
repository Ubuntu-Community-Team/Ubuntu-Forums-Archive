---
title: "I Tried...  I Really Did"
date: 2007-12-19
forum: General Help
---

### Post by Tiribulus on 2007-12-19
Alright folks, please forgive my frustration, but this is  the third time in the last year I've tried getting Ubuntu to work on 3 different machines and I'm all but ready to throw in the towel and go back to Suse.

This time it's a Latitude D400, standard Dell portable. 
1. Wireless just about never works (standard Intel adapter) always connected, but no ping, dhcp doesn't work, static settings disappear inexplicably, no option for no security, roaming mode will not go away no matter how many times I try. Went live once, spontaneously, and  then never worked again. Trying the same manual settings that work on every other machine that works fine, including this one minus Ubuntu. Either they don't work or roaming mode reasserts itself and the settings are negated.

2. Wired networking generally works, but after every reboot (which hangs) I have to tell it the domain name and DNS server to use as these are back to default.

3. Getting flash to work has been a nightmare. Not found in Firefox, not found using the sudo command. Ran apt get and the connection dropped in the middle leaving me unable to use it or uninstall it. Tells me to run dpkg manually and that tells me I need super user creds to run it.

Always the same. Installs fine and looks great for about five minutes until stuff that doesn't work starts to show up and defies my every attempt at resolution from post after post in these forums.

It could all be me. This distro is very popular and I don't know everything, especially with Linux,  but it's really getting not to be worth it. Windows and Suse are nearly effortless to configure on this very machine. All I ever hear is how great and EASY Ubuntu is. Maybe it just hates me.

Rant over. We now return you to your regularly scheduled posting.

---

### Post by rsambuca on 2007-12-19
Not every distro works with every combination of hardware.  If Suse works easily, why not stick with it?

---

### Post by HermanAB on 2007-12-19
Well, yeah, Ubuntu is not the easiest distribution around.  It is popular because it is heavily promoted. In reality there a quite a few other distributions out there with better wizards, for example Mandriva, Suse, Mint and even Fedora is easier to get going.  Mandriva is really the only Linux distro where you can do everything using a mouse - Suse comes close, but Ubuntu is not even in the running.

---

### Post by rsambuca on 2007-12-19
> **HermanAB said:**
> Well, yeah, Ubuntu is not the easiest distribution around.  It is popular because it is heavily promoted. In reality there a quite a few other distributions out there with better wizards, for example Mandriva, Suse, Mint and even Fedora is easier to get going.  Mandriva is really the only Linux distro where you can do everything using a mouse - Suse comes close, but Ubuntu is not even in the running.

I disagree with this, based on my personal experience.  Most installs of Ubuntu can easily be done with out the command line.

---

### Post by bingoUV on 2007-12-19
One thing I have been unable to figure out, rsambuca, is how to edit root owned files without command line in ubuntu? e.g. how to edit /etc/fstab ?

Newbies might need to edit some or the other root owned file, maybe at the instructions of more experienced linux users. Pretty common use case, but it is not easily evident how to do it. Is it just me?

---

### Post by Joshua on 2007-12-19
This can help with opening stuff as root.

[http://ubuntuforums.org/showpost.php?p=3950898&postcount=4]("http://ubuntuforums.org/showpost.php?p=3950898&postcount=4")

---

### Post by rsambuca on 2007-12-19
Editing root files is usually done via the command line, or a text editor with root permissions.  Shouldn't be a common occurrence for a new user though.

---

### Post by Tiribulus on 2007-12-19
It's not that I need anything laughably easy, it's just that I would like the stuff that I'm staring at and I know the purpose of to do what it's supposed to do. Suse has gotten bulky and Ubuntu "feels" clean and efficient until I run into these aggravating problems.

It's like, "oh cool, here's the networking stuff, etho, etho1, looks good. I'll just set this up and away we should go." Then away we don't go. It would be easier to take if it was just broke, period, but it looks like it should work. It's like a personal defeat when something as simple as a flash install, that I know thousands of people have working, becomes an arm wrestling match.

---

### Post by bingoUV on 2007-12-19
Thanks Joshua."gksudo nautilus" has to be written in command line, so not applicable. Right click to open as root could  have been done without command line but it is described in the link as needing chmod. I'll bookmark it. Though, cumbersome enough to make a new user curse ubuntu.

I have to strongly disagree with the sentiment that new users don't need to edit files as root. There are so many such files in /etc alone, and windows power users when switching to linux invariably like to customize some stuff according to their convenience. Search this very forum if you want to know the proportion of tasks that need opening stuff as root. Unfortunate. 

I am lucky that command line is most intuitive interface for me.

---

### Post by rsambuca on 2007-12-19
> **bingoUV said:**
> Thanks Joshua."gksudo nautilus" has to be written in command line, so not applicable. Right click to open as root could  have been done without command line but it is described in the link as needing chmod. I'll bookmark it. Though, cumbersome enough to make a new user curse ubuntu.

I have to strongly disagree with the sentiment that new users don't need to edit files as root. There are so many such files in /etc alone, and windows power users when switching to linux invariably like to customize some stuff according to their convenience. Search this very forum if you want to know the proportion of tasks that need opening stuff as root. Unfortunate. 

I am lucky that command line is most intuitive interface for me.

I think our definitions of "new user" is much different.  You sound like a power user in windows and want to be a power user in linux.  I don't think that most "new users" to linux want to be power users.

---

### Post by tech9 on 2007-12-19
> **rsambuca said:**
> I disagree with this, based on my personal experience.  Most installs of Ubuntu can easily be done with out the command line.

I agree

---

### Post by bingoUV on 2007-12-19
> **rsambuca said:**
> I think our definitions of "new user" is much different.  You sound like a power user in windows and want to be a power user in linux.  I don't think that most "new users" to linux want to be power users.


Yes, we will have to agree to disagree. Note that I am a power user in linux and I sometimes like to help other users become power users in linux. Some of them have been power users in windows. I seriously can't find my way to anything in windows.

---

### Post by Joshua on 2007-12-19
That may be, but even to make something mount on boot (say an extra internal disk that has all your music) you would need to edit a file as root.  Changing graphics configuration for something that's not automatically recognized almost always leads to editing /etc/X11/xorg.conf.

---

### Post by rsambuca on 2007-12-19
> **Joshua said:**
> That may be, but even to make something mount on boot (say an extra internal disk that has all your music) you would need to edit a file as root.  Changing graphics configuration for something that's not automatically recognized almost always leads to editing /etc/X11/xorg.conf.

Hey, I am not saying that the command line will never be required, especially if there are graphics card issues.  For the internal drive, though, that could have easily been added during the installation phase.

---

### Post by Tiribulus on 2007-12-19
Lemme also say that I don't mean to sound like I'm running Ubuntu down. All these happy users can't be wrong. It just seems in my case it doesn't wanna play for whatever reason.

---

