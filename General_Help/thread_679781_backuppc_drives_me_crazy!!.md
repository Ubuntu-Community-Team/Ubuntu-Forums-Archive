---
title: "backuppc drives me crazy!!"
date: 2008-01-27
forum: General Help
---

### Post by hades_6_6_6 on 2008-01-27
I've installed backuppc 3.0.0 on Gusty.
I'm using rsync over ssh. It was quite a pain to configure, but at least I did it :)
but still backuppc isn't able to backup all directories from the client.
If I use following config, it works just like a charm:
```
$Conf{XferMethod} = 'rsync';
$Conf{RsyncClientPath} = '/usr/bin/rsync';
$Conf{RsyncClientCmd} = '$sshPath -l root $host $rsyncPath $argList+';
$Conf{RsyncClientRestoreCmd} = '$sshPath -l root $host $rsyncPath $argList+';
$Conf{RsyncShareName} = ['/etc'];
$Conf{RsyncArgs} = [
  '--numeric-ids',
  '--perms',
  '--owner',
  '--group',
  '--devices',
  '--links',
  '--times',
  '--block-size=2048',
  '--recursive',
  '--one-file-system'
];
$Conf{RsyncRestoreArgs} = [
  '--numeric-ids',
  '--perms',
  '--owner',
  '--group',
  '--devices',
  '--links',
  '--times',
  '--block-size=2048',
  '--relative',
  '--ignore-times',
  '--recursive',
  '--one-file-system'
];
$Conf{RsyncLogLevel} = 6;
;
```

but if I replace
```
$Conf{RsyncShareName} = ['/etc'];
```
with ```
$Conf{RsyncShareName} = ['/'];
```
or ```
$Conf{RsyncShareName} = ['/var'];
```
It just break up after a couple of seconds :(
But, for instance, ['/var/lib', '/var/opt'];
The same issue happens with the 2 clients I try to backupp (one running Gusty and the other one Feisty). Any idee?
Moreover, one one of the client I cannot backup one of the home folder. It starts properly but hangs after empty folder have been created. I don't it is a rsync issue, since I'm able to copy the directory (using the same options except --sender --server) locally without problem. The funniest is I can backup the copied directory, the not the original one:confused:
Could someone help me??

---

