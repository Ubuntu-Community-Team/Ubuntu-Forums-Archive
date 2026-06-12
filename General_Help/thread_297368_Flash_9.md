---
title: "Flash 9"
date: 2006-11-11
forum: General Help
---

### Post by dc12volthippy on 2006-11-11
Someone said to upgrade to Flashplayer 9, but I don't think it exists for Linux. Does it?

---

### Post by meng on 2006-11-11
Yes there is a beta.

---

### Post by aysiu on 2006-11-11
Read this:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by NeoChaosX on 2006-11-11
Download it from [here](http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html).

---

### Post by dc12volthippy on 2006-11-11
Ok,I have the beta, but I can't move the .so to the plugins folder (/usr/lib/firefox/plugins) because I don't have the permissions, so somebody please tell me how to change the permissions.

---

### Post by xopher on 2006-11-11
> **dc12volthippy said:**
> Ok,I have the beta, but I can't move the .so to the plugins folder (/usr/lib/firefox/plugins) because I don't have the permissions, so somebody please tell me how to change the permissions.

Well you'll need superuser rights to be able to move the file.

This is achieved with eg. the sudo command. You could either run a root nautilus and copy/paste the file graphically, or then just sudo cp filename.so /usr/lib/firefox/plugins

---

### Post by dc12volthippy on 2006-11-11
I don't understand, I'm like a complete Linux idiot, so I'd need you to walk me through it. The flashplayer file is on the desktop if it helps.

---

### Post by digby on 2006-11-11
copy and paste these 3 commands into a terminal (from ubuntuguide.org)
```
wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/
```

[edit] bleh... it shortens my links... you'll have to just download that one by clicking and saving it, but the rest should work fine as long as you run it all from your home folder

---

### Post by skathrein on 2006-11-11
Read [THIS]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox") section of the ubuntu starter guide.  It's command line but works.  Hope this helps.

---

### Post by dc12volthippy on 2006-11-11
That Didn't Work!!!!!!!!

---

### Post by digby on 2006-11-11
> **dc12volthippy said:**
> That Didn't Work!!!!!!!!
A little more info (e.g. the error message) might help us...

---

### Post by dc12volthippy on 2006-11-11
I had already downloaded the file! I checked the properties of the libflashplayer.so that is in the plugins folder, and it doesn't match up to the one I downloaded, plus it didn't work on the games I tried!

---

### Post by dc12volthippy on 2006-11-11
It didn't have an error message, it just did it and went through abunch of stuff.

---

### Post by dc12volthippy on 2006-11-11
Wait a minute, I tried it again and ths is what happened (just the lat two commands):dc12volt@dc12volt-desktop:~$ tar xvzf FP9_plugin_beta_101806.tar.gz
flash-player-plugin-9.0.21.55/
flash-player-plugin-9.0.21.55/libflashplayer.so
flash-player-plugin-9.0.21.55/readme.txt
dc12volt@dc12volt-desktop:~$ sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
Password:
cp: target `/usr/lib/flashplugin-nonfree/' is not a directory: No such file or directory
dc12volt@dc12volt-desktop:~$

---

### Post by skathrein on 2006-11-11
Ok, if you already have the .so file, try this:
In a terminal type:
sudo cp path/to/libflashplayer.so /usr/lib/flashplugin-nonfree/

So for example, say you have downloaded and extracted the libflashplayer.so file to your home directory (which let's say is called Bob).  Then the exact command would be:
sudo cp /home/Bob/libflashplayer.so /usr/lib/flashplugin-nonfree/

You will have to enter your password when executing this command, so just enter it and then press enter/return.  Let me know if that works.  Good luck.

---

### Post by dc12volthippy on 2006-11-11
It says "cp: target `/usr/lib/flashplugin-nonfree/' is not a directory: No such file or directory"

---

### Post by digby on 2006-11-11
> **dc12volthippy said:**
> Wait a minute, I tried it again and ths is what happened (just the lat two commands):dc12volt@dc12volt-desktop:~$ tar xvzf FP9_plugin_beta_101806.tar.gz
flash-player-plugin-9.0.21.55/
flash-player-plugin-9.0.21.55/libflashplayer.so
flash-player-plugin-9.0.21.55/readme.txt
dc12volt@dc12volt-desktop:~$ sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
Password:
cp: target `/usr/lib/flashplugin-nonfree/' is not a directory: No such file or directory
dc12volt@dc12volt-desktop:~$
Hmm... did you have the flash8 plugin from the repos previously?

---

### Post by dc12volthippy on 2006-11-11
no

---

### Post by digby on 2006-11-11
> **dc12volthippy said:**
> no

Ah!  Ok - go back to this [link ]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")from Skatherin's post.  just above it, is instructions on how to install the flash8 plugin.  You may have to enable a repository that you don't have, but it has a link to instructions to that as well.

---

### Post by skathrein on 2006-11-11
Run this from a terminal:

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin


Then restart mozilla/firefox and then run:
wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 


Then restart mozilla/firefox

---

### Post by dc12volthippy on 2006-11-11
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libgtk1.2-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree gsfonts-x11
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.5kB of archives.
After unpacking 287kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
???

---

### Post by dc12volthippy on 2006-11-11
I'll be back in a half hour.

---

### Post by skathrein on 2006-11-11
That's odd.  Okay, try it the synaptic way:
Close firefox.
Go to System-->Administration-->Synaptic Package Manager
Enter your password
Go to Settings-->Repositories
(Assuming you are using edgy, but let me know if not, but you might be able to figure it out anyway with dapper), Click on the "Ubuntu 6.10" tab.
Looking at what is in parentheses, make sure the following are checked: (universe) (main) (multiuniverse) (restricted)
Then click close and you will have to relead by hitting the button.
Then click on search and search for "flashplugin-nonfree"
Then left click and then mark for installation.  Then hit apply at the top.

Now, try to run this command again from a terminal:

wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/

[good luck]("http://inconsequentialstuff.blogspot.com/")

---

### Post by viciouslime on 2006-11-11
> **digby said:**
> Hmm... did you have the flash8 plugin from the repos previously?

You mean flash 7 plugin from the repos, right? Just to clarify for anyone else who is new to ubuntu and tries to follow this thread but is unable to find version 8...](*,)  :D

---

### Post by clebin on 2006-11-11
> **dc12volthippy said:**
> I'll be back in a half hour.

You should know what these commands actually mean.

To run a command as super-user, you put sudo before the command.
To copy a file you use "cp <source file> <destination>"
To navigate to a folder as you would do if you weren't using the terminal, use "cd <exact folder name>"

Personally, I just copied the file to my Firefox plugins folder without installing any older version:

cd Desktop
cd flash-plugin-folder-blah
sudo cp flash-plugin-folder-blah.so /usr/local/firefox/plugins


EDIT: I assume people are saying you should install the earlier version so that it gets upgraded automatically when a newer version comes out (I'm newer to Linux than I am to Unix). Try following their instructions first.

---

### Post by ebash on 2006-11-11
You don't need root permissions in order to install a plugin for firefox. You can download the plugin manually and install it in your home folder. Put the files in your home folder in the folder ~/.mozilla/plugins/

```

mkdir -p ~/.mozilla/plugins/
cp flashplayer.xpt libflashplayer.so ~/.mozilla/plugins/

```

---

### Post by dc12volthippy on 2006-11-11
I meant drag-and-drop. But anyway, it worked! I cp'd the plugins through the terminal! Yay!

---

