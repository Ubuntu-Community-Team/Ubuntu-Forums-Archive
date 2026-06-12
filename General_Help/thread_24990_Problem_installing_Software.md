---
title: "Problem installing Software"
date: 2005-04-08
forum: General Help
---

### Post by Sleepy_Sentry on 2005-04-08
When typing in sudo dpkg -i filename.deb, I get a message in Konsole saying the file can't be found. The same thing happens when I do tar -xvpf filename.tar.gz.

---

### Post by DJ_Max on 2005-04-08
Is that file in the directory you're trying to install it in. You can put a file in the command thats not there.

```
ls
```
If the file isn't listed, you're in the wrong place.

---

### Post by Sleepy_Sentry on 2005-04-08
No it isn't. 

Where do I have to creat the directory and how do I go about installing from there?

Thanks so much!

---

### Post by Jezze on 2005-04-08
Well, I assume you have downloaded a .deb file right? May I ask what you are trying to do?

---

### Post by Sleepy_Sentry on 2005-04-08
I'm trying to instal ndiswrapper.

---

### Post by Jezze on 2005-04-08
If you have downloaded a .deb file I assume it is on your desktop because that is the default place for firefox to download to...

write:

cd Desktop
sudo dpkg -i filename.deb

it should work....

Note: ndiswrapper exists in the repository, start synaptic and search for "ndis".

---

### Post by Sleepy_Sentry on 2005-04-08
I figured out I was having that problem because my password wan't typed in. Once I typed it in and it started to install I got an error message saying a module was missing. I don't have the exact message but I can get it tomorrow if you need it. I'm guessing there's an add-on you need to install to install software?

---

### Post by c_dog on 2005-04-09
Only that you need to have 'root' rights to install software. Since Ubuntu doesn't give to default acess to root you need to use 'sudo' to super-user_do root things. So, yes you're going need to enter your password. Unbuntu does keep a root user password active in memory for for about 5 minutes so you don't have keep entering for every sudo you do.

---

### Post by Sleepy_Sentry on 2005-04-09
Here's the error message I'm getting. Is there something else I need to install?

---

### Post by c_dog on 2005-04-09
The development tools are not installed by default on the CD releases of Ubuntu. In this caause you're trying to install a source file package which needs to reference the generic c compiler 'gcc'. You'll need to install it  and it's libraries before this file.

---

### Post by Sleepy_Sentry on 2005-04-09
Ok how do I do that? I've already installed the builder tools though.

Here's what I get now:
[http://ubuntuforums.org/attachment.php?attachmentid=696](http://ubuntuforums.org/attachment.php?attachmentid=696)

It looks like I need to install something else. What is it and where do I get it?

---

### Post by DJ_Max on 2005-04-09
It tells you it needs module-assistant, which can be found in Synaptic.

---

### Post by Sleepy_Sentry on 2005-04-10
Uh what's Synaptic? I'm a newb lol sorry!

---

### Post by DJ_Max on 2005-04-10
It's a GUI to apt-get.

From the command line:
```
gksudo synaptic
```

Or
System >> Adminstration >> Synaptic Package Manager

---

### Post by Sleepy_Sentry on 2005-04-10
That command doesn't work. Does the fact that I'm using Kubuntu make a difference? And when I go to load the package manager, it starts to load then crashes.

---

### Post by DJ_Max on 2005-04-10
[QUOTE=Sleepy_Sentry]That command doesn't work. Does the fact that I'm using Kubuntu make a difference? And when I go to load the package manager, it starts to load then crashes.[/QUOTE]
 Yeah, that does make a difference, 

use apt-get then.

```
sudo apt-get install module-assistant
```

---

### Post by DJ_Max on 2005-04-10
I found out for KDE, it's kynaptic

---

### Post by RastaMahata on 2005-04-10
in console type this:
sudo apt-get install module-assistant gcc
then install the package.

---

### Post by digby on 2005-04-11
The easist way to do this is going to be to open synaptic and search for 'ndiswrapper.'  There are two packages that come up.  I imagine that you'll need both of them.  Synaptic will then figure out what else you need (e.g. the gcc dependency), and install that as well.

---

