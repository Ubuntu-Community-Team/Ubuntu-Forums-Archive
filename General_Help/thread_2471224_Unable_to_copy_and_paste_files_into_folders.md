---
title: "Unable to copy and paste files into folders"
date: 2022-01-24
forum: General Help
---

### Post by ancap19 on 2022-01-24
Hello,

Wierd problem while running Ubuntu 20.04 LTS: I cannot copy and paste common files (.odt, .pdf.....) into common desktop folders. For example, if I copy a file (ctrl+c), I cannot paste it (ctrl+v) into any folder. If I try to drag a file into a folder, I cannot do it, because the dragged file "gets rejected" and stays in the original place. Can someone help me to solve this problem?

Thanks in advance :)

---

### Post by Impavidus on 2022-01-24
Either you have no write permission in the target directory (which may result from sudo misuse) or the filesystem is mounted read-only (which may happen after I/O error on that filesystem). Let's try and find more details in the terminal:```
ls -ld ~/Desktop
findmnt
```That is assuming you have difficulty writing to the Desktop directory. Substitute another of your problem is somewhere else.

---

### Post by ancap19 on 2022-01-24
Thanks for your help :)

I typed the commands in the terminal. Now, If I drag a file on "closed folder icon", the file gets into the folder correctly. However, if the folder is already open and I try to drag something into it, I still can't. In addition, it is not possible to drag the file out of the folder, so I have to click the "move to" button.

---

### Post by mIk3_08 on 2022-01-24
> **ancap19 said:**
> Thanks for your help :)
I typed the commands in the terminal. Now, If I drag a file on "closed folder icon", the file gets into the folder correctly. However, if the folder is already open and I try to drag something into it, I still can't. In addition, it is not possible to drag the file out of the folder, so I have to click the "move to" button.

If you want to move your file you can do it in your terminal, Run your terminal from your apps list and when you successfully run your terminal just follow these command below:
```
sudo mv '/home/systemname/DownloadFoldder/Foldernames/filename.jpg' '/systemname/folderdestination/foldername'
```
Then input your password when ask then press enter. Good Luck and Cheers.

---

### Post by ancap19 on 2022-01-24
> **mIk3_08 said:**
> If you want to move your file you can do it in your terminal, 

Yes but isn't it possible to find a way to just copy-and-paste as common non-technical users?

---

### Post by ActionParsnip on 2022-01-24
> **ancap19 said:**
> [QUOTE=mIk3_08;14077322]If you want to move your file you can do it in your terminal, 

Yes but isn't it possible to find a way to just copy-and-paste as common non-technical users?

If you can give the output of the commands given by Impavidus then we can advise. Seems to be a permissions issue (See reply #2)

---

### Post by ancap19 on 2022-01-24
Here it is:

First command:

```
ls -ld ~/Desktop
drwxr-xr-x 17 ancap19 ancap19 4096 gen 24 15:06 /home/ancap19/Desktop

Second command: 

findmnt
TARGET                                      SOURCE           FSTYPE  OPTIONS
/                                           /dev/nvme0n1p2   ext4    rw,relatime
&#9500;&#9472;/sys                                      sysfs            sysfs   rw,nosuid,n
&#9474; &#9500;&#9472;/sys/kernel/security                    securityfs       securit rw,nosuid,n
&#9474; &#9500;&#9472;/sys/fs/cgroup                          tmpfs            tmpfs   ro,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified                cgroup2          cgroup2 rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd                cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset                 cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct            cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio       cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/pids                   cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma                   cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory                 cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb                cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio                  cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event             cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/misc                   cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/freezer                cgroup           cgroup  rw,nosuid,n
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/devices                cgroup           cgroup  rw,nosuid,n
&#9474; &#9500;&#9472;/sys/fs/pstore                          pstore           pstore  rw,nosuid,n
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars               efivarfs         efivarf rw,nosuid,n
&#9474; &#9500;&#9472;/sys/fs/bpf                             none             bpf     rw,nosuid,n
&#9474; &#9500;&#9472;/sys/kernel/debug                       debugfs          debugfs rw,nosuid,n
&#9474; &#9500;&#9472;/sys/kernel/tracing                     tracefs          tracefs rw,nosuid,n
&#9474; &#9500;&#9472;/sys/fs/fuse/connections                fusectl          fusectl rw,nosuid,n
&#9474; &#9492;&#9472;/sys/kernel/config                      configfs         configf rw,nosuid,n
&#9500;&#9472;/proc                                     proc             proc    rw,nosuid,n
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc                systemd-1        autofs  rw,relatime
&#9500;&#9472;/dev                                      udev             devtmpf rw,nosuid,n
&#9474; &#9500;&#9472;/dev/pts                                devpts           devpts  rw,nosuid,n
&#9474; &#9500;&#9472;/dev/shm                                tmpfs            tmpfs   rw,nosuid,n
&#9474; &#9500;&#9472;/dev/mqueue                             mqueue           mqueue  rw,nosuid,n
&#9474; &#9492;&#9472;/dev/hugepages                          hugetlbfs        hugetlb rw,relatime
&#9500;&#9472;/run                                      tmpfs            tmpfs   rw,nosuid,n
&#9474; &#9500;&#9472;/run/lock                               tmpfs            tmpfs   rw,nosuid,n
&#9474; &#9500;&#9472;/run/snapd/ns                           tmpfs[/snapd/ns] tmpfs   rw,nosuid,n
&#9474; &#9474; &#9500;&#9472;/run/snapd/ns/canonical-livepatch.mnt nsfs[mnt:[4026532638]]
&#9474; &#9474; &#9474;                                                        nsfs    rw
&#9474; &#9474; &#9492;&#9472;/run/snapd/ns/snap-store.mnt          nsfs[mnt:[4026532776]]
&#9474; &#9474;                                                          nsfs    rw
&#9474; &#9500;&#9472;/run/user/125                           tmpfs            tmpfs   rw,nosuid,n
&#9474; &#9474; &#9492;&#9472;/run/user/125/gvfs                    gvfsd-fuse       fuse.gv rw,nosuid,n
&#9474; &#9492;&#9472;/run/user/1000                          tmpfs            tmpfs   rw,nosuid,n
&#9474;   &#9500;&#9472;/run/user/1000/gvfs                   gvfsd-fuse       fuse.gv rw,nosuid,n
&#9474;   &#9492;&#9472;/run/user/1000/doc                    /dev/fuse        fuse    rw,nosuid,n
&#9500;&#9472;/snap/bare/5                              /dev/loop0       squashf ro,nodev,re
&#9500;&#9472;/snap/acrordrdc/53                        /dev/loop1       squashf ro,nodev,re
&#9500;&#9472;/snap/bitwarden/59                        /dev/loop2       squashf ro,nodev,re
&#9500;&#9472;/snap/core18/2253                         /dev/loop3       squashf ro,nodev,re
&#9500;&#9472;/snap/gnome-3-34-1804/77                  /dev/loop4       squashf ro,nodev,re
&#9500;&#9472;/snap/gnome-3-34-1804/72                  /dev/loop7       squashf ro,nodev,re
&#9500;&#9472;/snap/acrordrdc/62                        /dev/loop5       squashf ro,nodev,re
&#9500;&#9472;/snap/core20/1242                         /dev/loop6       squashf ro,nodev,re
&#9500;&#9472;/snap/canonical-livepatch/119             /dev/loop8       squashf ro,nodev,re
&#9500;&#9472;/snap/snapd/14295                         /dev/loop9       squashf ro,nodev,re
&#9500;&#9472;/snap/snap-store/547                      /dev/loop10      squashf ro,nodev,re
&#9500;&#9472;/boot/efi                                 /dev/nvme0n1p1   vfat    rw,relatime
&#9500;&#9472;/snap/gnome-3-38-2004/87                  /dev/loop28      squashf ro,nodev,re
&#9500;&#9472;/snap/bitwarden/58                        /dev/loop29      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-6-stable/14           /dev/loop30      squashf ro,nodev,re
&#9500;&#9472;/snap/gtk-common-themes/1515              /dev/loop31      squashf ro,nodev,re
&#9500;&#9472;/snap/canonical-livepatch/126             /dev/loop32      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-6-stable/8            /dev/loop12      squashf ro,nodev,re
&#9500;&#9472;/snap/core18/2284                         /dev/loop13      squashf ro,nodev,re
&#9500;&#9472;/snap/gtk-common-themes/1519              /dev/loop14      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-5-stable/18           /dev/loop15      squashf ro,nodev,re
&#9500;&#9472;/snap/snap-store/558                      /dev/loop27      squashf ro,nodev,re
&#9500;&#9472;/snap/gnome-3-28-1804/161                 /dev/loop16      squashf ro,nodev,re
&#9500;&#9472;/snap/gnome-3-28-1804/145                 /dev/loop17      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-3-stable/14           /dev/loop18      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-3-stable/11           /dev/loop19      squashf ro,nodev,re
&#9500;&#9472;/snap/core/11993                          /dev/loop20      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-5-stable/16           /dev/loop21      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-runtime/280           /dev/loop22      squashf ro,nodev,re
&#9500;&#9472;/snap/core20/1270                         /dev/loop23      squashf ro,nodev,re
&#9500;&#9472;/snap/core/11798                          /dev/loop24      squashf ro,nodev,re
&#9500;&#9472;/snap/vlc/2344                            /dev/loop25      squashf ro,nodev,re
&#9500;&#9472;/snap/wine-platform-runtime/281           /dev/loop26      squashf ro,nodev,re
&#9500;&#9472;/snap/snapd/14549                         /dev/loop33      squashf ro,nodev,re
&#9492;&#9472;/media/ancap19/My Passport                /dev/sda1        fuseblk rw,nosuid,n
```

---

### Post by wildmanne39 on 2022-01-24
Please use code tags when posting code.

Thanks

---

### Post by ajgreeny on 2022-01-25
Assuming the source and destination folders are both in your own home folder there should be no need to use **sudo** for any move command.

Let's check all folder ownership in your home with command
***ls -la*** in terminal.

Please use Code tags for all pasted output; see my signature below for doing so if you're not sure how.

---

### Post by ancap19 on 2022-01-25
Here it is:

```

ancap19@ancap19-laptop:~$ ls -la
total 422412
-rw-rw-r--  1 ancap19 ancap19         0 gen 18 15:04  -
drwxr-xr-x 32 ancap19 ancap19      4096 gen 21 16:27  .
drwxr-xr-x  3 root    root         4096 ago  4  2020  ..
-rw-------  1 ancap19 ancap19     13990 gen 25 01:41  .bash_history
-rw-r--r--  1 ancap19 ancap19       220 ago  4  2020  .bash_logout
-rw-r--r--  1 ancap19 ancap19      3771 ago  4  2020  .bashrc
drwxr-xr-x 56 ancap19 ancap19      4096 gen 25 10:08  .cache
drwxr-xr-x  3 ancap19 ancap19      4096 nov  1 10:04  .cert
drwxr-xr-x 32 ancap19 ancap19      4096 gen 23 16:28  .config
drwxr-xr-x 17 ancap19 ancap19      4096 gen 24 15:06  Desktop
drwxr-xr-x  4 ancap19 ancap19      4096 gen 19 19:35  Documents
drwxr-xr-x  3 ancap19 ancap19     12288 gen 20 16:35  Downloads
drwx------  2 ancap19 ancap19      4096 set 29 22:54  .gconf
-rw-rw-r--  1 ancap19 ancap19     18617 gen 18 15:00  get-docker.sh
drwx------  3 ancap19 ancap19      4096 ago  4  2020  .gnome
drwx------  3 ancap19 ancap19      4096 gen 25 10:08  .gnupg
drwxrwxr-x  2 ancap19 ancap19      4096 ago  2 20:42  .gphoto
-rw-rw-r--  1 ancap19 ancap19      2734 apr 14  2021  hashes.txt
-rw-rw-r--  1 ancap19 ancap19 209907219 set 24 12:06 'Il Green Pa...nopticon e la Morte della Privacy --- Parte 1.webm'
-rw-rw-r--  1 ancap19 ancap19 215950446 set 24 13:40 'Il Green Pa...nopticon e la Morte della Privacy --- Parte 2.webm'
drwxr-xr-x  3 ancap19 ancap19      4096 ago  4  2020  .local
drwx------  5 ancap19 ancap19      4096 ago  4  2020  .mozilla
-rw-rw-r--  1 ancap19 ancap19   3228216 lug 28  2020  mpow_MPBH456AB_driver+for+Linux.tgz
-rw-rw-r--  1 ancap19 ancap19   3228216 lug 28  2020  mpow_MPBH456AB_driver+for+Linux.tgz.1
drwxr-xr-x  2 ancap19 ancap19      4096 ago  4  2020  Music
drwx------  4 ancap19 ancap19      4096 set 19  2020  .nv
drwxrwxr-x 12 ancap19 ancap19      4096 set 27 10:55  .openshot_qt
drwxr-xr-x  8 ancap19 ancap19     20480 gen 24 14:09  Pictures
drwx------  3 ancap19 ancap19      4096 ago  4  2020  .pki
drwx--x--x  5 ancap19 ancap19      4096 gen 21  2021  .pokerth
-rw-r--r--  1 ancap19 ancap19       807 ago  4  2020  .profile
drwxr-xr-x  2 ancap19 ancap19      4096 ago  4  2020  Public
drwxrwxr-x  2 ancap19 ancap19      4096 ago 14  2020  .shared-ringdb
drwx------  6 ancap19 ancap19      4096 set 18 19:58  snap
drwx------  2 ancap19 ancap19      4096 ago 14  2020  .ssh
-rw-r--r--  1 ancap19 ancap19         0 ago  4  2020  .sudo_as_admin_successful
drwxr-xr-x  2 ancap19 ancap19      4096 ago  4  2020  Templates
drwx------  6 ancap19 ancap19      4096 set 14  2020  .thunderbird
drwxr-xr-x  3 ancap19 ancap19      4096 set 27 10:44  Videos
-rw-rw-r--  1 ancap19 ancap19       260 gen 17 15:39  .wget-hsts
drwxrwxr-x  4 ancap19 ancap19      4096 gen 24 13:15  .wine
drwx------  7 ancap19 ancap19      4096 dic 19 17:33  .zoom

```

---

### Post by KBar on 2022-01-25
Which files were you trying to move exactly? Which directory are they located in? Could you tell us the source (full path name to a file you want to move) and destination (full path name of a directory you want to move that file into) path names?

For example, I can move a file *~/Pictures/xubuntu-forum.png* to *~/Documents*, but I cannot move something like */usr/share/icons/hicolor/128x128/apps/firefox.png* because I'm not the owner of the file. For that, I'm going to have to resort to **sudo**.

---

### Post by ancap19 on 2022-01-25
> **KBar said:**
> Which files were you trying to move exactly? Which directory are they located in? Could you tell us the source (full path name to a file you want to move) and destination (full path name of a directory you want to move that file into) path names?

The problem is with every file, for example common LibreOffice files created by me, and with every folder, including simple folders on the desktop created by me.

---

### Post by Impavidus on 2022-01-25
If you run the command```
echo "This is a test" >~/Desktop/testfile.txt
```(mind the tilde character (~) in the command)
does that create a new file on your desktop with filename testfile.txt and contents "This is a test"? If not, what's the error message?

(Note: If you already have such a file, choose a different name.)

---

### Post by mIk3_08 on 2022-01-25
> **ancap19 said:**
> The problem is with every file, for example common LibreOffice files created by me, and with every folder, including simple folders on the desktop created by me.
ancap19 Please follow what Impavidus wants you to do. Impavidus is very willing to help you to solve your machine issues. This is one of the steps that positively helps your concern so Good Luck and cheers.

---

### Post by ancap19 on 2022-01-25
> **Impavidus said:**
> If you run the command```
echo "This is a test" >~/Desktop/testfile.txt
```(mind the tilde character (~) in the command)
does that create a new file on your desktop with filename testfile.txt and contents "This is a test"? If not, what's the error message?

(Note: If you already have such a file, choose a different name.)


I followed the instructions, and yes, it does create the file (testfile.txt) on my desktop: if I open it, I can read "This is a test" :)

---

### Post by Impavidus on 2022-01-25
So you can write a file to the desktop – at least today. Permissions don't reset spontaneously, so it appears that permissions are alright.

The other option considered was a filesystem mounted read-only. This happens automatically after an error. It's restored to read-write mode when you reboot, so if you have rebooted since the problem appeared, it may appear to have been fixed automatically. Don't be surprised if the problem pops up again though.

Those files that you can't copy, can you open them in whatever application they are for? And do they appear OK?

Have you got goods backups of all your important files? One should have those anyway, but I'm asking as I have to consider filesystem damage or failing hardware.

---

### Post by ancap19 on 2022-01-25
> **Impavidus said:**
> 
Those files that you can't copy, can you open them in whatever application they are for? And do they appear OK?

Yes, I can use all the files normally. For example, I can write a text, I can view an image, I can play a video, and so on.

> **Impavidus said:**
> 
Have you got goods backups of all your important files? One should have those anyway, but I'm asking as I have to consider filesystem damage or failing hardware.

Well, all started because I bought an SSD exactly to back up some stuff, but I noticed that I couldn't drag a file into it nor copy-and-paste into it. So I tried with other folders, and the same was true. Right now, the disk of my PC is almost full. Maybe that could be the issue?

---

### Post by The Cog on 2022-01-25
I think you need to get specific so we can ask for more details specifically. Otherwise we're all just guessing what you're hiding behind your back.
Pick on one file that you can't drag from one folder to another, and tell us the full paths of the source file and destination folder. Then we can ask precise questions and give precise commands to help find out what's going on.

---

### Post by tea for one on 2022-01-25
> **ancap19 said:**
> Well, all started because I bought an SSD exactly to back up some stuff, but I noticed that I couldn't drag a file into it nor copy-and-paste into it.

How have you formatted the SSD for backups?
Possibly, you are not yet the owner of the backup filesystem?

If you formatted it with ext4 using gparted, root may still be the owner?

More info here [https://www.computerhope.com/unix/uchown.htm](https://www.computerhope.com/unix/uchown.htm)

---

