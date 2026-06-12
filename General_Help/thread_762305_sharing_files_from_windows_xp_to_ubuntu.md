---
title: "sharing files from windows xp to ubuntu"
date: 2008-04-22
forum: General Help
---

### Post by fizban9 on 2008-04-22
how do i see files from my windows xp computer.  I can see my windows computer but when I open it, it shows 0 files.

---

### Post by overdrank on 2008-04-22
> **fizban9 said:**
> how do i see files from my windows xp computer.  I can see my windows computer but when I open it, it shows 0 files.

HI and I am assuming you are sharing over the network
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by HyperHacker on 2008-04-22
I simply did this in the terminal, but this was a WinXP box with no passwords at all, anonymous access/blank passwords allowed, etc; very minimal security. (Since I was about to format it anyway and just needed to get file sharing working NOW so I could get stuff off it. :P) Also I didn't really know what I was doing so some of these steps may be unnecessary, and I only needed read access.

First, not sure if this is necessary (I think it's for allowing Windows machines to see the shared files on the Ubuntu box):
sudo smbpasswd -a hyperhacker
It prompts for a password (after the sudo password prompt, "New SMB password") which the Windows machines will use to access that user's shared files. (Replace hyperhacker with your own username of course.)

Then I think you have to install smbfs:
sudo apt-get install smbfs

Next:
smbclient -U Admin -L 192.168.0.102
(Admin is the name of the user on the XP box you're logging in as; 192.168.0.102 is its IP address, you can also use its name. It prompts for the password for this user. If you see this:
```
        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.0.102.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
```you got the password wrong, just run the command again.

Then mount it:
sudo mount -t cifs //192.168.0.102/f /shares/laptopf -o"user=Admin"
Where //192.168.0.102/f is the share to access, /shares/laptopf is the directory (which must exist) we're mounting it at, and Admin is the username to log in as. It prompts for the password again. Then you can see if it worked by doing 'ls' on that directory; you should see the shared files.

There's a page on the wiki about mounting them permanently. I didn't bother to do that since I only needed to access it once, and then wipe the machine it was on.

---

