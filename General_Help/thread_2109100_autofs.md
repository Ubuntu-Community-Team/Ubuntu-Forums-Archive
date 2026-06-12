---
title: "autofs"
date: 2013-01-26
forum: General Help
---

### Post by DeMus on 2013-01-26
Hi,
I used to have autofs working till this afternoon where I installed 12.10. Before I worked with 12.04.

I have installed autofs, I have an auto.master file and 2 auto.xxx files, each pointing to a different mountpoint.
I tried direct mapping, I tried indirect mapping, it does not work.

In auto.master I have set /home/username/shares/ as base folder for the shares.
In the shares folder I do get 2 folders with the right names,the names I setup in the auto.xxx files.
When I try to open them I get: The file or folder /home/username/shares/xxx does not exist.
The folder does not exist but still I can see it in the file-manager. 
What is wrong in my setup? Who can help me?

---

### Post by Toz on 2013-01-26
Try this to troubleshoot. 

1. Stop the autofs service:
```
sudo service autofs stop
```

2. Run automount in verbose foreground mode to see what error messages come up:
```
sudo automount -vf
```

It might help identify where the problem is.

---

### Post by papibe on 2013-01-26
Hi DeMus.

Another idea is to mount the directories manually in order to check if everything is set up correctly.

Also, you can check the syslog for mount requests:
```
grep -i /home/username/shares/xxx /var/log/syslog
```
Let us know how it goes.
Regards.

---

### Post by DeMus on 2013-01-27
Toz, thank you for your answer. This is what I got:

sudo automount -vf
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
ignoring duplicate indirect mount /home/jan/shares
lookup(file): failed to read included master map auto.master
mounted indirect on /home/jan/shares with timeout 60, freq 15 seconds

auto.master file:
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc  /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#       "nosuid" and "nodev" options unless the "suid" and "dev"
#       options are explicitly given.
#
#/net   -hosts
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
/home/jan/shares /etc/auto.dea                  --timeout=60
/home/jan/shares /etc/auto.playonhd             --timeout=60

+auto.master

auto.dea file:
/Dea          -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode         ://192.168.1.11/Dea

auto.playonhd file:
/PlayonHD     -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode        ://192.168.1.12/HDD1

Does this help you in anyway to help me? I don't know if the text I got when starting automount is an error or just a warning.

**_Edit:_**
At the moment I don't get the folders at all in the folder shares. Plus, after a re-boot I can not even enter the shares folder. The more I do the less I can do.
Who should be the owner of the folder /home/jan/shares and its subfolders. I see, when I have started automount that root is owner. Is that correct?

I now returned to my original files which look like this:

auto.master:
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc	/etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#	"nosuid" and "nodev" options unless the "suid" and "dev"
#	options are explicitly given.
#
#/net	-hosts
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
/- /etc/auto.dea                  --timeout=60
/- /etc/auto.playonhd             --timeout=60

+auto.master

auto.dea:

/home/jan/shares/Dea          -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode         ://192.168.1.11/Dea

auto.playonhd:

/home/jan/shares/PlayonHD     -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode        ://192.168.1.12/HDD1

Now, after restarting the service autofs I can enter /home/jan/shares and I see the two folders Dea and PlayonHD. Entering those folders again give me the error: The file or folder /home/jan/shares/Dea does not exist.
Again root is owner of shares and its subfolders. Is this correct? If not, how to change that?

---

### Post by Toz on 2013-01-27
> auto.dea file:
/Dea -fstype=cifs,rw,username=guest,password=,uid=1000,[COLOR="Red"]i o[/COLOR]charset=utf8,codepage=unicode,unicode ://192.168.1.11/Dea

I believe there is a typo here, you have a space between the i and the o.

Have you tried doing what papibe suggests? Mounting the shares manually to see if it works?
```
sudo mount -t cifs -orw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode //192.168.1.11/Dea <mount_point>
```

---

### Post by DeMus on 2013-01-27
Hi Toz,

I don't know where the space came from but it is not in my files. I checked both and there is no space between the i and the o.

Yes, I did mount manually and it works fine, no problem.

Do you know your way around autofs? If so, can you give me step by step guideline what to do to set it up? I have a feeling I did not install something, but I have no idea what.
With the previous OS it just worked and now it doesn't. I use the same files so that can't be it.

---

### Post by Toz on 2013-01-27
I just checked your files and they didn't work here either. There were a couple of issues:

1. There is something with your mount command that isn't working for me. I get the error message > >> mount error(22): Invalid argument
...and removing the **codepage=unicode,unicode** parameter fixed that.

2. In your /etc/auto.dea and /etc/auto.playonhd files, the preceeding slash was leading to the error that the file or directory could not be found. 

So, here are the versions of the files that work for me:

**/etc/auto.master**
```

/home/jan/shares /etc/auto.dea --timeout=60 --ghost
```
...the ghost parameter makes the directory visible even if not mounted.

**/etc/auto.dea**
```
Dea -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.1.11/Dea
```
..note the removed leading slash and the **codepage=unicode,unicode** parameter. If you need that parameter, you might want to investigate how to properly use it.

Hope this helps.

---

### Post by DeMus on 2013-01-28
Hello TOZ,

Thanks again for your help. Unfortunately it still does not work.
I changed the files as you told me to, and I do see the Dea folder in /home/jan/shares, but I can not access it. I still get the error that the file or folder does not exist.
The other one, the PlayonHD folder is not showing at all. Both machines are on at the moment.
Using terminal it tells me this:
ls -l
ls: cannot access Dea: No such file or directory
total 0
d????????? ? ? ? ?            ? Dea

I also noticed that when I make the folder shares, I am the owner. As soon as I start autofs root becomes the owner. Is this normal?

What more can I do?


Edit:
sudo service autofs stop
[sudo] password for jan: 
autofs stop/waiting
jan@LinuxDesktop21:~$ sudo automount -f -v
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
ignoring duplicate indirect mount /home/jan/shares
lookup(file): failed to read included master map auto.master
mounted indirect on /home/jan/shares with timeout 60, freq 15 seconds
ghosting enabled
attempting to mount entry /home/jan/shares/Dea
>> mount: wrong fs type, bad option, bad superblock on //192.168.1.11/Dea,
>>        missing codepage or helper program, or other error
>>        (for several filesystems (e.g. nfs, cifs) you might
>>        need a /sbin/mount.<type> helper program)
>>        In some cases useful info is found in syslog - try
>>        dmesg | tail  or so
mount(generic): failed to mount //192.168.1.11/Dea (type cifs) on /home/jan/shares/Dea
failed to mount /home/jan/shares/Dea
attempting to mount entry /home/jan/shares/Dea
failed to mount /home/jan/shares/Dea
attempting to mount entry /home/jan/shares/Dea
failed to mount /home/jan/shares/Dea
^C
umount_autofs_indirect: ask umount returned busy /home/jan/shares
shut down path /home/jan/shares
autofs stopped

Does this help in any way?
I also see entries at Google saying in 12.10 things related to autofs have changed. Does it still work like it used to work in 12.04, or did things really change that much that I now have to use it in a different way, or not at all?

---

### Post by Toz on 2013-01-28
> attempting to mount entry /home/jan/shares/Dea
>> mount: wrong fs type, bad option, bad superblock on //192.168.1.11/Dea,
>> missing codepage or helper program, or other error
>> (for several filesystems (e.g. nfs, cifs) you might
>> need a /sbin/mount.<type> helper program)
>> In some cases useful info is found in syslog - try
>> dmesg | tail or so
Try manually mounting your share using the new parameters. Does it work?

> I also see entries at Google saying in 12.10 things related to autofs have changed. Does it still work like it used to work in 12.04, or did things really change that much that I now have to use it in a different way, or not at all?
I use autofs in 12.10 and it works fine. I've used the same files for the last number of ubuntu versions without issue. In fact, your files (with the last set of changes that I posted) are working here for me.

To rule out other issues, try the following procedure:
1. Reboot.

2. Confirm that you can manually mount the shares:
```
sudo mount -t cifs -orw,username=guest,password=,uid=1000,iocharset=utf8 //192.168.1.11/Dea /mnt
```

3. Stop autofs service:
```
sudo service autofs stop
```

4. Rename the folder that you created for the shares:
```
mv /home/jan/shares /home/jan/shares.OLD
```
...autofs will automatically create that folder for you.

5. Run automount in debug mode:
```
sudo automount -v -f
```

6. Post back the messages that are displayed when you try to view the directory.

---

### Post by DeMus on 2013-01-28
Hi Toz, thanks again for helping me with this.
It is so stupid, in the previous versions it used to work like I had it originally, but somehow in 12.10 it just does not want to work.

I have this for you:

sudo mount -t cifs -orw,username=guest,password=,uid=1000,iocharset=utf8 //192.168.1.11/Dea /mnt
[sudo] password for jan: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.11/Dea,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Same error message as when I use the auto.xxx files.


ls
dr-xr-xr-x  2 jan jan       4096 Jan 28 05:48 shares

mv shares shares.old

ls
dr-xr-xr-x  2 jan jan       4096 Jan 28 05:48 shares.old

sudo automount -v -f
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
ignoring duplicate indirect mount /home/jan/shares
lookup(file): failed to read included master map auto.master
mounted indirect on /home/jan/shares with timeout 60, freq 15 seconds
ghosting enabled
attempting to mount entry /home/jan/shares/Dea
>> mount: wrong fs type, bad option, bad superblock on //192.168.1.11/Dea,
>>        missing codepage or helper program, or other error
>>        (for several filesystems (e.g. nfs, cifs) you might
>>        need a /sbin/mount.<type> helper program)
>>        In some cases useful info is found in syslog - try
>>        dmesg | tail  or so
mount(generic): failed to mount //192.168.1.11/Dea (type cifs) on /home/jan/shares/Dea
failed to mount /home/jan/shares/Dea
attempting to mount entry /home/jan/shares/Dea
failed to mount /home/jan/shares/Dea

And here it hangs. I see no cursor in the terminal, nothing.
After stopping it (ctrl-z) I see a new folder shares with owner root:root.

Do I need to install something extra, or what could be the cause for these errors?

Thanks again, I really appreciate this.

---

### Post by steeldriver on 2013-01-28
iirc mount.cifs is part of cifs-utils which is not installed by default

```
sudo apt-get install cifs-utils
```> **DeMus said:**
> 
sudo mount -t cifs -orw,username=guest,password=,uid=1000,iocharset=utf8 //192.168.1.11/Dea /mnt
[sudo] password for jan: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.11/Dea,
       **missing codepage or helper program**, or other error
       (for several filesystems (e.g. nfs, cifs) [B]you might
       need a /sbin/mount.<type> helper program[/B])
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by DeMus on 2013-01-28
> **steeldriver said:**
> iirc mount.cifs is part of cifs-utils which is not installed by default

```
sudo apt-get install cifs-utils
```

That's it, I missed a package. Finally it works like I am used to.
Thank you so very much.

---

