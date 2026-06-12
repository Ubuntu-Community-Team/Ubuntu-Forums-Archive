---
title: "Sbackup not working"
date: 2007-02-07
forum: General Help
---

### Post by lakelovers on 2007-02-07
I've read most of the posts regarding simple backup, and have not found a solution. I have configured sbackup using sudo gedit /etc/sbackup.conf, and I have set a destination on the sbackup GUI, the same as in sbackup.conf. Sbackup indicates it's starting and gives a reference number but nothing is backed up. The back up target is a second internal drive that is partitioned and mounted. I used sbackup with a usb drive for awhile and it worked fine until the drive dropped dead. Any ideas on getting sbackup working? Or, suggestions for another backup program for Ubuntu.

---

### Post by Polygon on 2007-02-07
why are you manually editing the config file?  is there some reason not use the GUI?

maybe try running sbackup from the terminal, and see if any helpful error messages pop up

---

### Post by lakelovers on 2007-02-08
I edited the config file because the opening screen on sbackup says you can and also reading other postings on the same question there are comments about editing the config file. I used the GUI to set the configuration but tried editing the config file to see if that corrected anything. It did not, but I made sure that it was not in conflict with the GUI settings.

Finally, I found the cause. After perusing the config file, again, I noticed that under the General heading that the "lockfile" was on. I notated the file (#), and bingo, sbackup went to work.

[general]
maxincrement = 7
#lockfile = sbackup.lock
target = /second_drive/lost+found
format = 1

---

### Post by lakelovers on 2007-02-08
Well, I guess I was fooling myself. I found that the "lockfile" reset itself so it that must be a requirement. Nevertheless, Sbackup did save all the designated files but that must have been coincidental to my editing the config file. The problem now is that I cannot restore the saved filed. I tried deleting a photo then restoring it from sbackup. It appeared to be working but the file didn't appear where it should have, and I couldn't fine it using the search funtion. So, I have to assume that the file was not restored. It's frustrating. I'll keep searching for a solution but if anybody can help I'll certainly appreciate it.

Jerry

---

### Post by lakelovers on 2007-02-08
Don't know what the heck is going on, but now Sbackup is working perfectly backing up and restoring. I didn't do anything with the app after posting my last note. I had Sbackup timed to backup this evening and it did right on time, and I was able to restore a photo that I had renamed to ID in the backup. I guess I'm talking to myself, here, but I want to tell the whole story in case anybody is follows this thread. Jerry

---

### Post by glabouni on 2007-02-24
I've been experiencing a same problem, except that sbackup has been working for a couple month, and then without changing anything stopped working since later january.

when I start a manual backup from the GUI, a popup window says a backup process is started in background, the process do appear in htop but does nothing and fails silently.

I tried to point to another destination directory, to change ownership of the destination directory and to change permissions of the destination directory, to reinstall sbackup. none of that worked. 

-edit-
I just tried to remove and reinstall sbackup via apt-get and now it seems a manually initiated backup is working. I hope automatic backup is working too.
Once more, it seems a ubuntu related problem that emerged from nowhere for no apparent reason ends up fixed for no logical reason. 
If only there was some logic behind this, I would learn something from the experience. Instead if the problem appears again I'll be as clueless as I was the first time. how frustrating !

---

### Post by jongkind on 2007-02-25
Same for me. I stopped using sbackup and wrote my own scripts.

---

### Post by cboulanger on 2007-03-04
Hi!

I had the same problem (config data wasn't saved, no backup was started), and did a bit of error hunting. Seems like the config file is not written correctly, there is a section [places] with a config key "prefix" which is not being written. So the /usr/sbin/simple-backup-config script chokes at line 399 where it expects to get the value of this config key. 

After I changed line 399 to

		tail = "\troot\tif [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;"

everything worked for me. 

I also changed lines 488seqq like so

			# disable all tabs
			#self.widgets.get_widget("vbox11").set_sensitive( False )
			#self.widgets.get_widget("notebook2").set_sensitive( False )
			#self.widgets.get_widget("vbox12").set_sensitive( False )
			#self.widgets.get_widget("vbox14").set_sensitive( False )
			#self.widgets.get_widget("vbox21").set_sensitive( False )
			#self.widgets.get_widget("vbox22").set_sensitive( False )

because they were throwing errors. 

Hope that helps.

Christian

---

### Post by lakelovers on 2007-03-05
Thanks for your input. I have Sbackup working but don't remeber what I did to make it happen. Now I have another question. I using a small (6gb) second drive for my backups. It's filling up fast and I've wondered how I can delete old backup files to make more room. I was told to activate the "Purge" option but my versions of Sback up does not have a purge option. That facility was added after the version I have. I've tried upgrading to the new version of Sbackup, but have been unsuccessful. I'm running Dapper 6.06, and apparently Ubuntu 6.06 does not accommodate the newer verision of Sbackup. Any ideas on deleting old backup files?

---

