---
title: "update buggy Azureus 2.5.0.0 in repositories?"
date: 2007-08-02
forum: General Help
---

### Post by bsmith1051 on 2007-08-02
I experienced this bug, and when I searched the forums I found a lot of other people with it, too.  The version of Azureus in the repository, 2.5.0.0, is buggy and almost immediately crashes and won't reload.  The solution is 'simply' to download the now-old 2.5.04 update and overwrite the original Azureus2.jar file with the new one.  But none of this should be necessary.  Can someone please report this to whomever maintains this package in the repository?  It would be very helpful if it was updated to the 2.5.0.4 version.  Thank you.

---

### Post by Theimon on 2007-08-02
This has been reported quite a few times already, but since it's easy to work around the problem I guess it's no priority for the devvers to fix it.

---

### Post by bsmith1051 on 2007-08-02
> **Theimon said:**
> it's easy to work around the problem
yes, but Ubuntu beginners won't have any idea how to manage it, nor should they have to.  Oh well...

---

### Post by Theimon on 2007-08-02
Well, when they bump into the problem, they come here and search the forum (because for some reason I expect people to do some research before asking questions..) and find the answer.
I agree it's odd they it haven't fixed it yet, because it's an old bug. But luckily there are some solutions around.

---

### Post by bucketoftruth on 2007-08-07
> **Theimon said:**
> This has been reported quite a few times already, but since it's easy to work around the problem I guess it's no priority for the devvers to fix it.

Can you share that work-around with the rest of us?

EDIT: Or I could just link it once again so it tops out in google: [http://ubuntuforums.org/showpost.php?p=1680674&postcount=13](http://ubuntuforums.org/showpost.php?p=1680674&postcount=13)

---

### Post by bsmith1051 on 2007-08-07
workaround is to manually update the main 'Azureus2.jar' file,
[http://ubuntuforums.org/showthread.php?p=3028407](http://ubuntuforums.org/showthread.php?p=3028407)

---

### Post by Malvolio on 2007-09-01
Manually updating Azureus2.jar doesn't help that the local Ubuntu Azureus also uses an out of date SWT.jar file.  The workaround I did was to just uninstall Azureus and download the program off their site and run it from that.  And yes, I did try manually installing updated files to the local Ubuntu install but without being able to update the SWT.jar file I just ran into new problems.  I've been hoping Azureus has it's own dedicated repositories as I'm somewhat uncomfortable running Azureus 'invisibly'.

---

