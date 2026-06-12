---
title: "Unable to copy the user's Xauthorization file"
date: 2008-06-07
forum: General Help
---

### Post by euchrid33 on 2008-06-07
Whenever I try to run Synaptic or Add/Remove, I get the following error:

[B]Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.[/B]

I haven't been fooling around with permissions or anything like this, so I'm not sure what's happened.  I've already had a look around the forums, and tried this command:

sudo chown USERNAME .xauthority

I get a 'no such file' error.  Same happens when I try it with .xauthorization.

I can still open synaptic through the terminal.  Any suggestions?

---

### Post by x1a4 on 2008-06-07
Hi,

That's .Xauthority not .xauthority--capital X.

Also, check that the file /usr/share/applications/synaptic.desktop contains the following:
```
Exec=gksu -S /usr/sbin/synaptic
```
And modify it accordingly if it doesn't.

Further, run ```
sudo visudo
``` and ensure the sudoers file has the following:
```
%admin LOCAL=(ALL) ALL
``` then ensure you are in the **admin** group

If you have made additions to the sudoers file, ensure the changes aren't the cause.

---

### Post by cousinit2 on 2009-04-16
I had this same problem. Nothing I tried worked on it....
Until I used System Monitor and saw my /tmp folder was full.
Synaptic copies .Xauthority there (apparently) before making changes to it.
So, after deleting some partial downloads, Synaptic started working again just fine!

Sometimes the dumbest things can be the best correct answers to the problem at hand....

---

### Post by ccmorris on 2009-06-07
The suggestion by cousinit2 worked for me when I encountered the same problem. I doubt that my tmp folder was full, but deleting all the stuff in there worked anyways. :)

---

### Post by t2a on 2009-06-09
Yep, for me the same. Emptied the /tmp directory and it works like a charm.

Cheers,
Raymond.

---

