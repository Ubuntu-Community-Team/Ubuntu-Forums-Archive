---
title: "NVIDIA drivers work fine... til reboot"
date: 2008-05-16
forum: General Help
---

### Post by c0mp13371331337 on 2008-05-16
Having a bit of driver problem, wondering if anyone else has been getting this.  I've got an nVidia 8800GTS (512MB) card, I currently have the 173.08beta drivers from nVidia installed (although the problem arises with the 169.12 version, as well), and I'm running an up-to-date, fresh install of Hardy.

To install the drivers, I stopped gdm using the following command:

```
sudo /etc/init.d/gdm stop
```Then executed the driver installer.  Once that finished, I started gdm again:

```
sudo /etc/init.d/gdm stop
```And after tweaking a few settings with nvidia-settings, I had my dual-screens running at 3200x1200, Compiz working flawlessly, 3D games (such as doom3) look fantastic, the works.

However, I was in for a rude awakening when I rebooted, as it killed whatever life my system had and X started in safe graphics mode using the vesa drivers.  I've spent a fair bit of time tinkering with it and the best I can chizel the process down to is simply stopping gdm again, reinstalling the nVidia drivers (either version works), and firing gdm back up.

All my nVidia settings are exactly as I left them, so I don't have to reconfigure that at least, but I do still need to.... um.... reinstall the driver after each reboot.  And maybe it's just me, but it seems a little ludicrous that I would even entertain the idea of writing a script that executes before gdm starts to reinstall my nVidia drivers.  Please help me here, I'd feel dirty if I had to resort to that.

---

### Post by PmDematagoda on 2008-05-16
Do this:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reboot the PC and see if the Nvidia driver now works.

---

### Post by c0mp13371331337 on 2008-05-16
I challenge anyone to try and get this same level of support from M$.  Not gonna happen.

PmDematagoda, many thanks friend.  That worked like a charm.  I can now shut down my system without having to wonder if I'm going to have an extra 5 minutes of spare time to install the drivers when I reboot, or if I'll have to suffer 800x600 for whatever I'm doing!

Thanks again!

---

### Post by dchurch on 2008-05-20
Hmmm...I just edited that file, and now I have a very low res, and the screens are just duplicated on each.

Any idea how I can get back to where I was?

The file now seems to be empty upon reboot.

---

### Post by dchurch on 2008-05-20
Bizarre!

Not sure what I did, but I got back in ok, but the left screen was on the right and vice versa.

The option for swapping them is now missing.

I did the easiest thing and just swapped the cables. ;-)

---

### Post by WunSick on 2008-05-20
PmDematagoda, After searching the great and powerful Google, i searched here, found this thread, and you made my day! THanks!

---

### Post by Zer0Nin3r on 2008-05-22
> **PmDematagoda said:**
> Do this:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reboot the PC and see if the Nvidia driver now works.

How does it work and why?

---

### Post by PmDematagoda on 2008-05-23
> **Zer0Nin3r said:**
> How does it work and why?

The problem may be with modules conflicting with each other, in this case the nvidia and nvidia_new modules, this can cause the X-Server to crash and go to Fail-Safe. I am not sure of the explanation, but with my current knowledge, that is what I think is happening:).

---

### Post by ChameleonDave on 2008-06-02
> **PmDematagoda said:**
> The problem may be with modules conflicting with each other, in this case the nvidia and nvidia_new modules

Hmm, interesting.

So, there are three Nvidia modules: *nv*, *nvidia* and *nvidia_new*.  This raises the question of why we aren't using *nvidia_new*.  Surely it's the most up-to-date one.

---

### Post by llama320 on 2008-06-05
> **WunSick said:**
> PmDematagoda, After searching the great and powerful Google, i searched here, found this thread, and you made my day! THanks!

I second that 
Thanks!

---

### Post by mbradlcu on 2008-06-05
> **ChameleonDave said:**
> Hmm, interesting.

So, there are three Nvidia modules: *nv*, *nvidia* and *nvidia_new*.  This raises the question of why we aren't using *nvidia_new*.  Surely it's the most up-to-date one.

aren't the nvidia_new drivers for gt6600 and newer cards.. not sure what generation actually but I'm pretty sure that's why there's 2 different driver sets.

---

### Post by ChameleonDave on 2008-06-05
> **mbradlcu said:**
> aren't the nvidia_new drivers for gt6600 and newer cards.. not sure what generation actually but I'm pretty sure that's why there's 2 different driver sets.

I have a 7900 GS on one of my boxes.  Should I be using *nvidia_new*?

---

### Post by PmDematagoda on 2008-06-05
> **ChameleonDave said:**
> I have a 7900 GS on one of my boxes.  Should I be using *nvidia_new*?

Yes, you should be using nvidia_new.

---

### Post by ChameleonDave on 2008-06-06
> **PmDematagoda said:**
> Yes, you should be using nvidia_new.

I just enabled nvidia_new, rebooted, and X started in low-graphics mode.  Thanks!  LOL

---

### Post by PmDematagoda on 2008-06-06
> **ChameleonDave said:**
> I just enabled nvidia_new, rebooted, and X started in low-graphics mode.  Thanks!  LOL

Did you install the Nvidia drivers manually by any chance? 

Also post the output of:-
```
cat /var/log/Xorg.0.log
```

---

### Post by ChameleonDave on 2008-06-06
> **PmDematagoda said:**
> Did you install the Nvidia drivers manually by any chance? 

Also post the output of:-
```
cat /var/log/Xorg.0.log
```

No, I have the *nvidia-glx-new* and *nvidia-glx-new-dev* packages from the repos.

---

### Post by PmDematagoda on 2008-06-06
Do:-
```
sudo xfix
```
and see if that fixes the problem.

---

### Post by ChameleonDave on 2008-06-06
> **PmDematagoda said:**
> Do:-
```
sudo xfix
```
and see if that fixes the problem.

The command *xfix* isn't in my path.  I had to do *locate* to find it at */usr/share/recovery-mode/options/xfix*.

OK, I've run it, and all it seems to do is ruin my */etc/X11/xorg.conf* file by removing all my customisations (graphics tablet, etc).  I've going to restore my */etc/X11/xorg.conf* file that works.

---

### Post by herger on 2008-07-02
> **PmDematagoda said:**
> Do this:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reboot the PC and see if the Nvidia driver now works.


HI!! Thanks, guys, it works great!!
Thanks again

Herger

---

### Post by drewcoon on 2008-07-19
> **PmDematagoda said:**
> Do this:-
1) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

Then reboot the PC and see if the Nvidia driver now works.

I was having a similar problem and this fixed it for me. Thanks :)

---

### Post by shoey51 on 2008-07-29
I have just instaled studio but it friezes just as it is loading the login page im using a intel m/b and pci+ nvideo card
any help most apreciated.

---

### Post by PmDematagoda on 2008-07-29
> **shoey51 said:**
> I have just instaled studio but it friezes just as it is loading the login page im using a intel m/b and pci+ nvideo card
any help most apreciated.

Your problem does not seem to be related to what this thread is about, perhaps you will be better off making a new thread of your own.

Also this thread is closed, so as to prevent any further attempts at necromancy.

---

