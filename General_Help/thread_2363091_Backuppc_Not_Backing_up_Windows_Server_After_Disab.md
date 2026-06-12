---
title: "Backuppc Not Backing up Windows Server After Disabling SMBv1/Force SMBv2 in Backuppc?"
date: 2017-06-06
forum: General Help
---

### Post by jrajra on 2017-06-06
Hello all - title says it all really. Following the horrible wannacrypt business I've turned off SMBv1 on my Windows servers, but now backuppc can't back them up.

Adding *$smbClientPath \\$host\$shareName $I_option -m SMB2 -U $userName -E -d 1 -c tarmode\ full -Tc$X_option - $fileList* to Xfer options doesn't do it (note the -m SMB2 bit in there) and adding* min protocol = SMB2* into smb.conf (perhaps somewhat optimistically) doesn't do the job either.

Backuppc error logs for the server/s show the following:

Executing DumpPreUserCmd: /backups/bin/backup-preexec-control printserver smb
Running: /usr/bin/smbclient \\\\printserver\\papercut\$ -m SMB2 -U MYDOMAIN\\Administrator -E -d 1 -c tarmode\ full -Tc -
full backup started for share papercut$
Xfer PIDs are now 14181,14180
WARNING: The "syslog" option is deprecated
[ skipped 1 lines ]
tar:316  tarmode is now full, system, hidden, noreset, quiet
[ skipped 14941 lines ]
tar:712  Total bytes received: 6151845594
[ skipped 8 lines ]
tarExtract: Done: 0 errors, 11864 filesExist, 5538380794 sizeExist, 3143040589 sizeExistComp, 12028 filesTotal, 6151845594 sizeTotal
Got fatal error during xfer (No files dumped for share papercut$)
Backup aborted (No files dumped for share papercut$)
Saving this as a partial backup, replacing the prior one (got 12028 and 0 files versus 0)
Executing DumpPreUserCmd: /backups/bin/backup-preexec-control printserver smb
Running: /usr/bin/smbclient \\\\printserver\\papercut\$ -m SMB2 -U MYDOMAIN\\Administrator -E -d 1 -c tarmode\ full -Tc -
full backup started for share papercut$
Xfer PIDs are now 13153,13152
WARNING: The "syslog" option is deprecated
[ skipped 1 lines ]
tar:316  tarmode is now full, system, hidden, noreset, quiet
[ skipped 14860 lines ]
tar:712  Total bytes received: 6157528978
[ skipped 84 lines ]
tarExtract: Done: 0 errors, 11988 filesExist, 5678826415 sizeExist, 3267225687 sizeExistComp, 12023 filesTotal, 6157528978 sizeTotal
Got fatal error during xfer (No files dumped for share papercut$)
Backup aborted (No files dumped for share papercut$)
Not saving this as a partial backup since it has fewer files than the prior one (got 12023 and 0 files versus 12028)

[FONT=Verdana]I'm all out of ideas. Anyone know what to do to make Backuppc use SMB2?

Thanks for any and all ideas! :)[/FONT]

---

