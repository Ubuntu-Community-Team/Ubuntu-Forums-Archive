---
title: "Ubuntu 17.10 Where did my Hard drives go?"
date: 2017-10-22
forum: General Help
---

### Post by johnstefnds on 2017-10-22
I just upgraded to 17.10 from 17.04 and  I was unpleasantly surprised with the new gnome shellwhatever 

Anyway one of my main problems is that the Dock doesnt have my mounted drives (including internal harddrives) available and I did not find an option on settings or gnome tweaks...

I only can have them on my dekstop but I dont like that...


Bonus question: are all alternative themes/shells for 16.10 compatible with 17.10? because for most of them I find download links for up to version 16.10

---

### Post by Dennis N on 2017-10-22
Install extension "Removable Drive Menu" and see if that works for you.

---

### Post by Kris_M on 2017-10-22
gnome tweaks / desktop / mounted volumes?
sorry didn't answer your question - I realize I've always used window-list extension in 17.  I have always gotten my other partitions from Nautilus.

---

### Post by johnstefnds on 2017-10-22
> **Dennis N said:**
> Install extension "Removable Drive Menu" and see if that works for you.

It doesnt work for me since it only displays already mounted drivers... So I again have to open nautilus go to other drivers and open them there in order for them to be available in that extension... I really cant understand whats in people's minds when they are doing this... they also removed the trashcan you cant select to put the "show applications" icon on the top of the dock or the time to be not on the center of the top dock... those things to me seem very doable and very obvious to have.. and they already existed in the previous verysion! anyway...

---

### Post by Dennis N on 2017-10-22
I am using the removable drive menu to handle USB drives I plug in and remove while working. My second internal hard drive I use for data storage is mounted automatically at startup with an entry in /etc/fstab file. If you want internal hard drives mounted automatically when you log in, you should be using /etc/fstab to handle that if you are not already doing so.

---

### Post by johnstefnds on 2017-10-22
> **Dennis N said:**
> I am using the removable drive menu to handle USB drives I plug in and remove while working. My second internal hard drive I use for data storage is mounted automatically at startup with an entry in /etc/fstab file. If you want internal hard drives mounted automatically when you log in, you should be using /etc/fstab to handle that if you are not already doing so.

No I should not thats why I am so grumpy... in ALL the previous versions in ubuntu you could have all your disks (mounted or not) on your dock (you also could remove them if you didnt like them there)

And also the disks prog had a simple graphical trigger on/off for setting the disk to automount on startup... ubuntu 17.10 has **neither** and I really cant understand why... it serves no purpose to remove all those functions...

But obviously I have nothing against you I am just frustrated and grouch online as a result, thanks a lot for the advice.

---

### Post by eruby-knowledgematters on 2017-12-18
```
sudo apt install gnome-tweak-tool
gnome-tweak-tool
```

Desktop > Mounted Volumes > Off

---

### Post by stuwbjornin on 2018-01-27
So, I'm still fairly new to Ubuntu. Is it possible to put my internal drives on the dock or not?

This is the only thread I can find about this. After installing Gnome Tweak Tool and reading up on /etc/fstab files I am no closer to understanding if I can have the drives show up in dock or not. Much less on how to make it happen if it's possible.

---

### Post by deadflowr on 2018-01-27
Kind of an older discussion on that here:
[https://community.ubuntu.com/t/why-removable-device-menu-not-default/938/7]("https://community.ubuntu.com/t/why-removable-device-menu-not-default/938/7")

---

