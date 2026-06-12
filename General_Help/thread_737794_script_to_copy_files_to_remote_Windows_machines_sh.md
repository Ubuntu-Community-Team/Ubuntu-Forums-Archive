---
title: "script to copy files to remote Windows machines shared drive"
date: 2008-03-27
forum: General Help
---

### Post by munwin on 2008-03-27
Am trying to write a script that can copy a directory and it's contained files onto a remote Windows share. The Windows share needs no credentials to write to it. Windows doesn't have SSH (hence SFTP) installed.

I know in Nautilus, I could just type smb://windowsmachine/share and manually drag the folder across, but I am trying to script this for over 100 machines.

I want to provide a list of IPAddress's to the script (in an external file), have the script copy a folder to a specific share on each of those IP's.

Just to confirm - NO, no authentication is needed to write to this particular share on these Windows machines.

I can install Samba on my Ubuntu 7.10 box if I have to.

Any help much appreciated.

UPDATE
I have tried
mount -t smbfs "\\192.168.1.1\share" /home/myname/mytempfolder
But I get an error, thus
mount: wrong fs type, bad option, bad superblock on \192.168.1.1\share,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have libsmbclient and samba-common installed.
I am using Ubuntu 7.10 Desktop.

Again, any help much appreciated.

---

### Post by munwin on 2008-03-27
Go it.
You have to have smbfs installed.
The command is now
sudo mount -t cifs "\\\\192.168.1.1\share" /home/user/temp_dir
** Note the four \'s inside quotes.

---

