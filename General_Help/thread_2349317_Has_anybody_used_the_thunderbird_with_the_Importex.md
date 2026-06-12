---
title: "Has anybody used the thunderbird with the Import/export add-on?"
date: 2017-01-13
forum: General Help
---

### Post by l6griffin on 2017-01-13
I had a laptop fail to boot ubuntu but I was able to copy off my home directory to a thumb drive. Now I would like to import the thunderbird profile into a new install. I don't seem to be able to get the add-on to work. It doesn't see the .thunderbird directory (/home/.thunderbird).
Larry

---

### Post by ajgreeny on 2017-01-13
I'm not aware of an import/export add-on, but if you're using a file manager to copy the folder just hit Ctrl+H to show hidden files and folders and ~/.thunderbird should be there.

I have never used the import/export options in the menus so can't comment on that; it is much easier to transfer the whole of the hidden .thunderbird folder.

---

### Post by SeijiSensei on 2017-01-13
In case that's not a typo, it's not /home/.thunderbird, but /home/username/.thunderbird.

---

### Post by l6griffin on 2017-01-13
ajgreeny, The add-o is ImportExportTools-3.2.5.xpi for thunderbir and the file browser is limited. The pr when it goesoblem also exist in Tools-import and Profile manager. Tools-import asks what you want to import then hangs when it goes to the next scree. Profile manager doesn't see but one profile and has no file browser so forget switching profiles. There was a -migration option in seamonkey but that is no loner in the software center. I also have to wonder about the profiles are named since most docs I've read so far say they are named default yet all the profiles I've found on my systems are similar to 2hu8npd0.default with default as the extension.

[ 						 					]("https://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[**[COLOR=#000000]SeijiSensei, not in nautilus.[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")

---

### Post by SeijiSensei on 2017-01-13
I don't know what "not in Nautilus" means.  If you mean Nautilus reports your home directory as "Home," then that's just a convention using "Home" to represent "/home/username/."  Every user's home directory is /home/username.  You shouldn't actually be able to create a directory called /home/anything as an ordinary user, since the /home directory itself is owned by the "root" (administrative) user.

Two other ways to reference your home directory in the terminal are to use the environment variable $HOME or the tilde "~" in a path.  Both $HOME/.thunderbird and ~/.thunderbird represent /home/username/.thunderbird.

The Thunderbird directories are indeed called something.default.  If there are multiple such directories, the active one is determined by the Path= parameter in the file /home/username/.thunderbird/profiles.ini.  On my machine that file looks like this:
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=r7ecq3n4.default
Default=1

```
The name of the directory is an arbitrary sequence of characters like "r7ecq3n4" above that is created the first time you open Thunderbird.

---

### Post by l6griffin on 2017-01-13
Nautlus is the file bbrowser installed in Ubuntu

You are correct 'Home' is a commonly used convention to denote the users personal directory.

Unfortunately the use of a profile.ni file limits the ability to switch profiles since the ini file would have to modified or and a new created to replace it every time a profile was switched. The ability would be nice to view contents as thunderbird would display them. It becomes a non-issue since thunderbird as implemented to run on ubuntu only sees one profile.

---

### Post by SeijiSensei on 2017-01-14
Can you not simply copy the old /home/username/.thunderbird folder into the new /home/username directory and get Thunderbird to use it simply by opening the application?  Like ajgreeny that's the way I've migrated my Thunderbird configuration across machines for quite some time now.  I don't really understand why you're going to all the trouble of using an .xpi or worrying about multiple profiles.  You do have to make sure that your user and group IDs are identical across the machines, but if you are the only user you should have 1000:1000 as your uid:gid on both.  The .thunderbird directory and its subdirectories should have 0700 permissions to ensure the privacy of the messages stored therein.

It just feels like you're making this more complicated than it needs to be.

---

### Post by l6griffin on 2017-01-14
You are4 correct again and it is also more complicated than I wish it to be. The last time I went through this exercise was about 5+ years ago.  Seamonkey came out with anew version 2.0. They also include with the new version a migration wizard since they had changed the profile. The wizard took some effort to learn how it worked once learn it was just a matter of repetition to merge all seamonkey and netscape file back to 1997. I was hoping things had improved with thunderbird.

The ability to be able to copy a directory  and its' sub-directories to another machine re-start where you left off is one of best features of  unix/linux. I was doing it with sudo cp till I learned about gksu nautilus and then it was drqag and drop. Either way you have to be doubly sure where you copy your home directory. Even after working with computers for over thiry years mistakes are still made, and things get complicated. ;)

---

### Post by SeijiSensei on 2017-01-14
So is your problem solved?  If so, please use the Thread Tools to mark this thread [SOLVED].

---

### Post by chris354 on 2017-01-14
For this problem i would have used rsync with flags to ensure hidden files are also copied over. Something along like below.

```
cd /home/<user>/; rsync -arpv .thunderbird/ remote:/home/<user>
```

You will probably want to add the n flag to do a dry run so you can check what the output will be and the brackets make it so the cd only affect this command.

---

### Post by deadflowr on 2017-01-14
As long as a profile folder is located somewhere within the mounted file system, either locally or remotely, you can add it to your list of available profiles easily by running the -ProfileManager option
```
thunderbird -ProfileManager
```
Click on Create Profile
Click next
Give the Profile a name and then click on Choose Folder.
Then navigate your file system to where ever the profile you want to use is.
select it 
then click finish 
and that profile is eternally part of your current thunderbird profile selections, as is.

*mounted file system would mean any where that is mounted.
Could be located within your own Documents folder or on an external hard drive connected via usb
or on a network share down the hall in another room.
(or if you just want to use a profile that you moved into the current .thunderbird folder)
as long as the location is accessible to the user at hand.
Otherwise you run into the problem of it erring out because the location is not mounted within the current file system.

---

### Post by l6griffin on 2017-01-15
deadflowr, That worked. I had already moved the profiles to a directory that the import/export add-on would see. I had also previously created a new profile but hadn't pointed it to an old profile not wanting to corrupt the old profile some how. I looked at the profile.ini file and I now have an entry for each of the of the old profiles. Each entry with a new profile name has a path to the old profile name. By chance the last profile I created was the old profile I was using when the laptop was knocked of the table. I'll sort thru what I now have and marked this closed. First I'm going to have to nurse a cold or streph throat that arn't bad yet.

---

