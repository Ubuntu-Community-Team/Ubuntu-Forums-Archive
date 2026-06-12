---
title: "Ubuntu login loop"
date: 2022-12-16
forum: General Help
---

### Post by aashish-sharma-108 on 2022-12-16
Hi there, a noob to Ubuntu but it was working for several weeks on my HP EliteBook laptop. All of a sudden I am stuck in a login loop! Not sure what to do?

I did a search and none of the solutions work. I did the apt updatea/upgrades etc. There is no Xauthority file forme to change also. 

My Ubuntu version is 22.10.

Any help much appreciated! 

Cheers.

---

### Post by ajgreeny on 2022-12-16
The .Xauthority file that you say does not exist is hidden by default (the . at the start of the name hides files from view) but you can see all the hidden files and folders by hitting Ctrl+H when in your file manager.

However, if you are using wayland graphics which is the default in the latest versions of the main Ubuntu system rather than the older Xorg/X11 I wonder if the .Xauthority file is missing in your home.

---

### Post by aashish-sharma-108 on 2022-12-16
I'm not an expert but I did see all hidden files and no Xauthority file anywhere and Wayland does not use such files?

If it does, how to get it back? Not sure how it vanished.

---

### Post by ajgreeny on 2022-12-16
I'm sorry but I do not know if wayland graphics need or use that .Xauthority file because using Xubuntu does not give me a chance to use wayland and find out but from its name I assume it is superfluous in wayland.

Try logging in to an xorg session from the login screen.
After filling in your passsword but before hitting Enter or clicking the login button change from whatever the current session is to Ubuntu Xorg (I don't remember how it's named but it should be obvious) to see if that session works for you.

If you are able to login to that session use it in future while you do some more investigation of the problem you currently have. By default Ubuntu will login to the session last chosen so once you have chosen xorg that will remain the default until you change back to wayland.

---

### Post by MAFoElffen on 2022-12-16
A few things... If you press <Cntrl><Alt><F4> and log in
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah ~/ | grep "X"
-rw-------  1 mafoelffen mafoelffen   64 Dec 15 11:42 .Xauthority

```
Output like that would tell if the ~/.Xauthority file exists, has permissions of 600 (owner r/w) and is owned by the user and the user's group...

Next, sometimes it's a /tmp folder permissions problem
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah /tmp | head -n 2
total 100K
drwxrwxrwt 22 root       root        12K Dec 16 10:15 .

```
Should be owned by root:root, and permissions of 1777... If not, then when the Graphics layer tries to come up, it can't write temp files... <-- This causes a login loop with both Wayland and Xorg!

Post the results of yours first, and we will go from there.

---

### Post by #&amp;thj^% on 2022-12-16
> **MAFoElffen said:**
> 
Next, sometimes it's a /tmp folder permissions problem
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah /tmp | head -n 2
total 100K
drwxrwxrwt 22 root       root        12K Dec 16 10:15 .

```
Should be owned by root:root, and permissions of 1777... If not, then when the Graphics layer tries to come up, it can't write temp files... <-- This causes a login loop with both Wayland and Xorg!

Post the results of yours first, and we will go from there.

+1
I just use:
```
stat /tmp && ls -lah /tmp | head -n 2
  File: /tmp
  Size: 1250      	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 170664      Links: 1
**Access: (1777/drwxrwxrwt)  Uid: (    0/    root)   Gid: (    0/    root)**
Access: 2022-12-16 14:51:54.172384274 -0700
Modify: 2022-12-16 14:35:46.755654815 -0700
Change: 2022-12-16 14:35:46.755654815 -0700
 Birth: 2022-12-15 00:20:24.512432373 -0700
total 20K
drwxrwxrwt 1 root root 1.3K Dec 16 14:35 .

```

---

### Post by aashish-sharma-108 on 2022-12-17
Hey there, thanks for the tips.

I now see the .Xauthority file (not sure how it suddenly appeared) in my home directory and it has -rw------- permissions and is under my control (my user and usergroup which is aashish108:aashish108) but it's file size is 0.

I also checked the /tmp dir and it has permissions of drwxrwxrwt and it says root:root.

So not sure what it's failing still :/

---

### Post by aashish-sharma-108 on 2022-12-17
Thanks for that, tried it but still fails.

---

### Post by #&amp;thj^% on 2022-12-17
My only suggestion here is first have good back-ups, and just reinstall your session IE
```
sudo apt install --reinstall ubuntu-desktop
```
That is for Gnome only.
If that fails this usually works for me **but your mileage may vary**:
```
sudo apt remove ubuntu-desktop
sudo apt autoremove
```
If you have other Desktop versions installed you may have to remove those as well. (Plasma XFCE Mate)
Now install again
```
sudo apt install ubuntu-desktop
```
You need to reboot after.

---

### Post by aashish-sharma-108 on 2022-12-17
> **1fallen said:**
> My only suggestion here is first have good back-ups, and just reinstall your session IE
```
sudo apt install --reinstall ubuntu-desktop
```
That is for Gnome only.
If that fails this usually works for me **but your mileage may vary**:
```
sudo apt remove ubuntu-desktop
sudo apt autoremove
```
If you have other Desktop versions installed you may have to remove those as well. (Plasma XFCE Mate)
Now install again
```
sudo apt install ubuntu-desktop
```
You need to reboot after.

Thanks for the help. I did all this and still the same issue! I'm afraid I may have to reinstall the OS.

Is this an Ubuntu issue? If that's the case maybe I should try another distro? I came to escape Windows on my laptop but this issue just disables my laptop and research has proven ineffective. All the common reasons and their solutions have been tried.

What happened is that the laptops battery died while it was in sleep mode. Not sure what issue that would have caused.

:(

---

### Post by aashish-sharma-108 on 2022-12-17
Is this one of those Gnome sometimes breaking on update or something? I remember doing some apt update commands or similar. If so, would XFCE or KDE be a better choice?

---

### Post by #&amp;thj^% on 2022-12-17
> **aashish-sharma-108 said:**
> 
What happened is that the laptops battery died while it was in sleep mode. Not sure what issue that would have caused.

:(
That could possibly be what corrupted the normal login process.

> **aashish-sharma-108 said:**
> 
Is this an Ubuntu issue? If that's the case maybe I should try another distro?

Usually a power disruption is handled ok, but other times it just leaves something absent in a pristine install on any Linux OS.
They have a specific way of waking, login and logout, shutdown, restart yada yada .
I can't advise you to try another distro, solely your choice on that. :)

---

### Post by MAFoElffen on 2022-12-17
Can you boot on a LiveCD and see the data on your drives? If you do not have a recent backup, I would try that first, to backup anything important before the reinstall.

On sleep and hibernation's, yes. That makes sense now. On your new install, you may want to modify your sleep and hibernation settings to something a bit more conservative.

---

### Post by aashish-sharma-108 on 2022-12-17
> **MAFoElffen said:**
> Can you boot on a LiveCD and see the data on your drives? If you do not have a recent backup, I would try that first, to backup anything important before the reinstall.

On sleep and hibernation's, yes. That makes sense now. On your new install, you may want to modify your sleep and hibernation settings to something a bit more conservative.

I was able to create a new user and login successfully though. But I doubt that info will help narrow the issue down other than the fact that some config is gone bad! A reinstall is a last resort tbh, such a hassle.

I believe this issue can happen to any distro, right?

---

### Post by #&amp;thj^% on 2022-12-17
> **aashish-sharma-108 said:**
> 
I believe this issue can happen to any distro, right?

Absolutely.

---

### Post by MAFoElffen on 2022-12-17
If you created another user and that user is fine... Then it is your ~/.Xauthority file that is corrupt or boinked in some way...
```

rm ~/.Xauthority
touch ~/.Xauthority
chown $USER:$USER ~/.Xauthority
chmod 600 ~/.Xauthority
sudo chown -R $USER:$USER $HOME/

```

---

### Post by aashish-sharma-108 on 2022-12-18
> **MAFoElffen said:**
> If you created another user and that user is fine... Then it is your ~/.Xauthority file that is corrupt or boinked in some way...
```

rm ~/.Xauthority
touch ~/.Xauthority
chown $USER:$USER ~/.Xauthority
chmod 600 ~/.Xauthority
sudo chown -R $USER:$USER $HOME/

```

The thing is I tried renaming that file to see what happens after a reboot but the same issue occurs. Not sure how to fix the issue with that file, assuming that's it.

---

### Post by aashish-sharma-108 on 2022-12-18
> **MAFoElffen said:**
> If you created another user and that user is fine... Then it is your ~/.Xauthority file that is corrupt or boinked in some way...
```

rm ~/.Xauthority
touch ~/.Xauthority
chown $USER:$USER ~/.Xauthority
chmod 600 ~/.Xauthority
sudo chown -R $USER:$USER $HOME/

```

I tried that code block you sent and still the same issue unfortunately :(

---

### Post by #&amp;thj^% on 2022-12-18
Instead of using:
```
chown $USER:$USER ~/.Xauthority
sudo chown -R $USER:$USER $HOME/
```
replace "$USER:$USER" with your original user name, it's worth a shot. I've seen stranger things work.

---

### Post by aashish-sharma-108 on 2022-12-18
Thanks for all the help everyone, I gave up and reinstalled the OS. This time I am trying Xubuntu. I did some research and Ubuntu/Gnome/GDE sometimes came up together with login loop. I'm hoping the journey will be a lot smoother with XFCE!

It's strange, I have never come across a bug on Windows or Mac that disables your laptop. It's bugs like these that prevents Linux from going more mainstream.

---

### Post by #&amp;thj^% on 2022-12-18
> **aashish-sharma-108 said:**
> Thanks for all the help everyone, I gave up and reinstalled the OS. This time I am trying Xubuntu. I did some research and Ubuntu/Gnome/GDE sometimes came up together with login loop. I'm hoping the journey will be a lot smoother with XFCE!



+1 Big XFCE4 fan here as well.
> **aashish-sharma-108 said:**
> 
It's strange, I have never come across a bug on Windows or Mac that disables your laptop. It's bugs like these that prevents Linux from going more mainstream.
Well we can't gripe about the monetary cost, but Yes I can see where this would leave someone in doubt.
It's us old geeky farts that just push forward. Hope this one is a smoother experience for you. :)

---

### Post by dragonfly41 on 2022-12-18
As a learning (forensic) exercise you could use Meld to compare various selected folder/files in

working user session
failed user session

---

