---
title: "How do I delete the extra core snaps"
date: 2019-05-17
forum: General Help
---

### Post by RabbitWho on 2019-05-17
```
sudo unmount /snap/core18/731

```
says unmount command not found

so of course```

sudo rmdir /snap/core18/731

``` doesn't work

What am i doing wrong? [SIZE=2]
[/SIZE]
Thank you!!! 


[SIZE=1]
[/SIZE][SIZE=2][SIZE=1]
If you want to know why i want to delete those snaps it's because my root is filling up, see below. [/SIZE][/SIZE]

> 
My root folder is filling up and filling up



I looked at other threads on this and they suggested some useful stop-gap things to free up space in the file *[uninstalling programs i wasn't using or almost never used, making my root bigger.]* 

**Why does the folder keep filling up** (even though I'm not installing anything) **and is there a way to stop it?** It never happened before even when i'd had the same Ubuntu install for years, and this is new

Here's a screenshot of the message I'm getting in case I haven't explained it right:

[https://postimg.cc/xqcnr2sq](https://postimg.cc/xqcnr2sq)```


    user@computername:~$ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    udev            3.8G     0  3.8G   0% /dev
    tmpfs           785M  1.9M  783M   1% /run
    /dev/sda5        14G   13G  804M  94% /
    tmpfs           3.9G  185M  3.7G   5% /dev/shm
    tmpfs           5.0M  4.0K  5.0M   1% /run/lock
    tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
    /dev/loop0      3.8M  3.8M     0 100% /snap/gnome-system-monitor/81
    /dev/loop1      3.8M  3.8M     0 100% /snap/gnome-system-monitor/77
    /dev/loop3      2.3M  2.3M     0 100% /snap/gnome-calculator/260
    /dev/loop2       54M   54M     0 100% /snap/core18/941
    /dev/loop4       90M   90M     0 100% /snap/core/6818
    /dev/loop5      144M  144M     0 100% /snap/gnome-3-28-1804/23
    /dev/loop6      1.0M  1.0M     0 100% /snap/gnome-logs/61
    /dev/loop10     4.2M  4.2M     0 100% /snap/gnome-calculator/352
    /dev/loop7       35M   35M     0 100% /snap/gtk-common-themes/818
    /dev/loop8      219M  219M     0 100% /snap/gimp/130
    /dev/loop9      196M  196M     0 100% /snap/vlc/555
    /dev/loop11      15M   15M     0 100% /snap/gnome-logs/45
    /dev/loop12      15M   15M     0 100% /snap/gnome-characters/254
    /dev/loop14     152M  152M     0 100% /snap/gnome-3-28-1804/40
    /dev/loop15     141M  141M     0 100% /snap/gnome-3-26-1604/82
    /dev/loop13      35M   35M     0 100% /snap/gtk-common-themes/1122
    /dev/loop17     4.2M  4.2M     0 100% /snap/gnome-calculator/406
    /dev/loop16     141M  141M     0 100% /snap/gnome-3-26-1604/74
    /dev/loop18     203M  203M     0 100% /snap/vlc/770
    /dev/loop19      92M   92M     0 100% /snap/core/6531
    /dev/loop20     1.0M  1.0M     0 100% /snap/gnome-logs/57
    /dev/loop21     518M  518M     0 100% /snap/libreoffice/115
    /dev/loop22     3.8M  3.8M     0 100% /snap/gnome-system-monitor/70
    /dev/loop23     219M  219M     0 100% /snap/gimp/165
    /dev/loop24     161M  161M     0 100% /snap/midori/451
    /dev/loop25     484M  484M     0 100% /snap/libreoffice/106
    /dev/loop26      90M   90M     0 100% /snap/core/6673
    /dev/loop27     141M  141M     0 100% /snap/gnome-3-26-1604/78
    /dev/loop28      54M   54M     0 100% /snap/core18/731
    /dev/loop29      15M   15M     0 100% /snap/gnome-characters/206
    /dev/loop31     203M  203M     0 100% /snap/vlc/768
    /dev/loop30      54M   54M     0 100% /snap/core18/782
    /dev/loop32      36M   36M     0 100% /snap/gtk-common-themes/1198
    /dev/loop33      15M   15M     0 100% /snap/gnome-characters/258
    /dev/loop34     523M  523M     0 100% /snap/libreoffice/112
    /dev/sda6       101G   75G   22G  78% /home
    tmpfs           785M   48K  784M   1% /run/user/1000

```

I've already run ```
sudo snap set system refresh.retain=2 ^C
```

Thanks



---

### Post by deadflowr on 2019-05-17
First list all snaps so you can see the revision numbers then run the revision cleanup command like so,

```
snap list --all
sudo snap remove <snap-package> --revision ##
```
replace <snap-package> with the snap name and the ## with the number of whatever snap revision you want to remove, 
best to only remove those that are marked as disabled though.

(Though somewhere out in the wild of the web a Ubuntu user (developer, maybe?) created a simple script that does this,
I just don't remember who or where I saw it, since I too set the retain option and have no need to remove older snap revisions,,, manually)

.

---

### Post by Rubi1200 on 2019-05-17
Hi,

Would it not be easier to shrink the /home partition and give some back to /root?

What does this show?

```
sudo fdisk -l
```

Thanks.

---

### Post by TheFu on 2019-05-17
unmount isn't a Unix command.  'umount' , without the 'n', is the correct one, but loop devices aren't using any storage.  They are a trick used by snaps to compartmentalize storage. It is a security aspect for snaps.

If you want to remove snaps, then use the **snap remove** command.  If you don't want any snaps, you can remove the entire snap subsystem. I would remove each snap 1 at a time and install the non-snap version using either synaptic or apt as I went.  

If you like lots of GUI programs, then snaps and 15G for / are a bad idea.  25G is what we recommend for /. Making it larger really isn't necessary for 99% of Ubuntu users.  I have an entire desktop that I use daily with all the OS, logs, development tools + 25 projects and my HOME directory that fits into ....
```
$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on 
/dev/vda1      ext4       20G   16G  3.0G  84% /
```
that desktop was originally installed in 2010. It is running a minimal 16.04.6 today without any DE.

But in the end, it is your box.

---

### Post by RabbitWho on 2019-05-17
@thefu you say the snaps aren't taking up space? But yet when they fill up the partition, as they have in the past, the computer will only start in safe mode. That's as good as using up storage. Did I misunderstand? I don't know what a snap actually is or does, i only became aware of it when the partition filled up with them. I assume they are some kind of backup thing.

@rubi1200 I don't want to resize the partition, this is because the ssd is already very small and dualbooted to boot

@deadflowr

```
user@computer:~$ snap list -all
error: unknown flag `a'


``` 

what am i doing wrong?


```


rabbit@rabbit:~$ sudo umount /snap/core18/731
rabbit@rabbit:~$ sudo rmdir /snap/core18/731
rabbit@rabbit:~$ sudo snap remove <core18_731> --revision ##
bash: core18_731: No such file or directory
rabbit@rabbit:~$ sudo snap remove <core18_731.snap> --revision ##
bash: core18_731.snap: No such file or directory
rabbit@rabbit:~$ sudo snap remove </snap/core18/731> --revision ##
bash: /snap/core18/731: No such file or directory


``` ah i don't know what i'm doing 

Thanks very much for your responses so far everyone

---

### Post by deadflowr on 2019-05-17
sorry it's a double dash --all.

fixed it in post

---

### Post by oldfred on 2019-05-17
This is the way to remove all snaps if you do not want them. I prefer to have the .deb for same applications, but there are pros & cons to snaps.

sudo apt autoremove --purge snapd

boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by TheFu on 2019-05-17
> **RabbitWho said:**
> @thefu you say the snaps aren't taking up space? But yet when they fill up the partition, as they have in the past, the computer will only start in safe mode. That's as good as using up storage. Did I misunderstand? I don't know what a snap actually is or does, i only became aware of it when the partition filled up with them. I assume they are some kind of backup thing.  

What I meant was that the loop mounts don't take any extra storage, so removing them won't help.  You have to use the snap tool to remove any snaps you don't want anymore.  Sorry if that wasn't clear.  We don't need to touch any loop mounts. 

Everything that snaps do really aren't for a forum like this. Google "snap ubuntu" for that answer, at least a simplified version. Others have asked this question in these forums too.

---

### Post by maglin2 on 2019-05-18
This is a useful thread discussing snap version retention/removal options:
[https://superuser.com/questions/1310825/how-to-remove-old-version-of-installed-snaps](https://superuser.com/questions/1310825/how-to-remove-old-version-of-installed-snaps)

---

### Post by RabbitWho on 2019-05-18
Edit: 
I did what was suggested i might like to do and got rid of snapped and then restarted teh computer and all the .snap are gone! So happy! My root partition has loads and loads and loads of free space now, may it never fill up  again! 

I've googeld this and googled this and i still don't understand what i did.  I've left comments on the "beginners guides" asking for clarification, as no one says what they are or what they do, they all use a lot of terminology without definitions or a glossary, it's like trying to install dependancies one by one, every time you look up one definition the definition includes another word you need to look up. Hee hee don't worry about it.. 

Thank you so much everyone i really appreciate it

---

### Post by TheFu on 2019-05-18
Everyone goes through learning the words when starting out.  Looking things up is the only way to understand the technology. It takes time and effort.

If this thread is solved, please mark it that way using the 'thread tools' button near the top.

BTW, please use the normal fonts here.

---

### Post by VMC on 2019-07-23
> **oldfred said:**
> This is the way to remove all snaps if you do not want them. I prefer to have the .deb for same applications, but there are pros & cons to snaps.

sudo apt autoremove --purge snapd

boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)
Thanks Fred I first removed snap without purging it. The 'loops' stayed.

---

