---
title: "Can't run apt or Synaptic"
date: 2007-02-08
forum: General Help
---

### Post by bensode on 2007-02-08
Ok here's a fun one!  I get the following when trying to run any updates or installs with apt:

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.


So running sudo apt-get -f install ... I get:

Preconfiguring packages ...
(Reading database ... 104444 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I go into Synaptic Package Manager and try to "fix" the broken packages by marking samba for removal and get:

E: samba: subprocess pre-removal script returned error exit status 102
(Reading database ... 104443 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Any ideas how I can fix this?

---

### Post by tocleora on 2007-02-08
Doing a little searching on google, I see a lot of results with that error, but some minor digging only pulled up one possible solution... not enough space on the hard drive.  If that's not it maybe someone else has additional assistance for you, but you might check that just in case

```

$ df -h

```

---

### Post by shironeko on 2007-02-08
Delete samba. Don't try to reinstall it. Try to delete it completely:

As you can see here:

"
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ..."

It's trying to replace samba with a newer version, but as you can see later, an error ocurred and the newer version wasn't installed. That's why the problem persists.

Try deleting samba completely first. Do a sudo aptitude install -f
Then check that you can use apt-get (aptitude) agaIN and then afterwards try reinstalling samba.

---

### Post by bensode on 2007-02-08
Disk space is fine ...

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              27G   23G  2.3G  92% /


Running the aptitude -f resulted in the same error trying to remove, update or even purge Samba.

---

### Post by Fraoch on 2007-04-09
I've got the same exact issue.  samba is broken and won't let me touch it, Synaptic Package Manager or Automatic Updates.

Did you ever get it solved, bensode?

I never even touched samba, I'm not sure why it's doing this now.  Also this (obviously) prevents filesharing as well as any further updates or indeed any addition/removal of packages using Synaptic - it insists I correct the broken package first, which it can't fix, then it prevents me from doing anything else, saying that the broken packages must first be fixed.:(

---

### Post by Luke771 on 2007-04-12
I found this thread almost by mistake while looking for a solution to a similar problem; I don't se any "ultimate" answer here, so I'll reply even if this thread is kind of old, it can be useful to someone else (assuming you have fixed it in soome way during the two months since your post.).
Your problem seems to be the line
 ```
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
``` 
Looks like the problem is a symlink called K09samba, in the directory /etc/rc2.d, so one thing you could try is:
-Back up the file <= DO THAT ! (so in case I'm guessing wrong you can revert it)
-Remove the file.
-Make a new symlink (I guess the linked file would be /etc/init.d/samba)
```

sudo cp /etc/rc2.d/K09samba /etc/rc2.d/K09samba.bak
sudo rm /etc/rc2.d/K09samba
sudo ln -s /etc/init.d/samba /etc/rc2.d/K09samba

```

Now you should be able to access Synaptic: search for Samba and reinstall it, just in case.
After reinstalling Samba you may need to start it with ```
sudo /etc/init.d/samba start[code

Did it work?  Nice.
It didn't? Keep reading.

Why is the file called K09samba anyway?
Did you rename it in order to keep Samba from running at startup?
I've been off Ubuntu for a while, but if I remember correctly, the filenames in that directory should be called S(2-digit number)(app name) by default, they can be renamed to K(2 digit number = 100 - original number)(app name)
note: the S's and the K's are always uppercase
In such case you may also try reverting it to the default before trying to reinstall Samba:
[code]
sudo cp /etc/rc2.d/K09samba /etc/rc2.d/K09samba.bak
sudo rm /etc/rc2.d/K09samba
sudo ln -s /etc/init.d/samba /etc/rc2.d/S91samba

```

Open Synaptic, reinstall Samba. (start it?)

If any of the two above tries worked, you don't need to keep reading: you're done.

If neither one worked...  
Well, you can revert it to the way it was before you tried by renaming /etc/rc2.d/K09samba.bak to its original name, removing the backup, and remove the second-try symlink (S91samba) if you tried that too:
```

sudo cp /etc/rc2.d/K09samba.bak /etc/rc2.d/K09samba
sudo rm /etc/rc2.d/K09samba.bak
sudo rm /etc/rc2.d/S91samba

```

Now it's exactly as it was before you tried this (very wild-guessed) advice. It was worth a try anyway.

If anyone tries this, please post a message and tell how it went; it'd be useful for people searching the forums.

---

### Post by Fraoch on 2007-04-12
Luke771: that was exactly what worked for me.  I found it by several hours of searching through the forums.

Note, I never touched samba, the broken symlinks cropped up on their own after Synaptic encountered problems trying to stop an entirely unrelated service.

---

### Post by gnanda66541 on 2007-04-15
Hmm since that didn't work for me, if it doesn't work for anyone else you can try:

touch /etc/rc.status

and then remove it with synaptic.

---

### Post by Fraoch on 2007-04-15
BTW I had this problem again when I ran into trouble upgrading from 6.06 to 6.10.  The fix was the same but it's left me wondering if I'll encounter this again and again and how I can stop it.

(But Ubuntu still ran after this and all I had to do was install the rest of the updates through the Automatic Updater once I fixed this.  The upgrade is complete and working fine as far as I can tell.:D)

---

