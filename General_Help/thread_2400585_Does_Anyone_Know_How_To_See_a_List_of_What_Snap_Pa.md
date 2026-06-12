---
title: "Does Anyone Know How To See a List of What Snap Packages You've Installed"
date: 2018-09-07
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-09-07
I'm having a problem with totally removing something from my computer because I've installed a couple of Snap packages.  Does anyone know of a way to see what Snap packages you've installed?  I'm going to do a reinstall and need to know what packages they were so I don't reinstall them again.

---

### Post by $yl9pAR%t on 2018-09-07
Try this in terminal:
```
snap list
```

---

### Post by deadflowr on 2018-09-07
```
snap list
```
shows all snaps

Also more
```
snap list --all
```
shows all snaps and all revisions
to remove a snap 
```
sudo snap remove <snap-name>
```
to remove revisions
```
sudo snap remove <snap-name> --revision <revision-number>
```
replace snap-package and revision-number with the snap name and revision number you want to remove.
Typically dead or obsolete snaps will be marked as disabled in the description area at the end of the snap listing.
So those are usually okay to remove, revision wise.

And
```
snap help
``` 
for more commands and controls.

---

### Post by shane_faulkinbury2 on 2018-09-09
Thanks a ton guys!

---

### Post by shane_faulkinbury2 on 2018-09-09
I closed this and the command only worked for one file. How would I go about removing the following snap files?

---

### Post by deadflowr on 2018-09-09
Those are all in the snap directory in your home folder.
So you can simply delete or move to trash and then delete them.

Snaps are just like normal packages in regard to personal data.
In that when you remove the package the personal configurations are left.

By design they're (both the snap package system and the apt package management system) made to leave a users home folder alone.
Which makes sense because it would be very easy to inadvertently remove a personal file when removing some app.

---

### Post by shane_faulkinbury2 on 2018-09-09
Here's what I got when I tried to move one of them to trash.

---

### Post by Frogs Hair on 2018-09-09
If this document located in the root file system you would need elevated permissions to delete it. I see a lock on the item you are trying to delete.

---

### Post by shane_faulkinbury2 on 2018-09-09
How can I switch to root in Files?  I've already tried removing them as root in the terminal and nothing happens to them.

---

### Post by shane_faulkinbury2 on 2018-09-11
Can I get any help on the above question?

---

### Post by Frogs Hair on 2018-09-12
Use the following command. ```
sudo -H nautilus 
```

---

### Post by deadflowr on 2018-09-12
You're going in circles here:
[https://ubuntuforums.org/showthread.php?t=2399678]("https://ubuntuforums.org/showthread.php?t=2399678")
You cannot delete snap files, as they are read-only.
You must remove the snap package, and then the files will be gone.
Unfortunately I do not know why it was not deleted when (or if) you removed the snap package, my best guess is you had the snap running,
which may account for it not properly being removed.

I was mistaken earlier when I posted that they are in your home folder.
Upon further look, these snap files are in the /snap directory, which is a special directory where snap squashfs file systems are mounted.

---

### Post by number33ak on 2018-09-13
> **deadflowr said:**
> ```
snap list
```
shows all snaps

Also more
```
snap list --all
```
shows all snaps and all revisions
to remove a snap 
```
sudo snap remove <snap-name>
```
to remove revisions
```
sudo snap remove <snap-name> --revision <revision-number>
```
replace snap-package and revision-number with the snap name and revision number you want to remove.
Typically dead or obsolete snaps will be marked as disabled in the description area at the end of the snap listing.
So those are usually okay to remove, revision wise.

And
```
snap help
``` 
for more commands and controls.

This is great.  Thanks for the informative post.

If I remove snapd, Will it also remove any packages that were installed via it?  And will it cause problems later on down the line (such as missing dependencies)?

I just installed the latest Ubuntu (two days ago), I've installed chrome, spotify and slack and I'm already running out of space on my "/root" (16 GB were allocated); and snap is taking up over 2GB
```
sudo du -h --max-depth=1.

12M    ./sbin
13M    ./etc
4.0K    ./cdrom
16K    ./root
787M    ./lib
2.3G    ./home
4.0K    ./lib64
229M    ./boot
2.6G    ./usr
4.0K    ./srv
0    ./dev
16K    ./lost+found
2.1M    ./run
4.0K    ./mnt
13M    ./bin
2.7G    ./snap
8.0K    ./media
57M    ./tmp
7.1G    ./var
0    ./proc
0    ./sys
211M    ./opt


```

If it's not needed I would love it if I could remove it and get that space back.

Thanks.

---

### Post by shane_faulkinbury2 on 2018-09-14
Deadflower, Sorry for getting back so late, but work has been very hard and exhausting lately!  Anyway, I removed all snap packages that had to do with Google and I still see Google related files.  Here is what this command still tells me.

```
~$ snap list --all
Name                        Version                  Rev   Tracking  Publisher           Notes
asunder-casept              2.8.1                    1     stable    casept              -
clementine                  1.3.1.29+git             54    stable    kz6fittycent        -
core                        16-2.35                  5328  stable    canonical&#10003;          core
core                        16-2.34.3                5145  stable    canonical&#10003;          core,disabled
core                        16-2.32.5                4486  stable    canonical&#10003;          core,disabled
core18                      0.1                      19    stable    canonical&#10003;          base
darktable                   2.4.3snap2               20    stable    kyrofa              disabled
darktable                   2.4.4snap1               32    stable    kyrofa              -
darktable-empanada          2.2.5                    2     stable    empanada            classic
firefox                     62.0-2                   124   stable    mozilla&#10003;            -
firefox                     61.0.2-1                 118   stable    mozilla&#10003;            disabled
gnome-3-26-1604             3.26.0                   59    stable/…  canonical&#10003;          disabled
gnome-3-26-1604             3.26.0                   70    stable/…  canonical&#10003;          -
gnome-calculator            3.28.2                   199   stable/…  canonical&#10003;          disabled
gnome-calculator            3.26.0                   154   stable/…  canonical&#10003;          disabled
gnome-calculator            3.30.0                   222   stable/…  canonical&#10003;          -
gnome-characters            3.28.2                   117   stable/…  canonical&#10003;          -
gnome-characters            3.26.2                   69    stable/…  canonical&#10003;          disabled
gnome-logs                  3.26.2                   25    stable/…  canonical&#10003;          disabled
gnome-logs                  3.28.2                   40    stable/…  canonical&#10003;          -
gnome-system-monitor        3.26.0                   36    stable/…  canonical&#10003;          disabled
gnome-system-monitor        3.28.2                   54    stable/…  canonical&#10003;          -
gtk-common-themes           0.1                      319   stable    canonical&#10003;          -
handbrake-jz                1.1.1                    134   stable    jz                  -
keepassx-elopio             2.0.2                    1     stable    elopio              -
keepassxc                   2.3.4                    49    stable    keepassxreboot      -
keepassxc                   2.3.4                    40    stable    keepassxreboot      disabled
keepassxc                   2.3.4                    39    stable    keepassxreboot      disabled
kpcli-elopio                3.0                      1     stable    elopio              -
large-pcap-analyzer         3.5.1                    31    stable    francesco-montorsi  -
opera                       55.0.2994.44             8     stable    opera-software&#10003;     -
simplescreenrecorder-mardy  0.3.8-3                  4     stable    mardy               -
spotify                     1.0.88.353.g15c26ea1-14  19    stable    spotify&#10003;            disabled
spotify                     1.0.89.313.g34a58dea-5   21    stable    spotify&#10003;   
```

---

### Post by deadflowr on 2018-09-14
You still have the firefox snap installed.
Which is where the google references are.
Firefox provides search engines, which Google is one of.

I'm sort of surprised there aren't any listing for opera as well.
Since most browsers provide search engines for users to choose.
And among those search engine choices is most always Google.

---

### Post by shane_faulkinbury2 on 2018-09-15
But I'm using Duckduckgo!  Would just the suggestion be enough and would removing the Firefox snap do anything to Firefox?

---

### Post by deadflowr on 2018-09-15
You should already have the regular Ubuntu repository version of Firefox preinstalled and updated.
Since Ubuntu already ships with that version.

So removing the snap version shouldn't be that disruptive.

The one thing you might need to do is if you like the firefox profile you use, you'll need to (or can ) copy it from the snap directory to your normal mozilla/firefox directory.
The snap firefox directory is in the home folder, it should be something like ~/snap/firefox/common/.mozilla/firefox
Profiles are usually random string names like w34rft6.default.
So you would just need to copy that folder into the mozilla directory at ~/.mozilla/firefox.

Once you copy it over you'll need to set it as the profile to use.
Easy way to do that is open firefox and go to Help > Troubleshooting
scroll down until you see **about:profiles **and click it. 
(alternatively you can just copy and paste about:profiles into the address bar to access the page instantly without going through the help troubleshooting pages)

This will open the profile page and you can select the profile you want to use as default here.
To set it you need to actually Create it, so click on the Create profile button up top.
Then in the make profile popup page click on the folder button and in the file chooser selection box it'll open the mozilla firefox directory. find the snap profile folder you added and select it and click the Open button.
This will create the profile and now in the main profile page again go down to the new profile and select the set this as default.
Once set, close and restart firefox and the profile will now be the old nap profile you had been using for the snap version.

Sorry it's a tad convoluted, and there is probably an even easier way.
(Firefox sync might do...)

This is only if you really like all the settings you had setup in the very short time you've used the snap version.
If not, then  ignore and just remove the snap version and go about as you would with the normal apt version.

---

### Post by shane_faulkinbury2 on 2018-09-16
I'm still working on this.  I removed the Firefox snap package and many still remain.  I'll get a screen shot after I'. done removing the other non snap files.  I have another question however.  How do I remove a file with paranthesis in the name like this, UADescription (Googlebot/2.1)?

---

### Post by shane_faulkinbury2 on 2018-09-17
.

---

### Post by Frogs Hair on 2018-09-17
All my snap configurations are in the home/snap folder and at the moment there is only gnome apps and spotify, so if I remove spotify and delete the folder it should remove the entire configuration. Excuse me if you have tried this already.

---

### Post by shane_faulkinbury2 on 2018-09-19
Frogs Hair, I can do that when I get home, but I'm removing them from my home desktop.  I installed Spotify from Ubuntu Software Center because it was now offered on there.  Do you think I could remove it and reinstall on my command line and that would work?  I'm thinking all the Snap packages have to do with installations from Ubuntu Software Center.

---

### Post by deadflowr on 2018-09-19
> I'm thinking all the Snap packages have to do with installations from Ubuntu Software Center.
That.
While you can install the old apt version of packages from the Ubuntu Software, you can also install the snaps.
You have to pay attention to the details to see where what is being installed from.
A snap package will say it's from the Snap store, while apt will say something else like it's from bionic or xenial, universe or main, which refer to the apt repository version.

(also, I 'm not sure if it's still true, but for a while when you looked at the snap packages in the Software store it listed all snaps as non-free regardless of actual licensing.
So if you see an app listed as non-free which you know is not, then it might be the snap version)

---

### Post by Frogs Hair on 2018-09-19
> **shane_faulkinbury2 said:**
> Frogs Hair, I can do that when I get home, but I'm removing them from my home desktop.  I installed Spotify from Ubuntu Software Center because it was now offered on there.  Do you think I could remove it and reinstall on my command line and that would work?  I'm thinking all the Snap packages have to do with installations from Ubuntu Software Center.

I was using spotify as an example which would apply to other installed snaps. Their configuration file would be in home/snap and those folders could be deleted after removing the snap package.

---

### Post by shane_faulkinbury2 on 2018-09-20
Frogs Hair, I removed the snap folder in the home directory and now none of my extensions work.  When I delete them off the browser and go to re-download them it gives me an error.  Is there anyway of having extensions without having that snap folder?  I can just bookmark the page and go to it manually, but it was real convenient having the extension!

---

### Post by shane_faulkinbury2 on 2018-09-21
I finally succeeded with every ones ideas!  All snap packages and I still have Firefox!  I'll reinstall Spotify in the terminal!  Thanks a to guys!!!

---

