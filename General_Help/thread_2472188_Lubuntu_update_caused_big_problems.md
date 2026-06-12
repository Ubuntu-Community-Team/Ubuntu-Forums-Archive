---
title: "Lubuntu update caused big problems"
date: 2022-02-20
forum: General Help
---

### Post by rosika on 2022-02-20
Hi all,:)

I´m sorry to say I´ve encountered a huge problem today.

I guess (but I´m not sure) that the most recent system update has corrupted my OS (Lubuntu) to some extent.

The latest kernel update provided me with **5.4.0-100-generic** (which I think was still ok). I believe  I triggered the respective update the day before yesterday.

Yesterday however there was something new to be updated: 

[HTML]ii  base-files 11ubuntu5.5 amd64 Debian base system miscellaneous files[/HTML]
replaced
[HTML]ii  base-files 11ubuntu5.4 amd64 Debian base system miscellaneous files[/HTML]


This seems to be when the catastrophe happened.

When I booted my system today it was on 20.04.4 instead of 20.04.3.
Well, to me this looked good and I thought nothing if it.

When the login screen appeared (showing the Lubuntu logo etc.) everything was still behaving the normal way.

But when the login procedure came to an end the login picture still remained visible for quite a while (perhaps 15 secs. or so) before my desktop wallpaper was being displayed.
This was **NOT** normal behaviour as the wallpaper would be shown immediately after login...

What was still more disturbing was the fact that **thunar** file-manager didn´t start immediately as it used to. It certainly took well over a minute to start after clicking on the icon.

The worst thing however: it turned out not one of the usb-sticks which are attached to the PC at all times were shown in the file-manager.
Until now they were automatically mounted and displayed in the file-manager.

Plus: my third HDD-partition (I have root-, home- and a data-partition) wasn´t mounted either and indeed not shown (thus unavailable) in the file-manager.

This was horrid indeed, so I played back my latest _timeshift_ backup (1 week old) and now I´m on kernel 5.4.0.99 again.

Plus: 

[HTML] ii  base-files 11ubuntu5.4 amd64  Debian base system miscellaneous files[/HTML]

again.

What can I say:
everything works perfectly again like it used to. :P

[I]- Thunar opens up quickly.
- All USB-attached media (3 USB-sticks) mounted and displayed in file-manager automatically
- The same with the third HDD partition
- after the login procedure the wallpaper is displayed immediately
[/I]
The only deplorable thing is: I´ve lost all my bookmarks, history, saved login-passwords add-ons in firefox.

When starting firefox it complained about something. I´ve forgotten what it was exactly but I think it had something to do with the version number.
It wouldn´t start unless I opted for a new profile. That one seems to have overwritten everything - so everything is in a virgin state with firefox.

Well, for now I´ve disabled all automatic updates. So Lubuntu shouldn´t look for them all by itself. 
As long as I don´t perform a manual update things should be alright I guess.

BUT: that´s no solution. :(

Sooner or later I´ll have to update. 

Does anyone have any good ideas as how to proceed now? I´m really stuck here.
Something like that had never happened before...

Many thanks in advance and many greetings.
Rosika ):P

---

### Post by dragonfly41 on 2022-02-20
I can't comment on the causes.

But you might be lucky to find your old Firefox profile buried away. I suggest this since you refer to creating a new profile.

[Refer here]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles").

Run the command **firefox -P** .. capital P .. and you might see other profiles with your bookmarks etc.

---

### Post by deadflowr on 2022-02-20
Run the update commands but press n instead of y and review what would be installed.
```
sudo apt update
sudo apt full-upgrade 
press n to abort
```

---

### Post by GhX6GZMB on 2022-02-20
I think you chose an unlucky time to update.
Please see this post from guiverc:
[https://ubuntuforums.org/showthread.php?t=2472158](https://ubuntuforums.org/showthread.php?t=2472158)

---

### Post by deadflowr on 2022-02-20
Lubuntu's infrastructure has no affect on the repositories.

---

### Post by Impavidus on 2022-02-20
Kernel upgrades can be problematic, but usually the problems show up at a much deeper level than the desktop manager or file manager. Anyway, you can use grub to boot the older version. Maybe that still works.

base-files is a very basic package. It tells what version of Ubuntu is installed, creates the basic directory tree and sets some default settings. It's not involved with the file manager or anything like that.

I guess restoring your backup also restored an older version of Firefox. On my computer, Firefox was upgraded on 15-2. But you only restored the stuff on your root partition, not on your /home partition, so this older Firefox 96 sees a profile in your home directory made by Firefox 97 and Firefox refuses to use a profile that's too new. Either restore a backup of the profile or upgrade Firefox to 97. I don't think the Firefox upgrade triggered your problem.

Have a look at the exact list of available upgrades. If an upgrade triggered your problem, we have to find the most likely culprit. It appears to be limited to the desktop manager or file manager. Is thunar the default file manager on Lubuntu? I thought not, so maybe using a non-default filemanager has something to do with it.

BTW, don't you use fstab to mount your data partition, just like how you mount the /home partition? There's no need to get the file manager involved.

---

### Post by GhX6GZMB on 2022-02-20
"[COLOR=#000000]When I booted my system today it was on 20.04.4 instead of 20.04.3."

This makes me wonder. 20.04.4 is not officially out yet. Is your update set to use development versions?

[/COLOR]

---

### Post by oldfred on 2022-02-20
Slow boot and other issues seems like /home was not mounted using fstab & it had to create a new one that is empty.

If /home a separate partition, use live installer and see it it mounts ok or it may need fsck.
Or a corrupted /etc/fstab.

---

### Post by guiverc on 2022-02-20
I can't provide much, but I'll give my thoughts/responses to some things I've read.

- I confirm what @deadflowr said; Lubuntu's infrastructure will impact accessing the Lubuntu manual, our discourse (I concentrated on in the post ml9104 linked) & other sites of ours, but not package upgrades (*we don't provide any archive or download mirror; that's all Canonical*)

- I note you're using the GA kernel (ie. 5.4), which means the change from 20.04.3 to 20.04.4 I'd consider a minor change & not expect many changes; as all you got were security fixes; unlike users of the HWE kernel stack that changed from 5.11 kernel to 5.13 (*though that was weeks ago now anyway on boxes updated daily*). It's users of the HWE stack that usually have issues.

- you mention wallpaper; that's handled by `pcmanfm-qt` which in fact handles a lot of the LXQt operation (just like `pcmanfm` handled much of LXDE) but there have been no changes to that app that I recall; and Qt5 backend hasn't changed in awhile either (eg. [https://changelogs.ubuntu.com/changelogs/pool/universe/q/qtbase-opensource-src/qtbase-opensource-src_5.12.8+dfsg-0ubuntu2.1/changelog](https://changelogs.ubuntu.com/changelogs/pool/universe/q/qtbase-opensource-src/qtbase-opensource-src_5.12.8+dfsg-0ubuntu2.1/changelog))  so I doubt it's anything Lubuntu specific.

@ml9104.   When 20.04.4 reached RC state (*Release Candidate* - [https://lists.ubuntu.com/archives/ubuntu-release/2022-February/005317.html](https://lists.ubuntu.com/archives/ubuntu-release/2022-February/005317.html)), the 20.04.3 text changes to 20.04.4 (*if it hadn't changed already*) which is seen by installed systems; so yes that's official.  The **20.04.4 ISO isn't yet official** (*some OEM kernel changes may still be required*) so we have no guarantee the current ISOs will remain what's official (*good chance with Lubuntu's as we don't include OEM kernel options*)

I have no answers sorry though.

---

### Post by GhX6GZMB on 2022-02-20
@guiverc:
Interesting. I just issued lsb_release -a and got 20.04.4 as well. No problems, though.
But somehow there's a disconnect between Lubuntu version and kernel version. 20.04.2 and 20.04.3 installed 5.8.0. So only if you go back to the archives you'll get the GA kernel?
I'm getting confused here.

---

### Post by guiverc on 2022-02-20
> **ml9104 said:**
> @guiverc:
Interesting. I just issued lsb_release -a and got 20.04.4 as well. No problems, though.
But somehow there's a disconnect between Lubuntu version and kernel  version. 20.04.2 and 20.04.3 installed 5.8.0. So only if you go back to  the archives you'll get the GA kernel?
I'm getting confused here.

I'll word this in a way that's easy for me, so it'll contain details you already know, for which I apologize before I've started typing my reply.

Lubuntu is a *flavor* of Ubuntu, thus differs with Ubuntu 20.04 LTS with regards kernel stack, this didn't occur with prior LTS releases of Ubuntu (ie. 18.04 LTS, 16.04 LTS, 14.04 LTS etc)

Lubuntu 20.04 installs made with 20.04 or 20.04.1 media default to using the GA kernel stack (*just all installs with 18.04 or earlier LTS releases*), however *flavor* media of 20.04.2 or later default to HWE kernel stack (*indentical here to 18.04 & earlier LTS media*).

Key difference is Ubuntu 20.04 LTS Desktop media defaults to HWE kernel stack regardless of media used, Ubuntu 20.04 LTS Server ISOs default to GA (*but that can be changed during install if using the `subiquity` installer*), but with *flavors* 20.04 & 20.04.1 media default to GA, where as 20.04.2 & later media default to HWE.

- If using 20.04.2 with HWE - you got 5.8 kernel (from 20.10), if using GA you remained on 5.4
- If using 20.04.3 with HWE - you got 5.11 kernel (from 21.04), if using GA you remained on 5.4
- If using 20.04.4 with HWE - you get 5.13 kernel (from 21.10), if using GA you'll remain on 5.4
- If using 20.04.5 with HWE - you'll get 5.15 kernel (from 22.04), if using GA you'll remain on 5.4 kernel.

For full details; I'll refer you to [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Now Lubuntu also is simpler than most Ubuntu *flavors* too, as we use the `calamares` installer for releases past 18.10, and our ISO does **not** include any **OEM** kernel handling.  *Flavor*  ISOs that use `ubiquity` include logic that can replace the GA or HWE default kernel stack with an OEM kernel (*if included on ISO*); which is why my/Lubuntu 20.04.4 is less likely to *respin* compared to others remark (*not having OEM also reduces our ISO size!*).

(a quick look at what's there currently ([http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)) shows us [*Lubuntu*] at [2022.02.]18.1, Ubuntu Desktop at 18.2 (*hey Kubuntu/Kylin/Studio is 18 but that could just be the cron job that creates it didn't require a re-run making it 18.1 & I've no interest in exploring why sorry*])

(*reading official docs like the wiki is **always** better than most of what I write; whilst I intend well; I get tongue-tied, can change wording and introduce errors as I read what I intended, not what I actually type etc.. **If I'm writing official things (wiki, releases, announcements etc) I write it one day, then on a subsequent day re-read what I actually typed & thus find the errors **[I](as well as other team members reading it too)*; I'm not doing that for these type of replies[/I], *be they here on UF, **askubuntu, reddit or most sites. Sorry I can be confusing; I blame a brain-injury I suffered** years ago, but maybe it's age too*)

---

### Post by him610 on 2022-02-20
> thunar file-manager didn´t start
I was under the impression that *PCManFM *was included with Lubuntu. On the other hand,* thunar* is the file manager for Xubuntu.
Is *thunar* now included in Lubuntu, or did you install *thunar* manually?

---

### Post by guiverc on 2022-02-20
> **him610 said:**
> I was under the impression that *PCManFM *was included with Lubuntu. On the other hand,* thunar* is the file manager for Xubuntu.
Is *thunar* now included in Lubuntu, or did you install *thunar* manually?

`pcmanfm` was a LXDE based program that uses GTK2.
`pcmanfm-qt` is a newer Qt5 based program.

The author (PCMan) first ported a version of `pcmanfm` to GTK3, then blogged about how much heavier it was post-port (*the first L in LXDE is light*), then made another port of the program to Qt5 and the blog contains a comparison of how much lighter Qt5 was when compared to GTK3.

The result is the GTK3 port was never completed & was abandoned; and many of the LXDE *devs* stopped working on LXDE, joining instead with *devs* from the Razor-Qt project and created a new replacement for both LXDE & Razor-Qt that became known as LXQt.

- Lubuntu included `pcmanfm` until 18.04, the last LXDE release.

- Lubuntu from 18.10 & later does **not**include the app; instead using the far newer `pcmanfm-qt` program which is a new program (that yes started as a port of `pcmanfm` by its original author PCMan.

`pcmanfm` or `pcmanfm-qt` are mostly known as File Managers, however they both handle a huge portion of the LXDE/LXQt desktop functions respectively.

No version of Lubuntu has ever come with `thunar` (a Xfce file-manager), though as I do like the program, I can understand users adding it & using it (*it made more sense though years ago [when Xfce & LXDE were both GTK2] but not recently if you like an resource-light machine*).

Some non-Ubuntu projects use `thunar` on a LXDE system (eg. versions of peppermint, that moved from LXDE to Xfce) but *lightness* was not their primary goal.

---

### Post by rosika on 2022-02-21
Hi everybody ):P,

thanks a lot to all of you for this multitude of replies. They´re very much appreciated. :P

@dragonfly41:

Thanks so much for the hint and the link. That helped me indeed.
I was actually able to find my old **firefox** profile and could get it to work again.
But I had to get the latest version of firefox in order to make it work:
```
sudo apt update
sudo apt install firefox
```

Tnx a lot for your help. :-D

@deadflowr:

> press n to abort
Thanks for the hint. I think I´ll just try that.

@ml9104:

Thanks so much for the link. So it may be hoped the Lubuntu forum will be in working order soon.
Good to know. ;)

>  This makes me wonder. 20.04.4 is not officially out yet. Is your update set to use development versions?
Actually no, not that I´m aware of...

[HTML]lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal[/HTML]
O.K. That´s clear with me...
... as I applied my one-week-old timeshift backup.

@Impavidus:

> Anyway, you can use grub to boot the older version. Maybe that still works.

O.K., but I very much **suspect** something else than the kernel update to be the culprit here.


I made it my habit of running a script I once wrote regarding **updates**.

So after an update I get the results of what has changed in a text-file.
 I was just looking it up. 

I ran the script last Saturday at 6:30 PM  local time. So the updates had been applied  only minutes before.
 As the problem occured on Saturday and NOT before I may (hopefully) safely say that just these two packages received an update:

 [HTML]42c42
< ii  base-files                                    11ubuntu5.5                           amd64        Debian base system miscellaneous files
---
> ii  base-files                                    11ubuntu5.4                           amd64        Debian base system miscellaneous files
2604c2604
< ii  snapd                                         2.54.3+20.04.1ubuntu0.1               amd64        Daemon and tooling that enable snap packages
---
> ii  snapd                                         2.54.3+20.04.1                        amd64        Daemon and tooling that enable snap packages[/HTML]

 So if logics won´t fail me I may deduce that is has to be one of those two packages…
I **guess** setting them on **hold** ("sudo apt mark hold") might be the next step (before risking another system update).

On the other hand:

> base-files is a very basic package. It tells what version of Ubuntu is  installed, creates the basic directory tree and sets some default  settings. It's not involved with the file manager or anything like that.

...

Thanks for the explanation regarding firefox profiles. :)
> Is thunar the default file manager on Lubuntu? I thought not, so maybe  using a non-default filemanager has something to do with it

Lubuntu has moved from  pcmanfm    to pcmanfm-qt (because the DE is LXQt now, I guess).
 I installed thunar because it´s great for configuring **custom actions**.
Up to now it´s been working flawlessly and opening up in a second or two...

> BTW, don't you use fstab to mount your data partition, just like how you mount the /home partition?

Actually I haven´t added anything to **fstab** after the system installation. It looks like this:


[HTML]# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=31becd52-4df2-4b36-9910-d256e8cbda57 /              ext2    defaults   0 1
UUID=7b0c4fc9-ca50-435c-a56e-e1960228ae16 /home          ext2    defaults   0 2
[/HTML]

So there´s just the root- and the home-partition in it.

BUT: all 3 USB sticks (attached to the PC at any time) and the third data-partition on the HDD are still **automatically** *mounted* at startup.
And they´re available in both file-managers.
That is ... until the problematic update.

@oldfred:

Thanks for the suggestion. I´ll look into it.

@guiverc:

> you're using the GA kernel (ie. 5.4), which means the change from  20.04.3 to 20.04.4 I'd consider a minor change & not expect many  changes
I see. Thanks. Good to know.

I **suspect** *base-files* or *snapd* to be responsible because they´re the only two packages that received an update before things went awry.
But that´s a mere guess, of course...

Thanks also for the bulk of very interesting additional information.


@him610:

Indeed, I installed thunar manually.

Many thanks again to all of you. :P
Many greetings from Rosika ):P

---

### Post by GhX6GZMB on 2022-02-21
[COLOR=#000000]"I [/COLOR][B]suspect [I]base-files or [I]snapd to be responsible..."

[/I][/I][/B]**As snap is banned from my machine, I can't comment here. Sorry.**

---

### Post by rosika on 2022-02-22
@ml9104:

Hi, and thanks for your reply. :P

I think (but I´m not sure) it´s rather **base-files **which are to blame.
Of course I may be totally wrong here. 

I haven´t installed any snaps either, so 
[HTML] sudo apt-mark hold snapd[/HTML]
shouldn´t be problematic.

But I´m not so sure about setting **base-files **on hold.
[https://packages.ubuntu.com/focal/base-files](https://packages.ubuntu.com/focal/base-files) lists this package as ***essential***.
t depends on 5 other packages, it seems.
So basically I have no idea what it does to my system if I hold back updates for **base-files**… :o

Many greetings.
Rosika ):P

---

### Post by rosika on 2022-02-25
UPDATE:

Hi all,

in them meantime I could fix the problem but am not sure how exactly.

I still don´t know why the problems initially showed up.

The only **differences** between the first scenario and the scenario yesterday (my second attempt to perform the updates) were:


 
[LIST]
[*]the second time I updated in **2 steps**, the *first* one excluded the base-files and snapd packages, the *second* one just updated them exclusively
[*]in the meantime two additional packages were added to the update: libexpat1 and libsasl2-modules .
[/LIST]


Well, in the end it seems to have gone well and my system is up-to-date at the moment.:P

Many thanks to all of for your kind help ...
... and many greetings

Rosika ):P

---

### Post by Impavidus on 2022-02-25
Maybe the problem wasn't caused by the update at all.

---

### Post by rosika on 2022-02-26
@Impavidus:

Hi again,

well, the only thing I can say for sure is the fact that the phenomena described in my first post occurred after updating
"base-files" and "snapd" and nothing else.

However:

I´ve subscribed to the rss-feed provided by **Ubuntu security notices** and yesterday received an interesting message:


 [I][B]USN-5292-4: snapd _regression_
[/B][/I]


 Hmm, that made me wonder, especially in view of the fact that the snapd-package was one of the two &#8220;candidates&#8221; that might have been responsible for the problem. 

The feed began thus:

> USN-5292-1 fixed a vulnerability in snapd. Unfortunately that update introduced a regression that could break the fish shell

And that´s exactly the case with me. I´m using the fish-shell by default.


Taking a look at [https://ubuntu.com/security/notices/USN-5292-4](https://ubuntu.com/security/notices/USN-5292-4) and after that at
[URL="https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1961791"]https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1961791
[/URL]

 the bug description began thus:



> [INDENT] Yesterday I received snapd&#8217;s 2.54.3+21.10.1ubuntu0.1 update. And when I rebooted, my Plasma Desktop was **broken**. Applications that were still open worked (Firefox, Konsole), but **task panel was absent**, **icons missing**, &#8230; Basically **the desktop session became unusable**.

 Note that I am using **Fish shell** as my **default shell.** When I use Bash however, the Plasma Desktop is working fine.

 [/INDENT]


Well there are some differences when comparing it to my setup:


 I´m using


 2.54.3+20.04.1ubuntu0.2 instead of  2.54.3+21.10.1ubuntu0.1 now


 and the phenomena described were not quite the same with me , apart from the fact that it´s LXQt with me &#8230; but still:
 I´m beginning to wonder if it could´ve been **snapd** instead of **base-files** which introduced the phenomena described  in my first post ...


&#8230; especially in view of  the fact that I use the fish-shell be default&#8230;


Curiously enough - and God-be-thanked - my latest update hasn´t produced any problems whatsoever.  :P

So everything´s fine now.

Many thanks and many greetings
Rosika):P

---

### Post by Impavidus on 2022-02-26
It could have been the snapd update too, and another update of snapd may have fixed it. It sounds much more plausible than base-files. I don't keep track of snapd updates, as there is no snapd on my computer.

---

### Post by rosika on 2022-02-28
Hi @Impavidus:

> It could have been the snapd update too, and another update of snapd may have fixed it.

Yes, indeed I´m  beginning to think that´s the most likely explanation. Thanks for confirming that.

I haven´t installed a single snap package on my system either.
Lubuntu focal came with **snapd **installed by default and I never bothered to uninstall it.

Many thanks and many greetings.
Rosika ):P

---

