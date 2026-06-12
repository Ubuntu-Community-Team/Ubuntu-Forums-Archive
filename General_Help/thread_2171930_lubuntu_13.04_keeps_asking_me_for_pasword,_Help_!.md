---
title: "lubuntu 13.04 keeps asking me for pasword, Help !"
date: 2013-09-02
forum: General Help
---

### Post by abati2 on 2013-09-02
so guys,

im new to this, just installed lubuntu 13.04 and performed some updates through the software updater.

the problem is each time i want to install a programm from the lubuntu software center, it asks me for a pasword and thats not the only thing,
even if i want to acces my drive partition which are 2 partition (ntfs) it asks me for a pasword. 

This is annoying is there a way to disable it guyz ?

---

### Post by Impavidus on 2013-09-02
You need to enter your password when installing something on every Ubuntu system. In theory you could avoid it, but this is the backbone of Linux security, so don't. Anyway, how often do you install something? When you've spend two weeks to get everything up and running you won't need to anymore.

Considering mounting your ntfs partition, create an entry in [/etc/fstab]("https://help.ubuntu.com/community/Fstab") to mount them automatically or give ordinary users permission to mount them.

For more information, read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bucky Ball on 2013-09-02
Welcome to the forums. Try this for a simple fix for NTFS:

Software Centre>install ntfs-3g and ntfs-config

You should now find the config app in your apps menu (under System probably: I don't use the Unity desktop so unsure but it will be there somewhere). Run it and choose the NTFS partitions you want mounted at boot. This will write the /etc/fstab entries for you. Reboot and the NTFS partitions should now auto-mount. Opening partitions as root is a bad idea and you definitely want to sort that out.

To mount the NTFS partition on the fly, try this (and hope it's not too in-depth for you). 

Open a terminal and create a mountpoint for the partition:

```
sudo mkdir /media/MyNTFS
```

This creates the mountpoint (directory) 'MyNTFS' in the directory /media (you can call the mountpoint what you like).

Next, run:

```
sudo blkid
```

From the output take not of the /dev/sda* of the NTFS partition. Let's say it is /dev/sda5.

Mount it in the mountpoint 'MyNTFS' with:

```
sudo mount /dev/sda5 /media/MyNTFS
```

If that didn't work you need to install ntfs-3g (you don't need ntfs-config for this bit). Take note, this only mounts on the fly and the partitions will not auto-mount on reboot. 

___

As mentioned, you need to enter a password to make changes, like installing apps. It makes you root for that command, so to speak. If you were root all the time you could do some serious breakage without even knowing it. 

In short, sudo is used in a terminal for this purpose. If you run a command and start it with 'sudo' then you are running as root *for that command only*.

sudo = SuperUser do! You are superuser (root) after a sudo command. When you put your password into a GUI you are effectively running a sudo command. For instance ...

If you wanted to install Gimp with Software Centre you would find it in there then issue your password and away you go. In the background, what is happening is what you would do in the terminal to achieve the same end. In a terminal you would issue:

```
sudo apt-get install gimp
```

'sudo' means you're root for that command;
'apt-get install' means you are about to install something;
'gimp' is the app you mean to install. 

Hope that helps. ;)

(* Just a note: imagine if you didn't need to be root to make major changes to the system. Anyone using your computer could install/remove anything, including installing the entire Ubuntu repositories (which would kill virtually any system) or deleting everything on your local machine (not just data but all essential software/dependencies/apps required to run Ubuntu itself). And that is while you're on your coffee break. :-k)

---

