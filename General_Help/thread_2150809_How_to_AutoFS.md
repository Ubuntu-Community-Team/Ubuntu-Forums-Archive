---
title: "How to AutoFS?"
date: 2013-06-02
forum: General Help
---

### Post by DeMus on 2013-06-02
Hi,

I use Kububtu 13.04 and on the Kubuntuforums.net I have placed the following question. Since the forum is pretty quiet I thought I better give it a try here.
I pasted the whole conversation which exists so far so you know what has been done already.




When I have installed Kubuntu 13.04 with a fresh installation, what do I need to do to make autofs work?
Please be as specific as possible because I can't get it to work.


What I want is to automount 2 disks in 2 other computers and to shutdown this mount after a period of inactivity (let's say 60 sec).
Which packages do I need to install and how do I setup this automount?


I have 4 files in /etc already: auto.master auto.dea auto.laptop and auto.playonhd. What exactly do I need to write into these files when I want to use samba? What do I need to install to make Samba work?


I have a shared folder: /home/user/shares. Do I need to manually make the subfolders in there or will they be made automatically?


Questions Questions Questions 
I know, but I need answers. Who can give them to me and please be very detailed. Thank you so much.








First answer:
I've never tried to use autofs, but here's a good wiki how-to


[https://wiki.archlinux.org/index.php/Autofs](https://wiki.archlinux.org/index.php/Autofs)






My comment to that answer:
Thank you for pointing me to the wiki page. This helped me, it now works (again). Last year or so I also had it working but installing new OS'es prevented it.
When you say you don't use it, then how do you setup your network? How do you make connections to other computers?


I started using autofs because of the following situation:


I use computer A. In fstab I mount a partition on a disk in computer B. This works and I can read/write files in B.
Then B is suddenly switched off. Now my file-manager hangs because of the missing connection.
Before I can do something again in computer A I need to unmount the drive in computer B manually.


With autofs this is done automatically after a timeout. Result: no hanging computer A anymore.


Anyway, thanks again, you really helped.






Second comment:
I have a full time server. I mount it to my desktop and media player using nfs with bg (background) and soft options so it doesn't drag down the network. Basically, it sends the message "not available" but continues to try and connect is the background. Frankly, since it's my network I rarely have this happen. On our laptops, I also use no-auto so if we're not at home it doesn't try and connect automatically. It waits for a request from the user. 


I was a little interested in autofs after reading a bit though. I can see where it has some applications. In my case, I seem to be OK so no reason to fix it if it ain't broken - know what I mean? 




My answer to that:
Hello again,


Yes, when your server is on 24/7 you don't get the symptoms I get when I switch off a computer from which a drive is mounted in my working computer. The thing totally hangs. So I looked for a way to prevent that and found autofs.


Yesterday I wrote it worked, but I shouted too early. Yes, it does work for one computer, a windows computer. With my Linux laptop and my Linux operated media-player it is still a no go.
I have one auto.master file and three map files.
The contents are:


auto.master:
```
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc    /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#    "nosuid" and "nodev" options unless the "suid" and "dev"
#    options are explicitly given.
#
#/net    -hosts
#
# Include /etc/auto.master.d/*.autofs
#
#+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
/home/jan/shares /etc/auto.dea --timeout=30 --ghost
/home/jan/shares /etc/auto.playonhd --timeout=30 --ghost
/home/jan/shares /etc/auto.laptop --timeout=30 --ghost


+auto.master


```

auto.dea:
```
Dea -fstype=cifs,rw,username=guest,password=,uid=1000,i ocharset=utf8 ://192.168.2.11/dea

```
(this is the windows PC which works using autofs)


auto.laptop:
```
Laptop -fstype=cifs,rw,username=guest,password=,uid=1000,i ocharset=utf8 ://192.168.2.22/Home-Jan

```



auto.playonhd:
```
PlayonHD -fstype=cifs,rw,username=admin,password=,iocharset= utf8 ://192.168.2.12/HDD1

```

When I click /home/jan/shares/Dea I see the contents of the user partition Dea in the Windows PC. Great
When I click /home/jan/shares/Laptop I get a message: folder /home/jan/shares/Laptop does not exist. Same for the playonhd.
The folders don't exist but they are there: I can click on them.


What is wrong here? Or should I use nfs instead of samba to connect to the Linux operated machines? Samba always worked so why not now? Several versions of my operating system ago it did work, now I can't get it to work anymore.


Who can help? Please.

---

### Post by Toz on 2013-06-02
Since you've got dea working, autofs is probably configured properly. I'd focus my attention on the connectivity of the other two systems. There are a couple of debugging steps you could try to see if you could get more info as to why you are not connecting:

1. Try mounting manually to see if it works:
```
sudo mount -t cifs -o rw,username=guest,password=,uid=1000,iocharset=utf8 //192.168.2.22/Home-Jan /mnt
```
...you should be able to mount manually. If not, look at fixing that first. (Note: I've noticed some issues with cifs lately where you need to specify "sec=ntlm" as an option to get it to work. You might want to give that a try as well)

2. Try running automount manually to see any error messages that may come up. First, shutdown the daemon:
```
sudo service autofs stop
```
...then run it manually:
```
sudo automount -v -f
```

Post back any error messages that you may get.

Reference: [https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs")

---

### Post by DeMus on 2013-06-02
Thank you so much for your answer.
I tried what you told me and a manual mount is possible, no problem there.

When I manually started automount, I got this:

```
sudo automount -v -f
Starting automounter version 5.0.7, master map /etc/auto.master
using kernel protocol version 5.02
mounted indirect on /home/jan/shares with timeout 3, freq 1 seconds
ghosting enabled
attempting to mount entry /home/jan/shares/Dea
mounted /home/jan/shares/Dea
1 remaining in /home/jan/shares
attempting to mount entry /home/jan/shares/PlayonHD
key "PlayonHD" not found in map source(s).
failed to mount /home/jan/shares/PlayonHD
attempting to mount entry /home/jan/shares/Laptop
key "Laptop" not found in map source(s).
failed to mount /home/jan/shares/Laptop
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
expiring path /home/jan/shares/Dea
expired /home/jan/shares/Dea
attempting to mount entry /home/jan/shares/Dea
mounted /home/jan/shares/Dea
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
1 remaining in /home/jan/shares
expiring path /home/jan/shares/Dea
expired /home/jan/shares/Dea
statemachine:1363: got unexpected signal 28!

```
Laptop and PlyonHD won't mount. I still get the message that the directories in which they should appear do not exist.
Do the messages mean anything to you?

In the mean time I have some more info which might help, or might not.
In the left side of Dolphin (Places) I made some shortcuts to the two machines using this: smb://linuxlaptop22/ and smb://admin@playonhd/HDD1/.
They work fine. When I made contact to the laptop and switch it off my computer does not hang, Dolphin just continues to work.
When I change the shortcut to /home/jan/shares/Laptop I get the message that the folder does not exist, same for the PlayonHD.

I have connection now but not in the way I expected it. I wonder what is wrong with my setup.

---

### Post by Toz on 2013-06-02
I wonder whether you can only have one entry per directory location in auto.master. Can you try this in your **/etc/auto.master**:
```
/home/jan/shares /etc/auto.shares --timeout=30 --ghost
```
...and this in **/etc/auto.shares**:
```

Dea -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.2.11/dea
Laptop -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.2.22/Home-Jan
PlayonHD -fstype=cifs,rw,username=admin,password=,iocharset=utf8 ://192.168.2.12/HDD1
```

Make sure to restart autofs:
```
sudo service autofs restart
```

---

### Post by DeMus on 2013-06-03
You Sir, are a saint.

That's it. It is strange since I still used the same files I used last year or the year before, I forgot, when it did work.
Now I still have one problem and that is with the PlayonHD media-player but I'm sure this is caused by that machine itself. I can make connections to Dea, which was possible already and to the laptop meaning your system, your way of doing things, works.

Thank you so very much. How did you come up with this idea? Did you know it or did you read it somewhere on the net because I didn't and I have been looking around, I can tell you that.

Jan

---

### Post by Toz on 2013-06-03
Glad to hear it worked. 

> How did you come up with this idea?
Call it a hunch, based on what I read in the man file. From "man 5 auto.master":
> Each line describes a mount point and refers to an autofs map
       describing file systems to be mounted under the mount point.
...I wondered whether that meant one mount point per map file. Looks like that is correct.

If you don't mind, can you mark this thread solved so that others may benefit from this? To mark a thread as solved, first click on the "Edit" link in your _first_ post, click on "Go Advanced", change the Prefix to "[SOLVED]" and Save. Thanks.

---

