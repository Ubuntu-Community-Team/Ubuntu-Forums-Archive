---
title: "Symlink to Downloads Folder Doesn't Work?"
date: 2023-08-15
forum: General Help
---

### Post by somebodeez on 2023-08-15
I usually don't ask, I just figure it out and plough on regardless, but now I'm here with an account regarding another issue and it may be necessary to re-install my Ubuntu? in the near future, I was wondering if those people who know a lot more than me might have the answer to my unique? strange scenario, it might even give them an idea to re-configure their own system, who knows, since I'm unable to find anything like it anywhere else(or maybe I'm just not looking hard enough) or they may just look at it and think what an idiot is that some sort of joke.

Long ago I used to have a separate /home partition, but that never really worked, whenever something got broken to the point a fresh install was necessary, the problem normally existed somewhere within the /home folder, so even after a fresh install with the existing /home folder the problem still remained, so I just generally salvaged what I could formatted everything and started again including a new fresh /home folder. But that was rubbish and it didn't work for me, so I came up with my own solution to the problem.

So I have a partition named 'StoreX', don't worry about my naming conventions, I'm old skool and it's got an 'X' in it so it's kewl, and have all my important(well important to me) folders stored on this partition, triple backed up to external drives by another rubbish bash script(probably) just in case. During the installation process I immediately add StoreX to the fstab file thingy, and run my bash script which creates a whole bunch of Symlink's to my safe/protected folders, for me this is on another level and works way better than just having /home(in full) on another partition.

EDIT: If I install an new application, I identiy the folders/file associated that come with it, move those folders to 'StoreX' and create new Symlinks and add them to my bash script, that way I don't loose all my configuration setting when I reinstall the applications using yet another bash script.

If it hasn't gone whoosh over your head by now don't worry one day I will figure it out myself and as said plough on regardless. But if you can understand what's going on? As you'll see at the end of my bash script I use 'sed' to edit the .config/user-dirs.dirs and this is because if I create the 'Downloads' folder on 'StoreX' and Symlink to it in the for,,,,do loop, for some reason after a short period of time using my new fresh Ubuntu installation, the 'Downloads' folder gets deleted along with everything in it and the Symlink obviously is then broken.

Why can't I Symlink to a 'Downloads' folder, does anyone have a clue or is this too stupid, to advanced, to ridiculous for here?

```
#!/bin/bash


FOLDERS="/media/alan/StoreX/Home (Symlinks)"


# .config/KeePassXCrc
# "/Downloads"


# Read the values with space
for i in "/App Data" "/Documents" "/Movie Database" "/Mount" "/.jocala" "/.kodi" "/.config/keepassxc" "/Pictures" "/.cache/qBittorrent" "/.config/qBittorrent" "/.local/share/qBittorrent" "/Scripts" "/Temp" "/.smbcreds"; do


if [[ -d "$HOME$i" ]]; then
    rm -r "$HOME$i"
#    echo "Removed directory $HOME/$i"
elif [[ -f "$HOME$i" ]]; then
    rm "$HOME$i"
#    echo "Removed file $HOME$i"
fi


ln -s "$FOLDERS$i" "$HOME$i"
#echo "ln -s $FOLDERS$i $HOME$i"


done


if [[ -f "$HOME/.config/KeePassXCrc" ]]; then rm "$HOME/.config/KeePassXCrc"; fi
ln -s "$FOLDERS/.config/KeePassXCrc" "$HOME/.config/KeePassXCrc"


sed -i 's/$HOME\/Downloads/\/media\/alan\/StoreX\/Home (Symlinks)\/Downloads/g' $HOME/.config/user-dirs.dirs 



```

---

### Post by oldfred on 2023-08-15
I do similar thing and use scripts.
But do not have to change any app file locations.
I did this because I have multiple installs and wanted same data in all of them.
I used to be able to share Firefox, but that stopped working, if any version difference.

These are all similar posts on topic:
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

TheFu suggests not using /mnt but just a /d.
Mount to /d - TheFu
[https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243](https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243)

---

### Post by somebodeez on 2023-08-15
I had the Firefox thing with a separate /home partition, when I started Firefox for the first time after a fresh install but keeping my old /home partition, it had a mental breakdown because the files I had were for a different version, so I don't concern myself about backed up Firefox folders anymore because I have a Mozilla account and all my bookmarks and addons are backed up on the cloud(Mozilla servers) so as soon as I login to Firefox it simply refreshes my bookmarks and installs the addons that I use automatically, the only thing missing are cached internet data, pictures cookies, etc, all my login passwords for websites are stored in Firefox so as soon as I login it's ready to use.

It's only Buck Ball in those link's from 15 years ago who seems to do a similar thing to me, but manually deleting and Symlink'ing to folders, I'd hope he's written his own script by now to automate the process.But I do it for ease and speed of installation and backup, not for multiple OS installs, I could/can change my scripts to use multiple installs for example other distro's auto mount in /run/media/$USER/ so all I have to do is add an 'if' statement to check if /run/media/$USER/ exists else use /media/$USER/ instead, but I don't have multiple installs so I don't need to, 

After I run this script I run my application installation script, then setup MySQL manually and import my database, because I don't know how to do that any other way, and I can be up and running with a new fresh install of Ubuntu which is setup, configured and fully operational in less than probably an hour, as if I've literally just rebooted. My media library in Kodi, my shared toorents all my other household media devices can still access my MySQL database, everything is as it was. But the only thing that doesn't work in all this is that if I have my /home/Downloads folder on my StoreX partition and create a Symlink to it for some weird unexplainable reason I open Nautilus and at some point randomly the Symlink is broken, and if I go check my StoreX partition the Downloads folder has been deleted and gone along with everything in it. The only way I've found to get around this is to edit the user-dirs.dirs file, but then when I open Nautilus the Downloads folder icon no longer appears in the explorer window, it's in the list on the left menu but not in the actual window,, and I just wondered while I was here if anyone knew why if I Symlink to the Downloads folder it doesn't work gets deleted.

EDIT: Everything else all the other folders, etc works perfectly it's just the Downloads folder.

You can test it yourself, create a Downloads folder somewhere other than your /home folder, delete the /home/Downloads directory and create a Symlink instead pointing to the Downloads folder you just created, carry on doing what you normally do on the computer and at some random point you'll notice the Symlink is broken, now check the location you created the new Downloads folder and you'll discovered it's gone, disappeared, deleted, obviously don't put anything in it or download anything important, because that will gone too.

---

