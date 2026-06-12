---
title: "Authentication Failure with Fingerprint Reader"
date: 2008-05-02
forum: General Help
---

### Post by Rocketman1882 on 2008-05-02
Semi newbie Ubuntu user here.  Recently purchased a Lenovo R61 Thinkpad with Suse on it.  I partitioned the harddrive, installed Ubuntu, and Suse last so I could use the Suse grub loader.  Anyways, the lenovo thinkpad has a fingerprint reader on it and I've been trying to get it to work in ubuntu.

I followed this thread:
[http://ubuntuforums.org/showthread.php?t=775217](http://ubuntuforums.org/showthread.php?t=775217)

And now I cannot boot into Ubuntu.  I changed my /etc/pam.d/common-auth file after backing it up, and now I can't log in, obviously.  When I boot into Ubuntu and try to log in, I get an "Authentication Failed" error, and nothing else.  And I haven't figured out how to log into recovery mode because in the Suse gui boot manager, there isn't an option for Ubuntu recovery mode - just Ubuntu, Suse, and a Suse Failsafe.  I know in the Ubuntu grub there is the recovery mode option and memtest, but I don't have access to that through my Suse boot manager.  

So I guess I'm asking for an alternative way to get into recovery mode in order to restore my common-auth file.  

Thanks!

---

### Post by jimv on 2008-05-02
Can't you just boot into Suse and fix the file on your Ubuntu partition?

---

### Post by Rocketman1882 on 2008-05-02
> **jimv said:**
> Can't you just boot into Suse and fix the file on your Ubuntu partition?

My Ubuntu partition is encrypted, so I'm not sure.  Could I still do that if it was?

---

### Post by Rocketman1882 on 2008-05-02
Solved the problem after reconfiguring my grub on Suse to display all of Ubuntu's boot up options.  Went into recovery mode, recovered the common-auth, and reinstalled Thinkfinger successfully.

Now I can swipe my finger at sudo prompts!  Huzzah!

---

