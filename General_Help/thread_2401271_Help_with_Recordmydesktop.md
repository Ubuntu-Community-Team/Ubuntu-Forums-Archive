---
title: "Help with Recordmydesktop"
date: 2018-09-16
forum: General Help
---

### Post by MibunoOokami on 2018-09-16
Hi all,

I've been trying to use Recordmydesktop a number of times now, but within about 15-20 minutes of recording I keep getting messages telling me I'm low on disk space. ```
Low Disk Space on "Filesystem root" The volume "Filesystem root" has only 1.1GB disk space remaining.
``` This occurs even when I click "Save as" and specify a place for the video to save to. I don't understand what is happening here, because A) I have more than 800GB free space, and B) the 15-20 minute videos are only 283MB in size, despite running out of the supposed 1.1GB in the previous message(s).

Can someone please tell me how why this program thinks I have very little space, and how to correct it please? I have a feeling it has something to do with the "Filesystem root", so probably just need to know how to change that.

Thanks in advance

---

### Post by HermanAB on 2018-09-16
Well, if you are playing with video, then you should have oodles of disk space available, since some programs will pre-allocate space.

---

### Post by mc4man on 2018-09-16
The default working directory would be /tmp,maybe post results of df -h

---

### Post by HermanAB on 2018-09-16
Err... /tmp is a RAM disk.  It is not part of the root file system partition.

---

### Post by MibunoOokami on 2018-09-18
> **mc4man said:**
> The default working directory would be /tmp,maybe post results of df -h

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.6G     0  3.6G   0% /dev
tmpfs           749M  1.9M  747M   1% /run
/dev/sda6        29G  8.4G   19G  32% /
tmpfs           3.7G   87M  3.6G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.7G     0  3.7G   0% /sys/fs/cgroup
/dev/loop0      3.8M  3.8M     0 100% /snap/gnome-system-monitor/54
/dev/loop2       15M   15M     0 100% /snap/gnome-logs/40
/dev/loop4       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop6      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop8       99M   99M     0 100% /snap/audacity/15
/dev/loop10     2.3M  2.3M     0 100% /snap/gnome-calculator/222
/dev/loop9      196M  196M     0 100% /snap/vlc/555
/dev/loop13      88M   88M     0 100% /snap/core/5328
/dev/loop14      13M   13M     0 100% /snap/gnome-characters/117
/dev/loop15     2.4M  2.4M     0 100% /snap/gnome-calculator/199
/dev/loop1      3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop5       15M   15M     0 100% /snap/gnome-logs/43
/dev/loop7       43M   43M     0 100% /snap/gtk-common-themes/701
/dev/loop11     149M  149M     0 100% /snap/midori/79
/dev/loop12      13M   13M     0 100% /snap/gnome-characters/124
/dev/loop3      2.3M  2.3M     0 100% /snap/gnome-calculator/238
/dev/sda8       832G   25G  765G   4% /home
tmpfs           749M   16K  749M   1% /run/user/122
tmpfs           749M   48K  749M   1% /run/user/1000

```

So how can I set the default elsewhere?

---

### Post by MibunoOokami on 2018-10-09
Apologies for the bump. 

Can anyone tell me how to change the default location for saving files using Recordmydesktop? Thanks

---

### Post by mastablasta on 2018-10-09
i bet there is no rush...

> [COLOR=#000000][FONT=&quot]Before using recordMyDesktop, [/FONT][/COLOR][B]it is suggested that you 
[visit the Documentation section]("http://recordmydesktop.sourceforge.net/documentation.php") of this site and in particular,
[**read the User Guide**]("http://recordmydesktop.sourceforge.net/rug/index.php")[B], in order to get a better understaning of
how to use the program. 

[/B][/B] and within that user guide you would have found this:
[http://recordmydesktop.sourceforge.net/rug/p1_3a.php](http://recordmydesktop.sourceforge.net/rug/p1_3a.php)


otherwise it looks a bit abandoned.
here is another option if you don't mind using an alternative: [http://www.maartenbaert.be/simplescreenrecorder/](http://www.maartenbaert.be/simplescreenrecorder/)

of course there is also the OBS (Open Broadcaster Software) which may or may not be an overkill for you. depending on what you are trying to do.

---

### Post by MibunoOokami on 2018-10-12
> **mastablasta said:**
> i bet there is no rush...

What makes you think that?

I'm checking out the other two you mentioned, I don't mind an alternative as long is it can be recorded in an appropriate location without saying there's no space.

---

### Post by mc4man on 2018-10-13
When you open recordmydesktop click on the advanced button & set a new working directory , see screen, there set to a folder i created in home folder named tmp
(- after encoding the capture file created in /home/username/tmp will be auto removed

---

### Post by MibunoOokami on 2018-10-22
> **mc4man said:**
> When you open recordmydesktop click on the advanced button & set a new working directory , see screen, there set to a folder i created in home folder named tmp
(- after encoding the capture file created in /home/username/tmp will be auto removed

It might just be me, but I have found I have to set the working directory every time I use RMD.

I have been trying out Simplescreenrecorder and find that to be the most effective and hundreds of times faster/more efficient than RMD. It would take a good 45 mins for RMD to save a 20 min recording, and once I started setting a new working directory, a 60 minute recording would take several hours to save, and be running the CPU at a high rate. SSR seems to be able to record and save a video instantaneously, so that shall be my go to now. Thanks for the help though, it is appreciated.

There is a valid solution in this thread so I will close it.

---

