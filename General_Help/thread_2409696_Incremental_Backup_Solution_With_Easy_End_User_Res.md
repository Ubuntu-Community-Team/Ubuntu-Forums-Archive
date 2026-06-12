---
title: "Incremental Backup Solution With Easy End User Restore Interface?"
date: 2019-01-05
forum: General Help
---

### Post by jeff140 on 2019-01-05
[COLOR=#242729][FONT=Arial]Don't ask why. I need to devise an incremental file backup solution (writing to a USB attached disk array) that has a super easy interface to allow any end user (like even a receptionist) to restore a version of any file to their local workstation.  Most backup solutions' restore functions were designed with the Sys Admin in mind as the user.  This isn't my case.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My initial thoughts would be to devise a solution that stores the last 10 versions (or all versions in the last 30 days) in the same target folder but with an incremental number appended to the filename (filename_1.ext filename_2.ext). The end user can see the filenames date-time to determine when that version was created. The end user could browse the files via a mapped drive in Windows Explorer using SAMBA. I can think of anything easier for the user than that.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here's some potential challenges on the server side that may need to be addressed:[/FONT][/COLOR]

[LIST]
[*][FONT=inherit]Frequency of backup related to performance. We're talking a data storage folder containing probably 100,000 files and 5TB of data. The incremental backup needs to be run at least once an hour. So it's got to be a solution that is architected to handle pretty large file collections. I'm anticipating this may not be an issue though as the volume of file changes is low, maybe 100 files change every hour at most.[/FONT]

[*][FONT=inherit]Data duplication. Yes, storage is cheap, but with multiple versions the back storage requirement will be large. I don't think it's possible to have data de-duplication and let the end user be able to browse versions of files with a simple SAMBA file share. (Looked into RDIFF and you need to run the rdiff command to restore.)[/FONT]
[/LIST]
[COLOR=#242729][FONT=Arial]So I'd be open to a solution (free or low-cost) that instead of the users mapping a drive to the backup folder, they could bring up a web interface to browse the files and download as needed. Not quite as simple as mapping a drive but this would allow the backend to handle rebuilding a file version.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any suggestions on solutions?[/FONT][/COLOR]

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]jeff140[/COLOR]**]("https://ubuntuforums.org/member.php?u=1998900"),

You can take a look at Deja Dup which lets you schedule automatic (hourly, daily, weekly, monthly) backups and use a very simple restoration process (right click the file or folder from Nautilus > Revert to previous version, or Restore missing files).

I believe that this tutorial might be of help to you if you decide to explore that route:

[https://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](https://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

Bonus: Deja Dup (Backup) should already be installed on Ubuntu by default.

Hope this helps.

---

