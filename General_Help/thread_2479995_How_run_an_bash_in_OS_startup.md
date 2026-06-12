---
title: "How run an bash in OS startup ?"
date: 2022-10-15
forum: General Help
---

### Post by aug7744 on 2022-10-15
Hello.
Thanks for reading my topic.

I need to create an bash file to run pre install commands (sudo dpkg -i *.deb) when installing softwares in an pre installed Ubuntu.
I want the bash running in an terminal window to show progress information.
After all bash commands are finished the bash need to be removed.

Thanks for your reply.

---

### Post by TheFu on 2022-10-15
What I do from the installer is just after I setup the keyboard, I toggle to a different TTY using <cntl><alt>F2. This isn't a GUI. It is console only.  From there, I run an ssh/scp/sftp client to pull over my storage setup script, edit it locally in the console using vim, then run it to create the partition table, partitions, set the types, format the partitions, create the PV, VG, and LVs, then format the LVs.  This has massively streamlined my storage configuration on servers and desktops.

No terminal, since there isn't any GUI, but the result is the same.

Then I toggle back to the GUI TTY (is that F7 or F1 now?) and continue with the storage setup.  Now, instead of having to use the terrible TUI to create thing all those things, I just need to select the partition or LV and assign it to a purpose and mount location.

I always install Ubuntu Server for production use (even on my desktops), so I don't know what a desktop installation might look like.  I haven't done a production desktop install in over 2 yrs. Sorry.  I did a test install a few days ago, but those don't get all the fancy, customized, storage configurations, so I haven't done the script thing.

Since 20.04, Canonical has been screwing around with the automatic installation tools which has frustrated many people who want 100% automatic installs. Something massively changed when they switched to the "Live Installer". I think that's what they call it.  Both the Desktops and Server use it now.  Meh.

Perhaps these ideas will help you? Probably not.  Automatic installs are very convoluted for some reason I don't understand.  I just want enough to get the OS installed  with the storage setup the way I want and to have an ssh server running. Then I can point ansible at the system for all the real configuration work.

---

### Post by aug7744 on 2022-10-15
Thanks again.
You help very much here in the Ubuntu forums.
Your reply about more complex install tasks is good to read.
I want an more simple way.
Perhaps creating an systemd service pointing to multiple bash files can be the solution.
In any way ... thanks very much for your reply.
Have an nice night.

---

### Post by vanadium on 2022-10-16
A script can be automatically started in a graphical terminal emulator after launching the latter. For the default terminal emulator, the syntax looks like

```

gnome-terminal -- your_command

```

To run that on startup, an autostart entry can be made containing that command.

---

### Post by TheFu on 2022-10-16
> **aug7744 said:**
> Hello.
Thanks for reading my topic.

I need to create an bash file to run pre install commands (sudo dpkg -i *.deb) when installing softwares in an pre installed Ubuntu.
I want the bash running in an terminal window to show progress information.
After all bash commands are finished the bash need to be removed.

Thanks for your reply.

BTW, using dpkg directly isn't recommended.  If you use 'apt', the dependencies will be searched and installed from the .deb files.  Also, installing .deb files can have negative impacts which will make for a system that cannot be patched in 3-6 months due to dependency issues.  

Better to use 
1) the official Canonical repos, then 
2) an official PPA from the specific project team, then 
3) an AppImage/Flatpak/Snap, then 
4) install from .deb files that are from known sources, but not for Ubuntu, then 
5) install from source provided by the specific project team.  

That's my order of preference for installation of software.  When installing using .deb files directly, be certain to keep a list so you can remove those packages to get out of "APT Hell" in a few months, and patch the system.  Also, when installing using options 3, 4, 5, you've just taken on the manual patching for those items and lost a key reason why repos and PPAs are so much better.  Automatic updates.  There are tools to check for AppImage and Flatpak updates and there isn't a good way to stop snap updates - those come when they want - even if you want to delay them for a month.  
The snap store has the same issue that other packages have - forgotten releases by the specific packaging team.  Too many package types dilutes where each project team needs to spend their time and for a small team, they just become a hassle.

---

