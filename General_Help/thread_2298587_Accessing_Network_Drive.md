---
title: "Accessing Network Drive"
date: 2015-10-12
forum: General Help
---

### Post by bman on 2015-10-12
Hi,

I am trying to access a network drive which is on a Windows system. Trying to follow ([https://help.ubuntu.com/stable/ubuntu-help/nautilus-connect.html](https://help.ubuntu.com/stable/ubuntu-help/nautilus-connect.html)).

The Windows system is Windows 10 and I can't seem to connect. When I connect to the system from within another Windows 10, it requires a password. I actually had to add the password to make it work for Windows.

Yet when I try to connect using it, it fails. I think it might have to do with it the WORKGROUP listed, but I didn't create any workgroup so I assumed it would be that by default.

In the Browse Network section it clearly sees the drive without issue. Not sure what to do.

---

### Post by nknwn on 2015-10-12
What do the security settings on your proposed shared folder look like in Windows? Below are the permissions we are using in Windows 7 on a folder which can be read/write accessed by a Windows 8 and Ubuntu computers through a wireless router - (there is no account password set on the Windows 7 computer)
[ATTACH=CONFIG]264913[/ATTACH]

---

### Post by bman on 2015-10-12
Windows 7 is a bit different.

In Windows 8 and 10, it requires a password to be added to the user account, causing network sharing to be a bit more complicated.

I have that setting on the folder as to share all, everything is read/write.

---

### Post by bman on 2015-10-12
Apparently I am an idiot and had the username wrong lol

---

### Post by nknwn on 2015-10-12
FWIW I can use Ubuntu to read/write access a folder on a Windows 8.1 with the same permissions as above. No password required. I can't test ~from Windows 8.1 or Windows 10~ to Windows 8.1 as I have only one Windows 8.1 computer available. I'm disinclined to upgrade to Windows 10 currently. :)

---

### Post by nknwn on 2015-10-12
Good to hear you have found a solution

---

