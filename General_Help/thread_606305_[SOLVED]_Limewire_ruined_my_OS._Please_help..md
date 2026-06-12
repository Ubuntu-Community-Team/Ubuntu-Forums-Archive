---
title: "[SOLVED] Limewire ruined my OS. Please help."
date: 2007-11-07
forum: General Help
---

### Post by Sentience on 2007-11-07
Im using fiesty fawn. I just tried to download limewire, the new version made just for ubuntu. It froze in the middle of installation. I tried again, but it wouldnt let me because it said that there were two managers running at once and that I would have to close the other one first....this continues even after I reboot the OS. However, when I go to the package manager or ANYTHING that has anything to do with downloading new programs I get this message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

       So I cant install anything, cant use add/remove programs, cant access the synaptic package manager, and cant seem to undue any of this....I have limited skill with the command line, which is why I chose Ubuntu because I expected it to be easy. Im really hoping that I dont have to loose all of my media files to reinstall the OS. That would suck.

---

### Post by rsambuca on 2007-11-07
Open a terminal "Applications -> Accessories -> Terminal"

In the terminal enter the following code and press enter.```
sudo dpkg --configure -a
```

---

### Post by mpierce on 2007-11-07
Launch a terminal and try this:

sudo apt-get -f install

this will try to correct the dependencies or erase the corrupted/uninstalled file.

Hope this helps...

---

### Post by Sentience on 2007-11-07
Oh, my computer has also been slowing down like it has a virus. It even freezes up sometimes. It seems to be getting worse.

Is there a way to run anti-virus and add-aware and spybot from CD in safe mode?

How can I fix this without reinstalling the OS?

---

### Post by Sentience on 2007-11-07
> **mpierce said:**
> Launch a terminal and try this:

sudo apt-get -f install

this will try to correct the dependencies or erase the corrupted/uninstalled file.

Hope this helps...



I tried and got the same message I posted above when I tried to access the synaptic package manager.

---

### Post by Sentience on 2007-11-07
Nope. Still broken.

---

### Post by Sentience on 2007-11-07
Is there a way to just reinstall the OS without loosing all my files? I think I have a virus.

---

### Post by Hmarroqu on 2007-11-07
I doubt you have a virus, where you running windows that would be another answer. ANYWAYS, the way i would handle a reinstall without losing data is to take the current disk with the "broked" OS and remove the data via linking it to another disk as a slave, boot up and xfer your files to the good one.  I would only do this with Ubuntu OS since windows may get a virus that was chilling in your kaput drive and was not affecting ubuntu the carrier.  Yea its complicated but its a sure way of not losing your data.

---

### Post by Sentience on 2007-11-07
I havnt used any windows or even WINE. I do have a dual operating system with windows, but I almost never use it. This all happened when I was running Ubuntu and downloading the linux version limewire. It froze halfway through. I forced quit. Tried again, and then I keep getting told that another manager is running and nothing works right plus the computer is slowing down and freezing now.

I might be able to get a friend to help me make a backup disk of my important files.....what a pain in the *** if I have to reinstall it.

---

### Post by Maestro23 on 2007-11-07
> **Sentience said:**
> I havnt used any windows or even WINE. I do have a dual operating system with windows, but I almost never use it. This all happened when I was running Ubuntu and downloading the linux version limewire. It froze halfway through. I forced quit. Tried again, and then I keep getting told that another manager is running and nothing works right plus the computer is slowing down and freezing now.

I might be able to get a friend to help me make a backup disk of my important files.....what a pain in the *** if I have to reinstall it.

Try running these commands from terminal:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade

What format was limewire in that you tried to download?  .deb, .bin., .run?

---

### Post by spideygal on 2007-11-07
> **rsambuca said:**
> Open a terminal "Applications -> Accessories -> Terminal"

In the terminal enter the following code and press enter.```
sudo dpkg --configure -a
```



Same thing happed to me a few days back, when a pack is interupted while installing you have to run this command from terminal  ```
sudo dpkg --configure -a
```

---

### Post by Sentience on 2007-11-07
It was Debian based, made specifically for ubuntu.

Do you think the problem will be fixed if I upgrade to Gusty Gibbon?

---

### Post by Sentience on 2007-11-07
> **spideygal said:**
> Same thing happed to me a few days back, when a pack is interupted while installing you have to run this command from terminal  ```
sudo dpkg --configure -a
```

I must have typd that in 50 times by now, and it hasnt helped. Not only that but my computer is freezing up more and more.

---

### Post by Frak on 2007-11-07
> **Sentience said:**
> Is there a way to just reinstall the OS without loosing all my files? I think I have a virus.
You don't have a virus, I GUARANTEE you; you don't have a virus. Wine still isn't good enough to run viruses.

Just post the output of
```
sudo dpkg --configure -a
```

---

### Post by Sentience on 2007-11-07
I think my computer is fixed. I suspect what did it was doing the upgrade through the terminal, but it didnt kick in until I restarted my computer.

Sun something or other didnt install and I still dont have limewire, but my computer isnt broken anymore.....I think.


Thank you for all your help, especially the person who showed me how to upgrade through the terminal.

---

### Post by Maestro23 on 2007-11-07
> **Sentience said:**
> I think my computer is fixed. I suspect what did it was doing the upgrade through the terminal, but it didnt kick in until I restarted my computer.

Sun something or other didnt install and I still dont have limewire, but my computer isnt broken anymore.....I think.


Thank you for all your help, especially the person who showed me how to upgrade through the terminal.

Good deal.  Please mark this SOLVED using the Thread Tools.

Some links for future reference: 

Installing Software:
Installing Anything: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Psychocats Page: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Frak on 2007-11-07
> **Sentience said:**
> I think my computer is fixed. I suspect what did it was doing the upgrade through the terminal, but it didnt kick in until I restarted my computer.

Sun something or other didnt install and I still dont have limewire, but my computer isnt broken anymore.....I think.


Thank you for all your help, especially the person who showed me how to upgrade through the terminal.
Side-note, when using aptitude in Gutsy, use
```
sudo aptitude **safe-**upgrade
```
Instead of straight upgrade (less chance of destruction)
[B]
Mark your thread solved in Thread Tools -> Mark Thread [SOLVED][/B]

---

