---
title: "not able to login...."
date: 2007-02-27
forum: General Help
---

### Post by Mia_tech on 2007-02-27
guys after using my laptop for a while it got slow, so I decided to restart the gnome desktop, and when tried to login it goes into a black screen and comes back to login box.........I restarted my laptop in rescue mode and reset both password the root and mine, tried to login and with same results, it wont let me login under my user account
any help appreciated
thanks

---

### Post by taurus on 2007-02-27
What's the output of this command from a prompt?

```
df -h
```

---

### Post by Mia_tech on 2007-02-27
> **taurus said:**
> What's the output of this command from a prompt?

```
df -h
```


here's the output.......I can see now what's wrong, look at my nix installation drive, is full 100%
now is there any easy way to find out what files my be hugging most of my installation.

==========================================================
root@5601-RM00-00:~# hd f
hd: f: No such file or directory

root@5601-RM00-00:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              15G   14G     0 100% /
varrun                125M   20K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  108M  14% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1              11G  5.7G  5.1G  53% /media/hda1
//10.201.240.3/admintools
                      117G   95G   23G  81% /media/4261admin
//10.200.244.3/admintools
                       44G   23G   21G  52% /media/5601admin
root@5601-RM00-00:~# 
==========================================================

---

### Post by taurus on 2007-02-27
Yip.  You just maxed out your 15GB.  While still in recovery mode, run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
df -h
```
Replace **username** from above with your actual login name.

---

### Post by Mia_tech on 2007-02-27
> **taurus said:**
> Yip.  You just maxed out your 15GB.  While still in recovery mode, run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
df -h
```
Replace **username** from above with your actual login name.

ok, while that is going to give me some of my space back, I recall now I was imaging a hd to my laptop using DD, and then it happened I deleted the image I created but still is showing up as 100% full........
thanks

---

### Post by taurus on 2007-02-27
Do you remember where you saved that image?  

```
du -h /var
```

---

### Post by Mia_tech on 2007-02-27
aptitude clean
rm ~/.Trash/*
rm /home/username/.Trash/*
df -h

ok the only command that seems to work is aptitude clean which gave back around 200M
the others "it can't find the specified file"

---

### Post by taurus on 2007-02-27
Run this command to see if there is a big file taking up space in /var.

```
du -h /var
```

---

### Post by Mia_tech on 2007-02-27
> **taurus said:**
> Run this command to see if there is a big file taking up space in /var.

```
du -h /var
```

ok, after doing du -s on every directory, the /home/myusername directory shows about 10G, I went in and started to delete from the gui everything I could after that I go into console and with du -s still showing about 10G, I do  ls to see all files and folders and is exactly the same as Im seeing from the gui, is there any possibility that any hidden files or directory exist?

---

### Post by taurus on 2007-02-27
I bet you are not really removing them; just move them to your trash bin.  Therefore, you need to empty your trash bin.

```
ls -la ~/.Trash
```

---

### Post by Mia_tech on 2007-02-27
ok after doing du -h I finally go

9.9G    ./.local/share/Trash/files
9.9G    ./.local/share/Trash
12K     ./.local/share/applications
9.9G    ./.local/share
9.9G    ./.local
12K     ./.mozilla-thunderbird/if2uz5et.default/US
4.0K    ./.mozilla-thunderbird/if2uz5et.default/extensions
5.3M    ./.mozilla-thunderbird/if2uz5et.default/Mail/Local Folders
36K     ./.mozilla-thunderbird/if2uz5et.default/Mail/mail.bellsouth.net
5.4M    ./.mozilla-thunderbird/if2uz5et.default/Mail
24K     ./.mozilla-thunderbird/if2uz5et.default/ImapMail/mail.dadeschools.net
32K     ./.mozilla-thunderbird/if2uz5et.default/ImapMail
8.1M    ./.mozilla-thunderbird/if2uz5et.default
8.2M    ./.mozilla-thunderbird
4.0K    ./hacks
8.0K    ./.vmware
4.0K    ./vmware
5.1M    ./ghost
4.0K    ./dd
4.0K    ./.kpackage/dir
8.0K    ./.kpackage
8.0K    ./.ssh
10G     .

this was from my /home/myuser directory, why is all this showing on the console and not in the gui and what ./.local/share is doing on my home directory when I don't see it in the gui?
and also when I issue " rm ./.local/share/Trash/*" I get the directories are not empty!, how to you remove directories without getting that message, I already tried rmdir no good
any help appreciated

---

### Post by taurus on 2007-02-27
The reason ~/.Trash doesn't show up in nautilus because it's a hidden directory and you didn't enable it, showing hidden files/directories.  So, try this.

```
rm -rf ~/.local/share/Trash/files
df -h
```

---

