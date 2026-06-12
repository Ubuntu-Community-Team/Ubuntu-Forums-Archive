---
title: "Made changes, cannot login to gui"
date: 2012-10-21
forum: General Help
---

### Post by sturdy on 2012-10-21
Hi all,

I've moved my /home directory and files and now cannot login to the gui. I can login to a virtual terminal. Here is what I have done:

sdb1 is an NTFS WinXP partition, my /home was sdb2, sdb3 was empty.
1) Using Ubuntu on a thumbdrive, I moved /home to sdb3 and deleted the sdb2 partition.
2) Used gparted to resize sda1 to include what was sdb2.
3) Relabeled sdb3 (which is now new sdb2) to same as old sdb2.
4) Edited UUID of /home in fstab.
5) Login screen but cannot login.

Can someone tell me what I did wrong and how to correct. I have looked at /home and ownership is root.root. Can "chown -R ~user.user" get me out of this mess or will I muckup something else? TIA

Sturdy

---

### Post by MG&amp;TL on 2012-10-21
This doesn't really sound like a problem with the filesystem-it probably wouldn't boot if you'd mucked that up. :)

Try logging into a terminal and typing:

```
sudo service lightdm restart
```

...and see whether anything interesting turns up. 

Also post the output of:

```
cat ~/.xsession-errors
```

please. :)

/home should be root:root- /home/user should be user:user. :)

---

### Post by sturdy on 2012-10-21
Thanks for the quick response. The "restart" simply returns to the login screen so no joy. The "cat" gives me an access denied so seems to be a permissions problem. "ls -l ~/.xsessions-errors" gives ownership as root:root.

---

### Post by MG&amp;TL on 2012-10-21
> **sturdy said:**
> Thanks for the quick response. The "restart" simply returns to the login screen so no joy. The "cat" gives me an access denied so seems to be a permissions problem. "ls -l ~/.xsessions-errors" gives ownership as root:root.

Ahah, that's probably it then, you're right, it is a permissions problem. Try:

```
sudo chown -R username:username /home/user
```

...replacing username with your login, and /home/user, with /home/your username, i.e. /home/fred

---

### Post by sturdy on 2012-10-21
Success...thanks for the assist. Any idea what went wrong?

---

### Post by MG&amp;TL on 2012-10-21
> **sturdy said:**
> Success...thanks for the assist. Any idea what went wrong?

Not a problem. :)

When you start the X server, it needs to write to some files in your home directory, for logging, authority, DBus and such.

Sometime during your changes, your home folder got changed to root-access only (dodgy UUID/fstab?). Which meant the X server wouldn't start.

Hope that helps. Have a nice day!

---

