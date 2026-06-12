---
title: "$HOME/.dmrc and .gvfs drama"
date: 2008-06-14
forum: General Help
---

### Post by buntunub on 2008-06-14
Hi all. I just got through this drama today and noticed while fixing it that there are a ton of recent postings about these types of issues. This was the first time this has happened to me since the Hardy upgrade and I actually got this fixed so I thought I would post what worked for me.

1. This happened as a result of me copying files from my main user account over to another non admin account using gksu nautilus. These were files used with wine (not sure if that had anything to do with it or not but I dont think so).
2. Since I copied the files using gksu nautilus, the files copied in with root ownership. I then changed properties of each top level folder over to the user and user group.
3. When I tried to log back in to my main account the next time, I got the infamous $HOME/.dmrc error. I then did this to fix it:

```
sudo chown -R user /home/user
sudo chgrp -R user /home/user
sudo chmod -R 755 /home/user
sudo chmod 644 $HOME/.dmrc
```

I got those lines from other posts here, forget the OP's, but thanks for the tip.

4. I logged back into my non admin account and tested those files that I copied out. Everything seemed to work fine, but when I later tried to log back in to my regular account, I got that $HOME/.dmrc error again, and had to run that code over again to be able to log back in. Thinking something went seriously wrong with that whole copy operation, I deleted all those copied files, then tried to log back into my regular account. 
4. I got an error message stating that my $/home/user/.gvfs could not be found!
5. I checked /home folder ownerships and all was well. I checked every conceivable file and permission command I could think of and all was fine. However, not one command I ran from about 4.5 hours of Googling this issue, had any affect on fixing the problem. Frustrated and at my wits end, I did a reboot thinking the problem would rear its ugly head during the boot process. WRONG!
6. It finished rebooting and magically, all was well! I guess somehow it fixed the issue on its own during reboot. All I really learned from this whole ordeal was that gvfs is a system that still has a looooooooooooooooong ways to go yet to be called "stable". If its any consolation, try looking at the Fedora forums for some clue into just how big of a pain in the **** gvfs is for them. :)

---

