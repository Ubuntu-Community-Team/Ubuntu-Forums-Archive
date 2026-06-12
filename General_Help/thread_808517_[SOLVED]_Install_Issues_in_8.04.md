---
title: "[SOLVED] Install Issues in 8.04"
date: 2008-05-26
forum: General Help
---

### Post by griff36 on 2008-05-26
I'm am pretty new to ubuntu.  Whenever i try to install something, nothing happens.  When i go to add/remove programs, when i click add, it looks like it is working, but nothing happens. i have let it sit for hours, and nothing happens.  The rest of the computer is fine, nothing else freezes up except that window.  This also happened when i tried to install a codec to play music.  Any ideas?

---

### Post by dizee on 2008-05-26
Could you try installing it in a terminal?
for example ```
sudo apt-get install exaile
```
And then post the output it gives you here.

---

### Post by griff36 on 2008-05-26
It seems to have installed.  So do you think just something is wrong with the GUI way?

---

### Post by dizee on 2008-05-26
Actually I was expecting it not to work :lolflag:

So does Synaptic (System > Administration > Synaptic Package Manager) not run or is it just Add/Remove that is having trouble?

---

### Post by griff36 on 2008-05-26
the package manager isn't even opening.

---

### Post by dizee on 2008-05-26
That is weird because Synaptic and Add/Remove are just GUI versions of apt-get. I would have recommended ```
sudo apt-get update && sudo apt-get -f install
```but seeing how the package installed okay that shouldn't be the problem. You could try it anyway I suppose.

Could you try entering ```
gksu synaptic
``` in a terminal and post the output of that if any.

---

### Post by griff36 on 2008-05-26
i did the update, and 0 files replaced.
i also entered the other code and got no output.
i tried to open add/remove but it didnt, so i think those two arent opening because of the other install thing being frozen, im going to reboot and see what happens then.
any more ideas?

---

### Post by griff36 on 2008-05-26
I just rebooted, and Add/remove applications opens, but synaptic package manager still wont.

---

### Post by dizee on 2008-05-26
Yeah try rebooting it to make sure a package installer isn't running.

--edit-- too late :)

Are you sure the Add/Remove program is closed before you try to start Synaptic? If one of them is trying to install or remove something the other won't run.

---

### Post by griff36 on 2008-05-26
no. i'm sure.
synaptic package manager will not open.

---

### Post by dizee on 2008-05-26
Try re-installing it.
```
sudo apt-get remove --purge synaptic
sudo apt-get install synaptic
```
or use Add/Remove to do this ;)

--edit actually don't use add/remove cos it won't get rid of the config files (the --purge bit)

---

### Post by griff36 on 2008-05-26
no luck.
im starting to think its some issue with starting the administrative task, i saw this looking at another thread.
[http://ubuntuforums.org/showthread.php?t=729690]("http://ubuntuforums.org/showthread.php?t=729690")
that might be the problem, but i am a beginner and am not sure if my configuration is bad or not.
i have the local host, like they said, but im not sure where the computer name should be?

---

### Post by dizee on 2008-05-26
If it is that
```
cat /etc/hosts
``` will give you your computer name.

---

### Post by griff36 on 2008-05-26
yea, i went to another similar thread and finally got it working.
i edited my /etc/hosts to put my computer name in. 
thanks for all your help.

---

### Post by griff36 on 2008-05-26
hm actually if you are still reading. i somehow deleted add/remove applications from my computer, and its no where to be found.

---

