---
title: "screensaver broken"
date: 2007-08-08
forum: General Help
---

### Post by patmalcolm91 on 2007-08-08
my screensaver recently broke. when i try to lock the screen, a window pops up that says:

Error while running command
** Message: Screensaver is not running!

does anyone know how to fix this??? it's really annoying not being able to lock my screen!

---

### Post by tszanon on 2007-08-08
> **patmalcolm91 said:**
> my screensaver recently broke. when i try to lock the screen, a window pops up that says:

Error while running command
** Message: Screensaver is not running!

does anyone know how to fix this??? it's really annoying not being able to lock my screen!
Never seen anything like this, but let's see. Have you tried:
1. restarting GDM (CTRL + ALT + Backspace)?
2. rebooting?
3. checking if gnome-screensaver is installed?
4. reinstalling gnome-screensaver?
5. changing the screensaver in System > Preferences > Screen saver?

What else...I'm gonna think about it.

---

### Post by patmalcolm91 on 2007-08-08
Ya, i've tried all these. I rebooted, nothing, restarted GDM, nothing. i know gnome-screensaver is installed because it worked fine before, but i reinstalled it, still nothing. the only thing i really did between the last time i used the screensaver and when it stopped working was trying to get my bluetooth to work, i typed a command i found on this forum, "sudo lsusb -v|grep -i bluetooth" that's the only thing i think it could have anything to do with..

---

### Post by tszanon on 2007-08-08
> **patmalcolm91 said:**
> sudo lsusb -v|grep -i bluetooth"
It surely didn't brake the screensaver, since it just prints some information. Try this in the Terminal:
```
ps ax|grep screensaver
```
It should show you anything besides "grep screensaver", indicating that gnome-screensaver is running. If it's not, then there's something that's stopping it from running. When I get home I'm gonna check out how to make it run on demand.

---

### Post by patmalcolm91 on 2007-08-08
I tried that and i got this:

xxx@xxx:~$ ps ax|grep screensaver
16839 pts/0    R+     0:00 grep screensaver

i'm not sure what it means.. thanks for the help, i had no idea where to start w/ this

---

### Post by tszanon on 2007-08-08
> **patmalcolm91 said:**
> I tried that and i got this:

xxx@xxx:~$ ps ax|grep screensaver
16839 pts/0    R+     0:00 grep screensaver

i'm not sure what it means.. thanks for the help, i had no idea where to start w/ this
It means that gnome-screensaver is not running, because it didn't appear as it does here:
```
5657 ?        Ss     0:59 gnome-screensaver
26876 pts/2    R+     0:00 grep screensaver
```
So let's make some tests. Try running this:
```
gnome-screensaver
ps ax|grep screensaver
```
Now it should look like I said above, but I believe it does not solve the issue yet. If any error message appears after running gnome-screensaver, please paste it here. The purpose of this test is to know if gnome-screensaver is failing to run.

If there are no errors, please try to lock the screen and tell me if it works.

---

### Post by patmalcolm91 on 2007-08-08
patrick@malcolm-laptop:~$ gnome-screensaver
The program 'gnome-screensaver' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-screensaver
bash: gnome-screensaver: command not found
patrick@malcolm-laptop:~$ sudo apt-get install gnome-screensaver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-screensaver is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
patrick@malcolm-laptop:~$ ps ax|grep screensaver
 6221 pts/0    R+     0:00 grep screensaver
patrick@malcolm-laptop:~$ 

when i try to run gnome-screensaver it tells me it's not installed, but when i install it, it says i already have it... anything?

---

### Post by tszanon on 2007-08-09
> **patmalcolm91 said:**
> patrick@malcolm-laptop:~$ gnome-screensaver
The program 'gnome-screensaver' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-screensaver
[COLOR="Red"]bash: gnome-screensaver: command not found[/COLOR]

when i try to run gnome-screensaver it tells me it's not installed, but when i install it, it says i already have it... anything?
Somehow, it didn't find the program. Let's look for it. You can use the Search function in Gnome (I think it's in Places > Search for files or something like that) or you can type in the Terminal:
```
find / -iname gnome-screensaver
```
You can also try
```
whereis gnome-screensaver
```
because it will find it if it's in any folder featured in $PATH. Hmm...just had another idea: please post the output of
```
echo $PATH
```

---

### Post by patmalcolm91 on 2007-08-09
patrick@malcolm-laptop:~$ find / -iname gnome-screensaver
/etc/pam.d/gnome-screensaver
find: /etc/ssl/private: Permission denied
find: /etc/cups/ssl: Permission denied
find: /home/mary/.beagle: Permission denied
find: /home/mary/.Trash: Permission denied
find: /home/mary/.mozilla: Permission denied
find: /home/mary/.config: Permission denied
find: /home/mary/.gnome2: Permission denied
find: /home/mary/.local: Permission denied
find: /home/mary/.gconf: Permission denied
find: /home/mary/.thumbnails: Permission denied
find: /home/mary/.openoffice.org2: Permission denied
find: /home/mary/.nautilus/metafiles: Permission denied
find: /home/mary/.gconfd: Permission denied
find: /home/mary/.gnome2_private: Permission denied
find: /home/mary/.metacity: Permission denied
/home/patrick/.gconf/apps/gnome-screensaver
/usr/lib/gnome-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver
/usr/share/doc/gnome-screensaver
/usr/share/gnome-screensaver
find: /lost+found: Permission denied
find: /var/spool/cron/crontabs: Permission denied
find: /var/spool/cron/atjobs: Permission denied
find: /var/spool/cron/atspool: Permission denied
find: /var/spool/postfix/incoming: Permission denied
find: /var/spool/postfix/private: Permission denied
find: /var/spool/postfix/bounce: Permission denied
find: /var/spool/postfix/maildrop: Permission denied
find: /var/spool/postfix/saved: Permission denied
find: /var/spool/postfix/defer: Permission denied
find: /var/spool/postfix/public: Permission denied
find: /var/spool/postfix/corrupt: Permission denied
find: /var/spool/postfix/flush: Permission denied
find: /var/spool/postfix/deferred: Permission denied
find: /var/spool/postfix/trace: Permission denied
find: /var/spool/postfix/hold: Permission denied
find: /var/spool/postfix/active: Permission denied
find: /var/spool/mqueue: Permission denied
find: /var/spool/exim4: Permission denied
find: /var/spool/cups: Permission denied
find: /var/run/wpa_supplicant: Permission denied
find: /var/run/cups/certs: Permission denied
find: /var/lib/gdm: Permission denied
find: /var/lib/fetchmail: Permission denied
find: /var/lib/slocate: Permission denied
find: /var/log/samba/cores: Permission denied
find: /var/cache/beagle/.gnome2: Permission denied
find: /var/cache/beagle/.gconf: Permission denied
find: /var/cache/beagle/.gconfd: Permission denied
find: /var/cache/system-tools-backends/backup: Permission denied
find: /root/.synaptic: Permission denied
find: /root/.Trash: Permission denied
find: /root/.aptitude: Permission denied
find: /root/.gnupg: Permission denied
find: /root/.config: Permission denied
find: /root/.gnome2: Permission denied
find: /root/.gconf: Permission denied
find: /root/.thumbnails: Permission denied
find: /root/.nautilus/metafiles: Permission denied
find: /root/.gconfd: Permission denied
find: /root/.gnome2_private: Permission denied
find: /proc/bus/usb/.usbfs/005: Permission denied
find: /proc/bus/usb/.usbfs/004: Permission denied
find: /proc/bus/usb/.usbfs/003: Permission denied
find: /proc/bus/usb/.usbfs/002: Permission denied
find: /proc/bus/usb/.usbfs/001: Permission denied
find: /proc/tty/driver: Permission denied
find: /proc/1/task/1/fd: Permission denied
find: /proc/1/fd: Permission denied
find: /proc/2/task/2/fd: Permission denied
find: /proc/2/fd: Permission denied
find: /proc/3/task/3/fd: Permission denied
find: /proc/3/fd: Permission denied
find: /proc/4/task/4/fd: Permission denied
find: /proc/4/fd: Permission denied
find: /proc/5/task/5/fd: Permission denied
find: /proc/5/fd: Permission denied
find: /proc/6/task/6/fd: Permission denied
find: /proc/6/fd: Permission denied
find: /proc/7/task/7/fd: Permission denied
find: /proc/7/fd: Permission denied
find: /proc/30/task/30/fd: Permission denied
find: /proc/30/fd: Permission denied
find: /proc/31/task/31/fd: Permission denied
find: /proc/31/fd: Permission denied
find: /proc/32/task/32/fd: Permission denied
find: /proc/32/fd: Permission denied
find: /proc/154/task/154/fd: Permission denied
find: /proc/154/fd: Permission denied
find: /proc/175/task/175/fd: Permission denied
find: /proc/175/fd: Permission denied
find: /proc/176/task/176/fd: Permission denied
find: /proc/176/fd: Permission denied
find: /proc/177/task/177/fd: Permission denied
find: /proc/177/fd: Permission denied
find: /proc/178/task/178/fd: Permission denied
find: /proc/178/fd: Permission denied
find: /proc/1990/task/1990/fd: Permission denied
find: /proc/1990/fd: Permission denied
find: /proc/1991/task/1991/fd: Permission denied
find: /proc/1991/fd: Permission denied
find: /proc/2025/task/2025/fd: Permission denied
find: /proc/2025/fd: Permission denied
find: /proc/2112/task/2112/fd: Permission denied
find: /proc/2112/fd: Permission denied
find: /proc/2113/task/2113/fd: Permission denied
find: /proc/2113/fd: Permission denied
find: /proc/2162/task/2162/fd: Permission denied
find: /proc/2162/fd: Permission denied
find: /proc/2163/task/2163/fd: Permission denied
find: /proc/2163/fd: Permission denied
find: /proc/2189/task/2189/fd: Permission denied
find: /proc/2189/fd: Permission denied
find: /proc/2336/task/2336/fd: Permission denied
find: /proc/2336/fd: Permission denied
find: /proc/2542/task/2542/fd: Permission denied
find: /proc/2542/fd: Permission denied
find: /proc/3413/task/3413/fd: Permission denied
find: /proc/3413/fd: Permission denied
find: /proc/3415/task/3415/fd: Permission denied
find: /proc/3415/fd: Permission denied
find: /proc/3584/task/3584/fd: Permission denied
find: /proc/3584/fd: Permission denied
find: /proc/4236/task/4236/fd: Permission denied
find: /proc/4236/fd: Permission denied
find: /proc/4237/task/4237/fd: Permission denied
find: /proc/4237/fd: Permission denied
find: /proc/4242/task/4242/fd: Permission denied
find: /proc/4242/fd: Permission denied
find: /proc/4243/task/4243/fd: Permission denied
find: /proc/4243/fd: Permission denied
find: /proc/4244/task/4244/fd: Permission denied
find: /proc/4244/fd: Permission denied
find: /proc/4245/task/4245/fd: Permission denied
find: /proc/4245/fd: Permission denied
find: /proc/4371/task/4371/fd: Permission denied
find: /proc/4371/fd: Permission denied
find: /proc/4634/task/4634/fd: Permission denied
find: /proc/4634/fd: Permission denied
find: /proc/4665/task/4665/fd: Permission denied
find: /proc/4665/fd: Permission denied
find: /proc/4667/task/4667/fd: Permission denied
find: /proc/4667/fd: Permission denied
find: /proc/4689/task/4689/fd: Permission denied
find: /proc/4689/fd: Permission denied
find: /proc/4705/task/4705/fd: Permission denied
find: /proc/4705/fd: Permission denied
find: /proc/4706/task/4706/fd: Permission denied
find: /proc/4706/fd: Permission denied
find: /proc/4712/task/4712/fd: Permission denied
find: /proc/4712/fd: Permission denied
find: /proc/4714/task/4714/fd: Permission denied
find: /proc/4714/fd: Permission denied
find: /proc/4715/task/4715/fd: Permission denied
find: /proc/4715/fd: Permission denied
find: /proc/4716/task/4716/fd: Permission denied
find: /proc/4716/fd: Permission denied
find: /proc/4717/task/4717/fd: Permission denied
find: /proc/4717/fd: Permission denied
find: /proc/4718/task/4718/fd: Permission denied
find: /proc/4718/fd: Permission denied
find: /proc/4728/task/4728/fd: Permission denied
find: /proc/4728/fd: Permission denied
find: /proc/4741/task/4741/fd: Permission denied
find: /proc/4741/fd: Permission denied
find: /proc/4756/task/4756/fd: Permission denied
find: /proc/4756/task/4769/fd: Permission denied
find: /proc/4756/task/4790/fd: Permission denied
find: /proc/4756/task/5628/fd: Permission denied
find: /proc/4756/fd: Permission denied
find: /proc/4774/task/4774/fd: Permission denied
find: /proc/4774/fd: Permission denied
find: /proc/4775/task/4775/fd: Permission denied
find: /proc/4775/fd: Permission denied
find: /proc/4791/task/4791/fd: Permission denied
find: /proc/4791/fd: Permission denied
find: /proc/4807/task/4807/fd: Permission denied
find: /proc/4807/fd: Permission denied
find: /proc/4808/task/4808/fd: Permission denied
find: /proc/4808/fd: Permission denied
find: /proc/4855/task/4855/fd: Permission denied
find: /proc/4855/fd: Permission denied
find: /proc/4858/task/4858/fd: Permission denied
find: /proc/4858/fd: Permission denied
find: /proc/4861/task/4861/fd: Permission denied
find: /proc/4861/fd: Permission denied
find: /proc/4943/task/4943/fd: Permission denied
find: /proc/4943/fd: Permission denied
find: /proc/4944/task/4944/fd: Permission denied
find: /proc/4944/fd: Permission denied
find: /proc/4956/task/4956/fd: Permission denied
find: /proc/4956/fd: Permission denied
find: /proc/5015/task/5015/fd: Permission denied
find: /proc/5015/fd: Permission denied
find: /proc/5111/task/5111/fd: Permission denied
find: /proc/5111/fd: Permission denied
find: /proc/5125/task/5125/fd: Permission denied
find: /proc/5125/fd: Permission denied
find: /proc/5147/task/5147/fd: Permission denied
find: /proc/5147/fd: Permission denied
find: /proc/5172/task/5172/fd: Permission denied
find: /proc/5172/fd: Permission denied
find: /proc/5255/task/5255/fd: Permission denied
find: /proc/5255/fd: Permission denied
find: /proc/5273/task/5273/fd: Permission denied
find: /proc/5273/fd: Permission denied
find: /proc/5310/task/5310/fd: Permission denied
find: /proc/5310/fd: Permission denied
find: /proc/5352/task/5352/fd: Permission denied
find: /proc/5352/fd: Permission denied
find: /proc/5537/task/5537/fd: Permission denied
find: /proc/5537/fd: Permission denied
find: /proc/5620/task/5620/fd: Permission denied
find: /proc/5620/fd: Permission denied
find: /proc/5689/task/5689/fd: Permission denied
find: /proc/5689/fd: Permission denied
find: /proc/5844/task/5844/fd: Permission denied
find: /proc/5844/fd: Permission denied
find: /proc/5845/task/5845/fd: Permission denied
find: /proc/5845/fd: Permission denied
find: /proc/5903/task/5903/fd: Permission denied
find: /proc/5903/fd: Permission denied
find: /proc/5974/task/5974/fd: Permission denied
find: /proc/5974/fd: Permission denied
find: /proc/6000/task/6000/fd: Permission denied
find: /proc/6000/fd: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
patrick@malcolm-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


there's the search and the echo $PATH, as for what any of it means, i don't know. thanks for all the help, it's great having someone who knows what their doing!

---

### Post by Troubled on 2007-08-09
patmalcolm91, you're having problems with the search because you're not running it as root.
You can try placing "sudo" in front of your commands to run as root, or alternatively, use:

```
locate gnome-screensaver
```

---

### Post by tszanon on 2007-08-09
> **patmalcolm91 said:**
> ```
patrick@malcolm-laptop:~$ find / -iname gnome-screensaver
/etc/pam.d/gnome-screensaver
find: /etc/ssl/private: Permission denied
find: /etc/cups/ssl: Permission denied
find: /home/mary/.beagle: Permission denied
find: /home/mary/.Trash: Permission denied
find: /home/mary/.mozilla: Permission denied
find: /home/mary/.config: Permission denied
find: /home/mary/.gnome2: Permission denied
find: /home/mary/.local: Permission denied
find: /home/mary/.gconf: Permission denied
find: /home/mary/.thumbnails: Permission denied
find: /home/mary/.openoffice.org2: Permission denied
find: /home/mary/.nautilus/metafiles: Permission denied
find: /home/mary/.gconfd: Permission denied
find: /home/mary/.gnome2_private: Permission denied
find: /home/mary/.metacity: Permission denied
/home/patrick/.gconf/apps/gnome-screensaver
/usr/lib/gnome-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver
/usr/share/doc/gnome-screensaver
/usr/share/gnome-screensaver
find: /lost+found: Permission denied
find: /var/spool/cron/crontabs: Permission denied
find: /var/spool/cron/atjobs: Permission denied
find: /var/spool/cron/atspool: Permission denied
find: /var/spool/postfix/incoming: Permission denied
find: /var/spool/postfix/private: Permission denied
find: /var/spool/postfix/bounce: Permission denied
find: /var/spool/postfix/maildrop: Permission denied
find: /var/spool/postfix/saved: Permission denied
find: /var/spool/postfix/defer: Permission denied
find: /var/spool/postfix/public: Permission denied
find: /var/spool/postfix/corrupt: Permission denied
find: /var/spool/postfix/flush: Permission denied
find: /var/spool/postfix/deferred: Permission denied
find: /var/spool/postfix/trace: Permission denied
find: /var/spool/postfix/hold: Permission denied
find: /var/spool/postfix/active: Permission denied
find: /var/spool/mqueue: Permission denied
find: /var/spool/exim4: Permission denied
find: /var/spool/cups: Permission denied
find: /var/run/wpa_supplicant: Permission denied
find: /var/run/cups/certs: Permission denied
find: /var/lib/gdm: Permission denied
find: /var/lib/fetchmail: Permission denied
find: /var/lib/slocate: Permission denied
find: /var/log/samba/cores: Permission denied
find: /var/cache/beagle/.gnome2: Permission denied
find: /var/cache/beagle/.gconf: Permission denied
find: /var/cache/beagle/.gconfd: Permission denied
find: /var/cache/system-tools-backends/backup: Permission denied
find: /root/.synaptic: Permission denied
find: /root/.Trash: Permission denied
find: /root/.aptitude: Permission denied
find: /root/.gnupg: Permission denied
find: /root/.config: Permission denied
find: /root/.gnome2: Permission denied
find: /root/.gconf: Permission denied
find: /root/.thumbnails: Permission denied
find: /root/.nautilus/metafiles: Permission denied
find: /root/.gconfd: Permission denied
find: /root/.gnome2_private: Permission denied
find: /proc/bus/usb/.usbfs/005: Permission denied
find: /proc/bus/usb/.usbfs/004: Permission denied
find: /proc/bus/usb/.usbfs/003: Permission denied
find: /proc/bus/usb/.usbfs/002: Permission denied
find: /proc/bus/usb/.usbfs/001: Permission denied
find: /proc/tty/driver: Permission denied
find: /proc/1/task/1/fd: Permission denied
find: /proc/1/fd: Permission denied
find: /proc/2/task/2/fd: Permission denied
find: /proc/2/fd: Permission denied
find: /proc/3/task/3/fd: Permission denied
find: /proc/3/fd: Permission denied
find: /proc/4/task/4/fd: Permission denied
find: /proc/4/fd: Permission denied
find: /proc/5/task/5/fd: Permission denied
find: /proc/5/fd: Permission denied
find: /proc/6/task/6/fd: Permission denied
find: /proc/6/fd: Permission denied
find: /proc/7/task/7/fd: Permission denied
find: /proc/7/fd: Permission denied
find: /proc/30/task/30/fd: Permission denied
find: /proc/30/fd: Permission denied
find: /proc/31/task/31/fd: Permission denied
find: /proc/31/fd: Permission denied
find: /proc/32/task/32/fd: Permission denied
find: /proc/32/fd: Permission denied
find: /proc/154/task/154/fd: Permission denied
find: /proc/154/fd: Permission denied
find: /proc/175/task/175/fd: Permission denied
find: /proc/175/fd: Permission denied
find: /proc/176/task/176/fd: Permission denied
find: /proc/176/fd: Permission denied
find: /proc/177/task/177/fd: Permission denied
find: /proc/177/fd: Permission denied
find: /proc/178/task/178/fd: Permission denied
find: /proc/178/fd: Permission denied
find: /proc/1990/task/1990/fd: Permission denied
find: /proc/1990/fd: Permission denied
find: /proc/1991/task/1991/fd: Permission denied
find: /proc/1991/fd: Permission denied
find: /proc/2025/task/2025/fd: Permission denied
find: /proc/2025/fd: Permission denied
find: /proc/2112/task/2112/fd: Permission denied
find: /proc/2112/fd: Permission denied
find: /proc/2113/task/2113/fd: Permission denied
find: /proc/2113/fd: Permission denied
find: /proc/2162/task/2162/fd: Permission denied
find: /proc/2162/fd: Permission denied
find: /proc/2163/task/2163/fd: Permission denied
find: /proc/2163/fd: Permission denied
find: /proc/2189/task/2189/fd: Permission denied
find: /proc/2189/fd: Permission denied
find: /proc/2336/task/2336/fd: Permission denied
find: /proc/2336/fd: Permission denied
find: /proc/2542/task/2542/fd: Permission denied
find: /proc/2542/fd: Permission denied
find: /proc/3413/task/3413/fd: Permission denied
find: /proc/3413/fd: Permission denied
find: /proc/3415/task/3415/fd: Permission denied
find: /proc/3415/fd: Permission denied
find: /proc/3584/task/3584/fd: Permission denied
find: /proc/3584/fd: Permission denied
find: /proc/4236/task/4236/fd: Permission denied
find: /proc/4236/fd: Permission denied
find: /proc/4237/task/4237/fd: Permission denied
find: /proc/4237/fd: Permission denied
find: /proc/4242/task/4242/fd: Permission denied
find: /proc/4242/fd: Permission denied
find: /proc/4243/task/4243/fd: Permission denied
find: /proc/4243/fd: Permission denied
find: /proc/4244/task/4244/fd: Permission denied
find: /proc/4244/fd: Permission denied
find: /proc/4245/task/4245/fd: Permission denied
find: /proc/4245/fd: Permission denied
find: /proc/4371/task/4371/fd: Permission denied
find: /proc/4371/fd: Permission denied
find: /proc/4634/task/4634/fd: Permission denied
find: /proc/4634/fd: Permission denied
find: /proc/4665/task/4665/fd: Permission denied
find: /proc/4665/fd: Permission denied
find: /proc/4667/task/4667/fd: Permission denied
find: /proc/4667/fd: Permission denied
find: /proc/4689/task/4689/fd: Permission denied
find: /proc/4689/fd: Permission denied
find: /proc/4705/task/4705/fd: Permission denied
find: /proc/4705/fd: Permission denied
find: /proc/4706/task/4706/fd: Permission denied
find: /proc/4706/fd: Permission denied
find: /proc/4712/task/4712/fd: Permission denied
find: /proc/4712/fd: Permission denied
find: /proc/4714/task/4714/fd: Permission denied
find: /proc/4714/fd: Permission denied
find: /proc/4715/task/4715/fd: Permission denied
find: /proc/4715/fd: Permission denied
find: /proc/4716/task/4716/fd: Permission denied
find: /proc/4716/fd: Permission denied
find: /proc/4717/task/4717/fd: Permission denied
find: /proc/4717/fd: Permission denied
find: /proc/4718/task/4718/fd: Permission denied
find: /proc/4718/fd: Permission denied
find: /proc/4728/task/4728/fd: Permission denied
find: /proc/4728/fd: Permission denied
find: /proc/4741/task/4741/fd: Permission denied
find: /proc/4741/fd: Permission denied
find: /proc/4756/task/4756/fd: Permission denied
find: /proc/4756/task/4769/fd: Permission denied
find: /proc/4756/task/4790/fd: Permission denied
find: /proc/4756/task/5628/fd: Permission denied
find: /proc/4756/fd: Permission denied
find: /proc/4774/task/4774/fd: Permission denied
find: /proc/4774/fd: Permission denied
find: /proc/4775/task/4775/fd: Permission denied
find: /proc/4775/fd: Permission denied
find: /proc/4791/task/4791/fd: Permission denied
find: /proc/4791/fd: Permission denied
find: /proc/4807/task/4807/fd: Permission denied
find: /proc/4807/fd: Permission denied
find: /proc/4808/task/4808/fd: Permission denied
find: /proc/4808/fd: Permission denied
find: /proc/4855/task/4855/fd: Permission denied
find: /proc/4855/fd: Permission denied
find: /proc/4858/task/4858/fd: Permission denied
find: /proc/4858/fd: Permission denied
find: /proc/4861/task/4861/fd: Permission denied
find: /proc/4861/fd: Permission denied
find: /proc/4943/task/4943/fd: Permission denied
find: /proc/4943/fd: Permission denied
find: /proc/4944/task/4944/fd: Permission denied
find: /proc/4944/fd: Permission denied
find: /proc/4956/task/4956/fd: Permission denied
find: /proc/4956/fd: Permission denied
find: /proc/5015/task/5015/fd: Permission denied
find: /proc/5015/fd: Permission denied
find: /proc/5111/task/5111/fd: Permission denied
find: /proc/5111/fd: Permission denied
find: /proc/5125/task/5125/fd: Permission denied
find: /proc/5125/fd: Permission denied
find: /proc/5147/task/5147/fd: Permission denied
find: /proc/5147/fd: Permission denied
find: /proc/5172/task/5172/fd: Permission denied
find: /proc/5172/fd: Permission denied
find: /proc/5255/task/5255/fd: Permission denied
find: /proc/5255/fd: Permission denied
find: /proc/5273/task/5273/fd: Permission denied
find: /proc/5273/fd: Permission denied
find: /proc/5310/task/5310/fd: Permission denied
find: /proc/5310/fd: Permission denied
find: /proc/5352/task/5352/fd: Permission denied
find: /proc/5352/fd: Permission denied
find: /proc/5537/task/5537/fd: Permission denied
find: /proc/5537/fd: Permission denied
find: /proc/5620/task/5620/fd: Permission denied
find: /proc/5620/fd: Permission denied
find: /proc/5689/task/5689/fd: Permission denied
find: /proc/5689/fd: Permission denied
find: /proc/5844/task/5844/fd: Permission denied
find: /proc/5844/fd: Permission denied
find: /proc/5845/task/5845/fd: Permission denied
find: /proc/5845/fd: Permission denied
find: /proc/5903/task/5903/fd: Permission denied
find: /proc/5903/fd: Permission denied
find: /proc/5974/task/5974/fd: Permission denied
find: /proc/5974/fd: Permission denied
find: /proc/6000/task/6000/fd: Permission denied
find: /proc/6000/fd: Permission denied
find: /dev/bus/usb/.usbfs/005: Permission denied
find: /dev/bus/usb/.usbfs/004: Permission denied
find: /dev/bus/usb/.usbfs/003: Permission denied
find: /dev/bus/usb/.usbfs/002: Permission denied
find: /dev/bus/usb/.usbfs/001: Permission denied
patrick@malcolm-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
there's the search and the echo $PATH, as for what any of it means, i don't know. thanks for all the help, it's great having someone who knows what their doing!
I expected to see something like "/usr/bin/gnome-screensaver" in that long list, but that's ok. I'm gonna compare these results with mine and see what we should try next. :)
Let me explain the commands:
**find / -iname gnome-screensaver**
searches for files, starting from /, called gnome-screensaver, case-insensitive.

**echo $PATH**
prints the contents of the system variable PATH. When you run something, it searches for the program in each of those folders, in that exact order.

---

### Post by patmalcolm91 on 2007-08-09
patrick@malcolm-laptop:~$ locate gnome-screensaver
/etc/pam.d/gnome-screensaver
/etc/xdg/menus/gnome-screensavers.menu
/home/patrick/.gconf/apps/gnome-screensaver
/home/patrick/.gconf/apps/gnome-screensaver/%gconf.xml
/usr/lib/pkgconfig/gnome-screensaver.pc
/usr/lib/gnome-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper
/usr/lib/gnome-screensaver/gnome-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver/f-spot-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver/floaters
/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
/usr/lib/gnome-screensaver/gnome-screensaver-dialog
/usr/share/app-install/desktop/gnome-screensaver-preferences.desktop
/usr/share/applications/gnome-screensaver-preferences.desktop
/usr/share/desktop-directories/gnome-screensaver.directory
/usr/share/gconf/schemas/gnome-screensaver.schemas
/usr/share/gconf/defaults/10_gnome-screensaver
/usr/share/doc/gnome-screensaver
/usr/share/doc/gnome-screensaver/TODO
/usr/share/doc/gnome-screensaver/copyright
/usr/share/doc/gnome-screensaver/AUTHORS
/usr/share/doc/gnome-screensaver/changelog.Debian.gz
/usr/share/doc/gnome-screensaver/changelog.gz
/usr/share/doc/gnome-screensaver/README
/usr/share/doc/gnome-screensaver/NEWS.gz
/usr/share/gnome-screensaver
/usr/share/gnome-screensaver/lock-dialog-default.glade
/usr/share/gnome-screensaver/gnome-screensaver-preferences.glade
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-screensaver.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gnome-screensaver.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-screensaver.mo
/usr/bin/gnome-screensaver-preferences
/usr/bin/gnome-screensaver-command
/usr/bin/gnome-screensaver.org
/var/lib/dpkg/info/gnome-screensaver.md5sums
/var/lib/dpkg/info/gnome-screensaver.conffiles
/var/lib/dpkg/info/gnome-screensaver.prerm
/var/lib/dpkg/info/gnome-screensaver.postrm
/var/lib/dpkg/info/gnome-screensaver.list
/var/lib/dpkg/info/gnome-screensaver.postinst

this is what the locate command returned.

---

### Post by Troubled on 2007-08-09
patmalcolm91:
tszanon is right, there should be an entry of
```
/usr/bin/gnome-screensaver
```
which is the binary application that your computer runs.

Based on your locate results, I suggest that you try running
```
/usr/lib/gnome-screensaver/gnome-screensaver
```
and see if that works.

If not, then run Synaptic Package Manager and reinstall gnome-screensaver.
You can do this via the command line by typing
```
sudo apt-get reinstall gnome-screensaver
```

---

### Post by tszanon on 2007-08-09
> **Troubled said:**
> Based on your locate results, I suggest that you try running
```
/usr/lib/gnome-screensaver/gnome-screensaver
```
and see if that works.
I just checked. Unfortunately, that's a folder. :(
> **Troubled said:**
> If not, then run Synaptic Package Manager and reinstall gnome-screensaver.
You can do this via the command line by typing
```
sudo apt-get reinstall gnome-screensaver
```
I hope that works. But, if it doesn't, I have a suggestion. A weird one, but it's a suggestion. :)

Here are the files that Synaptic tells me that were installed when gnome-screensaver was installed:```
/usr/bin/gnome-screensaver
/usr/bin/gnome-screensaver-command
/usr/bin/gnome-screensaver-preferences
/usr/lib/gnome-screensaver/gnome-screensaver-dialog
/usr/lib/gnome-screensaver/gnome-screensaver
/usr/lib/gnome-screensaver/gnome-screensaver/floaters
/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
/usr/lib/pkgconfig/gnome-screensaver.pc
/usr/share/gnome-screensaver/themes/cosmos-slideshow.desktop
/usr/share/gnome-screensaver/themes/footlogo-floaters.desktop
/usr/share/gnome-screensaver/themes/personal-slideshow.desktop
/usr/share/gnome-screensaver/gnome-screensaver-preferences.glade
/usr/share/pixmaps/backgrounds/cosmos/cloud.jpg
/usr/share/pixmaps/backgrounds/cosmos/comet.jpg
/usr/share/pixmaps/backgrounds/cosmos/earth-horizon.jpg
/usr/share/pixmaps/backgrounds/cosmos/earthrise.jpg
/usr/share/pixmaps/backgrounds/cosmos/galaxy-ngc3370.jpg
/usr/share/pixmaps/backgrounds/cosmos/helix-nebula.jpg
/usr/share/pixmaps/backgrounds/cosmos/jupiter.jpg
/usr/share/pixmaps/backgrounds/cosmos/sombrero.jpg
/usr/share/pixmaps/backgrounds/cosmos/whirlpool.jpg
/usr/share/pixmaps/gnome-logo-white.svg
/usr/share/applications/gnome-screensaver-preferences.desktop
/usr/share/desktop-directories/gnome-screensaver.directory
/usr/share/doc/gnome-screensaver/README
/usr/share/doc/gnome-screensaver/TODO
/usr/share/doc/gnome-screensaver/AUTHORS
/usr/share/doc/gnome-screensaver/copyright
/usr/share/doc/gnome-screensaver/changelog.gz
/usr/share/doc/gnome-screensaver/NEWS.gz
/usr/share/doc/gnome-screensaver/changelog.Debian.gz
/usr/share/gconf/schemas/gnome-screensaver.schemas
/etc/xdg/menus/gnome-screensavers.menu
/etc/pam.d/gnome-screensaver
```
If all of these files are installed, but /usr/bin/gnome-screensaver isn't, I can send it to you (137KB). Reinstalling the package should reinstall it, but, if it doesn't happen, I can send you the file.

[COLOR="Blue"]**Edit:**[/COLOR] you can also get the file from the package. The package is in the CD, in /cdrom/pool/main/g/gnome-screensaver_2.14.3.......deb. It's a normal gzip archive, you can open the package using file-roller:
```
file-roller gnome-screensaver..........deb
```

---

### Post by tszanon on 2007-08-09
[SIZE="1"]I should have made a new post to warn the OP, but instead I edited the last one...here it goes then![/SIZE]

---

### Post by patmalcolm91 on 2007-08-09
thanks guys, i got it working!!! i reinstalled gnome-screensaver via synaptic, restarted X, and removed a bluetooth program from the session, which was apparently hanging up the system. it all works like a dream now. THANK YOU for putting so much thought, time, and effort into helping me!

---

### Post by tszanon on 2007-08-10
Good to know that your problem is solved. Have a nice day!

---

### Post by Troubled on 2007-08-10
Glad that we could help. :)

---

### Post by tszanon on 2007-08-10
What still bugs me is: why reinstalling didn't work for the first time? why that bluetooth program was giving so much trouble? who knows...:confused:

---

### Post by fakie_flip on 2007-08-11
How is it possible to get gnome-screensaver to look in another directory besides ~/Pictures for the screensaver? I've looked in gconf, but no luck yet.

---

### Post by tszanon on 2007-08-11
> **fakie_flip said:**
> How is it possible to get gnome-screensaver to look in another directory besides ~/Pictures for the screensaver? I've looked in gconf, but no luck yet.
I don't know either. I don't even remember how I found out that it looks for ~/Pictures.
I'm gonna search for it, since I want to know that too.

---

