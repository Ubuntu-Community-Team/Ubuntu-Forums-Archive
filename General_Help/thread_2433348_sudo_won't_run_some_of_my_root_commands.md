---
title: "sudo won't run some of my root commands"
date: 2019-12-17
forum: General Help
---

### Post by Skaperen on 2019-12-17
when i try to run my customized root commands via [COLOR=#0000cd][FONT=courier new]**sudo**[/FONT][/COLOR], it can't find them.  this is because it does not set the [COLOR=#800080][FONT=courier new]**PATH**[/FONT][/COLOR] environment variable correctly (it does not set it at all so it remains at the initial value.  i look though the [COLOR=#0000cd]**sudo**[/COLOR] man page and i find nothing that can get it to set that.  it would need to run [COLOR=#006400][FONT=courier new]**/root/.bashrc**[/FONT][/COLOR] to get [COLOR=#800080][FONT=courier new]**PATH**[/FONT][/COLOR] set correctly.  any idea how to do this?  if i start a root shell using [COLOR=#0000cd][FONT=courier new]**sudo**[/FONT][/COLOR], i can type in the command there and it works fine.

---

### Post by TheFu on 2019-12-18
sudo does have a setting to control the PATH.  **man sudoers**  These are security features.
To search manpages, use **apropos**
```
$ apropos sudo
gksu (1)             - GTK+ frontend for su and sudo
gksudo (1)           - GTK+ frontend for su and sudo
sudo (8)             - execute a command as another user
sudo.conf (5)        - configuration for sudo front end
sudo_plugin (8)      - Sudo Plugin API
sudo_root (8)        - How to run administrative commands
sudoedit (8)         - execute a command as another user
sudoers (5)          - default sudo security policy plugin
sudoreplay (8)       - replay sudo session logs
visudo (8)           - edit the sudoers file

```
Sometimes a useful manpage will be in a config file section, so specifying the manpage section is needed.

The best practice for all scripting is to use the full-path to all commands.  That way we get exactly the command and version we want.

---

