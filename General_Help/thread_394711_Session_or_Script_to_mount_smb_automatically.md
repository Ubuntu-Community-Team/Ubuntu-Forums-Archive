---
title: "Session or Script to mount smb automatically?"
date: 2007-03-27
forum: General Help
---

### Post by Lutherian on 2007-03-27
Thanks to the good folks of this forum I was able to get the correct command syntax to mount a remote drive on my Ubuntu SMB Sever.
i.e [COLOR="Red"][sudo mount -t blah blah etc etc][/COLOR] which was strange as I though I'd need to use the [COLOR="Blue"]smbmount command[/COLOR]...but I'm getting sidetracked..

Works every time from the console :) 

The next logical step is to mount it automatically and I though I was being clever by putting the command into the session manager, instead of using [COLOR="Red"][sudo mount etc, etc][/COLOR] I put [COLOR="Red"][gksudo mount etc, etc][/COLOR]

Turns out I'm not that smart ;) as it doesn't work.

From my reading I believe there's another alternative via editing the **[COLOR="Blue"]init.d[/COLOR]** file which I tried, but to no avail.

This brings me back to a related query I had in the beginning of the year where I was trying to make a script file that will automatically run a sudo command without asking for the password.

In any case - I'm curious about the session manager system not working and the alternative **[COLOR="Blue"]init.d[/COLOR]** method. 


In advance, I just want to say thanks to all the guru's out there, after a lot of reading I hope to be able to contribute in the same polite and kind way you all have done.

---

### Post by HereInOz on 2007-03-27
Check this out:

[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

Or this:

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by Lutherian on 2007-03-28
LOL, It's seems I got my init.d and fstab mixed up!

Thanks for the info, got it sorted out in  2 minutes thanks to you.

---

