---
title: "Please help...Lost home directory"
date: 2005-04-23
forum: General Help
---

### Post by lukem on 2005-04-23
I was working thru some of the suggestions for multiple sounds in other threads, when I rebooted and got a message at the log on screen that my home directory did not exist?  I'm presently logged on under a failsafe mode, and I can see the other two home directories on this machine.  One is a samba share I set up for myself and the other is for another user.  

I don't recall doing anything to delete my home directory!!!.   If anyone can help, Please offer a suggestion.  

Intel, Hoary

Thanks
Luke

---

### Post by k.ODOMA on 2005-04-23
Is /home on a separate partition? Is it possible that it's not mounted?

---

### Post by lukem on 2005-04-23
Unfortunately not.  Everything is on the same partition.  

Thanks for the suggestion however

---

### Post by lukem on 2005-04-24
Can any one tell me how to copy areas of hda1 (where my files may still be) to another location (as a file?) so I can examine them with hexedit or something similar and possibly retreive some missing data?

Thanks again

---

### Post by bin on 2005-04-24
I wonder if you've accidentally moved your user folder to somewhere else?

Any chance you had a USB or similar drive in place.

You mention a Samba share - any chance you user folder got moved there?

The find command may help in locating your folder if it is still on the same drive but hiding somewhere.

---

### Post by lukem on 2005-04-24
bin
Thank you for trying to help.
I don't have any other drives (like usb) that it could have been moved to and I did search for it even in the samba share, but no luck yet.

Still looking for a way to look at hda1 for the missing files.  It's not important that I restore the whole directory, I just want to try to save some family photos that I had not backed up yet.

Thanks again

---

### Post by crazybill on 2005-04-24
You think that you might have accidently moved your home directory somewhere.

Try this 
Open a terminal. Then type (or copy and paste the following:

**# find / -name *username* -print**

where "username" is your username

---

### Post by lukem on 2005-04-24
Thanks crazybill.  I learned a lot about  find.  Unfortunately I did not find my files though.  Find returned two hits

/var/run/sudo/username  and
/var/mail/username

I was unable to cd into /var/run/sudo and the file in /var/mail was empty.

---

