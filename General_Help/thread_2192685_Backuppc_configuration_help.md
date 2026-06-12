---
title: "Backuppc configuration help"
date: 2013-12-09
forum: General Help
---

### Post by 7-mark on 2013-12-09
I've installed backuppc from the 13.10 repository and managed to get it sort of working after copying apache2.conf files around and can now see the main web front end at localhost/backuppc.  

My environment:
Network: 2008 domain
Clients: xp/win7
BackupPC server: 13.10 Ubuntu
Credentials used: domain admin which is already a member of local admin group

My problems are now twofold.

1) DHCP clients aren't seen even though I've added the DNS server to the Ubuntu network settings panel.  From the terminal I can ping computer names so I know the machine can resolve them but backuppc doesn't see to want to know if I try and start the backup from either the server or my workstation.  Have I missed a setting somewhere to configure DNS or should it pickup the settings from the underlying OS?

2) More fundamental problem.  I can't get a full backup to run properly.  When I start it only 5 folders are copied before it stops.  These are complete and have all the files present, verified by restoring some.  

I get these errors:  

[LIST=1]
[*]NT_STATUS_ACCESS_DENIED listing \Documents and Settings\*
[*]NT_STATUS_SHARING_VIOLATION opening remote file \hiberfil.sys (\)
[*]NT_STATUS_SHARING_VOILATION listing \\*
[/LIST]

which seems really odd because I've added the below code to the exclude list I'd thought.

```

$Conf{BackupFilesExclude} = {
  '*' => [
    '/Documents and Settings',
    '/ProgramData/Application Data',
    '/ProgramData/Desktop',
    '/ProgramData/Documents',
    '/ProgramData/Favorites',
    '/ProgramData/Start Menu',
    '/ProgramData/Templates',
    '/Users/All Users',
    '/Users/Users/Default User',
    '/Users/Users/All Users/Application Data',
    '/Users/Users/All Users/Desktop',
    '/Users/All Users/Documents',
    '/Users/All Users/Favorites',
    '/Users/All Users/Start Menu',
    '/Users/All Users/Templates',
    '/Users/*/Application Data',
    '/Users/*/Cookies',
    '/Users/*/Local Settings',
    '/Users/*/My Documents',
    '/Users/*/NetHood',
    '/Users/*/PrintHood',
    '/Users/*/Recent',
    '/Users/*/SendTo',
    '/Users/*/Start Menu',
    '/Users/*/Templates',
    '/Users/*/AppData/Local/Application Data',
    '/Users/*/AppData/Local/History',
    '/Users/*/AppData/Local/Temporary Internet Files',
    '/Users/*/Documents/My Music',
    '/Users/*/Documents/My Pictures',
    '/Users/*/Documents/My Videos',
    '/Users/*/AppData/Local/Microsoft/Windows/Temporary Internet Files',
    '/Users/*/AppData/Local/Temp',
    '/Users/*/NTUSER.DAT*',
    '/Users/*/ntuser.dat*',
    '/Users/*/AppData/Local/Microsoft/Windows/UsrClass.dat*',
    '/Users/*/AppData/Local/Microsoft/Windows Defender/FileTracker',
    '/Users/*/AppData/Local/Microsoft/Windows/Explorer/thumbcache_*.db',
    '/Users/*/AppData/Local/Microsoft/Windows/WER',
    '/Users/*/AppData/Local/Mozilla/Firefox/Profiles/*/Cache',
    '/Users/*/AppData/Local/Mozilla/Firefox/Profiles/*/OfflineCache',
    '/Users/*/AppData/Roaming/Microsoft/Windows/Cookies',
    '/Users/*/AppData/Roaming/Microsoft/Windows/Recent',
    'ProgramData/Microsoft/Search',
    'ProgramData/Microsoft/Windows Defender',
    '*.lock',
    'Thumbs.db',
    'IconCache.db',
    'Cache*',
    'cache*',
    '/Program Files',
    '/Windows',
    '/$Recycle.Bin',
    '/MSOCache',
    '/System Volume Information',
    '/Boot',
    '/autoexec.bat',
    '/bootmgr',
    '/BOOTSECT.BAK',
    '/config.sys',
    '/hiberfil.sys',
    '/pagefile.sys'
  ]
};

```

After running the full backup and only seeing a few folders with files in them I ran an incremental.  This lists all of the folders on the machine I'd expect to be backed up but oddly does not contain any files at all.  133 xferlog errors as opposed to the original 3 for the full backup.

For the next backup I removed all of the code above to exclude files/folders and ran this command: ```
/usr/bin/smbclient \\\\<ipaddress>\\C\$ - U <domain\account> -E -d 1 -c tarmode\ full -Tc -
```
This give me the same few folders as the first backup again along with errors for \Documents and Settings\*  which leads me to believe the exclude code above isn't working.  Or, I am mis-interpreting how this is handled which is quite possible.

I've spent a few days digging around trying to resolve this or find an answer but I'm now going around in circles any help would be gratefully received.

Many thanks,
Mark

---

