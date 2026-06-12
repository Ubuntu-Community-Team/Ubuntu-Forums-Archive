---
title: "Script not running in OS restart and shutdown"
date: 2021-11-25
forum: General Help
---

### Post by aug7744 on 2021-11-25
I have tried to create a script to flush writecache buffer.
All commands works in terminal.

Tested in a VM installed Lubuntu 20.04.3.

The script was named K99 being executable and owner root.
The script was copied to /etc/init.d/ and created symbolic link to /etc/rc0.d/ and /etc/rc6.d/

The script is
-----------------------------------------------------------------------------------------------------------------------------------
#!/bin/bash
sudo dmsetup message /dev/mapper/rc-wb_sda3 0 flush
sudo dmsetup suspend /dev/mapper/rc-wb_sda3
sudo dmsetup message /dev/mapper/rc-wb_sda4 0 flush
sudo dmsetup suspend /dev/mapper/rc-wb_sda4
sudo dmsetup message /dev/mapper/rc-wb_sda5 0 flush
sudo dmsetup suspend /dev/mapper/rc-wb_sda5
sudo dmsetup message /dev/mapper/rc-wb_sda6 0 flush
sudo dmsetup suspend /dev/mapper/rc-wb_sda6

exit 0

-----------------------------------------------------------------------------------------------------------------------------------

After copying the script and creating symbolic links was done shutdown command and GUI was finalized showing only the "shutdown screen terminal command" with the OS halted not being possible shutdown.
Thus I had forced a power off shutdown.
I next OS starting was done shutdown command. The OS not was halted, but running commands several times in "shutdown screen terminal command" and repeating the same commands not being possible shutdown the OS.

The script is correct ? All steps was correct ? Need more actions to work ?
I had searched in internet how create a script to run command in restart and shutdown, but unhappily is very much wrong information that not work.

Thanks for reply.

---

### Post by ajgreeny on 2021-11-25
Ubuntu no longer uses the init system having replaced it with systemd a long time ago.
However, I think init will still work if you add things to it as iong as all requirements are satisfied.
Two possibilities I can think of:-

1- Is the script executable?

2- As all init actions are carried as root already by default, you will not need the sudo prefix for them.

---

### Post by aug7744 on 2021-11-25
Having several scripts in init.d path.

1 ) Yes.
2 ) I had tested with 2 same scripts one using sudo and other script not using sudo in each line having exactly the same issue.

---

