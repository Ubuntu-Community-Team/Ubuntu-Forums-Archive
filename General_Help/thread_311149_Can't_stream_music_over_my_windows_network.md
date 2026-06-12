---
title: "Can't stream music over my windows network"
date: 2006-12-02
forum: General Help
---

### Post by Phalangees on 2006-12-02
Hi. Sorry if this is in the wrong place. I installed everything needed to get mp3's to play and they work fine if they are saved locally on the hard drive but I can't play any music over the network where all my music is. All the music I want to access is on a windows computer and amarok will crash when I try to play them.

A little side problem too is windows can't access my Ubuntu computer over the network. It comes up with a password prompt and my Ubuntu username and password won't work.

Any help would be greatly appreciated.

---

### Post by Phalangees on 2006-12-02
I tried installing gxine and automatix things but they haven't worked.

---

### Post by pingvin on 2006-12-02
I've found you need to mount Samba (Windows) shares into your filesystem in order for the music files to play. Have a look [here]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")

As for the Windows machine accessing the Ubuntu one - the easiest way I've found is to change "security = user" to "security = share" in /etc/samba/smb.conf having first made a backup of smb.conf. You may also need to change the share itself. I have found that allowing Samba shares unrestricted access, then controlling access via local permissions works okay. Obviously there are more secure ways to do this :-)

Hope I've understood your questions properly, apologies if not

Mike

---

### Post by Phalangees on 2006-12-02
thank you very much. i'll let you know if it all works out. thanks so much for your help.

---

