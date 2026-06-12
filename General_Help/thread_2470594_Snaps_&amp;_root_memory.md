---
title: "Snaps &amp; root memory"
date: 2022-01-05
forum: General Help
---

### Post by lorna51 on 2022-01-05
I have read the recent thread about Snaps bloating the memory and it has been closed as solved, but I don't see how it helps me.
Forgive my ignorance - I am an 'educated user' and know just about enough to keep my system running - until it doesn't!

My root partition is 20GB (not 30GB as per the previous poster). I set it up like this because i was told this would be 'more than sufficient for my needs'. My drive is 1TB and I set it up with 4 partitions -537MB boot/efi, 977GB filesystem (38% full), 20GB root & 2GB swap.

Snaps is currently taking up 9GB and I don't have any redundant snaps, as far as I can see. My system is set to only keep a max of 2 versions.

I shut down my machine every night so it is unlikely it is accumulating lots of old logs, unless you know different.

I keep getting warning messages that I am running out of space in root.
I have toyed with the idea of resizing my partitions and have looked at several 'how tos' on this but have come to the conclusion that they are either aimed at people who know how to do this already or are written by people who don't speak English very well!  Is there a trustworthy link I can follow?  Is resizing my partition even going to help?

I don't want to leave this until my system stalls altogether.
Thanks for any info you can provide.

---

### Post by Impavidus on 2022-01-05
The snaps are actually stored in /var/lib/snapd/snaps. The disk usage you see in /snap is fake. So to check:```
du -hs /var/lib/snapd/snaps
```
Logs aren't wiped on reboot, so you may have accumulated quite a bit. But old logs should be automatically deleted. To check the journald logs, use```
journalctl --disk-usage
```

If you think the logs are too large, try cleaning a bit, for example with```
sudo journalctl --vacuum-time=1week
```That will remove stuff older than one week. To clean up permanently, edit the config file with```
sudoedit /etc/systemd/journald.conf
```Edit the file, save and close the editor. If you haven't changed the defaults, this will use the nano text editor. You can save with ctrl+o and close with ctrl+x. I changed one of the lines to```
SystemMaxUse=1G
```The default limit is using up to 10% of the size of the filesystem or until less than 15% is still free.

The old style logs are in /var/log. I currently have 64MB of logs, including 48MB in journal/.

A 20GB root partition may be a bit smallish these days, but should work if you don't install too much. I have a 30GB root partition, but currently use only 11GB. But then, there are no snaps on my system (Xubuntu 21.10) at all.

---

### Post by lorna51 on 2022-01-05
Thank-you.  du -s /var/lib/snapd/snaps returns 3028500 (3MB?)
the journals were taking up 920.0M in the file system and after running journalctl as su it is now down to 40M.
Still not sure why I am getting low memory messages if there is 20GB available, though!  I guess the programs must be loaded in there to run, which is using up the rest?
I use GIMP a lot, and kdenlive, and spotify.  The rest seem to be the gnome desktop and core.

---

### Post by TheFu on 2022-01-05
To help, we need lots of facts.  There are other threads in these forums with CLI commands to be run to figure out where all the storage is being used.  Please go read those and post the command AND the output.  We never need to see anything with /snap/ in it. That storage is already includes in the real (not fake) mounts.

Also, if you use a swap file, consider using a swap partition instead.

If resizing is needed, how hard it will be depends on the file system(s) being used and whether any advanced, flexible, volume management is used. There is a 1 check-box option in most ubuntu installers that setup LVM and make resizing storage areas fairly painless (for certain values of painless).  If you happened to check that box, it shouldn't be too bad.  If you didn't check the "Use LVM" box during installation, how good are your backups?

If you have good backups, wiping and restoring everything into better allocated storage areas should be less than 1 hr of effort.

Here are a few aliases that I use when tracking down storage stuff:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```
Those commands and the output would be helpful as a starting point.  Facts. That's what we need.

---

### Post by dragonfly41 on 2022-01-05
I am one of the minority who finds GUI dashboards helpful, although I know that commands can be used as above.

I use Stacer as my dashboard and I see at a glance that I have 26 snap packages installed but there are 187 running processes referring to snaps. I do recommend it to at least work alongside CLI usage when troubleshooting.

---

### Post by Holger_Gehrke on 2022-01-05
Another command that's very useful in tracking down what's using up storage is
```

du -x --max-depth=1 /|sort -g

```
du stands for **d**isk **u**sed, '-x' stops it from crossing over into other mounted file systems and '--max-depth=1' makes it show only the level of directories directly inside the directory given as a parameter and the size of files and directories inside. Piping the result through sort is mostly cosmetic, the '-g' tells sort to expect field to sort on to be some general kind of number.
You can then work down into subdirectories to see exactly what is using up space. A thing to keep in mind is the part of Linux file systems reserved for use by root and system programs running as root. For ext3 and ext4 this defaults to 5% of the size of the file system.

Holger

---

### Post by deadflowr on 2022-01-05
> du -s /var/lib/snapd/snaps returns 3028500 (3MB?)
It's in kilobytes (or is it kibibytes?) so it's 3GB.

---

### Post by TheFu on 2022-01-05
```
$ du -hx --max-depth=1 / | sort -h
```

prevents confusion between kb, mb and gb. It shows the units and the sort honors those units.  
For example:
```
1.9M    /opt
15M     /bin
16M     /tmp
18M     /sbin
23M     /etc
1.2G    /lib
5.4G    /var
5.5G    /home
7.4G    /usr
20G     /    {<---- includes all the directories previously in the list  That's why I prefer the du -sh * style of command with a sort. See below ...}

```

So, /var ... needs more looking at on my system.
```
$ du -hs   /var/* |sort -h
0       /var/lock
0       /var/run
4.0K    /var/crash
4.0K    /var/local
4.0K    /var/mail
4.0K    /var/opt
1.5M    /var/snap
2.0M    /var/spool
17M     /var/backups
358M    /var/tmp
362M    /var/log
1.5G    /var/cache
3.2G    /var/lib 
```
So ... /var/cache and /var/lib need more details ...
 /var/cache is nearly all in /var/cache/apt/.   **sudo apt autoclean** is the command to clean up the safe stuff in there. It did nothing on my system, because autoremove and autoclean get run often enough.

```
$ du -hs   /var/lib/* |sort -h
.... {all small, unimportant stuff}
98M     /var/lib/dpkg
149M    /var/lib/dkms
244M    /var/lib/apt
633M    /var/lib/clamav
2.0G    /var/lib/snapd
```
Which is all the snap packages ...   The largest ones are framework dependencies for different versions of Gnome and KDE.  In short, /var/lib/ isn't going to get any smaller unless I start removing snaps and preventing them.

See how this all works?

---

