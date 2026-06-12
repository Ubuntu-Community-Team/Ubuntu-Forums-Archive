---
title: "Network folder only has windows network"
date: 2016-06-08
forum: General Help
---

### Post by janat08 on 2016-06-08
So the network folder only has windows network folder? Im not using  the <snip> samba since it's ubuntu on ubuntu sort of deal and despite  the share folder option being a dumb security feature. Additionally my  software doesn't appear to have "the full library" of software since  16.04 articles would indicate that it should for example have samba and a  couple of other thing's aren't there, so besides the softwares deficiencies it's supplemented with eccentric behaviors where installed and updates refuse to load and yet the all page is fine all the time despite requiring hypothetically internet as that's where it's utility lies. Any chance that these are by some humorous fashion are rather connected, where the software isn't working and then nor does share a folder option.

---

### Post by bab1 on 2016-06-08
> **janat08 said:**
> So the network folder only has windows network folder? Im not using  the <snip> samba since it's ubuntu on ubuntu sort of deal and despite  the share folder option being a dumb security feature. Additionally my  software doesn't appear to have "the full library" of software since  16.04 articles would indicate that it should for example have samba and a  couple of other thing's aren't there, so besides the softwares deficiencies it's supplemented with eccentric behaviors where installed and updates refuse to load and yet the all page is fine all the time despite requiring hypothetically internet as that's where it's utility lies. Any chance that these are by some humorous fashion are rather connected, where the software isn't working and then nor does share a folder option.
Anything is possible.  You would need to be more specific with what is actually happening. Tell us what error codes you get or describe a specific action that does not give you the expected results.  I've used Samba and NFS for more than 10 years with Linux (8 years with Ubuntu) with no failures.  Occasionally there are regressions but they are quickly resolved.  I find that most problems (95%) are due to misconfiguration.

By default Ubuntu ships with only the Samba client software.  You need to install and configure the server.

---

### Post by Morbius1 on 2016-06-09
> So the network folder only has windows network folder? Im not using the <snip> samba since it's ubuntu on ubuntu sort of deal .....
Long ago a Red Hat / Gnome developer knew a guy who knew another guy whose girlfriend’s mother's hairdresser told her that Samba was just for Windows. It's not true but the developer had never seen it before so he just assumed it was true.

"Windows Network" is the label he gave to what happens when you enter smb:/// in your file manager. He could have labelled it "Samba Shares" like KDE does, or perhaps "Netbios Network", or even "Scarlett Johansson Network" - although she would have been a little girl back then and that would have been creepy.
> Additionally my software doesn't appear to have "the full library" of software since 16.04 articles would indicate that it should for example have samba and a couple of other thing's aren't there ....
The samba server package is not installed by default in Ubuntu and while it's true that smbclient itself is no longer installed by default libsmbclient is and that is what the file manager uses to access samba shares..

---

