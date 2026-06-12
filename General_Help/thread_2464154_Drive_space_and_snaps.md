---
title: "Drive space and snaps"
date: 2021-06-24
forum: General Help
---

### Post by pantazi on 2021-06-24
> **dddman said:**
> Not so long ago I needed to clean my file system and
```
df -h
```
showed me what to remove.

Will it help you any?


What does this show you about my system? Do I need to remove anything? If so, how?

```
user@rob-hp-elitebook-8460p:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           788M  3.5M  784M   1% /run
/dev/sda1       213G  150G   52G  75% /
tmpfs           3.9G   26M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop2      9.2M  9.2M     0 100% /snap/canonical-livepatch/98
/dev/loop3      9.2M  9.2M     0 100% /snap/canonical-livepatch/99
/dev/loop1      242M  242M     0 100% /snap/brave/118
/dev/loop4       62M   62M     0 100% /snap/core20/1026
/dev/loop5      100M  100M     0 100% /snap/core/11187
/dev/loop6       62M   62M     0 100% /snap/core20/975
/dev/loop8       56M   56M     0 100% /snap/core18/2066
/dev/loop9      141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop11     304M  304M     0 100% /snap/wine-platform-5-stable/16
/dev/loop10     216M  216M     0 100% /snap/wine-platform-5-stable/13
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/100
/dev/loop13     291M  291M     0 100% /snap/kde-frameworks-5-qt-5-14-core18/4
/dev/loop14     100M  100M     0 100% /snap/core/11167
/dev/loop15     324M  324M     0 100% /snap/kde-frameworks-5-qt-5-15-core20/14
/dev/loop16      66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop17     2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop18     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop19     162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop20     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop21     338M  338M     0 100% /snap/wine-platform-runtime/220
/dev/loop22     2.3M  2.3M     0 100% /snap/gnome-system-monitor/157
/dev/loop23      65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop24     219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop25     338M  338M     0 100% /snap/wine-platform-runtime/216
tmpfs           788M   36K  788M   1% /run/user/1000
/dev/loop26      56M   56M     0 100% /snap/core18/2074
/dev/loop7      244M  244M     0 100% /snap/brave/119
```

---

### Post by pantazi on 2021-06-25
Following my post#1 showing results from df -h, I then typed *snap list* into terminal. the result is:

```

user@rob-hp-elitebook-8460p:~$ snap list
Name                             Version                     Rev    Tracking         Publisher   Notes
brave                            1.26.67                     119    latest/stable    brave       -
canonical-livepatch              9.6.2                       99     latest/stable    canonical&#10003;  -
core                             16-2.51                     11187  latest/stable    canonical&#10003;  core
core18                           20210611                    2074   latest/stable    canonical&#10003;  base
core20                           20210429                    1026   latest/stable    canonical&#10003;  base
gnome-3-26-1604                  3.26.0.20210401             102    latest/stable/&#8230;  canonical&#10003;  -
gnome-3-28-1804                  3.28.0-19-g98f9e67.98f9e67  145    latest/stable    canonical&#10003;  -
gnome-3-34-1804                  0+git.3556cb3               72     latest/stable    canonical&#10003;  -
gnome-system-monitor             3.38.0-17-g38c1ce1d62       157    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes                0.1-52-gb92ac40             1515   latest/stable/&#8230;  canonical&#10003;  -
kde-frameworks-5-qt-5-14-core18  5.68.0                      4      latest/stable    kde&#10003;        -
kde-frameworks-5-qt-5-15-core20  5.79.0                      14     latest/stable    kde&#10003;        -
wine-platform-5-stable           5.0.3                       16     latest/stable    mmtrt       -
wine-platform-runtime            v1.0                        220    latest/stable    mmtrt       -

```

So, (I'm just trying to learn something new),  do I remove the snap items from post #6?   The result from *snap list *doesn't seem to relate to snaps.

---

### Post by QIII on 2021-06-25
Posts moved to their own thread from [https://ubuntuforums.org/showthread.php?t=2464000](https://ubuntuforums.org/showthread.php?t=2464000)

Please do not hijack the threads of other users.  Your symptoms may sound similar but arise from entirely different causes.  When the community attempts to address two lines of investigation in the same thread, confusion is inevitable and the OP loses.

Consider whether you would like to have someone butt in to your support session with their issues.

Thanks.

---

### Post by pantazi on 2021-06-25
Ok, apologies, unintentional I assure you.

---

### Post by Impavidus on 2021-06-26
Those lines starting with /dev/loop are related to snap packages, but they don't show real disk usage. They do take quite a bit of disk space though. Snaps you don't use can be removed. Most are not important. Ubuntu installs some by default, but not all flavours do so.

---

### Post by pantazi on 2021-06-26
Thanks, I presume I can use *sudo snap remove (package name),*do they need to be removed in order?  

Can anyone explain why my* snap list *doesn't appear to show any snaps? ( another thread answer by AJ Greeny says to remove the snaps from that list (confused).

---

### Post by Dennis N on 2021-06-26
Everything listed in post #2 is a snap package. Some are support packages for running your snap applications. The only applications I see are brave (browser), livepatch, and gnome-system-monitor. If you intend to use any of these, you need to keep their support packages. You can see all the snap packages and their sizes by browsing in the folder **/var/lib/snapd/snaps**. There are two of each. Snap keeps the two most recent versions.

---

### Post by dddman on 2021-06-26
```
/dev/loop2 9.2M 9.2M 0 100% /snap/canonical-livepatch/98
/dev/loop3 9.2M 9.2M 0 100% /snap/canonical-livepatch/99
/dev/loop1 242M 242M 0 100% /snap/**brave**/118
/dev/loop4 62M 62M 0 100% /snap/core20/1026
/dev/loop5 100M 100M 0 100% /snap/core/11187
/dev/loop6 62M 62M 0 100% /snap/core20/975
/dev/loop8 56M 56M 0 100% /snap/core18/2066
/dev/loop9 141M 141M 0 100% /snap/**gnome-3-26-1604**/102
/dev/loop11 304M 304M 0 100% /snap/**wine-platform-5-stable**/16
/dev/loop10 216M 216M 0 100% /snap/wine-platform-5-stable/13
/dev/loop12 141M 141M 0 100% /snap/gnome-3-26-1604/100
/dev/loop13 291M 291M 0 100% /snap/**kde-frameworks-5-qt-5-14-core18**/4
/dev/loop14 100M 100M 0 100% /snap/core/11167
/dev/loop15 324M 324M 0 100% /snap/**kde-frameworks-5-qt-5-15-core20**/14
/dev/loop16 66M 66M 0 100% /snap/**gtk-common-themes**/1515
/dev/loop17 2.3M 2.3M 0 100% /snap/**gnome-system-monitor**/148
/dev/loop18 219M 219M 0 100% /snap/**gnome-3-34-1804**/72
/dev/loop19 162M 162M 0 100% /snap/**gnome-3-28-1804**/128
/dev/loop20 163M 163M 0 100% /snap/gnome-3-28-1804/145
/dev/loop21 338M 338M 0 100% /snap/**wine-platform-runtime**/220
/dev/loop22 2.3M 2.3M 0 100% /snap/gnome-system-monitor/157
/dev/loop23 65M 65M 0 100% /snap/gtk-common-themes/1514
/dev/loop24 219M 219M 0 100% /snap/gnome-3-34-1804/66
/dev/loop25 338M 338M 0 100% /snap/wine-platform-runtime/216
tmpfs 788M 36K 788M 1% /run/user/1000
/dev/loop26 56M 56M 0 100% /snap/core18/2074
/dev/loop7 244M 244M 0 100% /snap/brave/119 

```
Start with the ones in bold print, choose to remove any or all.  Snaps will notify you of any needed removal order.  Example:
```
sudo snap remove wine-platform-runtime
```
check this out when you have some time
[https://www.putorius.net/beginners-guide-snap-packages-linux.html](https://www.putorius.net/beginners-guide-snap-packages-linux.html)

---

### Post by deadflowr on 2021-06-26
I wouldn't remove any of them unless you know that you don't want it.
You can, however, remove the older revisions.
If you look at the snap listing with the --all flag it'll list both the current and the older revisions, which will be marked as disabled.
```
snap list --all
```
To remove the disabled revisions you can either do so piecemeal or wholesale.

To remove piecemeal you run the snap remove command and add the --revision ##.
Example, you have two brave snaps, revision 118 and revision 119.
Mos likely revision 118 is marked as disabled.
To remove that simply run
```
snap remove brave --revision 118
```
and then only the 118 revision will be removed.

To remove older revisions wholesale a simple script like this works
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
```
Simply copy it into a text file, save it as something like snap-cleanup.sh
Make the file executable.
And to run use
```
sudo ./snap-cleanup.sh
```

The wholesale option is usually the easier one to do, as most of the time you'd want to flush everything at once.
The overall affect of it will be freeing up disk space.

Snaps have an extensive help section builtin
```
snap help
```


For what it's worth the only snap which is only a snap is the canonical-livepatch.
Both gnome-system-monitor and brave have apt versions, albeit, you have to grab the brave apt version from outside source.

I have no idea why you have the wine snaps for.
They have a limited ability to help with dealing with wine based snaps,
but you don't seem to have any wine based snaps, so...


Edit: for more on snaps see: [https://snapcraft.io/docs/getting-started]("https://snapcraft.io/docs/getting-started")

---

### Post by dddman on 2021-06-26
snap-cleanup.sh

I may not be using snaps at the moment, but it's a keeper.  Thanks

---

### Post by pantazi on 2021-06-27
Thank you for all the responses, I'll work through them with some trepidation!

I have a fairly simple system, therefore these possibly unwanted snaps have only been added through updates, not by me.  Still learning.

---

### Post by pantazi on 2021-07-03
I followed the advice above with thanks (not enough members return to say how they got on with the advice given), and learned in the process how to make a file executable and run it. The result of df -h is now:

```

Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           788M  3.5M  784M   1% /run
/dev/sda1       213G  148G   55G  74% /
tmpfs           3.9G   26M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop2      244M  244M     0 100% /snap/brave/120
/dev/loop5      9.2M  9.2M     0 100% /snap/canonical-livepatch/99
/dev/loop3      100M  100M     0 100% /snap/core/11316
/dev/loop6       62M   62M     0 100% /snap/core20/1026
/dev/loop9      324M  324M     0 100% /snap/kde-frameworks-5-qt-5-15-core20/14
/dev/loop8      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop15      56M   56M     0 100% /snap/core18/2074
/dev/loop17     141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop18     219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop19     291M  291M     0 100% /snap/kde-frameworks-5-qt-5-14-core18/4
/dev/loop20     2.5M  2.5M     0 100% /snap/gnome-system-monitor/160
/dev/loop24     244M  244M     0 100% /snap/gnome-3-38-2004/39
/dev/loop26      66M   66M     0 100% /snap/gtk-common-themes/1515
tmpfs           788M   44K  788M   1% /run/user/1000


```

Thanks to all again.

---

### Post by deadflowr on 2021-07-03
For what it's worth you can narrow down file systems listed in df by -x outing useless file systems, or file systems not related to drive space.
running df with the T option will list the used file system types like
```
df -hT
```
from there you can use the -x flag to exclude those file systems like squashfs and tmpfs
Neither of which take up any more space on the hard drive than what is already listed for the hard drives themselves.

So running something like
```
df -hT -x squashfs -x tmpfs
```
will cut it down to a more reasonable and readable output.

Also, in case you wonder where the snaps are on the actual hard drive it's in the directory /var/lib/snapd/snaps.
They are special files which snapd mounts at /snap directory.
But the actual hard drive space used is at the /var/lib/snapd directory.

Maybe someone mentioned all this before and I missed it.
In which case sorry about repeating what others have already stated.

Hope it helps.

---

### Post by TheFu on 2021-07-03
A few aliases to make looking at storage easier:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```
A one-line script to search for huge files from the CWD down.
```
find . -type f -size +1G -ls
```
"+1G" says over 1GB in size, but there are some caveats about that.  "+1000M" is NOT the same as "+1G". But for our needs, it is probably close enough. If you want to understand the details, dig into the 'find' manpage.

Once you have a directory with lots of huge files, probably want to see those files sorted by size:
```
du -hs * | sort -h
```
or to reverse the results:
```
du -hs * | sort -rh
```

---

### Post by pantazi on 2021-07-04
Thanks deadflower, I'll work through that. Opening var/lib/snapd/snaps gives me 'file not supported'. Doesn't seem to affect anything. For anyone reading this, I haven't a problem, I'm just on a learning curve.

Thanks TheFu, I'll get around to that too.

---

