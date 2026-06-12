---
title: "rsync: connection unexpectedly closed"
date: 2014-09-08
forum: General Help
---

### Post by zirby on 2014-09-08
Hello all,

I have a remote backup by rsync.
I have good private/public key with the remote.

When I do:
> rsync -azP --timeout=600 --ignore-errors --delete login@ip_adress:/home/something/Public/ home/something/Public

Everything goes well until I receive:

[COLOR=#ff0000]rsync: connection unexpectedly close (666555 bytes received so far)[/COLOR]
rsync error: unexplained error (code 255) at io.c(605)

Can someone help me ?

---

### Post by coffeecat on 2014-09-08
Not a Forum Feedback & Help question.

*Thread moved to **General Help**.*

---

### Post by nerdtron on 2014-09-08
First line of troubleshooting:

Try the "ssh -vvv login@ip_adress" and post the output here.
If you have setup good ssh public/private keys then you should have no problems logging in.

Are you sure ssh-server is installed an running on the remote machine?
```
sudo apt-get install openssh-server
sudo service sshd status
```

---

### Post by zirby on 2014-09-09
Hello nerdtron,

I send my ssh -vvv :
> crem@SVRBIS:~$ ssh -vvv crem@192.168.1.110OpenSSH_5.9p1 Debian-5ubuntu1.4, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /home/crem/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.110 [192.168.1.110] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/crem/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/crem/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/crem/.ssh/id_rsa-cert type -1
debug1: identity file /home/crem/.ssh/id_dsa type -1
debug1: identity file /home/crem/.ssh/id_dsa-cert type -1
debug1: identity file /home/crem/.ssh/id_ecdsa type -1
debug1: identity file /home/crem/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.4
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.110" from file "/home/crem/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/crem/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA eb:2e:25:f0:57:d7:41:53:97:d3:25:ca:d3:86:d2:56
debug3: load_hostkeys: loading entries for host "192.168.1.110" from file "/home/crem/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/crem/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.1.110' is known and matches the ECDSA host key.
debug1: Found key in /home/crem/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/crem/.ssh/id_rsa (0xb9707370)
debug2: key: /home/crem/.ssh/id_dsa ((nil))
debug2: key: /home/crem/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/crem/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp 6a:ba:23:35:99:61:ed:23:60:76:5b:02:8d:34:13:a2
debug3: sign_and_send_pubkey: RSA 6a:ba:23:35:99:61:ed:23:60:76:5b:02:8d:34:13:a2
debug1: Authentication succeeded (publickey).
Authenticated to 192.168.1.110 ([192.168.1.110]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env XDG_SESSION_PATH
debug3: Ignored env XDG_SEAT_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug1: Sending env LANG = fr_BE.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env COMPIZ_CONFIG_PROFILE
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env XDG_CURRENT_DESKTOP
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 3.5.0-54-generic i686)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


26 packages can be updated.
26 updates are security updates.






Your current Hardware Enablement Stack (HWE) is no longer supported
since 2014-08-07.  Security updates for critical parts (kernel
and graphics stack) of your system are no longer available.


For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)


There is a graphics stack installed on this system. An upgrade to a 
supported (or longer supported) configuration will become available
on 2014-07-16 and can be invoked by running 'update-manager' in the
Dash.
    


*** /dev/sdb1 will be checked for errors at next reboot ***


Last login: Wed Sep  3 23:31:48 2014 from svrbis.local
crem@SVRLAN:~$ debug2: client_check_window_change: changed
debug2: channel 0: request window-change confirm 0
crem@SVRLAN:~$ 




and on the the server openssh is installed.
BUT 
> sudo service ssh start 
is OK
> sudo service sshd status
give me an 
> unrecognized service

---

### Post by SeijiSensei on 2014-09-09
The service name is "ssh" not "sshd" so you get an "unknown service" error in the second case.  RedHat calls the SSH service sshd on its platform.

What if you try copying some other set of files with rsync or scp?  You're obviously making a connection and can send 665K bytes, so I'm wondering if there's some corruption problem with one of the source files.

---

### Post by nerdtron on 2014-09-09
In addition, since you can successfully ssh to the remote machine, have you tried using the scp command instead of rsync? If scp works, we can narrow it further down the problem.

---

### Post by zirby on 2014-09-10
I try with scp and it stops after a certain time, with:
> corrupted MAC on input
Disconnected: Packet corrupt
lost connection

---

### Post by SeijiSensei on 2014-09-10
And do you have the same problem with other files?

---

### Post by zirby on 2014-09-11
Each time I relaunch my Rsync script it goes a bit further.
Now I have reached the end of my sync.
But I still don't know WHY the connection closed randomly?

---

### Post by nerdtron on 2014-09-11
Any firewall or proxy between the two machines?

---

### Post by colemar on 2014-09-30
> **zirby said:**
> Each time I relaunch my Rsync script it goes a bit further.
Now I have reached the end of my sync.
But I still don't know WHY the connection closed randomly?

```
#!/bin/bash

while true
do
    if /usr/bin/rsync "$@"; then
        echo "rsync completed normally"
        exit
    else
        echo "rsync failure. Retrying..."
        sleep 1
    fi
done
```

---

