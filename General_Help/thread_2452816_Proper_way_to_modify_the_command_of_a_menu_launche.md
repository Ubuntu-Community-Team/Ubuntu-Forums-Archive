---
title: "Proper way to modify the command of a menu launcher? (Blender)"
date: 2020-10-28
forum: General Help
---

### Post by rocco-xyz on 2020-10-28
Hello friends.
I am new to Linux (I have some experience with Windows), I am using Xubuntu 18.04, I know it is a somewhat old distribution but it is the latest version that supports the computer I am using (x86).
I installed Blender (2.79b) using the Software launcher (gnome-software% U) from the menu, but Blender does not start when I click on its launcher; typing [FONT=courier new][SIZE=2]blender[/SIZE][/FONT] in a terminal prints:
```
[FONT=courier new][SIZE=2]Error! Blender requires OpenGL 2.1 to run. Try updating your drivers.[/SIZE][/FONT]
```
Searched the web, I found [this post]("https://community.parrotsec.org/t/ayuda-con-opengl-resuelto/4912") (in spanish), where they "fix" the problem with the command: ```
[FONT=courier new]MESA_GL_VERSION_OVERRIDE = 2.1 blender[/FONT]
```
Doing so blender does start and seems to be working fine.
I want to modify the blender launcher from the menu, so I right click it > "Edit application ..." the "Edit Launcher" window appears where I modify the "Command" field from "blender% f" to "MESA_GL_VERSION_OVERRIDE = 2.1 blender" and I save it, but clicking it gives me a
"Error :
Failed to execute command "TABLE_GL_VERSION_OVERRIDE = 2.1 blender".
Failed to execute child process "MESA_GL_VERSION_OVERRIDE = 2.1" (No such file or directory)"
So how do I modify the launcher so I don't have to open the terminal and type that command when I want to run Blender?
Thanks in advance.

PS. cat /etc/*release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.5 LTS"
NAME="Ubuntu"
VERSION="18.04.5 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.5 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
```

---

### Post by &amp;KyT$0P# on 2020-10-28
Copy Blender's .desktop file from /usr/share/applications to ~/.local/share/applications (create this folder if it does not exist), then edit the [FONT=Courier New]Exec=[/FONT] line of your copy to -
```
Exec=/bin/sh -c "MESA_GL_VERSION_OVERRIDE=2.1 blender"
```

Then open a Terminal and run -
```
cd ~/.local/share/applications;update-desktop-database .
```

Does it work now?

---

### Post by rocco-xyz on 2020-10-28
There was no .desktop file in /usr/share/applications, but it already existed in ~/.local/ share/ applications/, I edited it as you said and it works now. Thanks

---

