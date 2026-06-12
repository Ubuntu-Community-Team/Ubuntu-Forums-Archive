---
title: "CUPS setup,  but always prompts for user/pass?"
date: 2006-11-28
forum: General Help
---

### Post by a.d.gardiner on 2006-11-28
hey all,

sorry to post about something which has been widely mentioned here. I've looked but I still can't find a fix for problem.

I just setup CUPS on xubuntu, and can see the windows printer I am trying to print to accross the network.

First I did this "smbclient -L accounts -N" to get this...

```


        Sharename       Type      Comment
        ---------       ----      -------
        HP1200          Printer   HP Business Inkjet 1200 Series
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Documents       Disk
        Printer         Printer   SagePDFPrinter
Domain=[ACCOUNTS] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

Then used the information there to point CUPS at smb://accounts/HP1200 via the web browser based CUPS manager at [http://localhost:631/](http://localhost:631/)

Thing is I can't 'start printer' or send anything to it without CUPS prompting for a user and password. My system crudentials don't match what its asking for!?

Im confused! lol

Any ideas?

---

### Post by feest on 2006-11-28
well you can change the /etc/sudoers file so you have default acces to all root privileges. more of this can be found on google

---

### Post by a.d.gardiner on 2006-11-28
I think what I mean is do I have to create a user for this, or is it asking for the accounts machine user/password. If so the accounts crudentials don't seem to match up either.

If it can't be fixed anybody reccomend a good linux/CUPS compatible usb print server?

:)

---

### Post by a.d.gardiner on 2006-11-28
Cool, thanks, not tried it yet, will in a few when my boss is out,

so its essentially a permissions thing on xubuntu box, nothing to do with the windows machine.

So I guess its just a case of Terminal >> "sudo gedit 'relevant file'".

It seems really odd i need to grant myself access to the permission to print on a shared network printer?

Is it standard procedure to have to modify things like this to get CUPS running?

:)

---

### Post by a.d.gardiner on 2006-11-28
Just looking it over one thing im really worried about is nuking my whole installation by wrongly modifying the sudoers file.

currently my file looks like this:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

If I uncomment the bottom two lines would that work? One presumes because this file is completely commented out that it serves no current purpose on my system?

Alex (confused.. again!) :)

---

### Post by a.d.gardiner on 2006-11-29
Ok, I checked the manual and did this DUH!:

Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups

Select the group shadow and click Properties.

Add the user cupsys to the group.

Restart CUPS with this command:
```

$sudo /etc/init.d/cupsys restart

```

Then I loaded the HP1200 PPD file from linxprinting.org (they have most other printers there too) and it worked. CUPS now no longer asks for a password and I could correctly configure my printer. Only thing is it won't print centered! lol :)

---

