---
title: "VMWare Server error when trying to start"
date: 2006-10-27
forum: General Help
---

### Post by NZ-Wanderer on 2006-10-27
HI all, I was running vmware server on edgy before the official version was released last night with no problems at all.
I decided to clean things out and reinstalled Edgy today, and have just reinstalled vmware server...

Now I get an icon error:

```
Could not load icon
Failed to open file '/usr/share/pixmaps/vmware-server.png': Permission denied
```

And then when I try to run vmware server I get this:

```
Could not launch application
Failed to execute child process "vmware" (Permission denied)
```

Can anyone help me please?? (simple instructions please :) )

---

### Post by NZ-Wanderer on 2006-10-27
Just another thing...

If I do a "sudo vmware" in terminal it works and loads vmware..

Hmmm, while it loads vmware, it doesn't actually load either of my virtual XP's, If I try to open either of my XP's it returns the error:

```
Unable to change virtual machine power state: Could not execute /usr/lib/vmware/bin/vmware-vmx.

```

when I try to open either of my XP's.

---

### Post by sefs on 2006-10-27
Maybe your user configuration is set so that root has permissions.

Try checking under /home/<yourcomputername>/<yourhomedirectory>/.vmware

This is a hidden directory so you will have to show hidden files.

right click on the .vmware and click on the permissions tab and see if it says root or anything else ... it should be set to the user you are currently logged in on.  

That could be the problem not sure....

---

