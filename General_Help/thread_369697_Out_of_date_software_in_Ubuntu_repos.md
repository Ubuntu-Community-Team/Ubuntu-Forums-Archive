---
title: "Out of date software in Ubuntu repos"
date: 2007-02-24
forum: General Help
---

### Post by dr_d on 2007-02-24
Hi. I've noticed in my time using Ubuntu that a lot of the software packages in the repos are out of date. 

Just today, I fired up gtk-gnutella and it gave me the message (clock icon, top right hand corner):

> Indicates that gtk-gnutella finds the version you run very VERY old. You should upgrade as soon as possible to avoid suffering from non-optimal Gnutella support that may not only damager your abilities to search and download but also harm the network since you're not supporting the newest features.

Gtk-gnutella wouldn't let me connect (I suspect it was because of this, but not 100% sure).


There are several other software packages I've been waiting since pre-dapper for updates to:

- gtkpod (no albumart in the old repo version)
- network-manager-gnome (old repo version uses gnome-keyring. new version doesn't so don't have to type in passwd every time)
- easytag (old repo version has a bug regarding unicode tags)


Don't get me wrong. I'm not complaining here. I think Ubuntu is by far the best distro I've ever used. However I'd like to see the repos get updated more often.

If I was to compile/test/package some of the new versions myself, what would I have to do in order to get them uploaded to the repos?

Considering the huge user-base we have, I'm sure there must be some more people out there who would be willing and able to help do this.


Cheers,
Dr D

---

### Post by MetalMusicAddict on 2007-02-24
> **dr_d said:**
> Considering the huge user-base we have, I'm sure there must be some more people out there who would be willing and able to help do this.

Are you raising your hand? If so, I can point you in the right direction.

---

### Post by disturbedite on 2007-02-24
each package has its own maintainer.  some maintainers maintain more than one pacakage tho.  but i here ya, there are more than several apps i've compiled myself for this reason too.  (and i'm on feisty herd 4!)

so being that there are a lot of maintainers for different packages, this is a more difficult prospect cuz i guess you'd have to bug each maintainer to update their respective package.......or do it yourself of course.

@ MetalMusicAddict
sweet avatar you've got there.  it'd make a great kubuntu logo!  rock on.  :guitar:

---

### Post by dr_d on 2007-02-24
MetalMusicAddict,
Yeah I'd be glad to help support the community. Where do I sign up? :)

disturbedite,
So if I compile the new version of gtkpod myself, then I won't be able to upload it to the reops because I'm not the maintainer? Is that what you're saying?

---

### Post by hikaricore on 2007-02-24
> **MetalMusicAddict said:**
> Are you raising your hand? If so, I can point you in the right direction.

Zomg you changed your avatar again.. I almost didn't notice it was you. :P

Sneaky sneaky there metal.

---

### Post by _duncan_ on 2007-02-25
> Gtk-gnutella wouldn't let me connect (I suspect it was because of this, but not 100% sure).


I'm still able to download stuff using the old gtk-gnutella package from the repo, so the connection problem may be due to something else. I actually downloaded a small file using gtk-gnutella minutes before posting this.

---

### Post by MetalMusicAddict on 2007-02-25
> **dr_d said:**
> MetalMusicAddict,
Yeah I'd be glad to help support the community. Where do I sign up? :)

Best way to see that packages become updated and/or new apps get in is to learn packaging and become a MOTU (Master Of The Universe). They maintain our Universe and Multiverse repos.

Here are some links:
[http://wiki.ubuntu.com/MOTU](http://wiki.ubuntu.com/MOTU)
[http://wiki.ubuntu.com/MOTU/Documentation](http://wiki.ubuntu.com/MOTU/Documentation)

Also hop on their IRC channel: #ubuntu-motu on Freenode

---

### Post by disturbedite on 2007-02-25
> **dr_d said:**
> MetalMusicAddict,
Yeah I'd be glad to help support the community. Where do I sign up? :)

disturbedite,
So if I compile the new version of gtkpod myself, then I won't be able to upload it to the reops because I'm not the maintainer? Is that what you're saying?

no, that isn't what i meant.  i just meant that in order to get up-to-date packages you'd either have to bug the maintainers of the packages, or do it yourself.

and others have already given you the relevant links, so i guess thats all i have to say.  good luck! ll&p

---

### Post by dr_d on 2007-02-25
Cool. Thanks guys :)

---

### Post by veruus on 2007-03-15
Hey.  With regard to gtk-gnutella not running; if you run it from the command line you'll see:

[FONT="Courier New"]*** ANCIENT VERSION DETECTED! ***

Sorry, this program is too ancient to run without
an explicit user action: If it's not possible to upgrade
you may edit the file

        /home/veruus/.gtk-gnutella/config_gnet

and set the variable "ancient_version_force" to
"gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)".

You will then be able to run this version forever, but
please consider upgrading, as Gnutella is an evolving
network in which ancient software is less useful or even
harmful!

*** EXITING ***
[/FONT]

Uncomment that line, add the variable edit and run it again.  You should be golden.

---

### Post by 2nvme on 2007-03-22
Hi! I am EXTREMELY new to Ubuntu. I desperately need to download songs for my daughter's birthday party CD. Now I have gtk-gnutella (I also have Frostwire, but that's a whole other set of problems!) and in my Terminal it says
 
*** ANCIENT VERSION DETECTED! ***

Sorry, this program is too ancient to run without
an explicit user action: If it's not possible to upgrade
you may edit the file

        /home/nat/.gtk-gnutella/config_gnet

and set the variable "ancient_version_force" to
"gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)".

You will then be able to run this version forever, but
please consider upgrading, as Gnutella is an evolving
network in which ancient software is less useful or even
harmful!

*** EXITING ***

How do you fix this? What does it mean? I need very basic instructions. I have no clue what to do or use to get things to work. If you could type it and I can copy and paste, I would really appreciate it. 

I really like Linux Ubuntu, but I've only used Windows. I'm confused, frustrated and clueless...Please can someone help?!

---

### Post by _duncan_ on 2007-03-22
1. open a terminal:  Applications > Accessories > Terminal

2. type the following:

```
sudo gedit /home/nat/.gtk-gnutella/config_gnet
```

3. enter your password if prompted.

4. an editor will pop-up. Maximize the editor window so it will be easier to edit.

5. look for the phrase "ancient_version_force". It's probably somewhere in the vicinity of line 742.

6. edit that line so that it looks like this:

```
ancient_version_force = "gtk-gnutella/0.96.1 (2006-02-22; GTK2; Linux i686)"
```

7. save the file and exit.

8. start up gtk-gnutella and see if it works.

---

### Post by anaconda on 2007-03-22
> **2nvme said:**
> Hi! I am EXTREMELY new to Ubuntu. I desperately need to download songs for my daughter's birthday party CD. Now I have gtk-gnutella 

Why wont you try eg. ktorrent?  much easier.. dont know really, because I have never used gnutella.. only different torrent clients.

ktorrent is good, because it has a search function... ofcource you can also use google to search torrents..

---

### Post by 2nvme on 2007-03-22
Hi! I tried the first suggestion nothing happened. So I tried downloading KTorrent via applications-add/remove programs and I got this message:

E: sun-java5-doc: subprocess post-installation script killed by signal (Interrupt)

The installation was interrupted and I had to cancel it.  What happened? Am I missing Java? If that's the case that's weird since I can see I have the program Sun Java 5.0 Web Start in applications-internet. 

I really appreciate the help you are giving me...I just wish I could get something to work for me :( :confused:

---

### Post by anaconda on 2007-03-23
try to install it with synaptic.. it should work. I always install programs with synaptic or apt-get..

and no. ktorrent doesn't nee java, because it is a c++ program.

oh and ubuntu does have a bittorrent client installed by default.. it just isn't very good. and it doesnt have a search function at all.  It is in Aplications>internet>BitTorrent. you just need to open a .torrent -file with it and it will start to download it.
eg. here are torrent files for ubuntu install CD:s
[http://www.solidz.com/torrents/linux/ubuntu/](http://www.solidz.com/torrents/linux/ubuntu/)

one good way to search for torrents is google. just search.. 
eg. 
ubuntu torrent
which means that you search for what you want and include a word torrent in your search.

But try to install ktorrent.. it is much easier because it has the search option.. you could also install it from the terminal with:
sudo apt-get install ktorrent

---

