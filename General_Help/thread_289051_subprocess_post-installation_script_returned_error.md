---
title: "subprocess post-installation script returned error"
date: 2006-10-30
forum: General Help
---

### Post by kindafunnylookin on 2006-10-30
When I -using aptitude- try to install backuppc the terminal get as far as the setup then this happens:

CODE]Setting up backuppc (2.1.2-2ubuntu5) ...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 3.
 * Starting backuppc... 2006-10-30 12:15:38 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up backuppc (2.1.2-2ubuntu5) ...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 3.
 * Starting backuppc... 2006-10-30 12:15:47 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
[/CODE]

No matter what I try to load with the terminal it tries to fix backuppc but fails. I have been trying to get this done for a week with no joy.

Please help.
Peter

---

### Post by kindafunnylookin on 2006-11-01
....bump...

---

### Post by highneko on 2006-11-01
Starting backuppc... 2006-10-30 12:15:47 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program

That looks like the error. I don't know. Are you using the livecd? What exactly are you typing to get this?

Edit: Try:
sudo apt-get install sendmail

---

### Post by kindafunnylookin on 2006-11-01
>  That looks like the error. I don't know. Is this where you're installing ubuntu? Are you using the livecd? What exactly are you typing to get this?I'm typing:
```
sudo aptitude install backuppc
```This is dapper 6.06 and has been installed for two months. I installed it with a Breezy 5.10 install CD

---

### Post by highneko on 2006-11-01
Read my last post again; I edited it. Any success?

---

### Post by kindafunnylookin on 2006-11-01
YES, that was the problem. backuppc is now installed. Thank you for your help.

Peter

---

