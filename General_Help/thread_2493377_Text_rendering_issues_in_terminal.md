---
title: "Text rendering issues in terminal"
date: 2023-12-13
forum: General Help
---

### Post by spearhead2 on 2023-12-13
After fresh re-install I face some really annoying issues with text rendering in bash. Consider string "111111111100000000000000000000". If I paste in from clipboard into mate-terminal (gnome-terminal is the same), what I have displayed is, as expected:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293195&stc=1[/IMG]

But after that if I press arrow right suddenly six initial characters are duplicated:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293196&stc=1[/IMG]

This is just render artifact: if I press enter, console behaves as if only original input was present.

Similarly, I can write bunch of characters in the terminal:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293197&stc=1[/IMG]

Now when I press Crtl+U to clear the line, what I got is:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293198&stc=1[/IMG]

This is only an artifact, If I press enter console just behaves as if prompt was empty.

This is bash-only behaviour, I can't reproduce it in ZSH or fish.

Any hint how to fix this?

---

### Post by ActionParsnip on 2023-12-13
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy `dpkg -l | grep -i terminal | awk {'print $2'}`

```
Thanks

---

### Post by spearhead2 on 2023-12-13
Here's the output
```
$ lsb_relsb_release -a; uname -a; apt-cache policy `dpkg -l | grep -i terminal | awk {'print $2'}`
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy
Linux mariusz-HP-Pavilion-Notebook 6.2.0-37-generic #38~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov  2 18:01:13 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
caja-open-terminal:
  Installed: 1.26.0-1ubuntu0.22.04.1
  Candidate: 1.26.0-1ubuntu0.22.04.1
  Version table:
 *** 1.26.0-1ubuntu0.22.04.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.26.0-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
gnome-terminal:
  Installed: 3.44.0-1ubuntu1
  Candidate: 3.44.0-1ubuntu1
  Version table:
 *** 3.44.0-1ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
gnome-terminal-data:
  Installed: 3.44.0-1ubuntu1
  Candidate: 3.44.0-1ubuntu1
  Version table:
 *** 3.44.0-1ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
guake:
  Installed: 3.8.5-1
  Candidate: 3.8.5-1
  Version table:
 *** 3.8.5-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status
konsole:
  Installed: 4:21.12.3-0ubuntu1
  Candidate: 4:21.12.3-0ubuntu1
  Version table:
 *** 4:21.12.3-0ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libncurses6:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
libncurses6:i386:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
libncursesw6:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
libncursesw6:i386:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
libterm-readkey-perl:
  Installed: 2.38-1build4
  Candidate: 2.38-1build4
  Version table:
 *** 2.38-1build4 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
libtext-charwidth-perl:
  Installed: 0.04-10build3
  Candidate: 0.04-10build3
  Version table:
 *** 0.04-10build3 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
libtinfo6:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
libtinfo6:i386:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
libvte-2.91-0:
  Installed: 0.68.0-1
  Candidate: 0.68.0-1
  Version table:
 *** 0.68.0-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
libvte-2.91-common:
  Installed: 0.68.0-1
  Candidate: 0.68.0-1
  Version table:
 *** 0.68.0-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
mate-terminal:
  Installed: 1.26.0-1ubuntu2
  Candidate: 1.26.0-1ubuntu2
  Version table:
 *** 1.26.0-1ubuntu2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
mate-terminal-common:
  Installed: 1.26.0-1ubuntu2
  Candidate: 1.26.0-1ubuntu2
  Version table:
 *** 1.26.0-1ubuntu2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status
nautilus-extension-gnome-terminal:
  Installed: 3.44.0-1ubuntu1
  Candidate: 3.44.0-1ubuntu1
  Version table:
 *** 3.44.0-1ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
ncurses-base:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
ncurses-bin:
  Installed: 6.3-2ubuntu0.1
  Candidate: 6.3-2ubuntu0.1
  Version table:
 *** 6.3-2ubuntu0.1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.3-2 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
python3-colorama:
  Installed: 0.4.4-1
  Candidate: 0.4.4-1
  Version table:
 *** 0.4.4-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
python3-ptyprocess:
  Installed: 0.7.0-3
  Candidate: 0.7.0-3
  Version table:
 *** 0.7.0-3 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
terminator:
  Installed: 2.1.1-1
  Candidate: 2.1.1-1
  Version table:
 *** 2.1.1-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status
tilda:
  Installed: 1.5.4-1
  Candidate: 1.5.4-1
  Version table:
 *** 1.5.4-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
xfce4-terminal:
  Installed: 0.8.10-1
  Candidate: 0.8.10-1
  Version table:
 *** 0.8.10-1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
xterm:
  Installed: 372-1ubuntu1
  Candidate: 372-1ubuntu1
  Version table:
 *** 372-1ubuntu1 500
        500 http://pl.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Holger_Gehrke on 2023-12-13
This looks like the kind of problem I got when I originally tried to customize my prompt and didn't put '\[' '\]' around non-printing characters and the shell calculated my visible prompt to be longer than it actually was. Check the definition(s) of PS1 in your ~/.bashrc.

If that's not the problem, knowing what version of Ubuntu (lsb_release -a), bash (echo $BASH_VERSION), the terminals in question (can probably be found in the help-menu of the terminal), and possibly of libreadline (apt show libreadline8) might help us help you.

Holger

---

### Post by spearhead2 on 2023-12-13
> **Holger_Gehrke said:**
> This looks like the kind of problem I got when I originally tried to customize my prompt and didn't put '\[' '\]' around non-printing characters and the shell calculated my visible prompt to be longer than it actually was. Check the definition(s) of PS1 in your ~/.bashrc.

If that's not the problem, knowing what version of Ubuntu (lsb_release -a), bash (echo $BASH_VERSION), the terminals in question (can probably be found in the help-menu of the terminal), and possibly of libreadline (apt show libreadline8) might help us help you.

Holger

Looks like this is it - when I commented out my `PS1` everything behaves normally. Thanks!

---

