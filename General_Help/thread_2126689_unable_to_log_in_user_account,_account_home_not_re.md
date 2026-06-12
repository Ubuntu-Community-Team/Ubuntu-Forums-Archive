---
title: "unable to log in user account, account home not recognized by root"
date: 2013-03-17
forum: General Help
---

### Post by Jack Vermicelli on 2013-03-17
Attempting to update my video drivers to what Steam requires, I  logged out and changed my session to the console, after being told I  couldn't run the script with x running. I tried to paste the location of  the script and realized that the clipboard doesn't carry across  sessions like that, so I changed my session back to Xubuntu desktop and  put in my password, only to get a black screen for a second and then be  dumped back at the login. Tried again, with same result. 
  I think I went back to the console, tried to startx there, but that didn't work either.
  
I *can* log in to the desktop on the guest account, but not my  own. Googled, found some tips, involving restarting and logging in as  root in the recovery console. (Was going to try modifying .ICEauthority  or .Xauthority, but haven't been able to get that far.)

The scary thing now, is that (as root, from recovery mode boot) "cd /home/ajs" tells me no such  location, "ls /home" returns nothing, "ls -l /home" returns "0."  "passwd ajs" returns with no such user. Still, my name (different  capitalization- "AJS") shows up on the login screen.

From the guest account I went into the Users options, confirmed that  my account still is shown, and noticed/remembered that while my username  is ajs, my home folder is /home/aj. 
  
Rebooting into recovery mode and dropping to root again, I first make sure  to mount with "mount -o rw, remount /". Again, "cd /home/aj" and "cd  /home/ajs" both tell me that the location is not found. At around this point I find I can no longer login as ajs to the console mode from the login screen.

  
Back into the guest account, I try "sudo thunar /home/aj" and it  looks like I don't have sudo permission, so I create another account in  the Users menu, and when I'm asked for an admin password, my ajs  account's password is accepted. 

  
I log out and into the new non-guest account, again try "sudo thunar  /home/aj", and am so relieved to find that the home contents are there, but that doesn't solve the problem. Any ideas? So much appreciated.

[http://www.reddit.com/r/linuxquestions/comments/1aftys/nuked_user_account/](http://www.reddit.com/r/linuxquestions/comments/1aftys/nuked_user_account/)

---

### Post by steeldriver on 2013-03-17
Do you have /home on a separate partition? if so it might not be mounted automatically in recovery mode

Back to your login problem - now that you have an alternative sudo account you can check/fix the .Xauthority and .ICEauthority on the old account from there - or you can mount /home in the recovery console

---

### Post by Jack Vermicelli on 2013-03-18
Thanks! I do have /home on a separate partition; I didn't realize that it wouldn't be mounted with /, and it didn't occur to me to attempt the below step from another user account at the same level as the my account in question.

"sudo chown username:username /home/username/.Xauthority" (per advice I had found elsewhere) appears to have solved it.

Much appreciated, steeldriver.

---

### Post by steeldriver on 2013-03-18
Great! glad you got it fixed

---

### Post by Jack Vermicelli on 2013-03-18
I don't suppose you'd happen to know (or would care to speculate on) what may have caused the problem? I don't know that it was anything that *should* have happened as a result of my actions, but it strikes me as very unlikely that it was spontaneous.

---

