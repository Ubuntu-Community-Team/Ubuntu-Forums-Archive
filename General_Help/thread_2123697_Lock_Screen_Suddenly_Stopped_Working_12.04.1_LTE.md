---
title: "Lock Screen Suddenly Stopped Working 12.04.1 LTE"
date: 2013-03-08
forum: General Help
---

### Post by spl3001 on 2013-03-08
Hi everyone.  Let me begin by saying I have scoured the internet for the exact solution to the exact problem I'm having, but I have not found one yet.

Up until yesterday, my system has been functioning just fine.  Now the lock screen no longer accepts my password (though it works everywhere else).  Let me go through the steps I've take already:

1.) My home directory was encrypted with ecrypts.  From the console, I mounted, unencrypted, copied back all the files to my home directory with all the permissions in place.  I thought it might be an .ICEAuthority issue (an error showed up mentioning the file but that has dissapeared, and I don't remember what the error was.)  I couldn't even LOG IN when this was happening, but by unencrypting my home directory, I can at least do that now.  I could however still do sudo at the console.
2.) **/etc/shadow**: checked on owner: it IS **-rw-r----- 1 root shadow**
3.) I can do the "Switch user..." option in the lock screen and log back in just fine.
4.) Password works everywhere else
5.) I still have a README.txt in my home directory (it is a link to a ecrypts folder).  When I do an ecrypts-mount-private, I get:
```
Inserted auth tok with sig [dc92cdd150de8786] into the user session keyring
setreuid: Operation not permitted
```
I'm not even sure what that file is anyway.  It's in my home directory.  Not sure if that's even related.

This problem started while the system was just sitting there and went into lock screen by itself, as it had done several times earlier that day with out issue.  I have looked around the internet and found that older versions of Ubuntu were having similar issues, but I don't seem to have the same symptoms.  Thanks in advance.

---

### Post by spl3001 on 2013-03-12
Sorry to bump this.  Any one have any ideas?  I can post extra info if needed.

---

