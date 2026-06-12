---
title: "Expand Tree to show Network."
date: 2008-01-16
forum: General Help
---

### Post by tickmike on 2008-01-16
Hello All.
Had to do a post, could not find info with a search !.

I installed Audiacity on Ubuntu 7.10.
I would like to access files via my wired home network on XP machines.
Is it possible to expand the Tree on the LHS to show my network.( see screen shot)
 I can get access via Places> Network Etc. but not via the above program or others.

---

### Post by _sAm_ on 2008-01-16
Go to Places > Connect to Server. Chose Windows share and type in the needed info(hostname of the xp box, username, path and so on). After doing this it will show up under «Documents, Music, Pictures, Videos». 

More info here; [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

You could also mount the windows share with cifs, and it will turn up as a local; [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by benanzo on 2008-01-16
I'm actually not sure that the first suggestion by *_sAm_* will work since that requires Audacity to recognize gnome-vfs mounts, which it doesn't.  His second suggestion will definitely work though since it will just mount the remote share as a local filesystem.

The easiest way to do this is to add this line to your **/etc/fstab** file:

```

# Shared Music folder
\\192.168.0.100\Shared_Music /home/username/Shared_Music cifs auto,user,defaults 0 0

```

Replace the IP address (192.168.0.100) with the address of the computer that's sharing your folder.

**Shared_Music** is the name of the share as seen in the network browser.  /home/username/Shared_Music is the directory you want to mount the share into.  Be aware that I've experienced problems with smbfs/cifs sometimes causing Nautilus to hang if the remote computer stops responding.  Also, you need to make sure that **/home/username/Shared_Music** exists before trying to mount the share, otherwise it wont work.  After you add that line and save it you can mount the share with:
```
mount /home/username/Shared_Music
```

Good Luck!

---

### Post by tickmike on 2008-01-19
Thank you both for taking the time to reply.

I have somehow found this link .  

[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

And I have installed 'Firestarter' and followed the advice it that post,

I then could make a 'Mount' (Places>Connect to Server) on the desktop to the folder with my audio files on the other network machine (so I could now copy and paste to my music folder if I want ).

I then tried to follow 'benanzo' advice but could not get it to work.

I'm new'ish to Linux.

You said.."Replace the IP address (192.168.0.100) with the address of the computer that's sharing your folder."
I use DHCP ! 
I did try it with the latest  ip it had got today. 192.168.0.183  (DHCP comes from my Smoothwall Box).

I then tried running this in Root terminal mount /home/username/Shared_Music (after changing username).
I got.."mount: wrong fs type, bad option, bad superblock on \\192.168.0.183\Shared_Music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

---

