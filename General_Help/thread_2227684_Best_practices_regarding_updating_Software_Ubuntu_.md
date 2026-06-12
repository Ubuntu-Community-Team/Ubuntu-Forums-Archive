---
title: "Best practices regarding updating Software Ubuntu 14"
date: 2014-06-03
forum: General Help
---

### Post by Caleb012 on 2014-06-03
What is the best way to ensure  software updates are current.........Using the Terminal (sudo apt-get update) or using the "Software Updater"? Thank you for your input..........

---

### Post by deadflowr on 2014-06-03
Software Updater is easier, since apt-get update doesn't actually install any updates.
Software updater grabs the freshest package listings from the repo system and then lists which packages are update-able on your machine.
It also gives you *some* info about what each updates will do, or is for.

apt-get update only grabs the package listing, and doesn't install anything.
And then the install command  (apt-get upgrade) doesn't even install everything when invoked, sometimes.
In those instances you would run the apt-get dist-upgrade command.

But for all that, the benefit of the terminal, for me, is it is easier to troubleshoot when things go weird.
And it's a lot faster, since it doesn't require you load a bunch of graphical libraries and stuff.

As far as best practice, set the software and updates program > updates to notify security updates immediately and everything else whenever you want.

Me ends meandering post.

---

### Post by Caleb012 on 2014-06-03
Thank you very much!

---

### Post by LastDino on 2014-06-03
The command will be:
For software part.
```

sudo apt-get update
sudo apt-get upgrade
```

However, I recently found out that this could leave out some major kernel updates even though they are available in GUI software updater. So, the best command will be:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Software updater receives notification for update automatically in either of those cases and job will be done for you if you do a simple click. However, *sometimes* you will not receive notification  as soon as they are released, there will be delay of few hours depending on when you log into your PC,  from what I read on this forum once, these updates are released in some cycle. So, if suppose you happen to miss todays they will be available for you tomorrow when you log in. Or you might as well receive notification twice in single log in session, just due to you being on-line during the immediate next release point even though you updated when you logged in. (I could be wrong about this) 

It's not a bad idea to get into habit of doing this from command line as it lets you know exactly what's going on and you are manually checking so there is no question of cycle or w/e. And don't forget to update your mirror before running updates as sometimes your closest are not necessarily best available. For example; I sometimes end up updating from Australian mirror and sometimes African, I live in neither of those.

---

### Post by malspa on 2014-06-03
My preference is to install and use Synaptic.

---

### Post by Caleb012 on 2014-06-03
I now know that there are multiple ways to update my Ubuntu Operating System. Question.........I had already run "Software Updater" earlier today. I downloaded "Synaptic Package Manager" and ran it. It downloaded a number of items and installed them. Is it somehow more thorough or do you think that additional updates became available after running "Software Updater"? Thank you very much!

---

### Post by oldos2er on 2014-06-04
I'm lazy, so I have an alias in ~/.bashrc of ```
alias up='sudo apt-get update && sudo apt-get dist-upgrade'
```

---

