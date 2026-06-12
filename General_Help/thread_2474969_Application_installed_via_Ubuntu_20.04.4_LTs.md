---
title: "Application installed via Ubuntu 20.04.4 LTs"
date: 2022-05-12
forum: General Help
---

### Post by cam17 on 2022-05-12
When using Ubuntu software to install application it appears all downloaded apps use SNAP by defualt. Is that the default ?

I had an update for Lenovo T470 appear on 12 May-2022 from the "ubiuntu software" it had a scant description. Can somoen direct me to a more detial information on that update ?

---

### Post by TheFu on 2022-05-12
Snap packages are being inflicted more and more, but hardly the default.  Of 2000 packages on our systems, 10 might be snap packages.

Lenovo had some well publicized firmware/bios security updates to prevent some nasty remote and local escalation access that you wouldn't want.  Could it be that you didn't patch earlier in the month?

To know what any package update is about, search for the full package name which should show a list of packages with dates, dependencies, etc. I don't use snaps enough to know where to look for them.  If you don't like snaps, run
**sudo apt purge snapd**

Then, when installing package, if you see snapd in the list, it means it is a dependency for the package - i.e. it is a snap.  A few programs on only distributed officially as snap packages, but most can be found from other *unofficial* sources.  Whether those unofficial sources are trustworthy is something only you can decide. Just beware that any package installed can do root things - including inserting back doors to your system.

Until Canonical gives up on snaps - perhaps in 5 more years, if we are lucky, we'll be fighting this battle, it seems.
There are other distros which are very similar to our loved Ubuntu desktops which don't use snaps at all.  Linux Mint is one.  Some people in my LUG are really happen with it.  It is very ubuntu-like.

---

### Post by GhX6GZMB on 2022-05-12
The main snap problem seems to be Firefox, almost all other packages are also available as deb, meaning PPA installs.
As Firefox has devolved to heavy bloatware over the years, changing to, eg, Brave solves the issue.
I can only applaud your suggestion to purge snapd.

---

### Post by cam17 on 2022-05-12
When I perform a df -k I get results like
/dev/loop0           128      128         0 100% /snap/bare/5/dev/loop0           128      128         0 100% /snap/bare/5
/dev/loop2        259712   259712         0 100% /snap/brave/159
/dev/loop3         63488    63488         0 100% /snap/core20/1434
/dev/loop4         56960    56960         0 100% /snap/core18/2344
/dev/loop5         63488    63488         0 100% /snap/core20/1405
/dev/loop6         52224    52224         0 100% /snap/snap-store/547
/dev/loop7         66816    66816         0 100% /snap/gtk-common-themes/1519
/dev/loop8        434432   434432         0 100% /snap/kde-frameworks-5-91-qt-5-15-3-core20/1
/dev/loop9         45824    45824         0 100% /snap/snapd/15534
/dev/loop2        259712   259712         0 100% /snap/brave/159
/dev/loop3         63488    63488         0 100% /snap/core20/1434
/dev/loop4         56960    56960         0 100% /snap/core18/2344
/dev/loop5         63488    63488         0 100% /snap/core20/1405
/dev/loop6         52224    52224         0 100% /snap/snap-store/547
/dev/loop7         66816    66816         0 100% /snap/gtk-common-themes/1519
/dev/loop8        434432   434432         0 100% /snap/kde-frameworks-5-91-qt-5-15-3-core20/1
/dev/loop9         45824    45824         0 100% /snap/snapd/15534

I never selected Snapd from the default use of Ubuntu and when installing software I only use "ubuntu software" to install apps
So this is why I suspect Ubuntu 20.0.4.4 LTs.

The update for my T470 was only recognized today 12-may-0222 and was displayed in the top right corner of "Ubuntu software" 
If i search the ubuntu site for T470 i do not find any inofmration that describes the update. Where would i search

---

### Post by TheFu on 2022-05-12
Why did you paste the same output twice?

Canonical didn't ask anyone if we wanted snaps. They decided to make it the default/only way to install some packages.  I don't want Gnome installed, but they install that on desktops too ... so this isn't without precedent. 

You can tell the snap system to only retain 2 versions of snaps.  There is a command to make that setting permanent. If you only want to keep one, there is an awk script in these forums that will create a list of snaps and remove those that aren't used.

Whenever posting terminal stuff, please wrap it in forum code-tags, so the columns line up.

There are a number of threads about snaps in these forums. If you don't like the way it is working, reading through those would probably help.

---

### Post by cam17 on 2022-05-13
didn't you say snapd are "hardly the default " ?

Is there a driver description on the ubuntu site for a specific driver called t470?

---

### Post by aug7744 on 2022-05-13
You can install manually Firefox or other Firefox based browser downloading an file an extracting to an folder.

---

### Post by TheFu on 2022-05-13
> **cam17 said:**
> didn't you say snapd are "hardly the default " ?

Is there a driver description on the ubuntu site for a specific driver called t470?

I see what you did there. Nice.  True, for some packages.  Looking at the list of snap mounts, seems that Brave is the only actual program using it.  All the others are libraries for dependencies.  To see the actual list, use **snap list**.  

But my point stands.  10 snap package on a system with 2000 APT packages installed ... which is the "default"?

I know very little about that make of computer.  Nobody here works for Canonical. 

OT: Think of us like neighbors. Sometimes we know things and sometimes we don't.  I'm willing to pull your trash cans in once a year, but I won't be trimming shrubs in the fall. ;) Sometimes you have to use the phone book (google) to find stuff or hope that some other friend knows about the specific stuff you seek.  I know a little about ant and grub control, but nothing about controlling chipmunks (besides to use a neighbor's cat or owl). I've been missing the cat, but the owl has been doing a great job this year.

If it isn't clear, I have yard work on my mind today. ;)

---

### Post by grahammechanical on 2022-05-13
There are three ways to update Ubuntu. The terminal, Software Updater and clicking the Updates tab in Ubuntu Software application. At the moment I am on Ubuntu 22.04 and Ubuntu Software is actually the Ubuntu Snap Store. So, it does offer snap apps. But scroll down the Installed section and you will see that nearly all the installed apps have come from the Ubuntu deb repositories.

Firefox and Thunderbird are now snaps as the default install. Libreoffice is offered as a snap but the deb version is still installed as default. This is my result of snap list

```
graham@UbuntuDev:~$ snap list
Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
core18                     20220428          2409   latest/stable    canonical&#10003;  base
core20                     20220329          1434   latest/stable    canonical&#10003;  base
firefox                    100.0-2           1300   latest/stable/…  mozilla&#10003;    -
gnome-3-38-2004            0+git.1f9014a     99     latest/stable/…  canonical&#10003;  -
gtk-common-themes          0.1-79-ga83e90c   1534   latest/stable/…  canonical&#10003;  -
snap-store                 41.3-60-gfe4703a  582    latest/stable/…  canonical&#10003;  -
snapd                      2.55.3            15534  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               10     latest/stable/…  canonical&#10003;  -
thunderbird                91.8.1            204    latest/stable    canonical&#10003;  -
zoom-client                5.9.6.2225        170    latest/stable    ogra        -
```

The fact that we can update through Ubuntu Software which is a snap app does not mean that all updates are snap packages. Updating through Software Updater might give more information on the packages than you get with Ubuntu Software.

You might want to check your /etc/apt/sources.list file and see if it has a repository for the machine's manufacturer. What I find interesting is that you are looking for a driver called t470 in the Ubuntu repositories when your machine is a Lenovo T470

Regards

---

### Post by cam17 on 2022-05-14
I think I understand the snap description and that not apps may be installed using snap.


For the T470 driver the name T470 displayed on the software update not Lenovo t470. I was trying to find where the descriptive driver information is located. The  source.list only has URL lists.

---

