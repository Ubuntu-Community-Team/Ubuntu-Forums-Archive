---
title: "Drop box damon"
date: 2014-11-18
forum: General Help
---

### Post by SpikeLS6 on 2014-11-18
I downloaded and installed the 64-bit Drop Box software from the Drop Box site.

But, I must type into Terminal the Damon "~/.dropbox-dist/dropboxd" each time I use it. When I shut down Terminal the Drop Box program completely Exits. Consequently it is not able to stay constantly synced.

Where and how can I put this Damon to get the Drop Box Program to stay active with the Sync Icon on the upper Menu?

Spike

---

### Post by deadflowr on 2014-11-18
I would think that it should have added a startup entry.
But it seems yours did not?

You could try adding an entry, either through startup applications or manually
If through the startup appications program
use
```
dropbox start -i
```
as the command.
If manually, open gedit/text-editor of choice and copy/paste this
```
[Desktop Entry]
Name=Dropbox
GenericName=File Synchronizer
Comment=Sync your files across computers and to the web
Exec=dropbox start -i
Terminal=false
Type=Application
Icon=dropbox
Categories=Network;FileTransfer;
StartupNotify=false



```
then save as /home/user/.config/autostart/dropbox.desktop

From here on, dropbox should start at login, and sync the same.

Hope it helps, and hope it works.
And hope it is what you actually want...

---

### Post by SpikeLS6 on 2014-11-18
dropbox start -i
After this command enterred Terminal gold me to do a "sudo apt-get install nautilus-dropbox". I did, but it would not install because I have broken packages it can not fix.


[Desktop Entry]
Name=Dropbox
GenericName=File Synchronizer
Comment=Sync your files across computers and to the web
Exec=dropbox start -i
Terminal=false
Type=Application
Icon=dropbox
Categories=Network;FileTransfer;
StartupNotify=false
When I tried to save this command I got an error screen that the Folder contents could not be displayed. The File */home/user/.config/autostart; no such file or directory.
   Looking at the results I can not guess what I need to do next.

---

### Post by deadflowr on 2014-11-18
> [COLOR=#000000]*/home/user/.config/autostart[/COLOR]

Change user to your current user's name.
Example /home/bob/.config/autostart.

If you use gedit, when you save as, right click in the main folder window area and select show hidden files.
This should bring up the .config folder, and then you can open that to get to autostart, and the add the entry name to that.

Also, what dropbox package from dropbox did you install?
nautilus-dropbox should have been install if you installed from the dropbox deb package...

---

### Post by SpikeLS6 on 2014-11-19
Nothing will Paste into my /Home/.config folder.

Would I be better off deleting everything Drop Box Related then downloading the Debian File to extract with Archive Manager?

I got the program I am trying to use now at: "www.dropbox.com/install?os=lnx and clicked on Ubuntu(ideb) 64-bit then used the 64-bit command of 
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -

---

### Post by Frogs Hair on 2014-11-19
I would completely remove the downloaded version and install nautilus-dropbox from the software-center. Start dropbox from dash and either connect to an existing account or create a new one if needed. I've not used the .deb downloaded from the website.

Edit: Prior to installing nautilus-dropbox open the home folder and use Ctrl + H to show hidden folders and delete the .dropbox folder if it wasn't already removed. A new folder will be created during installation.

---

### Post by oldos2er on 2014-11-19
Moved to General Help.

---

### Post by buzzingrobot on 2014-11-20
Adding "~/.dropbox-dist/dropboxd" (no quotes) as an entry in Startup Applications should work.  Replace the '~' with the full path to your /home folder.  E.g., "/home/username/.dropbox-dist/dropboxd"

---

### Post by spronkc on 2014-11-20
Thank you for the suggestion of deleting the Dropbox folder I had previously downloaded from the Dropbox website. 

 It kept disappearing on me similar to the description on the first postof this thread.  

Some of the other suggestion did not work for me.

I found the previously download Dropbox folder in my home folder, right clicked it and deleted it by moving it to the rubbish bin.

I then reinstalled Dropbox through the Ubuntu software-centre.  

I located it with Unity.  It then automatically took me through a couple more steps, and now it functions properly--syncing as it should, and not disappearing.

---

### Post by SpikeLS6 on 2014-11-21
I used the "Find" Command to find three different Drop Box entries and used "rm" to remove them.

I then went to the Ubuntu Software Center and searched for Nautilus-Dropbox and clicked on Install. An error screen came up telling me that there were too many Dependencies, so it would not install Drop Box.

I next went to Synatic and found three more Dropbox installs to try: a) Nautilus-Dropbox 2.10.0 - Trusty, b) Nautilus-Dropbox 1.6.1 - Trusty, and c) Dropbox. All returned an error screen of too many dependencies to install. I even used "Forced Version" in Synaptic, but had the same results.

I did a "sudo apt-get -f install", then repeated the above, but still dependencies halted the installation.

Can you please suggest a next step? Thank you.

To think that all this could have been prevented had I known that Nautilus preceded Drop Box in my searches for it in the Ubuntu Software Center when I started.

Spike

---

### Post by buzzingrobot on 2014-11-21
> **SpikeLS6 said:**
> 
To think that all this could have been prevented had I known that Nautilus preceded Drop Box in my searches for it in the Ubuntu Software Center when I started.


Are you running Ubuntu Unity or one of the other variants?  I ask because Nautilus -- the file manager -- is installed by default on Ubuntu Unity.  (Other variants use other file managers.)  

The actual Dropbox daemon must be downloaded from dropbox.com.  The "nautilus-dropbox" package allows you to do that, and it also configures Nautilus to more conventiently work with Dropbox.

In other words, Nautilus itself won't be *installed* as a dependency of nautilus-dropbox on Unity because it's already installed.

I'll assume you use Unity.

Try using Synaptic to search for 'dropbox'.  Mark any *installed* packages it finds for removal. (Multiple failed attempts to install the same package in different ways can leave the package management system in a state of disarray.)  If the Dropbox packages were installed correctly, and nothing else has affected the system's package manager, then the removal should be clean and simple, with only a very limited amount other dependent packages being removed. (Synaptic will show these to you before you commit to their removal.)   However, if Synaptic wants to remove a large number of packages, or packages that seem to you unrelated to Dropbox, don't do it.

If the first scenario is the one you see in Synaptic, remove the Dropbox packages.  Then, open a terminal an do "sudo apt update" and "sudo apt upgrade" to make sure the system is up to date and not missing anything.  Then, a "sudo apt install nautilus-dropbox" should install Dropbox.  If/when that succeeds, search in the Dash for 'Dropbox', launch it, and set it up.

---

### Post by SpikeLS6 on 2014-11-22
buzzingrobot,

I believe I am using Ubuntu Unity 14.04, because I once had to re-install Unity to get the Launcher and Menu back on the screen.

I did as you suggested and went through The Software Center and Synaptic looking for anything Drop Box or Nautilus-Dropbox. Finding nothing, I tried the Nautilus-Dropbox in Synaptic, but it advised there were dependencies. So I next tried the plain Drop Box 2.10.0. It began the install, but paused before finishing advising it needed "pyton-gpgme" to work properly. I searched for that file in Synaptic and found it, and the python3-gpgme listed below it. I installed both of them then started Drop Box as the screen asked. It installed successfully, I have the Icon on the Menu line, and it sync's properly.

Thank you very much for everyone's help on this snafu. I will show this thread as [SOLVED]

Spike

---

