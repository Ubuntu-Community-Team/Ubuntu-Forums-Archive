---
title: "I broke it..."
date: 2007-10-31
forum: General Help
---

### Post by jamison on 2007-10-31
This is a copy of a post I amde some where else

Ok, first what I did.

- I could not run Azureus and I thought that the problem might have to do with improperly loaded Java.
   -So, I went into the package manager (packet manager?), searched Java and deleted permanently every file that showed up, hoping to get a fresh start. While the files were being removed, my computer start to act funny and all the other currently running problems became inaccessible due to some error. (I forgot what it said…sorry)
   -I tired to stop further removal to no avail and in a state of panic cut the power....
- I restarted
   - the ubuntu logo came up and ubuntu started loading but when it finished all that came up was what my very feeble mind can only describe as a DOS like ubuntu. I was asked to sign-in to a black screen and now can only access what seems to me to be very similar to the ubuntu terminal.
- I have tried
   - rebooting with cd
   - Every command I can think of (not that I ever learned any)
   - crying
- I know
   -I am a hick
Ubuntu is still loaded on the thing but it won’t run the desktop. Needless to say, I would really prefer not to reformat and if at all possible just add the missing parts from the CD.

I have another computer running windows with internet access and some CDRs.

Anyone have any ideas?

Thank you so much for your time!!

 Alex White said 7 hours ago: 
You probably removed some critical packages. If you have access to bash (the DOS-like prompt), you can run the following command to reinstall them:

sudo aptitude install ubuntu-desktop

   
 Jamison said 2 minutes ago: 
Dear Alex,

Thank you for your help!

I ran the command you suggested&#12289;but to no avail.

The machine did some install type stuff but still won’t load into the desktop

Any ideas?

 Jamison said 5 seconds ago: 
it seems I cant access archine.ubuntu.com

---

### Post by jayaramk on 2007-10-31
i say it would better be if installing the ubuntu agian!!!!

---

### Post by jamison on 2007-10-31
I cant access my cd drive even when I restart

also no internet...

Help....

---

### Post by cdenley on 2007-10-31
Did you try rebooting after installing ubuntu-desktop? What happens when you run
```

sudo /etc/init.d/gdm start

```

---

### Post by jamison on 2007-10-31
Thank you so much for your help!

but, nothing changes

it just gives me a jamison@jamison-laptop:~$ after I put in my sudo password

---

### Post by jamison on 2007-10-31
actually, i was getting a download error when I first started using ubuntu and switched to the "main server" as apposed to the one in Japan, where I am

any I idea how I can do that from the terminal?

---

### Post by cdenley on 2007-10-31
repositories are stored in /etc/apt/sources.list
```

sudo nano /etc/apt/sources.list

```

After running "/etc/init.d/gdm start", I'm pretty sure it should give you some output. Either it would say "Starting GNOME Display Manager..." or give you an error. Are you sure there wasn't any output?

> 
it seems I cant access archine.ubuntu.com

Does your sources.list file contain "archine.ubuntu.com" or "archive.ubuntu.com"?

---

### Post by PmDematagoda on 2007-10-31
Try:-

```
sudo dpkg-reconfigure xserver-xorg
```

After reconfiguration, do:-

```
startx
```

---

### Post by jamison on 2007-10-31
I ran archive.ubuntu.com and got a big list of stuff I can manipulate...

and the sever is a jp.    

sorry I ment

archive.ubuntu.com

---

### Post by jamison on 2007-10-31
I ran the xserver thing and when it was finished I got a screen with my mouse pointer but that was it....

no desktop

did i do smth wrong?

---

### Post by cdenley on 2007-10-31
That's what was supposed to happen. It means you have a working xserver. To kill it, press ctrl+alt+backspace. If you installed ubuntu-desktop without any errors, then it should have installed gdm as a dependency, which should start when your computer boots up. If the command "/etc/init.d/gdm start" doesn't give you any output, then I'm out of ideas. Maybe you can try:

```

sudo dpkg -P gdm ubuntu-desktop
sudo apt-get install gdm ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by jamison on 2007-11-01
I tried them all and i get nowhere.....

I think I deleted GPD... and my PC cannot access the ubuntu server...

How can I access files on my CD drive?

---

