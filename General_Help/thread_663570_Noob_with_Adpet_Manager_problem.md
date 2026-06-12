---
title: "Noob with Adpet Manager problem"
date: 2008-01-10
forum: General Help
---

### Post by Khane on 2008-01-10
I work with Kubuntu and while surfing I found[ this page]("http://www.watchingthenet.com/switch-between-gnome-and-kde-desktops-in-ubuntu-or-kubuntu.html") and decided to install Ubuntu and I followed the instructions. All seemed to go well and I rebooted my machine. First I was surprised not to find any option to select between KDE and Gnome at the logon screen. Then I logged as usual and once I got to Kubuntu I went to Adept Manager to look if Ubuntu was installed or not but I got the following  message: " *The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.*sudo "

I ran "apt-setup" but got *command not found*. I ran" apt-get update" and got this line at the end: "dpkg was interrupted, you must manually run 'dpkg --configure -a". I ran "dpkg --configure -a" and then I got an other thing to run and then an other etc...Before posting this message I searched the forum but got more confused about what to do.

How can I get things OK again. Thanks

---

### Post by taurus on 2008-01-10
Run these from a terminal.

```
sudo dpkg --configure -a
sudo apt-get update
```
And if you want to check out Gnome, you can install it with

```
sudo apt-get install ubuntu-desktop
```
Then, you can select which window manager you want to use from the Sessions (bottom left) at the GUI login screen.

---

### Post by Khane on 2008-01-10
Thank you

I ran "sudo dpkg --configure -a" and got this : " *dpkg: failed to write status record about `librsvg2-2' to `/var/lib/dpkg/status': No space left on device* "

---

### Post by taurus on 2008-01-10
Could be running out of disk space?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by Khane on 2008-01-10
df -h. That's the result:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.8G  2.8G     0 100% /
varrun               1014M  156K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda8             9.2G  573M  8.1G   7% /home
/dev/sda1              40G   15G   25G  37% /media/sda1
/dev/sda5              98G   25G   74G  25% /media/sda5
overflow              1.0M   80K  944K   8% /tmp

---

### Post by taurus on 2008-01-10
> **Khane said:**
> df -h. That's the result:

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda6             2.8G  2.8G     0 100% /[/COLOR]**
varrun               1014M  156K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda8             9.2G  573M  8.1G   7% /home
/dev/sda1              40G   15G   25G  37% /media/sda1
/dev/sda5              98G   25G   74G  25% /media/sda5
overflow              1.0M   80K  944K   8% /tmp

You run out of disk space.  Try clearing the cache to buy you some space on /.

```
sudo apt-get clean
df -h
```

---

### Post by Khane on 2008-01-10
Adept works again. I must go out now and I'll try to install Ubuntu with "sudo apt-get install ubuntu-desktop" later.

Thanks a lot,
Khane

---

### Post by Khane on 2008-01-11
Now that the Adept Manager's works again I have set its filter to "installed" only and searched for "Ubuntu" and got the following results ( apart some Kubuntu packages):

[i]1 app-install-data
2 hwdb-client-common
3 language- selector- common
4 linux-ubuntu-modules-2.6.22.14-generic
5 ubuntu-keyring
6 ubuntu-minimal
7 ubuntu standard [/i]

Does that mean that Ubuntu is installed or not and if "yes" then why can't I log to ubuntu but only to Kubuntu ? (something wrong with the instructions maybe ?)

> **taurus said:**
> 
And if you want to check out Gnome, you can install it with

```
sudo apt-get install Ubuntu-desktop
```
Then, you can select which window manager you want to use from the Sessions (bottom left) at the GUI login screen.

Ok, do I have first to uninstall all the 7 "Ubuntu" packages I listed above before installing with "sudo apt-get install ubuntu-desktop" (is it safe and recommended )? Is there a difference between installing Ubuntu using "udo apt-get install ubuntu-desktop" or Adept Manager ?

After freeing some space with "df -h" I ran it again and got this result :

Filesystem            Size     Used      Avail      Use%     Mounted on
**[COLOR="Blue"]/dev/sda6             2.8G      2.3G      341M      88%  [/COLOR]**     /
varrun               1014M     160K     1014M     1%         /var/run
varlock              1014M           0     1014M     0%        /var/lock
udev                  1014M       64K     1014M     1%        /dev
devshm             1014M            0    1014M     0%       /dev/shm
lrm                    1014M       34M      980M      4%      /lib/modules/2.6.22-14-generic/volatile


/dev/sda8             9.2G       546M     8.2G        7%        /home
/dev/sda1              40G          15G     25G        37%       /media/sda1
/dev/sda5              98G           25G     74        25%        /media/sda5


The part of my HD on which I installed Kubuntu is 12GB. Now, "/home" is almost free of space (7% used) and the same for the rest except for */dev/sda6* which  has 2.3GB use of its 2.8GB. I do not  understand how thing really work in ubuntu/Linux but what does that shortage of space mean? Is it normal or not and what will I be able or unable to do because of that ?

Sorry for asking so may questions that may look trivial but I really want understand what I do and how things work.

Thanks.
Khane

---

### Post by taurus on 2008-01-11
If you want to try Gnome and haven't done so, you should install the ubuntu-desktop package.  No need to remove anything first.  Just run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Then, you can pick Gnome from the Options at the GUI login screen.

---

