---
title: "Printer sharing problem"
date: 2007-06-13
forum: General Help
---

### Post by Moonshine on 2007-06-13
"the server for the printer does not have the correct driver installed...."

Is the error I get when I try to add the printer that is shared with Samba. I am trying to add it to Window XP clients, from Xubuntu. Printing works fine locally, and samba file sharing works file sharing works fine over the network. 

The printer is a Canon MP150.

Would anyone have any ideas?? :popcorn:

---

### Post by mitch.c on 2007-06-14
> **Moonshine said:**
> Would anyone have any ideas??

Yes. Forget Samba.

If you need it for file sharing... great. For printing, CUPS is a wonderfully capable IPP print server out of the box, and Windows has absolutely no trouble printing via IPP.

All that is really required, is configuring CUPS to listen to incoming requests. Then on the Win XP side: Add Printer -> Network Printer -> URL = [http://yourxubuntuserver:631/printers/printer_name](http://yourxubuntuserver:631/printers/printer_name)

See the blue link in my sig for details. Need help, let me know.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

