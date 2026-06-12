---
title: "Problem with the tftp Server"
date: 2016-04-25
forum: General Help
---

### Post by Semproms on 2016-04-25
Hi, I'm trying to set up a tftp server on Kubuntu 14.04 in order to install an operating system through the network. The DHCP Server works perfect, but when I follow the steps to install and start the tftp server I get this message:

sudo /etc/init.d/tftpd-hpa start (This command does nothing).
sudo /etc/init.d/tftpd-hpa status
 * in.tftpd is not running 

My tftpd configuration file is:

# /etc/default/tftpd-hpa


TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="[::]:69"
TFTP_OPTIONS="--secure"
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"

Anyone knows what could be the problem?

Thank you.

---

