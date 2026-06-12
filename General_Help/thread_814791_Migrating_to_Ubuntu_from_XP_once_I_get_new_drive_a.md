---
title: "Migrating to Ubuntu from XP once I get new drive and need some pointers"
date: 2008-06-01
forum: General Help
---

### Post by Phastor on 2008-06-01
Let me first start off by saying that I have had a little experience with Linux.  I had Feisty set up on an old drive and was playing with it several months ago, as well as had an apache server set up on a redhat box several years ago (completely set up using a walkthrough word for word).  Every time I play around with it I get fairly familiar with operating it, and after I spend some time away from it for a while I forget everything.  So i've decided it's time to just take a chance and jump into it by installing Ubuntu on my main machine.  I've always wanted to migrate over from WinXP anyway and will be doing this once my new drive arrives in the mail.  

Aside from just spending some time with it and getting used to it again I need one other pointer.  While playing with Ubuntu, I never knew where a good place would be for storage such as my music, pictures, documents etc.  In case there are multiple acceptible solutions for this, the way I have always had it set up in Windows is I just had a storage partition on the drive that I threw everything in.  So that gives you an idea of my style of organizing things. I do it this way to make it easy to wipe and reinstall Windows without having to worry about copying my files to another location.  When I install Ubuntu, I plan to locate my /home directory on a partition other than the boot partition (again, so I don't have to worry about copying it to a different location if I ever reinstall Ubuntu) if that affects any solutions.

I'm sure there are other things I could be asking, but I will stick to just one thing at a time for now, however if anything comes to mind that you would like to share, I would gladly be willing to listen.  I'll admit even though I've spent some time with it, I am very new to the OS and understand this is going to be a big change using it as my main operating system.

---

### Post by HermanAB on 2008-06-01
It depends on your backup strategy.

Sometimes I make a directory called /export (which is the traditional way to do it) and sometimes I make directories under /home.

The only partitions I backup are /home and /export, so if something  important is somewhere else, I move it to /home (or /export) and make a soft link from the original place.

For example, MySQL and Apache like to store their stuff somewhere on /var, so I redirect those with soft links, so that I only need to backup a single partition.

---

### Post by vvvladut on 2008-06-01
For setting up a separate /home partition, **psychocats** said it all here:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Hope this helps.

---

### Post by Phastor on 2008-06-01
> **HermanAB said:**
> It depends on your backup strategy.

Sometimes I make a directory called /export (which is the traditional way to do it) and sometimes I make directories under /home.

The only partitions I backup are /home and /export, so if something  important is somewhere else, I move it to /home (or /export) and make a soft link from the original place.

For example, MySQL and Apache like to store their stuff somewhere on /var, so I redirect those with soft links, so that I only need to backup a single partition.

Ok.  This gives me an idea then.  To further explain how I have it set up in Windows, I actually have three partitions.  One for the OS and apps, a larger one for my storage, and then a small one that I just throw stuff I have downloaded into until I'm ready to sort it out into it's proper place on the storage partition.  I also have an external drive set up that I clone the storage partition over to every couple of months for backup.

Now to apply that to how I do things in Ubuntu, would it be efficient to do the exact same thing that I do in Windows, and put the /home folder in the storage partition?  That way everything will be backed up at once and isolated on it's own partition whenever I do an OS reinstall.

---

### Post by Phastor on 2008-07-17
Ok.  I'm bringing this thread back from the dead to throw in an update.  I ordered a 640GB WD SE16 drive and it arrived today.  Here's what I'm planning to do.

After thinking about how my mind works with filekeeping and with what was said here, I'm going to set up a 150GB to 200GB partition for the OS and apps.  The rest of it will be set off in a storage partition where I will have my /home directory and a /storage directory where I will dump all of my media and documents.  This way I can save a lot of grief by keeping my settings and files on their own partition if I ever reinstall or try out different distros.

Given my history in file management this seems like a setup I can adapt to easily.  Will I run into any problems later on down the road where I will regret doing this way?  I'm also open to any suggestions that could make this setup better or more practical.  Thanks!

---

### Post by capndunder on 2008-07-17
So, my experience with Hardy Heron has been less than stellar. I've read many posts, tried to familiarize myself with the terminal, reinstalled multiple times, installed many supposed packages for upgrade and repair, installed and reinstalled video drivers, tried new apps, but still have weird desktop visual issues and an inability to run two or three different programs at a time. Too much time spent to do what I can do 'out of the box' with windows. And I hate windows. What's a n00b supposed to do?

---

### Post by Phastor on 2008-07-17
> **capndunder said:**
> So, my experience with Hardy Heron has been less than stellar. I've read many posts, tried to familiarize myself with the terminal, reinstalled multiple times, installed many supposed packages for upgrade and repair, installed and reinstalled video drivers, tried new apps, but still have weird desktop visual issues and an inability to run two or three different programs at a time. Too much time spent to do what I can do 'out of the box' with windows. And I hate windows. What's a n00b supposed to do?
Excuse me?

---

