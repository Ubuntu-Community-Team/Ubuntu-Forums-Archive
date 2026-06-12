---
title: "All VLC menus greyed out"
date: 2020-06-11
forum: General Help
---

### Post by NoDeity on 2020-06-11
Lubuntu (System information shows Ubuntu 18.04.4 LTS)
VLC 3.0.8 Vetinari

All menus in both VLC and Kdenlive are greyed out, including the right-click menu. I can guess at where different menu items might be, click the spot, and the appropriate window shows up.

I'll attach two photos to show what I'm seeing.
[ATTACH=CONFIG]286189[/ATTACH]
[ATTACH=CONFIG]286190[/ATTACH]

---

### Post by &amp;KyT$0P# on 2020-06-11
How do you have Qt 5 appearance configured?

---

### Post by NoDeity on 2020-06-11
Sadly, I have no idea what QT 5 is.

---

### Post by ActionParsnip on 2020-06-12
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy vlc

```
Thanks

---

### Post by NoDeity on 2020-06-25
> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a; apt-cache policy vlc

```
Thanks

brad@bradbot:~$ lsb_release -a; uname -a; apt-cache policy vlc
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
Linux bradbot 4.15.0-108-generic #109-Ubuntu SMP Fri Jun 19 11:33:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
vlc:
  Installed: 3.0.8-0ubuntu18.04.1
  Candidate: 3.0.8-0ubuntu18.04.1
  Version table:
 *** 3.0.8-0ubuntu18.04.1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.0.1-3build1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
brad@bradbot:~$

---

### Post by MoebusNet on 2020-06-27
@NoDeity - When I last had a problem with VLC, this is what fixed it:

1) Open LXTerminal (in Lubuntu) and type

```
sudo pcmanfm
```

Of course replace 'pcmanfm' with the name of your file manager (ie, 'nautilus' for Ubuntu).

2) In your flie manager, click View>Hidden Files

3) Scroll down to the '.config' folder

4) Double-click the '.config' folder to open it

5) Scroll down to the 'vlc' folder

6) Right-click the 'vlc' folder

7) In the menu that pops up, Left-click 'Move to Trash'

8) Close your file manager

9) Close the LXTerminal window.

10) Reopen VLC; it should now reconfigure itself and work as designed.

I can't promise this will fix your problem, but I've had to do this a couple of times with no ill effects and solved my problem of off-screen portions of the VLC window.

---

### Post by NoDeity on 2020-06-27
@[**[COLOR=#000000]MoebusNet[/COLOR]**]("https://ubuntuforums.org/member.php?u=150834")
Thank you for the effort but this didn't solve the issue.

---

### Post by NoDeity on 2020-06-27
I don't think the problem is specific to  VLC. I'm having the same issue with Kdenlive.
(I should edit the first post to reflect that.)

---

### Post by MoebusNet on 2020-07-15
If you're still having problems, it may have to do with the fact that Lubuntu 18.04 used the LXDE dektop while 20.04 uses the LXQt desktop. Since LXDE is being deprecated, it is no longer well-supported as to minor bugs. If you can live with the issues you have until 20.04.1 comes out, you may be better off upgrading ( or even better backing up your data and doing a clean installation then restoring your data. )

---

### Post by monkeybrain20122 on 2020-07-15
Start vlc (or any other application that is affected) from the terminal and post the output messages. just open a terminal and type vlc.

---

