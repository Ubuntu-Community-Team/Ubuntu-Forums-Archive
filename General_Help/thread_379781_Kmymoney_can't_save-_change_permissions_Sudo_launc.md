---
title: "Kmymoney can't save- change permissions? Sudo launch?"
date: 2007-03-08
forum: General Help
---

### Post by zami on 2007-03-08
I just installed Kmymoney and setup a file, noted some transactions, etc.

But I can't "save" my money file.  I get the message

> 
Error - KMyMoney

Unable to write changes 
to '/usr/share/apps/kmymoney2/templates/en_US/mine.kmy'
OK


The /usr/share/apps/kmymoney2 directory permissions are set to "root only".  I noticed a lot of programs that work just fine are also root only.

Should I change the permissions of the kmymoney2 directory and subfolders?  Should I launch with sudo kmymoney?  Something else?  If I launch something with sudo, wont it "time out" eventually and leave me again unable to save?  Or will it just ask my password again if it times out?

Thanks for any help!

-zami

---

### Post by zami on 2007-03-08
In answer to my own query...

I went ahead and did a 
gksudo nautilus
and cruised on over to the /usr/share/apps and change the permissions to kymymoney2.

The program is working AND saving now... huzzah!  I'm not sure if this was the proper route to take but it worked, gurshdarnnit.

If someone happens across this post though and has a better thought on how to fix the save problem, do share!

(I'm also sure I could have chmod'd the directory from the terminal, but wasn't sure how.  It seems I give a daily "thank you" to whoever it was that first posted "gksudo nautilus" in some forgotten thread.  What a HANDY command!)

Thanks!
-zami

---

### Post by msak007 on 2007-03-11
Well it seems you fixed it, but I'm not sure why you had the problem or what the proper solution should have been. One of the greatest KMyMoney resources is the user distribution list, and you'll get any KMyMoney specific questions answered there much faster. Go to [https://lists.sourceforge.net/lists/listinfo/kmymoney2-user](https://lists.sourceforge.net/lists/listinfo/kmymoney2-user) and sign up. People send emails to that distribution list, and other users provide solutions. The devs are very active with regards to that list and are usually the ones that respond to the emails and provide solutions, workarounds, or other suggestions.

---

