---
title: "single mode approach"
date: 2022-03-22
forum: General Help
---

### Post by mhs122 on 2022-03-22
I applied super user and password to the 00_header file of the GRUB file, and it boots as follows.

help

[https://github.com/M00nHeeSung/help/blob/main/%EB%85%B9%ED%99%94_2022_03_22_16_48_40_381.mp4](https://github.com/M00nHeeSung/help/blob/main/%EB%85%B9%ED%99%94_2022_03_22_16_48_40_381.mp4)

This is a video about this phenomenon. Also, I did poweroff and login without pressing any key.

---

### Post by mIk3_08 on 2022-03-22
> **mhs122 said:**
> [SIZE=3][FONT=arial]I applied super user and password to the 00_header file of the GRUB file, and it boots as follows.[/FONT][/SIZE][SIZE=3][FONT=arial]
help

[https://github.com/M00nHeeSung/help/blob/main/%EB%85%B9%ED%99%94_2022_03_22_16_48_40_381.mp4](https://github.com/M00nHeeSung/help/blob/main/%EB%85%B9%ED%99%94_2022_03_22_16_48_40_381.mp4)
[/FONT][/SIZE][SIZE=3][FONT=arial]This is a video about this phenomenon. Also, I did poweroff and login without pressing any key.[/FONT][/SIZE]
Can you elaborate more on your issue so that people here in this Ubuntu forum community who's very much willing to help know whats best solution to your machine issue. And also, the video that you are trying to share is not playing on git. Best advise, if you want to share video. Upload it on YouTube for best sharing out put. Good Luck and cheers.

---

### Post by MAFoElffen on 2022-03-22
I am not going to download a raw video file from an unknown source... From a GitHub User that only has one repo, which contains only one user file (that media file). Sorry.

Besides what the previous post suggested... You said that you "applied super user and password to the 00_heaer file of the GRUB file"... Why would you do that & for what purpose? What was your intent on what you wanted to do? Because that script is call by update-grub, which is already running as sudo, so why the attempted hack on something that was already running as a privileged user?

This file... and the other grub scripts, are not called during the boot process, but rather, only called during update-grub, which when ran, would display errors, trace-backs and exit codes if there were problems, so I am a bit perplexed by what you are saying and have yet to describe.

Sorry again, but something is odd about this and doesn't make logical sense... and I believe there are safety/security concerns about how you are going about this.

---

### Post by mhs122 on 2022-03-23
[SIZE=2]Oh I didn't know that, I'll upload it to YouTube next time[/SIZE]

---

### Post by mhs122 on 2022-03-23
[COLOR=#202124][FONT=&amp]Yep, next time I upload it, I will supplement the content and upload it to YouTube.[/FONT][/COLOR]

---

### Post by mhs122 on 2022-03-23
I'd like to enable Enter username and Enter password only when accessing singlemode, but I haven't been able to solve this. My problem is that Enter username and Enter password disappear when booting.
Enter username nad Enter password should only appear when accessing in single mode
Please tell me how to set user and password. Please refer to the YouTube video
[https://www.youtube.com/watch?v=wS7X4PTUf20](https://www.youtube.com/watch?v=wS7X4PTUf20)
If you select Korean subtitles on YouTube, you will see English subtitles with the explanation you want.
Single-mode access security
Ubuntu version is 18.04 LTS

---

### Post by wildmanne39 on 2022-03-23
Please only post in English as this is an English only sub-forum.

Thanks

---

### Post by QIII on 2022-03-23
@mhs122

You have been asked by a Super Moderator to post in English.  Yet, for some reason, you edited your first post and changed it to Korean.  I have edited it to the original content.  This is especially odd, since after being told to use English earlier you translated post #5 to English.

You are now being told by a Forum Admin to post in English.  We have nothing at all against Korean or any other language.  However, this is an English-speaking area of the Forums, so we expect posts to be in English.  If you persist in posting in Korean in an English speaking area of the forums -- particularly editing English content into Korean -- you may find yourself shown to the door.

Threads merged.  Please do not start separate threads dealing with the same issue.

Also, use the default font and color.

---

### Post by MAFoElffen on 2022-03-24
I posted a reply to this, right as the threads were being merged. My post was orphaned and lost. I reconstructed it.

Because of a language difference, I understand that you are really trying to secure the physical security of your computer...

To others: (And my disclaimer) Physical Security is paramount. There are things that you can do to harden a computer in case physical security is lost, but that is not a guaranty that the compromised device can not be accessed.

The title of the thread is referring to "Single User Mode Security" hardening. We do not commonly think of this as a vulnerability, as when doing diagnostics and fixing machines, we use this to get into a machine to fix it or change passwords when we are locked out. One of these is using systemd's recovery.service (Recovery Mode), and emergency.service. While the Grub Menu can be configured to not offer Recovery Mode in  it's Boot Menu Generation, but that does not stop anyone (like me for over a decade) from editing the Grub Boot Menu options to add a Single User Mode (or other boot options) to add a Single User Mode boot. 

What does those Single User Modes do? Well, they boot the kernel into a mode as if they were the 'root' user... (usually) without asking for a root password.

Locking up that hole, if you do consider it as a Security Risk, has changed over the years. In fact the OP says in his merged duplicate post, that he was trying to do this for Ubuntu LTS 18.04... But he did not say which version of 18.04.x he is running. If all updates and security updates are applied, then to 18.04.6, then he is golden in that respect and he doesn't have to manaully edit many config and/or service files. Since he mentioned he is on 18.04, I will not mention how it was done before 'systemd'... But there were still 2 different ways we had to do this between late 2017 (shortly before 18.04.1 was released), and later.  I can confirm that in 3/2018, one month before 18.04 was released, that DEV 18.04 was the first method.it was still the first method...

At 'systemd' around March 2018, what you first had to do was to edit two service files in /lib/systemd/system, named 'recovery.service' & 'emergency.service'. You wnet down to the 'ExecStart=' line and changed where it said '/usr/sbin/sushell ' to '/usr/sbin/sulogin '... Then you used passwd to set a secure password to the 'root' user.

Sometime after that, both those files changed when someone created '/lib/systemd/system/systemd-sulogin-shell', which now is what is in the 'ExecStart=" line... the original utility file '/user/sbin/sulogin" is still there. '/usr/sbin/sushell' was deprecated and removed. systemd-sulogin-shell now decides if the prerequisites are there to start a shell or to use 'sulogin' to ask for the root password if any form of a single user mode is asked for... But now, since using that new utility, you do not have to edit any service files... All you have to do it to use passwd to set a secure password to the 'root' user.

To lock Grub from being edited, you still add lines to the Grub Script files... but not to '/etc/grub.d/00_header'. You use 'grub-mkpasswd-pbkdf2' (from package grub-common) and get password hash output of that to get your desired password. Grub Superusers are commonly either 'root' or 'admin'. So not to confuse with an OS root user, most admin's use 'admin'. 
```

grub-mkpasswd-pbkdf2

```
Then you edit grub file '/etc/grub.d/40_custom' to append these two lines:
```

set superusers="admin"
password_pbkdf2 admin <password-hash>

```
...where the password-hash is was the output you got from using 'grub-mkpasswd-pbkdf2'. That way the password in not stored in plain text... but rather in an encrypted hash.

Then run:
```

sudo update-grub

```
Notice I said in Grub file '40_custom'... All the other files except that one are changed and updated during system updates...
RE: [https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)
> 
* The superuser/user information and password do not have to be contained in the /etc/grub.d/00_header file. The information can be placed in any /etc/grub.d file as long as that file is incorporated into grub.cfg. The user may prefer to enter this data into a custom file, such as /etc/grub.d/40_custom so it is not overwritten should the Grub package be updated.


Then, if your BIOS allows, only set the boot order to that boot device (and no others), then set a BIOS Password to lock that down...

****
Now the rest of the Disclaimer: 
Remember me saying that Physical Security is paramount? Off the top of my head, I know over 4 ways to get around that. This is why Computer Rooms in DataCenters are locked and have secure access. And you should be aware that these methods will make things harder, take time, but not impossible to get around.

---

### Post by mhs122 on 2022-03-24
umm, i'm not have boot login, i want to only single mode login
i don't boot login [COLOR=#202124][FONT=&quot]question[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-03-24
Now you have me confused at what you want as your goal... What you have created in Grub's 00_header has already created multiple login processes... nd the usual reason for doing that is to secure Single User Modes at boot.

That will prevent any editing of Grub Boot menus, and not ask for a Grub password, except if you try to edit one of the menu items, use the grub cli, or use a recovery mode. That is the only reasons I know of to use a Grub Password.

Maybe you should try to explain what your goal actually is. We are having problems "guessing" the unknown.

---

### Post by MAFoElffen on 2022-03-24
Are you "trying" to change the boot process so that only boot into a "single user boot mode", where it would be in that mode "without" having to use a password?

If so, then you went the opposite direction towards that, in what you described in your first post.

Again... Help us, to enable us to help you. Communications is the mutual understanding between the involved parties... That "mutual understanding" is clearly not there yet. 

More information needed.

---

