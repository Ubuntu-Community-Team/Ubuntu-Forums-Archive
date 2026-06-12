---
title: "I broke it again (cant log on)"
date: 2012-12-06
forum: General Help
---

### Post by greatsirkain on 2012-12-06
Long story short: I uninstalled some stuff now it wont boot up, I get the menu for ubuntu, recovery mode etc it seems to be going ok, I see the lubuntu loading screen then a window pops up saying something about my screen resolution being set to minimum. None of the options it gives me work (like use default config, the box just flashes but does nothing) . I never get to the actual password screen because it freezes after that.

Short story longer: I was using lxde with ubuntu to start with then I noticed there was loads of unity and gnome stuff running making my computer freeze up all the time so I removed all of that, thing seemed to be going good then I installed lxde login manager or something because the boot looked a little disjointed jumping from lubuntu to ubuntu. Rebooted and that's when it happened. Any ideas how I can fix it?

I booted from my ubuntu live usb thinking I might be able to reinstall some things and remove others but I can't even open my files because 'they don't belong to me' so is there a way I can log into my files files and settings from the the live version? 

I did back the system up to the cloud but I'm not sure how to go about this to make sure I don't lose anything or have to mess around reinstalling everything? Help?!?

mini story: I need to replace the login for ubuntu or I need to access my ubuntu install & files from ubuntu live and reset everything to about an hour ago. As a last resort I need to use the backup of my version I put on the cloud from the live version.

Edit:  
tried this suggestion from askubuntu but it didn't work:
ubuntu@ubuntu:~$  ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
ubuntu@ubuntu:~$

---

### Post by greatsirkain on 2012-12-06
...sudo...
ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...

 found it mounted it in tmp opened it in nautilus annnnd it's locked

clicked on properties, noticed there is an option to share this file, with 'guest account'. Tried that and it said I had to install windows sharing service or something but when I tried to do that I got this:

Can not install 'samba' (E:Unable to correct problems, you have held broken packages.) 

It's ridiculously annoying that you can't easily log into your own user account with your own user name and password from a live version of the same OS. And when I tried to restore my back up from Ubuntu One it said there were no back ups to restore. If I lose all my stuff again I'm done with it. I wouldn't of had to mess with the packages if unity was so laggy and full of complete rubbish like zeitgeist. ](*,)

Edit:
I was trying to restore the wrong system folder...I think someone needs a nap. Welllll, it doesn't give you options in back up you have to open the web page to see all your devices....It even has a back up of the first time I messed it up with a different install.

---

### Post by greatsirkain on 2012-12-07
I have the files, I have ownership of them with read write privilages, I have them mounted but they're all still encrypted??
tried some stuff:

$ sudo ecryptfs_passthrough /media/91b2804e-3346-4322-a55c-5d84a2c07055
[sudo] password for sir: 
sudo: ecryptfs_passthrough: command not found


sudo ecryptfs-unwrap-passphrase /media/91b2804e-3346-4322-a55c-5d84a2c07055

sudo mount -t ecryptfs /media/91b2804e-3346-4322-a55c-5d84a2c07055 /home/sir

sudo ecryptfs_passthrough /media/91b2804e-3346-4322-a55c-5d84a2c07055

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA." From me?? Why??!!
ecryptfs-mount-private 

e$ sudo ecryptfs-recover-private utility
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/91b2804e-3346-4322-a55c-5d84a2c07055/home/.ecryptfs/sir/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [e1a5d475f40fab77] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.4R0DAopB].
INFO: Found [/home/.ecryptfs/sir/.Private].
Try to recover this directory? [Y/n]: n

 muahahahahaha success! And it's only 5:15am

---

