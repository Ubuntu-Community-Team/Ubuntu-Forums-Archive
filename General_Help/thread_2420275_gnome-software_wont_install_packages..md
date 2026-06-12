---
title: "gnome-software wont install packages."
date: 2019-06-02
forum: General Help
---

### Post by aprekates2 on 2019-06-02
gnome-software wont allow me to install any software

 i get :   I cannot do this operation since I don't have permission. 

Strangely i think i didnt had this problem in the past. 

Permission was asked and i typed my passwd. 

But not now. 

Alexandros 

------------------ 

System:    Host: enous-ubuntu Kernel: 4.15.0-50-generic x86_64 bits: 64 
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.2 LTS

---

### Post by aprekates2 on 2019-06-02
Strangely   update-manager also wont work. It crashed suddenly just when it should display a dialog asking for my password. strange, what action i did could mess with two.

---

### Post by TheFu on 2019-06-02
Run these:
```
sudo apt update
sudo apt dist-upgrade
```
Those two should be run weekly to maintain any Ubuntu-based desktop or server with current patches.  Weekly backups would be good too. After the 2nd one, might need to reboot if a new kernel or new libc was installed.  The patch tools create an empty file, /var/run/reboot-required, if a reboot is needed. If it exists, reboot. If it doesn't, then you are patched - assuming no errors.

After the above, assuming there aren't any errors encountered, run:
```
sudo apt install {name of the package}
```
I don't have a package available called "gnome-software", so perhaps the package name is wrong?

If you need a GUI to install, update, remove software, then run **sudo -H synaptic**.  The -H option is VERY important. May need to install synaptic.

Every few weeks, you might want to clean up old packages that aren't used anymore.
```
sudo apt autoremove
sudo apt autoclean
```

---

