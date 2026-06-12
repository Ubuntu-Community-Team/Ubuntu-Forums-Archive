---
title: "Luckybackup Ubuntu 22.10 - Broken Pipe"
date: 2022-10-23
forum: General Help
---

### Post by rudolf-kunzli on 2022-10-23
[INDENT] 					I just upgrade to Ubuntu 22.10 and almost everything went fine.
Except LuckyBackup that produces the following error message:

---
 [COLOR=#ff00ff]Removing old snapshots and logfiles of task: [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR]
=====================================

 

 Removed all older snapshots data
 

 Removing /home/rudolf/.luckyBackup/snaps/Ubuntu-backup rudolf-20221021234656.changes.log
 

 Removing /home/rudolf/.luckyBackup/logs/Ubuntu-backup rudolf-20221021234656.log
 =====================================
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR][COLOR=#ff00ff], starting[/COLOR]
Source : [COLOR=#0000ff]/home/rudolf[/COLOR]
Destination : [COLOR=#0000ff]/media/rudolf/Backup RK/home/[/COLOR] 
 building file list ... 
  0 files...
  100 files...
 
 ---snip---

 [COLOR=#ff0000]E[/COLOR][COLOR=#ff0000]RROR: rejecting  excluded file-list name: rudolf/.luckybackup-snaphots rsync error:  protocol incompatibility (code 2) at flist.c(994) [Receiver=3.2.5] [/COLOR]
  2800 files...

--- snip
 
 [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: [sender] write error: Broken pipe (32) [/COLOR]
 .
 [COLOR=#00ffff]    -----| Backing-up profile, logfiles and snapshot data -> Ok |-----[/COLOR]
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR][COLOR=#ff00ff], finished[/COLOR] 
=====================================

This worked perfectly before the upgrade...
It's produced on all 3 systems upgrade to 22.10

Any idea ? 				[/INDENT] 			
  			   		
 			 			 			[INDENT] 				 					[Last edited by rudolf-kunzli]("https://ubuntuforums.org/posthistory.php?p=14116563"); 22 Hours Ago at 09:00 AM. 				 				 			[/INDENT] 			 			 				 			 				 			 			 			 		 	 	 		 			 				 				 					[[IMG]https://ubuntuforums.org/clear.gif[/IMG] Edit Post]("https://ubuntuforums.org/editpost.php?p=14116563&do=editpost")  				  				 				 					[[IMG]https://ubuntuforums.org/clear.gif[/IMG] Quick Reply]("https://ubuntuforums.org/newreply.php?do=newreply&p=14116563&noquote=1")  				  				                                               [[IMG]https://ubuntuforums.org/clear.gif[/IMG] Adv Reply]("https://ubuntuforums.org/newreply.php?p=14116563&noquote=1")                                                  				 					[[IMG]https://ubuntuforums.org/clear.gif[/IMG]  Reply With Quote]("https://ubuntuforums.org/newreply.php?do=newreply&p=14116563")  				  				 				 					 [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/multiquote_40b.png[/IMG] ]("https://ubuntuforums.org/newreply.php?do=newreply&p=14116563")  				 			 			 				 					 				 				  				  				  					  					 					 					 [ ]("https://ubuntuforums.org/report.php?p=14116563")

---

### Post by coffeecat on 2022-10-23
Duplicate of [https://ubuntuforums.org/showthread.php?t=2480192](https://ubuntuforums.org/showthread.php?t=2480192) . Thread closed.

Please do not post duplicates in different parts of the forum. This causes confusion and dilutes community effort. If you do not get a reply within 12-24 hours, you are welcome to bump the thread.

---

