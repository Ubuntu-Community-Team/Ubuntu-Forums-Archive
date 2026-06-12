---
title: "Broken Packages!!!"
date: 2005-08-10
forum: General Help
---

### Post by bh4887 on 2005-08-10
Hi all,
Let me just start by saying that Ubuntu is my first introduction to Linux, so it feels like I'm more than incompetent with my computer.  
I installed an addon called Ubuntuaddon.zip which is supposed to give me all kinds of new packages and applications I thought.  Well after the installation I checked Synaptic to see the new packages and an error window popped up says the following:
"The following problems were found on your system:

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or directory)"

I'm not really sure what I'm supposed to do to fix these "problems".  So far I've only seen the effects in Synaptic (when I try to download certain packages it tells me I can't for some reason or another), and Ubuntu Update manager where it tells me that it couldn't download all the repository indexes and then spits the same messages at me.  
Any help would be appreciated.
Thanks.

---

### Post by pmjdebruijn on 2005-08-10
Hi,

Hmmm 'ubuntuaddon.zip' ? Where did you get this file...

Also linux files, are generally **not** distributed as .zip files, so it's a reason to think this file is a bit suspicious...

Also, I noticed you're using ubuntu backports... Do you really need them? These are **not** official ubuntu packages... I can't recommend it...

But looking at the error messages, it seems your downloading from: [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

This is a master repository of ubuntu backports... Recently the ubuntu backports project has **denied access** to the master mirror for the general public. They have done this, to prevent the master mirror from being overloaded, which in turn prevents propagation of new packages the mirrors...

So substitute the backports master repository for a ubuntu backports mirror in your /etc/apt/sources.list.

Regards,
Pascal de Bruijn

---

### Post by bh4887 on 2005-08-10
i got the zip from [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)  


btw, what will "substitute the backports master repository for a ubuntu backports mirror in your /etc/apt/sources.list." do, and how do I do it?

---

### Post by cutOff on 2005-08-10
[QUOTE=bh4887]Hi all,
Let me just start by saying that Ubuntu is my first introduction to Linux, so it feels like I'm more than incompetent with my computer.  
I installed an addon called Ubuntuaddon.zip which is supposed to give me all kinds of new packages and applications I thought.  Well after the installation I checked Synaptic to see the new packages and an error window popped up says the following:
"The following problems were found on your system:

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or directory)"

I'm not really sure what I'm supposed to do to fix these "problems".  So far I've only seen the effects in Synaptic (when I try to download certain packages it tells me I can't for some reason or another), and Ubuntu Update manager where it tells me that it couldn't download all the repository indexes and then spits the same messages at me.  
Any help would be appreciated.
Thanks.[/QUOTE]
Try with these backports instead of

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```

---

### Post by bh4887 on 2005-08-10
[QUOTE=cutOff]Try with these backports instead of

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```[/QUOTE]

how do i exactly "try with these backports?"
Sorry, I really need it spelled out for me. thanks

---

### Post by pmjdebruijn on 2005-08-15
Open /etc/apt/sources.list in your favorite text editor as root. Then substitute the backports URL, with a URL, from the ubuntu backports mirror list...

But like I said, if you're a newbie, I highly recommend **against** using backports...

Regards,
Pascal de Bruijn

---

