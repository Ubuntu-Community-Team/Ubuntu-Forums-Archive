---
title: "I can share external drive - but not give access to it (12.04)"
date: 2014-01-03
forum: General Help
---

### Post by freebird54 on 2014-01-03
The situation:

I just built a new system, and decided to put 12.04 LTS and 13.10 on it - with 12.04 being the 'trusted workhorse' version - and the version with the following 'problem'.  I also needed to make an external HD wirelessly available to an Android tablet for someone bedridden, and unable to store enough 'stuff' on any conceivable local storage.

Sharing the access to *MY* tablet was instantly accomplished (I recommend ES File Explorer on the tablet side) - with only the directories I specified appearing and being accessible.  However, trying to set up the alternative user I mentioned above has NOT worked.

First no access to the 'server' - solved by sharing the whole drive.  But nothing so far has enabled entry to the shared directories.  While 'researching' possible causes, I noticed that the drive was *EQUALLY* inaccessible from a 'local' login at the physical keyboard as that user.  No combination of attempts to use chown, chgrp, creating a group with access, attempting to see if ACL's were involved, or finding a GUI tool with an answer has yet met with success.

My knowledge is only partial (and outdated - my best CLI skills were on AmigaDOS!) - but the theory of networked access hasn't changed all that much since my days as netadmin on Netware4 - so it must be a slowing mind - or perhaps an unforeseen error in my starting point?  Could the fact that I installed the OS with those drives hooked up (though unaccessed) have affected something?  Is there a reason that chown and chgrp appear to make no changes at all?  Any thoughts?

Thanks for any ideas

---

### Post by mikewhatever on 2014-01-03
If, presumably, you've allowed shared access from Nautilus, have you allowed guest and read/write access?
If you've done it from Terminal, showing the configs would have been useful.
Can you open a terminal window in Ubuntu, run <smbclient -L localhost>, and post the output.

---

### Post by freebird54 on 2014-01-03
I can't seem to get any output from that command - as I can't get any valid reference for host name.  What I have from the "other" end (on the Android) is: (approx)

```
Brother 7060D$
:pro?$:
Lora_C_Drive
Lora_D_Drive
print$
```

(can't remember the second entry - the 2 Loraxxx references are the directories to be shared)

I can fire it all up now if you need it exactly....

Thx

---

### Post by mikewhatever on 2014-01-03
Of cause, my bad, try <smbclient -L localhost>.

So, Lora_C and Lora_D are visible, but not accessible?

---

### Post by freebird54 on 2014-01-03
I suspected that - but I'll have to switch over to the new box to get that correctly...  back in 5....

---

### Post by freebird54 on 2014-01-03
OK - back on the new box - here it is...
```

freebird@nest:~$ smbclient -L=nest
Enter freebird's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (nest server (Samba, Ubuntu))
	Lora_C_Drive    Disk      
	Lora_D_Drive    Disk      
	Iomega HDD      Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	NEST                 nest server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            NEST
```

I am afraid I did this from Nautilus - rather than setting up the whole thing myself - but I could have!  :)

Does it tell you anything?


And - as it actually appears on Android:

```

Iomega HDD
IPC$
Lora_C_Drive
Lora_D_Drive
print$

```

It appears the same way whether I log in as freebird (self) or as Lora (sister) - but access not available to Lora's login.  And nopt available locally to Lora's login either!

Thx

---

### Post by mikewhatever on 2014-01-03
So, Lora may not be in the sambashare group. Can you check with the **id Lora** command. Users outside the sambashare group login as guests, which is why I've asked about guest access above.
Alternatively, just add Lora to sambashare with **sudo adduser Lora sambashare**.

PS: I've no idea what "nopt" stands for.

---

### Post by freebird54 on 2014-01-03
output = 

```
freebird@nest:~$ id lora
uid=1001(lora) gid=1001(lora) groups=1001(lora),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),30(dip),44(video),46(plugdev),104(fuse),1002(remote)

```

and

```
freebird@nest:~$ sudo adduser lora sambashare
Adding user `lora' to group `sambashare' ...
Adding user lora to group sambashare
Done.
```

OK  - I added Lora to sambashare - with no change in outcome.  At the Android end, the message speculates that permissions are the problem with the failed attempt to access. Good idea, though!  She wasn't in there...

P.S.    nopt = no operation - often used in 68000 assembly to hold a place in the binary for self-modifying code to reside....
           (or it could be a fat or slipped finger typo for **not**?)

---

### Post by mikewhatever on 2014-01-03
Now is a good idea to restart the Samba server to apply the new configs - 
```

sudo service smbd stop

sudo service smbd start

```

You don't tell us much about the settings of the shares, but it looks like you've created the shares as yourself, so that only freebird has access. The way around this is allowing guest access, or using System-Config-Samba from the repositories to do it globally.

---

### Post by freebird54 on 2014-01-03
Well - I tried both parts of those suggestions - to no avail.  I first added guest access to both directories in Nautilus (it headed off to change permissions) - then I tried the stop and start commands. No luck.  Then I tried adding guest access at the drive level as well - still no change in accessability.

I still have the feeling that Samba is doing everything right, and that the configuration is alright in that department.  The problem, I still suspect, is that **even when logging in locally**, the ***lora*** account cannot get in to the folders....

Thanks for the help though - I'm sure SOME way will be found  :)

---

### Post by mikewhatever on 2014-01-03
If lora doesn't have local access, the question is, how are those partitions mounted. Are there lines for them in /etc/fstab, or do you just click in the file browser to get local access?

---

### Post by freebird54 on 2014-01-03
I never looked, actually.  Whatever the installer wanted to do.... (blush).  Should have thought of looking at that!  I have been GUI seduced!!

OK - no entries there for externals (both are mounted through /media - no idea where details might be!

---

### Post by mikewhatever on 2014-01-03
I wasn't implying you should have done the sharing (and mounting) any other way, just needed to find out how. GUI is the prefered way, actually.
So, what happens if you log out of freebird, then log in as lora, and try accessing one of those partitions? I don't think there should be a problem  with the local access. As long as a partition on the external HDD is not already mounted under some other user, it should mount under lora.

---

### Post by freebird54 on 2014-01-03
I was half kidding about the 'attitude' as to allowing the system and GUI to do their thing.... it really has been so long that I tend to forget how things work in the CLI.  To think I remember MS-DOS 6.22 as Redmond FINALLY putting a usable CLI on its WIndows boxes !

Anyway - the practical side of what I have done is that the external drives BOTH auto-mount under MY name AND ownership, and cannot be UNmounted (because of Samba keeping them busy) and can't be accessed because they are owned elsewhere.  If I 'upped' the other account to a sudoer (admin level, whatever) might I manage to take them over?  Where would an auto-mount command reside, and could it be edited?  I guess those are the real questions at this point.

It's amazing what fun you can cause because not wanting to crawl on the floor to find out which connectors went with which devices when I set up the new machine - and had them all 'present' when I did the first install....

Thx

---

### Post by Morbius1 on 2014-01-03
Please post the output of the following commands so we can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by freebird54 on 2014-01-03
OK - here the outputs:

```

freebird@nest:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```


```

freebird@nest:~$ net usershare info --long
[Iomega HDD]
path=/media/Iomega HDD
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Lora_D_Drive]
path=/media/Iomega HDD/Lora_D_Drive
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Lora_C_Drive]
path=/media/Iomega HDD/Lora_C_Drive
comment=
usershare_acl=Everyone:F,
guest_ok=y

```


There we have it.  Notes for pondering (don't know which, if any, have relevance)

1. I got chown to change owner of drive to **lora**
2. It appears that the system gives BOTH external drives to the first to login after a reboot - and the next to login sees nada
3. Information for mounting is in /proc/mounts (so far)

Situation at Android end the same - if **freebird** attaches the share, everything works - if **lora** attaches the share, the directories are visible, but not accessible (error message suggests permissions are at fault).

Thx

---

### Post by Morbius1 on 2014-01-03
Here's what has me confused:

All of your shares are on this external Iomega HDD thing and based on what you are calling them "C_drive" and D_Drive" it sounds like they are NTFS or possibly FAT32 formatted partitions. If they are, a chown would do nothing and it will be owned by whoever plugs the device in just as you just described. 

It's also not clear how many local login users you have on this box. 

*** If it's only one user - let's call him/her UserA - then the solution is simple:

Edit smb.conf and place the following line - right under the workgroup line in the [global] section:
```
force user = UserA
```
Then restart samba:
```
sudo service smbd restart
```
When the guest user accesses the samba share his identity will be converted to UserA and since that local user is the one who owns the mounted partition the remote user also has access to the shares located on that mounted partition.

*** If you have many local login users then this is going to get tricky since we would have to use something like bindfs to make anything mounted to /media appear to be accessible by anyone.

---

### Post by freebird54 on 2014-01-03
This machine has one local user (freebird) and (if I get it to work) one remote user on Android.  The references to Lora_C_Drive etc are to the contents of the drives from her old desktop (an XP from 2000) - back when she could do exotic things like sit up :)

The external drive (Iomega HDD) is formatted NTFS and connected by USB 2.0.  I (as freebird) have no need to access the drive from local - she will need access to the whole thing eventually )as I clear unneeded extras off it.  It should NOT have been so difficult - and I am tempted to just reconfigure my older machine to serve as a NAS for her, and get that drive off my system entirely!  After all - everything works for ME to access what I need!

I just got used to being to do ANYTHING with an Ubuntu box - perhaps not worth further effort in this case though.  Thanks for you efforts - and bringing the 'way of thinking' back to me - it has been too long since I thought in a computer admin manner!

---

### Post by Morbius1 on 2014-01-03
Then "force user = freebird" placed below the workgroup line in smb.conf seems to be the way out of this mess.

---

### Post by freebird54 on 2014-01-03
Strangely enough - that does not seem to work.  I added the statement suggested directly on the line below, stopped and restarted the service, and got no difference in the result.  However, if it HAD worked, I assume it would have functioned in much the same way as logging in remotely as freebird in the first place...?  If that is so, that's what I'll do for the moment - and then when I have the old system moved and set up I'll try to have it accessed from there.

Thanks again - I will just mark it SOLVED and get onto the next problem.

---

