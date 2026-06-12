---
title: "Removing stuff without breaking base and desktop"
date: 2006-10-14
forum: General Help
---

### Post by bobosity on 2006-10-14
I am extremely limited on space so I decided to trim down my system. The problem is stuff that seems to be required by ubuntu-desktop. 

An example is bluetooth stuff. I do not have any bluetooth devices but when I try to uninstall it, I'm told that synaptic is also going to remove ubuntu-desktop.  WTF?

Also Openoffice. I don't need it but removing it takes out the desktop. Am I missing something here?

There are also some games I can't remove. How does the desktop depend on games?

---

### Post by meng on 2006-10-14
ubuntu-desktop is a metapackage. You won't break anything by removing it. It doesn't install anything itself, it just lists a whole bunch of dependencies for the sake of convenience (convenience while installing that is).

My analogy is this: think of it as the big cardboard box that houses many components. The way the package manager is set up, you only need to check one item (the metapackage) to install the complete set. However, by the same token, when you remove one or more of the components, you have to discard the box too. But the box itself does nothing for your system.

---

### Post by bobosity on 2006-10-14
Unfortunately, this is not my first trip down this path. Recently I uninstalled all those things I don't use and was only able to boot to a terminal login. Startx did not work.

I forget all the error messages but they had to do with a broken ubuntu-desktop. apt-get ubuntu-desktop install failed with a whole bunch of errors. I was able to install xubuntu from the command line and finally resolved everything and got gnome back. I'm a little gun shy now when synaptic says it is taking out base and desktop.

---

### Post by meng on 2006-10-14
I can understand the gun-shyness, it would be foolish if you weren't. But if it's only asking to remove the ubuntu-desktop, it's not going to cause a problem. One wonders if you may have gone overboard last time and actively removed something you thought you didn't need but in fact you did. That wouldn't explain why you couldn't reinstall (although of course the command "apt-get ubuntu-desktop install" wouldn't work, I assume you meant and used "apt-get install ubuntu-desktop"). I fail to see where it is asking you to remove base packages this time around - of course I would be more concerned if it was showing this message.

To repeat, if it is just ubuntu-desktop that it is trying to remove, that's expected, it's a well recognized problem, I've advised many other members this way, and haven't heard back about any catastrophes.

---

### Post by K.Mandla on 2006-10-14
If you're feeling really adventurous, you might trying things the other way round -- install a server version of Ubuntu, and add on the packages you want. You'll reach the same results -- a thinner, lighter version of your desktop -- with much less unwanted stuff.

---

### Post by Ptero-4 on 2006-10-14
Or install fluxbuntu. IT's ubuntu with fluxbox instead of gnome.

---

### Post by emarkay on 2006-10-14
Confirming this:

Removing all the games will NOT break Ubuntu event though the warning says it may?

The Server version is the 'minimum' version of the same Ubuntu that is the standard release, and it will function EXACTLY as teh standard release?  Is GRUB there (for dual booting, for example).

Can the standard Ubuntu be "converted" to the server version post install?

Thanks!

---

### Post by meng on 2006-10-14
> **emarkay said:**
> Removing all the games will NOT break Ubuntu event though the warning says it may?

The Server version is the 'minimum' version of the same Ubuntu that is the standard release, and it will function EXACTLY as teh standard release?  Is GRUB there (for dual booting, for example).

Can the standard Ubuntu be "converted" to the server version post install?

1. What warning says that it may break your system? There'll be a warning that the ubuntu-desktop package has to be removed, but I'm not aware of any warning that it will break the system. The two are not equivalent! If you have received some other warning, then please quote it properly.

2. The server edition does not have a GUI desktop installed. So most people would not consider that it functions EXACTLY as the standard release. The only thing that functions EXACTLY as the standard release (desktop install I assume you mean) is the standard release. (

3. One can convert from one version to the other, as the underlying package management is identical. For that matter, one can convert from Kubuntu to Xubuntu to Ubuntu to Fluxbuntu to Ubuntu CE ... it's all a matter of which packages are selected and which aren't.

---

### Post by bobosity on 2006-10-14
OK, I went and uninstalled a few things that also took out ubuntu-desktop and it rebooted just fine. It's entirely possible that I was drunk the first time.:???: To bad synaptic doesn't have a sobriety monitor.

While we're on the subject, how about 'laptop-detect'? I think that's one of the packages that I killed the first time. Why does it uninstall so many things? Also 'reiserfs' takes out base. Why?

---

### Post by K.Mandla on 2006-10-14
There are some fundamental packages that form the bottom layer of what gets installed. Take a look at [ubuntu-minimal]("http://packages.ubuntu.com/dapper/base/ubuntu-minimal") and [ubuntu-standard]("http://packages.ubuntu.com/dapper/base/ubuntu-standard"). A lot of things are intertwined at that level. You can removee ubuntu-standard or ubuntu-minimal without ripping out the packages them imply. If you take out one that relies on some others, it might strip those out as well.

If you're not using a laptop, you could probably uninstall laptop-detect and get away with it. Same goes for things like pcmciautils and others.

But again, if you're this keen on reducing the unnecessary (and I'm a fellow believer on that point), start with a server installation and build up. There are some ideas [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems") and [here]("http://www.ubuntuforums.org/showthread.php?t=206022"). It's a great way to learn, although I can almost guarantee things will break. ;)

---

### Post by bobosity on 2006-10-14
> If you're not using a laptop, you could probably uninstall laptop-detect and get away with it.

Laptop-detect is a perfect example. Go to synaptic and mark it for complete removal. The list of things it uninstalls is long. In fact, it appears to take out my whole system. 

Why are so many things tied to what appears to be a nonessential package?

---

### Post by K.Mandla on 2006-10-14
It's hard to say. If I understand the description of [laptop-detect]("http://packages.ubuntu.com/dapper/utils/laptop-detect"), it signals to other programs when the host machine is a laptop. 

I suppose you could say that those other programs wouldn't function without the information they get from laptop-detect. If that's the case, it might be the rationale for removing them.

---

### Post by bobosity on 2006-10-14
> If I understand the description of laptop-detect, it signals to other programs when the host machine is a laptop. 

I see a problem here. In your quote above you gave a link to the package list pages. I went there and looked. What they show there is NOTHING like what I see when I look at it in synaptic.

In synaptic getting rid of laptop-detect means also losing almost everything on my disk.

Seriously, go to synaptic and try it. Mark laptop-detect for removal and see what happens. You can cancel out before you go to far. Something seems very wrong here.

---

### Post by meng on 2006-10-14
I did try exactly that, and got the result you suggested. Now the page you pointed to only tells you what the dependencies of laptop-detect are, it doesn't tell you what packages count laptop-detect as a dependency (which is what synaptic is forced to remove if you remove laptop-detect). So there's nothing wrong with the package listing on the webpage.

Bottom line: just because your computer isn't a laptop doesn't mean you don't need laptop-detect.

---

### Post by emarkay on 2006-10-15
> **meng said:**
> 1. What warning says that it may break your system? There'll be a warning that the ubuntu-desktop package has to be removed, but I'm not aware of any warning that it will break the system. The two are not equivalent! If you have received some other warning, then please quote it properly.

My bad in presuming that the Ubuntu-desktop is teh system - in the way I see it onscreen now.

I will try to remove some games and see what happens (!)

---

### Post by emarkay on 2006-10-15
Whew!  I did it an no more silly games and wow - I can stil see my desktop.

Somebody "in charge" needs to make that clearer that removing the Ubuntu-Desktop doesn't!!!!

Now to kill more Ubuntu bloatware!  Mwo ha ha haaa! :mrgreen:

Firefox - gone
Braile - gone
Bluetooth - gone
a few other things I forget - gone!

EXCELLENT!

(I even added a few things...)

What a great OS!

---

