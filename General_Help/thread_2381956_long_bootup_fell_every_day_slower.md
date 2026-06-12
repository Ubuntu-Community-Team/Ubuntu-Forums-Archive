---
title: "long bootup fell every day slower"
date: 2018-01-07
forum: General Help
---

### Post by eslavko on 2018-01-07
Hello...

I have Ubuntu 14.04 LTS 64 bit installed for long time. And bootup process is slow. (mostly black screen) and fell every day slower. Actually the overall response is slower too. What I can do? (I don't like to update as some software I doesn't work with new version)

Memory 4GB
Processor Intel® Core&#8482; i5-3450 CPU @ 3.10GHz × 4 
Graphic Intel® Ivybridge Desktop 
Ubuntu 14.04 LTS 64 bit
Disk 1TB

Here is bootlog
[https://pasteboard.co/H1NxljA.png]("https://paste.ubuntu.com/26338280/")

Here is dmesg 

[URL="https://paste.ubuntu.com/26338280/"]https://paste.ubuntu.com/26338280/



[/URL]

[IMG]https://pasteboard.co/H1NxljA.png[/IMG]

---

### Post by cruzer001 on 2018-01-07
> I don't like to update as some software I doesn't work with new version

Your asking for help troubleshooting an unmaintained system.  I don't think anyone will want to touch this.

What software do you have that fails after a upgrade?

---

### Post by eslavko on 2018-01-08
Isn't 14.04 maintained until April 2019?!?

And Proview (process automation) is software in question along some instrument I have. (oscilloscopes and similar)

---

### Post by Impavidus on 2018-01-08
14.04 is old, but still maintained. It will be supported until April 2019.

I can't tell from the log file you provided what causes the problem. There are some large gaps in the timestamps, but I don't know the processes around those gaps. Maybe somebody can.

---

### Post by cruzer001 on 2018-01-08
Hello

As stated above; supported till 2019.  I thought you ment you were not updating 14.04 and just to verify we are now on track could you run a manual update and look for anything wrong.  Thankyou

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Like Impavidus, I am not seeing anything in your logs.  With your computer specs your system should be very fast.

I think 14.04 has systemd so try this command for information on boot processes.

```
systemd-analyze blame
```

Not enough HDD free space can slow down the whole system.  How much free space do you have?

```
df -h
```

Could swap/memory be a problem?

```
free -m
```

---

### Post by eslavko on 2018-01-08
I have 14.04 up to date. 

Here is requested command output. 
(the I386 libraries are sometime required by some scripts so I don't purge them)

```

slavko@podstresnik:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for slavko: 
...
...
...
Fetched 3654 kB in 10s (349 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libaudio2:i386 libdbusmenu-qt2:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libmkv0 libmysqlclient18:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-network:i386 libqt4-opengl:i386
  libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386
  libqtwebkit4:i386 libxss1:i386 libxv1:i386 sni-qt:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

slavko@podstresnik:~$ systemd-analyze blame
systemd-analyze: command not found

slavko@podstresnik:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G  4,0K  1,9G   1% /dev
tmpfs           382M 1016K  381M   1% /run
/dev/sda1       913G  579G  288G  67% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none            1,9G   52M  1,9G   3% /run/shm
none            100M   56K  100M   1% /run/user

slavko@podstresnik:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3815       3302        513        658         57       1726
-/+ buffers/cache:       1518       2297
Swap:         3956          4       3952
slavko@podstresnik:~$ 


```

---

### Post by cruzer001 on 2018-01-08
Everything looks good.

The systemd command did not work, meaning 14.04 runs upstart.  There is a boot info script that you can install.

```
sudo apt-get install boot-info-script
```

To start it my guess would be in terminal:

```
sudo boot-info-script
```

Or google that info

I hope this will help isolate the slow boot problem.  I'm running low on ideas :(

---

### Post by eslavko on 2018-01-09
don't know what to look for....

[https://paste.ubuntu.com/26352805/](https://paste.ubuntu.com/26352805/)

---

### Post by pqwoerituytrueiwoq on 2018-01-09
There is a piece of software called [bootchart]("apt:bootchart") it will put a chart in /var/log/bootchart/ (it will appear about a minute after boot)
that will tell us what is taking so long
do not attach the image file here, use a image host like imgur, the forums will scale the image down so we can not read it

if OP is using a SSD and not using TRIM it will cause the system to get slower and slower over time, but it should bottom out at some point
i think 14.04 has a scheduled task for trim by default

---

### Post by eslavko on 2018-01-09
Actually I added botchart image at first post here. But something are messed with links and text files are shown in both....

so here again bootchart
[https://pasteboard.co/H1NxljA.png](https://pasteboard.co/H1NxljA.png)

---

### Post by eslavko on 2018-01-09
...and I have regular hard drive, not the SSD. But I never do any kind of optimization of harddrive. I heard it's not needed on linux and can't find the tool to do it.

---

### Post by cruzer001 on 2018-01-09
Hello again :)

First let me say that I have not delt with this nor do I have anyway of testing a fix.  So what I am doing is just pointing you at what I am finding.  I could be right or wrong, I just don't have a way to confirm my findings.  What I see common in all boot attempts is (grub) "recordfail'.  So I will point out one of many hits that I received on google.

[https://askubuntu.com/questions/55551/how-can-i-force-ubuntu-to-boot-on-a-stuck-boot-menu](https://askubuntu.com/questions/55551/how-can-i-force-ubuntu-to-boot-on-a-stuck-boot-menu)

This seems not to address the cause of the problem, but a work-a-round.

Perhaps Mr.Pq.... will have some thoughts on this.

Whats your thoughts??

---

### Post by pqwoerituytrueiwoq on 2018-01-09
[**[COLOR=#000000]@cruzer001[/COLOR]**]("https://ubuntuforums.org/member.php?u=2084993") i do not believe that is OPs's issue, that is the system waiting on user input when there is no user at the system

There are 2 things that come to my mind that i have found to cause a long boot time
1 an issue with my swap partition where i had changed the UUID were i made a new one, there was a second reference in /etc/mtab
another very odd issue i has was caused my of all things a USB device being plugged in (obviously not a very linux friendly piece of hardware, it worked well somewhat)

in the boot chart i do see OP is using samba, if you have any drives that do not need to be loaded before user login you can mount them via /etc/rc.local
here is a chunk of my rc.local
```
if [ ! -d "/var/cache/apt/archives/lost+found" ];then
    mount -U bcbf1c29-de47-42e6-8f53-280358aceca0 /var/cache/apt/archives
fi
if [ ! -d "/mnt/iso/lost+found" ];then
    mount -U 85b4b658-8de3-4364-92d7-cd2ca4d85c47 /mnt/iso
fi
if [ ! -d "/mnt/virtual_box/lost+found" ];then
    mount -U 68715821-36e4-4962-a583-a41115151dcd /mnt/virtual_box
fi
```
this will let you skip waiting on them to mount and do it later as opposed to doing it with /etc/fstab

another issue i had on this note was on my laptop after upgrading to 16.04 from 14.04
something got screwy involved the change over to systemd and the way stuff was mounted, sometimes it would not mount at all so i could not even login unless i used a tty and mounted it manually
i ended up doing a clean install
[https://ubuntuforums.org/showthread.php?t=2333121](https://ubuntuforums.org/showthread.php?t=2333121)

another thought is use [gsmartcontrol]("apt:gsmartcontrol") to run a self test on your HDD to be sure it is not starting to fail

Also be sure [ureadahead]("apt:ureadahead") is installed, this tells the system were to look on the hdd for files i needs, think of it like a index or table of contents used for booting

---

### Post by cruzer001 on 2018-01-09
Samba could be a problem.  Wish we had that bootchart to work with.

---

### Post by eslavko on 2018-01-10
> **cruzer001 said:**
> Samba could be a problem.  Wish we had that bootchart to work with.

Bootchart is appended in post #10!

Is there a way to temporary disable samba (for one boot) to check if that is cause?

---

### Post by pqwoerituytrueiwoq on 2018-01-10
relevant to disabling samba: [https://forums.linuxmint.com/viewtopic.php?t=205032](https://forums.linuxmint.com/viewtopic.php?t=205032)

---

