---
title: "Help!"
date: 2007-04-11
forum: General Help
---

### Post by bks on 2007-04-11
I have a problem.  I have been trying to get the flash player to work, so I used aptitude and it would just hang and hang and generally do nothing.  So I went to Adobe's site and got the .tar.gz file and ran that.  Flash works perfect, but now I have a whole other problem. I can't run apt-get, aptitude, synaptic or update manager for anything else.  I keep getting an error message that says I need to fun "dpkg --configure -a" manually.  When I run the command it says:

bradford@bradford-laptop:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading... 

And there it stays.

What can I do, I need to download a new kernel release!?

---

### Post by banditti on 2007-04-11
Have you tried to remove the package?

apt-get remove package_name
apt-get autoclean

---

### Post by bks on 2007-04-11
I get the same error:

bradford@bradford-laptop:~$ sudo apt-get remove flashlplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
bradford@bradford-laptop:~$

---

### Post by bks on 2007-04-11
Bump...sorry this is serious.  Meanwhile I'm scouring the net. thanks.

---

### Post by bks on 2007-04-11
Just FYI, I think I got around it.  I was able to get into Synaptic and uninstall flash.  I am currently updating the kernel and then I will reinstall flash.  Thanks fo the help though.

---

