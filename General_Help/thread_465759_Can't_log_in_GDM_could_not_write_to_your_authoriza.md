---
title: "Can't log in: GDM could not write to your authorization file"
date: 2007-06-06
forum: General Help
---

### Post by tk03759 on 2007-06-06
Okay, so I connected my Ubuntu to the internet for the first time in a few weeks and it told me there were updates. I let it perform all updates (40 or so) and it told me it needed to restart. I restarted and when it got to the log in screen, I typed in the user name and password and then got the error:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. Please contact your system administrator."

I looked it up on in the forum and didn't get much help, so I looked it up on the internet and found an article that said that (obviously) the disk was probably full. One of the guides ([http://www.gossamer-threads.com/lists/mythtv/users/175048]("http://www.gossamer-threads.com/lists/mythtv/users/175048")) advised that I delete some files. So at the login window, I used ctrl + alt +F1 to get to the shell, logged in, and used "df-h" which showed it to be 100% full.

I tried emptying the /tmp/ folder, but I don't think it worked, or that there was really anything in there. I'm really at a loss here. I'm completely not used to working with the shell so I'm gonna need step by step instructions for how to do anything.

PS. Seeing it was a space issue, I wound up using "sudo apt-get remove wine" to uninstall wine and sudo apt-get remove easyubuntu" to uninstall easyubuntu (which I'd been meaning to do for a while). IT didn't do anything, but I feel better knowing that easyUbuntu isn't installed anymore. :D

---

### Post by viciouslime on 2007-06-06
If you type "cd ~" or "cd /home/<your user name> that will take you to your home directory. From there you can use the command "rm" followed by the filename of what you want to delete. BE CAREFUL there is no getting files back once you delete them like this. If you had files in your Trash Can/Deleted Items Folder/Whatever it is called and you didn't empty that, then you might want to go to /home/<your user name>/.Trash there you will find those files and can "rm" them.

---

### Post by viciouslime on 2007-06-06
Another quick thought, assuming you just have a root partition and no separate home partition (the default in Ubuntu at present) then you might want to run "sudo apt-get clean" that will clear apt-gets cache, i.e. remove all the debs you have downloaded, they will of course still be installed, but as it stands apt-get caches the deb file so it doesn't need to be downloaded again should you want to reinstall. However, if you're short on space it's a great way to free some up. If you ever do need those files again, apt-get will automatically re-download them anyway. :)

---

### Post by tk03759 on 2007-06-06
Okay, well I removed a few things.. though I couldn't quite get the rm command to work, but there wasn't really anything in my trash or home folder anyways. I still can't log in though. I did "df -h" again and here's the result of that:

[IMG]http://i18.tinypic.com/6gwah6e.png[/IMG]

Would it make any difference that I have 4 users set up on this computer?


------- EDIT ------

Okay, I uninstalled the GIMP and it left enough space to restart. I'm in the GUI now. Thanks!!!

---

