---
title: "Working with an Ubuntu Server"
date: 2008-01-06
forum: General Help
---

### Post by RampageAI on 2008-01-06
I am considering options of creating a mixed Ubuntu/Windows office environment administrated by Ubuntu server(s), but as of yet I haven't been able to find out about some key issues even after searching for quite awhile.

Issue #1 - Group Policy (Domain Administration)
I know that Ubuntu/OpenLDAP (or another combination) will allow login authentication but what about making it so that home folders are redirected to a server properly and printers are setup after authentication regardless of which Ubuntu workstation is logged into.  Also, what about individual permissions on that workstation can those be administrated by a central server after authentication?  Is it possible to install software from the server to a large group of clients or push updates from a server to a large group of clients?

Issue #2 - GroupWare (Mail/Calendar/Address Book/Public Folders?)
I have found a very large number of great GroupWare tools that allow mail, calendar and address book sharing but what about public folders?  Is this specific only to Microsoft Exchange or can it be done with something like OpenLDAP?  Mostly I'm just puzzled why it's so overlooked among so many GroupWare tools.

Issue #3 - Server GUI?
I think this is an issue that gets talked about a lot.  Before I make a switch to an Ubuntu server though I need to know that the next person who gets hired in my place doesn't necessarily have to come with specialized Linux knowledge or at least that there are training options.  I could install a GUI for the server but can anyway say clearly why it's worth having or not having a server GUI?

Thanks for any help on these issues,

---

### Post by colo on 2008-01-07
I'm sorry I cannot answer all your questions to your satisfaction, but I'll at least try to answer some of them to my best knowledge:

1.) You can maintain your users and groups in an LDAP directory, as you already found out. Of course, it's also neat to have the same ~on all machines one could possibly login, and that's what samba could do for you (in a Windows/GNU-mixed environment). I've never personally dealt with such a setup's making (as I'm not a Windows-guy), yet have seen it working fairly well at several IT-departments I've been in.
When it comes to pushing software/updates to clients, I know there is this Windows Software Update Server (or whatever it'scalled) that can do this for MSFT boxes - however, I doubt that that there's a free replacement for *N*X available.
It's not that much of a problem to push software to GNU/Linux-clients that have proper package management - you could set up an apt repository of your own, and have cron-apt on each machine handle the rest (well, granted, that's more of an automated pull-mechanism then, but it still works the way you'd probably like it to).
Btw, rumor has it Samba4 is going to deliver really nice features for mixed networks, like an integrated directory service for managing user accounts (no need for OpenLDAP/slapd any more here) etc.

2.) I don't know Exchange, but I'm a fan of KDE's groupware application suite (KDE-PIM). I can only speculate about what "public folders" are, but it'd be easy enough to make a sub-directory of each user's samba-share (and home-directory) world-accessible, for other users to browse. Or export some sub-directory via HTTP/DAV. It might not be as tightly integrated as some Exchange-specific feature, but it sure does work - and work well.

3.) To be honest, I don't think you can avoid that. I couldn't take over an MCSE's place in a rush either, so anyone who's not familiar with the services you set up and use won't make it to replace you in your office. A "server GUI" won't make any difference here, simply because of the fact that having a GUI alone doesn't abstract away the underlying complexity of sysadmin tasks. You'll still have to know what you are doing, you'll still have to edit $configfily by hand - and it doesn't make any difference if your text editor's UI is rendered by using GTK, Qt, or ncurses. It doesn't give you any benefits at all, more to the contrary: an X server that's constantly running on any given machine just adds attack vectors for malevolent wrongdoers, as the code that's running in addition to all the viable services certainly isn't bug-free, and one or more of those bugs probably opens up a locally or even remotely exploitable exploitable security hole. It's just not worth risking that for having 16M colors instead of those displayable by an ANSI terminal.

---

