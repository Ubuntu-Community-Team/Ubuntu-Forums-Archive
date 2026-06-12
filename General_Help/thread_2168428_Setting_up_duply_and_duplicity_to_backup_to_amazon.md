---
title: "Setting up duply and duplicity to backup to amazon S3"
date: 2013-08-17
forum: General Help
---

### Post by James_Corkhill on 2013-08-17
Hi
I have attempted to setup duply and duplicity to backup a wordpress site on ubuntu server, using this tutorial [http://www.guyrutenberg.com/2013/03/28/incremental-wordpress-backups-using-duply-duplicity/](http://www.guyrutenberg.com/2013/03/28/incremental-wordpress-backups-using-duply-duplicity/) 
(I've tried asking the author for help but not response).

I am getting the following errors when I try and run the backup, and was wondering if anyone on these forums would be able to help. I'm fairly used to linux but not set anything like this up before.

[COLOR=#000000][FONT=Helvetica]--- Start running command BKP at 13:04:38.166 ---[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Import of duplicity.backends.giobackend Failed: No module named gio[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/bin/duplicity\", line 1411, in <module>[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   with_tempdir(main)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/bin/duplicity\", line 1404, in with_tempdir[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   fn()[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/bin/duplicity\", line 1255, in main[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   action = commandline.ProcessCommandLine(sys.argv[1:])[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/lib/python2.7/dist-packages/duplicity/commandline.py\", line 1007, in [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ProcessCommandLine[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   backup, local_pathname = set_backend(args[0], args[1])[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/lib/python2.7/dist-packages/duplicity/commandline.py\", line 900, in set_backend[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   globals.backend = backend.get_backend(bend)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/lib/python2.7/dist-packages/duplicity/backend.py\", line 158, in get_backend[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   return _backends[pu.scheme](pu)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica] File \"/usr/lib/python2.7/dist-packages/duplicity/backends/_boto_single.py\", line 49, in [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]__init__[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]   import boto[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ImportError: No module named boto[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]13:04:38.495 Task \'BKP\' failed with exit code \'30\'.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]--- Finished state FAILED \'code 30\' at 13:04:38.495 - Runtime 00:00:00.329 ---

Thanks in advance[/FONT][/COLOR]

---

### Post by Habitual on 2013-08-17
sshfs and fuse+s3fs can do this job easily.
or "s3cmd sync" can all synchronize to an s3 bucket easily.

[Duplicity Requirements]("http://duplicity.nongnu.org/duplicity.1.html#sect1") have you met them?

---

### Post by James_Corkhill on 2013-08-18
Thanks I think I've got s3cmd sync working and i think that will do what i need :)

---

### Post by Habitual on 2013-08-18
Awesome! Good stuff.

---

