---
title: "[SOLVED] 6GB Dapper Install: No Space; Unable to copy the user's Xauthorization file."
date: 2007-01-30
forum: General Help
---

### Post by altonbr on 2007-01-30
I've just installed Dapper, downgrading from Edgy. I thought I'd be smart with my partitions and seperate my /home, /vmware and /var/www.

Here is my "df -h":
[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.0G  5.3G  353M  94% /
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  184K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   19M  1.5G   2% /lib/modules/2.6.15-27-386/volatile
/dev/sda8             178G   62G  108G  37% /home
/dev/sda1              10G  4.6M   10G   1% /media/windows
/dev/sda7              20G  129M   19G   1% /var/www
/dev/sda6              15G  4.8G  9.4G  34% /vmware
/dev/hda              6.6G  6.6G     0 100% /media/cdrom0
[/HTML]

**I realized my mistake with /var/www because my servers will only be running in /vmware (how silly of me)

1) Went to ubuntuguide.org and added extra repositories

2) Installed:
```
$ sudo aptitude install gnomebaker gxine w32codecs msttcorefonts j2re gstreamer0.8* k9copy libdvdcss2 qemu vmware thunderbird ntfs-3g
```

3) Removed:
```
$ sudo aptitude remove evolution gnome-games sound-juicer tsclient
```

The only things I can see here that would take up 6GB are two things: kde packages for k9copy and the tmp folder for k9copy...

How can I tell all these programs to stop using root as a tmp folder and start using /home???

Should I bite the bullet and merge /var/www into / and remember to always give Ubuntu at least 10GB?

I also installed Filelight due to a suggestion in another thread. I love the diagrams, but I can't find anything too suspicious. /usr is taking up the most space on root, and the next are /usr/lib and  /usr/share.

---

### Post by altonbr on 2007-01-31
Sorry: bump.

---

### Post by gwpritch on 2007-01-31
First of all running

```
 sudo apt-get clean 
```
will get all the .deb files downloaded to /var cleaned out.
As to the /tmp... and I have never done this so I don't know if it will work or even if it is a good idea, but you could make /tmp a simlink to say /home/tmp.

---

### Post by altonbr on 2007-01-31
Thanks, but I've already tried that. That /tmp idea is good though, thanks.

Here's my current "df -h":

[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.0G  2.2G  3.5G  39% /
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  180K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   19M  1.5G   2% /lib/modules/2.6.15-27-386/volatile
/dev/sda8             178G   62G  108G  37% /home
/dev/sda1              10G  4.6M   10G   1% /media/windows
/dev/sda6              15G  4.8G  9.4G  34% /vmware[/HTML]

Odd. Must have been k9copy like I stated above. Anyone know about changing the tmp files for k9copy???

---

