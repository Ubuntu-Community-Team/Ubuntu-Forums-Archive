---
title: "Reinstall/upgrade best practices?"
date: 2024-04-05
forum: General Help
---

### Post by madscientist032 on 2024-04-05
Hello all - I have a 22.04 install alongside a Win10 pro as a dual-boot setup. 

I am looking for advice & best practices for how to perform the following (also my apologies in advance if this is already answered, I did a quick online search and couldn't find anything I deemed relevant to my situation)

1 - An in-place fresh install of Ubuntu (i am expecting to do this after 24.04 is released) vs an in-place dist-upgrade command
2 - Minimal to no impact to my files in my /home directory 
3 - Apt install code to install all my currently-installed utilities & programs (eg apt install <all my stuff> ) *Ive seen someone's signature with this info on these forums but I don't remember who's it was!!

Basically I'm looking for how to take my customized ubuntu setup, upgrade to 24.04, and basically have everything work w/o issues, though I doubt it'll be that simple & straightforward. 

Let me know of any questions/feedback accordingly & thanks in advance!

---

### Post by oldfred on 2024-04-05
Always have good backups.
At minimum include /home, list of installed apps, perhaps some settings in /etc if you changed any & any server apps like database or web that are in / (root).
those with an important server install like to wait for the .1 update to include further fixes that testing may not have found.

I prefer new clean install and keep at least two / (root) partitions and all data normally in /home in a separate data partition which I use for both installs. I still have 20.04 and use 22.04 as main working install. Then will overwrite 20.04 with 24.04 and once configured and working well will make it my main working install. I keep /home which then is almost only the hidden .configuration files in / .  That way I can do a test install and experiment with different setting without changing main working install.

Some like upgrades & they work if you do not have or remove any proprietary drivers & ppas, as they may be different. And then reinstall after upgrade.

You also can do "dirty" install. That is new install, but not checking format box. Then everything not part of system is not removed, but all settings will be updated to new install's versions. So if you changed anything, you still need those settings backed up.
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by #&amp;thj^% on 2024-04-05
> **madscientist032 said:**
> 
3 - Apt install code to install all my currently-installed utilities & programs (eg apt install <all my stuff> ) *Ive seen someone's signature with this info on these forums but I don't remember who's it was!!


Along with oldfreds solid suggestions, Assuming all your installed applications is written to a packages.txt, then run the following command:
```

xargs sudo apt-get -y install < packages.txt
```

xargs is used to pass the package names from the packages.txt file to the command line.
See also "man xargs"

---

### Post by dragonfly41 on 2024-04-05
You can also open Synaptic Package Manager, go to File > History and you have a timeline of past installments of apps. Other than those installed manually by gdebi.

---

### Post by guiverc on 2024-04-05
My usual method is what OldFred refers to as a *dirty* install, though I tend to prefer *Upgrade via re-install*.

I was requested to write about it on askubuntu, and you'll find me talk about it here - [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)  (*its an old question; but I just picked a question where I felt the answer made some sense*).

I use it **very often**... HOWEVER [issues]("https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058638") have been detected in QA for *noble *(Xubuntu & Ubuntu Desktop) with insufficient time remaining to resolve before release, so the short-term solution with *noble* (or 24.04 LTS on release) will be to prevent non-format installs using the `ubuntu-desktop-installer` ISOs.

Lubuntu, Kubuntu & Ubuntu Unity ISOs use the `calamares` installer, thus have this re-install option, alas the main Ubuntu Desktop & *flavors* using ubuntu-desktop-installer will not, at least not at release time of 24.04.

The plan is to fix the issue(s) in `subiquity` in the future.. but no timeline for that.  As `ubuntu-desktop-installer` is a *snap* package, when the fix is completed; you'll be able to boot the existing 24.04 ISOs, update the *snap*, then use this *unclean re-install* option when its working, but we have no idea when that will be, except its in the future (post 24.04 release).

FYI:   Historically... my *upgrade *approach has always been

- do-release-upgrade after reading release notes & upgrade instructions doc, esp. if server

- If it's a desktop install & I have limited time, just *unclean *re-install of new release (no-format) as this is done in under fifteen minutes, and as almost all my *manually-installed *or additional packages are found in Ubuntu repositories; thus these get auto-reinstalled anyway (*if available on new release*).

- I also elect to do the *unclean re-install* if my do-release-upgrade had a problem & I wasn't able to fix it, or more likely just decided I was lazy and am using this *unclean* install as my quick-fix.


For servers, you'll almost always need to restore data, as the *unclean* install is best on Desktop installs, and at least for release time this option will be [*disabled*]("https://github.com/canonical/ubuntu-desktop-provision/pull/580") for 24.04 Desktop anyway (*unless using a flavor that uses calamares)*.

FYI:  With *unclean* re-installs, all your user configs are left untouched; only GLOBAL configs are lost.  The only GLOBAL changes I lose are all my fonts, themes, sound files etc. as I store all those in /usr/share/ folders intentionally, as I don't want those increasing the size of my $HOME backups... I have script I can run that will just copy/add those  when I re-install (*from a network share**; if/when I discover a new theme/sound/font/pixmap I decide I want to use in the future, I manually add it to my network share*).  *Please note I'm talking about desktop installs here, as user configs are stored in $HOME which a dirty re-install will NOT touch.. Server apps/installs use system directories that are wiped.*

---

### Post by MAFoElffen on 2024-04-05
From my script 'system-info'...
```

function GetUserInstalled()
{
    ## Get a list of User Installed Packages 
    # This only works for Debian Branch...
        
    echo -e "   --- User Installed Package List:"
    # check if Debian Branch. Otherwise 'apt-mark' will not be found...
    if [[ "$debian_branch" == "0" ]]
    then    
        manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
        default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
        user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
        # Use apt-mark to list all packages marked as manually installed. 
        apt-mark showmanual | sort -u > $manually_installed
        # Check to see if default installed list exists
        # for prebuilt system images, it does not exist
        if [ -f /var/log/installer/initial-status.gz ]
        then 
            # Get the list of default installed packages at initial installation.
            gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | \
                sed -n 's/^Package: //p' | \
                sort -u > $default_installed
        else 
            touch $default_installed
        fi
        # Use compare, to exclude those defaults that are unique, AND exclude defaults 
        # that are presently marked as manually installed. (Those 'may' have been changed.)  
        comm -23 $manually_installed $default_installed > $user_installed
        # Print the list in two columns
        awk 'NF' $user_installed 
        #\ Removed 2022.03.10 to turn to one column
        #| pr -2T  # You can remove the pr filter on this to keep output in a single column...
        nl # Add newline in report
        # Remove the temporary files
        rm -f $manually_installed
        rm -f $default_installed
        rm -f $user_installed
    else
        echo -e "The system tested is not in the Debian Branch. "
        echo -e "The method written in this script is for Debian Branch conventions."
        nl
    fi
    unset -v manually_installed default_installed user_installed
}

```
Boils down to:
```

manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
apt-mark showmanual | sort -u > $manually_installed
gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | \
  sed -n 's/^Package: //p' | \
  sort -u > $default_installed
comm -23 $manually_installed $default_installed > $user_installed
awk 'NF' $user_installed 

cp $user_install packages.txt   That 1fallen was referring to.
rm -f $manually_installed
rm -f $default_installed
rm -f $user_installed

```
I use that list to reinstall applications during a migration.

---

### Post by madscientist032 on 2024-04-06
Just wanted to pop in & say THANKS for all the recommendations & detailed instructions on everyone's approach to this situation. Some of the techniques mentioned in here are relatively new to me and I will have to play with them on my sandbox system (which is also a 22.04 + win10 dual-boot) before I depoy them on my main workstation (E.G I want to try out oldfred's recommendation of having 2 / (root) partitions & getting my /home data separated (right now it's just a standard OotB install) accordingly. I can do backups w/o issue.

guiverc: Your AskUbuntu post is exactly what I was looking for. I'm bummed that there's some bugs with that method and not enough time for that to be resolved before Noble's release. I'll have to keep tabs on that and test with 22.04 in the meantime on my sandbox install. I would hope the bug is patched either sometime after noble's release or during a point release (eg 24.04.x)

MAFoElffen: Super appreciate the script! I will absolutely give that a try on my sandbox and see how things work out. 


Thanks so much for all the feedback folks!

---

### Post by oldfred on 2024-04-06
You can move /home, but i prefer to keep /home inside each install. I may want different settings and sometimes if installs are different you should not share a /home.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[Move Home]([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)

The actual user settings are small. My /home is [FONT=monospace][COLOR=#000000]1.5G [/COLOR][/FONT]including Firefox.  Because /home is small I now keep it as part of / (root) which is a total of 14GB with /home in my typical 30GB / (root). But I am using Kubuntu which is slightly smaller & do not have any snaps which can take a lot of space.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install.

For data only storage, for better security, you might want to add nodev and nosuid options, if you want to add some options. Even noexec could be useful, if you never intend to have any programs or scripts there.

I have always used /mnt/data and linked folders back into /home. But I may change to something more like TheFu's suggestion as /data or something off root rather than /mnt.
The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install.

For data only storage, for better security, you might want to add nodev and nosuid options, if you want to add some options. Even noexec could be useful, if you never intend to have any programs or scripts there.

Mount to /d - TheFu
[https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243](https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243)
Label=WD1 /d/WD1 ext4 defaults,nofail,nodev,nosuid,noexec  0 2

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)  & 
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

There are lots of other posts, some prefer a bind mount.
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

