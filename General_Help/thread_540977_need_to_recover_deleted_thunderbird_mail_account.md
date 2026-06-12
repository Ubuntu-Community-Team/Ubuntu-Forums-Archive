---
title: "need to recover deleted thunderbird mail account"
date: 2007-09-02
forum: General Help
---

### Post by zapcojake on 2007-09-02
Hello,  I have 2 Linux distro's on my box.  Ubuntu and Sabayon.  My primary use system is the Ubuntu install which is where I have a couple years worth of email stored.  I installed Sabayon and as an experiment I tried using symlinks in my home folder to my original .mozilla-thunderbird and .thunderbird folders.  It did not work so I rm -rf'd the symlinks as root and it seems to have taken the original files with it.  Is there a way to get them back?  They don't seem to be in the trash in my Ubuntu home folder or in anything I can find in the Sabayon install.  I tried a couple of tutorials about recovering deleted files from /proc but it is empty.  Would testdisking the partition Sabayon is on do any good?  It is my testing ground for various OS's and gets formatted frequently.  


Past all this is there a good way to centralize my mailbox?  I.E on folder 2 or more distro's could both use as an inbox?   Thanks,   Jake

---

### Post by fjgaude on 2007-09-02
I can't help you with any recovery of lost files but I've used one .Thunderbird file to handle many distros over many systems over the years.

After you do a semi-fresh install of Thunderbird, i.e., just start to install then exit. You now have a profiles.ini file in your hidden .thunderbird. Edit it to point to the file that has your thunderbird mail database, the Path=xxxxxxxx.default file. Soft link as needed, not hard.

On my main box I have the .thunderbird folder on a raid5 array, and copy it down the line to other machines. On the main box I have each mail installation pointing to that same .thunderbird folder. I have copies on three different boxes for safety, using Unison to do the syncing.

It's hard to fully put into words but I think you get the message.

frank

---

### Post by zapcojake on 2007-09-02
Yes, thank you that will help in the future.   

I have done some digging and I have a .mozilla-thunderbird/ea14qxlu.default folder that contains many things including Mail/inbox/mypop.account/inbox and inbox.msf.  The inbox file contains all my lost messages in one very long text document.  Is there a way to make Thunderbird reconsider this document and restore my messages?  I tried copying every file, directory and sub-directory over one at a time and haven't had any luck.  When I copy the .mozilla-thunderbird and .thunderbird directory that contains the above mentioned files and then restart Thunderbird the new Account Wizard opens up like it was never setup.  It seems like there has to be a way to get Thunderbird to re-recognize my messages.

---

### Post by fjgaude on 2007-09-02
You need to make sure in profiles.ini that the Path=xxxxxxxx.default is the one that is being used by your new partial install. This partial install is what I was pointing to: start the install, and then exit. You will now have a .thunderbird folder, hidden, that you use to edit its profiles.ini file and change the Path= to the exact default that you have saved. Don't do anything to the original .default, keep it as is. You want to use the whole folder and after you change the Path= from the new install, and you exit and reload Thunderbird you will have all your old stuff.

frank

---

### Post by zapcojake on 2007-09-02
So the folder can always exist anywhere as long as I point the profile to it?

---

