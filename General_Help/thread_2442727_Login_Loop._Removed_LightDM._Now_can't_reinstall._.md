---
title: "Login Loop. Removed LightDM. Now can't reinstall. / root is Full what to do???"
date: 2020-05-07
forum: General Help
---

### Post by 777funk on 2020-05-07
I've found myself in a bit of trouble by doing the following:

1. Problem - Login Loop . Sign in and it just goes right back to the sign in screen. 

My failed attempt to fix:
1.Remove LightDM 
2.Reinstall LightDM

This fails with the error"
E: You don't have enough free space in /var/cache/apt/archives/.

So I do 
Df -H 

and can see that 
/ is at 100% of it's capacity

So what can I do? I tried booting in on a startup disc of Ubuntu 12.04 to see if I could clean things up from outside of the OS and I can't mount the /sdb/ disk (the entire drive is unmountable) that / resides on. I have cleared old kernels off and that did nothing unfortunately. 

Thanks in advance for any pointers!

---

### Post by Impavidus on 2020-05-07
Is that information about your system in the signature under your post still accurate? Because if it is, your system is severely outdated and the best thing to do would be a fresh install. If it isn't accurate, tell us a bit more about your system, like the complete output of df -h. And Ubuntu isn't installed on the sdb partition, because that's a hard drive, not a partition.

---

### Post by 777funk on 2020-05-07
Sorry! I haven't been here in a while. I have 18.04 and it's on sdb1 - 4 (/ is on sdb2 I believe and that is a 100GB partition).

---

### Post by guiverc on 2020-05-07
You cannot login via a GUI if there is insufficient space in $HOME (/home/$USER/ or your user directory) for the creation of workfiles used by your desktop. Your login will fail & you'll be instantly logged out if there is insufficient space there, which `df -h` would show (as terminal logins don't require work files, you can login there to check).  If there is no separate /home partition, it'll get stored on your / partition

Your "[COLOR=#000000]E: You don't have enough free space in /var/cache/apt/archives/." indicates you're out of space in / too (or /var if it's on it's own partition)

@[/COLOR][Impavidus]("https://ubuntuforums.org/member.php?u=1417721")[COLOR=#000000] asked for the full output of `df -h` so we could help you, we don't have it, so you'll have to evaluate the results yourself (check your /home/ and / partition(s) or any space allocation rules you have setup).  It's not the size (unless it's too small), but how much space is unused on it.[/COLOR]

---

### Post by ActionParsnip on 2020-05-07
Try:

```

sudo apt-get clean
sudo apt-get --purge autoremove
sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```

Should help. Also remove old unused kernels.

---

