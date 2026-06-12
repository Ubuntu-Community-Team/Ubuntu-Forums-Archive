---
title: "SSH issue"
date: 2019-10-12
forum: General Help
---

### Post by gmf2012 on 2019-10-12
Hello,
I have an odd situation, when I setup SSH on a Ubuntu Mate 18.04.3 LTS it works fine, I can access the client remotely. if i log off the Ubuntu Mate 18.04.3 LTS client i can no longer ssh it remotly. unless i physically logon to the Ubuntu Mate 18.04.3 LTS client

tia,
GFlanagan

---

### Post by TheFu on 2019-10-12
Do you have HOME directory encryption enabled?

What is the ssh server running?

---

### Post by gmf2012 on 2019-10-12
> **TheFu said:**
> Do you have HOME directory encryption enabled?

What is the ssh server running?

Thanks for you feed back. Home drive is not encrypted. doing a ls -A /home does not show he home drive is encrypted.

I have two other laptops running the same OS, one wired and one wireless, no problem. However the client giving me the ssh problem is i386, not sure if that is the difference.

also, i tried the client both wired and wireless and no luck.

thanks!

---

### Post by TheFu on 2019-10-12
I have an i686 desktop running 16.04. i386 support was dropped about 10 yrs ago, methinks. No issues with it ssh'ing into any other systems that support ed25519 ssh-keys.

Please be EXTREMELY clear.  What is the client and what is the server?

Does **ssh -vvvv** show anything wrong?

---

### Post by gmf2012 on 2019-10-12
ssh -vvvv tells me I using the wrong otpion
root@user-1000HE:~/Downloads# ssh -vvvv
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]

This client I am ssh'ing **from** is a windows 10 box and the client i am ssh'ing to is an ubuntu 18.04 i386 box

root@user-1000HE:~/Downloads# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
root@user-1000HE:~/Downloads# 

root@user-1000HE:~/Downloads# sudo systemctl status ssh.service
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-10-12 11:24:12 EDT; 2h 15min ago
 Main PID: 971 (sshd)
    Tasks: 1 (limit: 4505)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;971 /usr/sbin/sshd -D


Oct 12 12:50:43 user-1000HE sshd[971]: Received SIGHUP; restarting.
Oct 12 12:50:44 user-1000HE sshd[971]: Server listening on 0.0.0.0 port 22.
Oct 12 12:50:44 user-1000HE sshd[971]: Server listening on :: port 22.
Oct 12 12:50:44 user-1000HE systemd[1]: Reloading OpenBSD Secure Shell server.
Oct 12 12:50:44 user-1000HE sshd[971]: Received SIGHUP; restarting.
Oct 12 12:50:44 user-1000HE systemd[1]: Reloaded OpenBSD Secure Shell server.
Oct 12 12:50:44 user-1000HE sshd[971]: Server listening on 0.0.0.0 port 22.
Oct 12 12:50:44 user-1000HE sshd[971]: Server listening on :: port 22.
Oct 12 12:51:01 user-1000HE sshd[5676]: Accepted password for user from 172.16.0.11 port 53348 ssh2
Oct 12 12:51:01 user-1000HE sshd[5676]: pam_unix(sshd:session): session opened for user user by (uid=0)

---

### Post by TheFu on 2019-10-12
Sorry, I don't know **anything** about win10, but if you don't provide the correct options to ssh, it isn't going to attempt any connection.

ssh -vvvv userid@remote-system

The userid needs to be the Server userid.
The remote-system should be either an IP or DNS name that can be used to "ping". This is not necessarily the same name as 'hostname' returns or what network file sharing uses.  Windows is non-standard in broadcasting that data.

---

