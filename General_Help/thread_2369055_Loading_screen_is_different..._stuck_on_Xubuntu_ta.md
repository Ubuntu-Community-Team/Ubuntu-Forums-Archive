---
title: "Loading screen is different... stuck on Xubuntu takes ages to boot"
date: 2017-08-18
forum: General Help
---

### Post by fiddybux on 2017-08-18
I have been exploring different desktop environments, and decided I want to stop using Xubuntu and go back to Ubuntu (default)?

I did some research and used:

```
sudo apt remove --purge Xubuntu
```

Sure enough, this got rid of Xubuntu from the desktop selector on the login screen, but now when I shutdown or startup I still get the Xubuntu loading screen (blue) and it seems to take a very long time to get to the login screen.

After this it's fine, so maybe it's just cosmetic, but I would like it back how it was with the orange Ubuntu loading screen.

Can someone help please?

Thanks.

---

### Post by westie457 on 2017-08-18
Hi, firstly do not be surprised if you have to do a clean installation. Personally I have always found reverting a Desktop problematic (somethings work, others don't).
Do you have your files backed up? If not, do so now.
Once the back up is done run these. Some are not strictly necessary but I run them anyway.```
sudo apt update
sudo apt remove --purge xubuntu-desktop
sudo apt install --reinstall ubuntu-desktop && sudo apt install --reinstall unity
sudo apt upgrade
sudo update-grub
reboot
```When the system is running again ```
sudo apt clean
sudo apt autoclean
sudo apt autoremove
```
Hopefully with fingers and toes crossed you should be back to Ubuntu with Unity and the associated loading screen.

Just to repeat the opening statement, 'things can go wrong so be prepared to do a fresh installation'.

Good luck.

---

### Post by fiddybux on 2017-08-18
> **westie457 said:**
> 
Just to repeat the opening statement, 'things can go wrong so be prepared to do a fresh installation'.

Good luck.

Hi,

I managed to fix the loading screen with:

```

sudo update-alternatives --config default.plymouth

sudo update-initramfs -u

```

...and chose the correct option.

There was a load of xubuntu stuff in there, which I might see if I can remove first.

It still takes ages to load though, even though I have the right plain Ubuntu loading screen now. Maybe a loop until a timeout?

If my other efforts fail, will your suggestions leave my /home intact? This is all I really care about TBH.

Thanks.

---

### Post by fiddybux on 2017-08-18
Well, I've done all this now. My own efforts, and your suggested solution...and whilst Xubuntu is gone, and I haven't lost anything, it's still slow to boot. It's taking about 10 times longer than normal.

Any further ideas please?

Thanks.

---

### Post by VMC on 2017-08-18
Maybe this terminal command will shed some light:
```
systemd-analyze blame
```

---

### Post by fiddybux on 2017-08-18
> **VMC said:**
> Maybe this terminal command will shed some light:
```
systemd-analyze blame
```

Thanks, I've actually solved it now. I had a UUID mismatch - my swap wasn't being used, so during boot it was searching and timing out.

I just:

```
sudo gedit /etc/fstab
```

Then compared the UUID for my swap partition with the same in gparted (for me /dev/sda2). 

I edited /etc/fstab to match the UUID shown in gparted for my swap partition, and ran (for good measure):

```
sudo update-grub
```

Rebooted and now I'm back to a 7 second boot! Hurrah! :D

Out of interest, what does this do?

```
systemd-analyze blame
```

I ran it and it showed me a list of processes, but it didn't make much more sense to me than that.

Thanks for trying to assist me!

---

### Post by VMC on 2017-08-18
It lists which systemd unit finished in how much time.

---

### Post by fiddybux on 2017-08-18
> **VMC said:**
> It lists which systemd unit finished in how much time.

Well I can see how that would be useful. Thanks for your support.

---

