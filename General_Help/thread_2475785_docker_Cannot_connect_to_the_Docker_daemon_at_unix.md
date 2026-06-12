---
title: "docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock."
date: 2022-06-08
forum: General Help
---

### Post by chat-4432 on 2022-06-08
when I run
docker run hello-world
that I install  docker engine on ubuntu WSL
it shows
```
docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.
```
i try 
systemctl start docker
> System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down

method 1
```
[FONT=Consolas]sudo -b unshare --pid --fork --mount-proc /lib/systemd/systemd --system-unit=basic.target
sudo -E nsenter --all -t $(pgrep -xo systemd) runuser -P -l $USER -c "exec $SHELL"
#this will enable systemctl command for linux ubuntu subsystem on windows[/FONT]
```
method 2
i change systemd as init
[https://linuxhandbook.com/system-has-not-been-booted-with-systemd/](https://linuxhandbook.com/system-has-not-been-booted-with-systemd/)
[COLOR=#333333][FONT=Inter]service docker start
[/FONT][/COLOR]>  * Starting Docker: docker                                                                                       [ OK ]
[COLOR=#333333][FONT=Inter]if not work try [/FONT][/COLOR][https://crapts.org/2022/05/15/install-docker-in-wsl2-with-ubuntu-22-04-lts/](https://crapts.org/2022/05/15/install-docker-in-wsl2-with-ubuntu-22-04-lts/)[COLOR=#333333][FONT=Inter]
work on 20.04 ,but still not 22.04 [/FONT][/COLOR]because 22.04 need to switch [COLOR=#222426][FONT=monospace]iptables-nft to [/FONT][/COLOR][COLOR=#222426][FONT=monospace]iptables-legacy[/FONT][/COLOR][COLOR=#333333][FONT=Inter]
[/FONT][/COLOR]error installation [COLOR=#232629][FONT=-apple-system]22.04  [/FONT][/COLOR]because [COLOR=#232629][FONT=-apple-system]new TUI configuration [/FONT][/COLOR][COLOR=#333333][FONT=Inter]
[/FONT][/COLOR]> The system cannot find the file specified.
if can't install 22.04 (wsl2)
[https://linuxconfig.org/ubuntu-22-04-on-wsl-windows-subsystem-for-linux](https://linuxconfig.org/ubuntu-22-04-on-wsl-windows-subsystem-for-linux) not showing the  step 8 
[COLOR=#333333][FONT=Inter]now i switch to 20.04 or [/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]skip [/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]TUI configuration to [/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]console-based[/FONT][/COLOR][COLOR=#333333][FONT=Inter]
[/FONT][/COLOR][https://askubuntu.com/questions/1406388/how-to-fix-0x8027025a-error-when-installing-ubuntu-22-04-lts-on-wsl](https://askubuntu.com/questions/1406388/how-to-fix-0x8027025a-error-when-installing-ubuntu-22-04-lts-on-wsl)[COLOR=#333333][FONT=Inter]
[/FONT][/COLOR]```
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
```
[COLOR=#333333][FONT=Inter]sudo service docker start
# note
# wsl docker service are not start on boot
# wsl are use old init not systemd
# 22.04 use new [/FONT][/COLOR][COLOR=#222426][FONT=monospace]iptables-nft[/FONT][/COLOR][COLOR=#222426][FONT=monospace] & new TUI

[/FONT][/COLOR]

---

### Post by chat-4432 on 2022-06-08
> the system cannot find the file specified.[COLOR=#171717][FONT=SFMono-Regular]
uncheck wsl in  [/FONT][/COLOR]windows features[COLOR=#171717][FONT=SFMono-Regular]
method 2 not reinstall [/FONT][/COLOR][https://askubuntu.com/questions/1406388/how-to-fix-0x8027025a-error-when-installing-ubuntu-22-04-lts-on-wsl](https://askubuntu.com/questions/1406388/how-to-fix-0x8027025a-error-when-installing-ubuntu-22-04-lts-on-wsl)[COLOR=#171717][FONT=SFMono-Regular]
create new user
[/FONT][/COLOR][FONT=var(--ff-mono)]
[/FONT][FONT=var(--ff-mono)]# Enter your desired username
[/FONT]adduser $NEWUSER
# This will create your username/password
usermod -aG  adm,cdrom,sudo,dip,plugdev,lxd $NEWUSER

# The following 4 lines must be entered together
cat <<EOF > /etc/wsl.conf
[user]
default=$NEWUSER
EOF

cat /etc/wsl.conf
# Confirm the contents
restart ubuntu
[COLOR=#232629][FONT=-apple-system]Exit Ubuntu, and from PowerShell:[/FONT][/COLOR]
wsl --terminate Ubuntu-22.04

---

