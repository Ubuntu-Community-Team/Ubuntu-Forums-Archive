---
title: "Nautilus Crashes and HOME dir is empty (Ubuntu 13.10)"
date: 2014-02-20
forum: General Help
---

### Post by Claudia_Behnke on 2014-02-20
Hey,

so while i moved some files from my Download directory to my home directory my nautlius crashed. Even my desktop was empty. 
I rebooted and then the content of my home directory was gone. I tried several things like killing nautilus and reinstall it (i'm not sure if i did it right.)

The current status is the i have a nautilus that crashes immediately:

Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 14: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 23: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 32: out of memory

(nautilus:5371): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed

(nautilus:5371): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: »net usershare« gab den Fehler 255 zurück: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Datei oder Verzeichnis nicht gefunden
Please ask your system administrator to enable user sharing.

Furthermore my home directory is completely empty. When i check the mounted partitions i see that there is still content on it.
Does anyone has any ideas.... I'm a bit desperate because i don't want to loose the content on my home directory.... Thanks in advance ;) 


Greetings Claudia

---

### Post by CitadelUniversal on 2014-02-20
You may simply need to reset nautilus settings did you find this [http://ubuntuforums.org/showthread.php?t=878606](http://ubuntuforums.org/showthread.php?t=878606)  - in your searches & also this [http://askubuntu.com/questions/17917/how-do-i-reset-nautilus-to-the-default-configuration](http://askubuntu.com/questions/17917/how-do-i-reset-nautilus-to-the-default-configuration)

---

### Post by ajgreeny on 2014-02-20
Have you made any changes to mount manually or using fstab in **/home/*user* **any other devices or partitions?

You can not have both your home and another mounted device showing in the same folder, though you could mount a device to a folder within your home, eg **/home/*user*/mountfolder**.  Your home files and folders will still be in their original sites but just not accessible until you unmount whatever is currently in their place.

Let's see the output of command **mount**.

---

### Post by Claudia_Behnke on 2014-02-21
Hey,

thanks for you help.
I reinstalled nautilus because there was no ./nautilus visible. When i restart it now, i got the following error message:
 Initializing nautilus-image-converter extension
Intializing nautilus-pastebin extension...
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 1.4.0
Initializing nautilus-ideviceinfo extension
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 14: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 23: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 32: out of memory
sys:1: Warning: g_object_set: assertion 'G_IS_OBJECT (object)' failed
Traceback (most recent call last):
  File "/usr/share/nautilus-python/extensions/RabbitVCS.py", line 470, in get_background_items_full
    window.set_data("base_dir", path)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GObject.py", line 590, in _unsupported_data_method
    raise RuntimeError('Data access methods are unsupported. '
RuntimeError: Data access methods are unsupported. Use normal Python attributes instead

the output of my mount dir is: /dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,relatime,hugetlb)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=claudia)

Still no files are visible and the nautilus still crashes...

Greetings Claudia

---

### Post by ibjsb4 on 2014-02-21
You running third party software?

```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by Claudia_Behnke on 2014-02-21
ähmm i don't know

i would say no....:
The output is: 
/etc/apt/sources.list.d/gnome3-team-gnome3-saucy.list
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-saucy.list

---

