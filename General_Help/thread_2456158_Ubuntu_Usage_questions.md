---
title: "Ubuntu Usage questions"
date: 2021-01-05
forum: General Help
---

### Post by COKEDUDE on 2021-01-05
Is there a way to set up Ubuntu as a server in an office and meet all of these needs? All of the computers in the office use Windows. I would like to be able to use the server to backup AutoCAD project files, Our library files for AutoCAD, Word, Excel, Quicken, QuickBooks and PDF files? I would also like to use the server as a print server for HP-1050c, Okidata 5200, and HP-7740. I know Linux works well with Windows, but Windows unfortunately does not like to work well with Linux.

---

### Post by CelticWarrior on 2021-01-05
You want a server with two roles, files and printers.
I see no reason for it not to work regardless of the clients OSes but is there any specific reason for using Ubuntu in this context? Setting up another Windows for this would be trivial.

---

### Post by COKEDUDE on 2021-01-05
> **CelticWarrior said:**
> You want a server with two roles, files and printers.
I see no reason for it not to work regardless of the clients OSes but is there any specific reason for using Ubuntu in this context? Setting up another Windows for this would be trivial.

I am sick of virus's, malware, and all the other problems Windows has. I have virus protection, malware protection, and a firewall. I have never had any of these problems on any type of Linux server.

---

### Post by TheFu on 2021-01-05
File and print servers is sorta what got Linux into companies back in the 1990s.

However, support for an specific printer is always a question until it is up and working. Postscript printers with IPP network support will "just work." HP tend to be the best non-postscript supported printers. Okidata 5200 - who knows?

Any sort of files can be served from Linux to any different clients.  You might want to deploy a document management server, not just a simple file server.  Sometimes that is very useful, provided a librarian can be available to organize the documents and workflows. DMS handle document versioning automatically.  I've seen that embraced and ignored. Some people don't trust that versioning of a file with the same name happens and they insist on adding a -v1, -v2, -v3 ... to the filenames.
Or perhaps something like nextcloud which can completely transform the way a company works. Nextcloud as any modules that can be very helpful these days, like nextcloud-talk. It is a video, voice, text chat server. Perfect when a company doesn't want to pay external providers for that. Lost and lost of modles for nextcloud. Most are 1-click installs.

Maybe setup each as a trial in separate VMs? See what the different groups like.

---

### Post by COKEDUDE on 2021-01-06
> **TheFu said:**
> File and print servers is sorta what got Linux into companies back in the 1990s.

However, support for an specific printer is always a question until it is up and working. Postscript printers with IPP network support will "just work." HP tend to be the best non-postscript supported printers. Okidata 5200 - who knows?

Any sort of files can be served from Linux to any different clients.  You might want to deploy a document management server, not just a simple file server.  Sometimes that is very useful, provided a librarian can be available to organize the documents and workflows. DMS handle document versioning automatically.  I've seen that embraced and ignored. Some people don't trust that versioning of a file with the same name happens and they insist on adding a -v1, -v2, -v3 ... to the filenames.
Or perhaps something like nextcloud which can completely transform the way a company works. Nextcloud as any modules that can be very helpful these days, like nextcloud-talk. It is a video, voice, text chat server. Perfect when a company doesn't want to pay external providers for that. Lost and lost of modles for nextcloud. Most are 1-click installs.

Maybe setup each as a trial in separate VMs? See what the different groups like.

Do you think a document management server would be useful for a small 3 person office?

---

### Post by TheFu on 2021-01-06
> **COKEDUDE said:**
> Do you think a document management server would be useful for a small 3 person office?

Perhaps, but I'd go all-in on Nextcloud for that team.  I had a tiny company, just a few more people than yours and we tried a DMS (Alfresco) for about a year.  1 person couldn't understand it and wasn't going to.  The effort to support it during an upgrade was pretty painful, so I dropped it for an NFS+sftp server for the team. Nobody complained at all.  Alfresco competes with $1M+ DMS systems, so I certainly wouldn't head that direction.

Nextcloud is a company dropbox-like tool that does other things too. Maintenance for it is pretty easy. There are clients for every platform and for most of the addons.  I use 4 addons on Android to handle ... let me see:
[LIST]
[*]File sync - drop-box with easy sharing within a team
[*]News/RSS feeds - same view of all RSS feeds regardless of which client I'm on.
[*]Talk/Chat/Text/Video meetings - video meetings are necessary these days
[*]Contacts (integrates with Android)
[*]Calendaring (integrates with Android)
[*]Tasks - like a todo list
[*]Notes - mostly for shopping lists, but almost anything. Stuff other people put on Github in a GIST, I create a Note.
[/LIST]

The web-client is pretty great. I don't use the Linux thick client.  Nextcloud-Files can be accessed using WebDAV, so any file manager on any platform should be able to access it.

We limit Nextcloud access to the LAN, so remote people must use our VPN for access. Common sense, really.  Don't put corporate assets on the internet directly. Require a VPN, always.  Ok, we aren't really THAT strict. Some of our people have static IPs at home, so we've allowed those IPs direct access to Nextcloud.  All the Nextcloud traffic uses HTTPS with a LE cert. We aren't protecting supersecret govt stuff here, though I've done that in prior jobs.

There are Docker Nextcloud setups if you just want a quick look at it. The Nextcloud team makes a Docker image, which is probably trustworthy.  I've never used docker. I don't trust it from a few lies they pushed early on. I did a real, manual, NC install, into a virtual machine years ago.  Just moved to NC v20 last weekend.  Of about 20 addons, 1 didn't migrate smoothly - and I haven't fixed it yet.  I could have fallen back to 19.x.  Almost always the patching/upgrades go smoothly, but having a backup BEFORE is part of my steps. I don't trust their pre-upgrade backup methods.

Or you can start with a simple CUPS + Samba server. Samba should only be used by Windows clients.  Everyone else should use NFS or sftp instead.  IMHO.

---

