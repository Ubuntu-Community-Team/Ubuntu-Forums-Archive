---
title: "i cant believe...."
date: 2008-05-03
forum: General Help
---

### Post by zenithlt on 2008-05-03
I installed winamp with "Wine" restarted pc and now my desktop is totally black and winamp apears on it i can use 3d cube but all desktops is black too... :confused: anyone help me

edit: when i said totally black that means no buttons or smth...

---

### Post by Helios38 on 2008-05-03
winamp + wine = trouble.


ive seen it cause a lot of problems. i wouldnt use it if i were you

---

### Post by zenithlt on 2008-05-03
> **Helios38 said:**
> winamp + wine = trouble.


ive seen it cause a lot of problems. i wouldnt use it if i were you

ok but hove can i  remove it now ? (now i`m in Win Vista)

---

### Post by ibuclaw on 2008-05-03
First, I must ask you... Do you have any WINE software other than winamp installed?

If so, take a more relaxed method than what I describe...
1) Boot into recovery mode in Ubuntu.
2) Select the option that gets you into the root shell (Option 2 I think).
3) type in:
```
su **yourname**
```
to switch to your user account
4) type in:
```
cd
```
to switch to your home directory.
5) type in:
```
rm -r .wine
```
To completely remove your current WINE folder (Thus, all traces of winamp gets destroyed too).

As I said, if you have other software. Use:
```
cd ~/.wine/drive_c/Prog*/
```
and then "**rm -r WINAMP-FOLDER**".

When winamp is gone. type **exit** twice to get back out and choose "Option 1" to continue as normal user. Though just for kicks, you can select "Fix X" just incase too.

Regards
Iain

---

### Post by zenithlt on 2008-05-03
> **tinivole said:**
> First, I must ask you... Do you have any WINE software other than winamp installed?

If so, take a more relaxed method than what I describe...
1) Boot into recovery mode in Ubuntu.
2) Select the option that gets you into the root shell (Option 2 I think).
3) type in:
```
su **yourname**
```
to switch to your user account
4) type in:
```
cd
```
to switch to your home directory.
5) type in:
```
rm -r .wine
```
To completely remove your current WINE folder (Thus, all traces of winamp gets destroyed too).

As I said, if you have other software. Use:
```
cd ~/.wine/drive_c/Prog*/
```
and then "**rm -r WINAMP-FOLDER**".

When winamp is gone. type **exit** twice to get back out and choose "Option 1" to continue as normal user. Though just for kicks, you can select "Fix X" just incase too.

Regards
Iain
 yes i installed Silkroad Online, i will try this... thnx man

---

