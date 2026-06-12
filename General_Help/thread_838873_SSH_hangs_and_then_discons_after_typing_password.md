---
title: "SSH hangs and then discons after typing password"
date: 2008-06-23
forum: General Help
---

### Post by rainrunner87 on 2008-06-23
I've lately been having some problems using SSH.  When I attempt to connect to a server, I type my password and then it hangs for about two and a half minutes before disconnecting me.  Here's the debugging output on level three:

```
emhs@greytop:~$ ssh -vvv shell.kracknet.net
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to shell.kracknet.net [208.68.239.244] port 22.
debug1: Connection established.
debug1: identity file /home/emhs/.ssh/identity type -1
debug1: identity file /home/emhs/.ssh/id_rsa type -1
debug1: identity file /home/emhs/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.5p1 FreeBSD-20061110
debug1: match: OpenSSH_4.5p1 FreeBSD-20061110 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 477/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/emhs/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/emhs/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'shell.kracknet.net' is known and matches the DSA host key.
debug1: Found key in /home/emhs/.ssh/known_hosts:1
debug2: bits set: 530/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/emhs/.ssh/identity ((nil))
debug2: key: /home/emhs/.ssh/id_rsa ((nil))
debug2: key: /home/emhs/.ssh/id_dsa ((nil))
debug3: input_userauth_banner
 ____ ____ ____ ____ ____ ____ ____ ____
||K |||r |||a |||c |||k |||N |||e |||t ||
||__|||__|||__|||__|||__|||__|||__|||__||
|/__\|/__\|/__\|/__\|/__\|/__\|/__\|/__\|

 KrackNet Communications, 1999-2008.
    Administrator: 954-812-1758

 *** New Users: ************************
 *                   *      BLUE       *
 *  Login: new       *  .KRACKNET.NET  *
 *  Password: new    *     FreeBSD     *
 *                   *  admin@kracknet *           
 ***************************************
 *       Free-Shells = Free-Dom!       *
 ***************************************
 *     IRC.KRACKNET.NET / #kracknet    *
 *************************************** 
 *         ADMIN: 954.812.1758         *
 ***************************************

 ***************************************
 ! We will be capping the blue box off !
 ! at 1500 users. Check out our IRCd   !
 ! for a chance to get into our new    !
 ! black.kracknet.net monster server!  !
 !   irc.kracknet.net - #kracknet      !
 ***************************************
 
debug1: Authentications that can continue: publickey,keyboard-interactive
debug3: start over, passed a different list publickey,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/emhs/.ssh/identity
debug3: no such identity: /home/emhs/.ssh/identity
debug1: Trying private key: /home/emhs/.ssh/id_rsa
debug3: no such identity: /home/emhs/.ssh/id_rsa
debug1: Trying private key: /home/emhs/.ssh/id_dsa
debug3: no such identity: /home/emhs/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
Password:
debug3: packet_send2: adding 32 (len 27 padlen 5 extra_pad 64)
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 0
debug3: packet_send2: adding 48 (len 10 padlen 6 extra_pad 64)
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env B
debug3: Ignored env D
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env H
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env S
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug3: Ignored env b
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env d
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env h
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env s
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
<2.5 minute pause>
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host shell.kracknet.net: Connection reset by peer
Connection to shell.kracknet.net closed.
debug1: Transferred: stdin 0, stdout 0, stderr 110 bytes in 142.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.8
debug1: Exit status -1
emhs@greytop:~$ 
```

This being said, I'm a little frustrated.  Anyone have any suggestions?

---

### Post by HalPomeranz on 2008-06-24
Looks like the authentication is succeeding, so I suspect a problem on the remote server.  Can you check the logs on the remote machine?

Are you able to ssh to other machines successfully?

---

### Post by rainrunner87 on 2008-06-24
Nope.  Can't connect to any servers.  Additionally, the server I connected to in that log is a major public server with plenty of people connecting to it all the time.  They're not having any problems.

---

### Post by HalPomeranz on 2008-06-24
I'd still try and get log/debugging information from the remote server.  Everything in your client debugging output looks sane/correct to me, so I'd be curious to see if the server side has any indication of why the connection is closing.

---

### Post by mexpolk on 2008-06-26
I have the same problem, here's my output:

```

some_user@some_machine:~$ ssh -v some_user@some_public_server
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to some_public_server [189.169.00.000] port 22.
debug1: Connection established.
debug1: identity file /home/some_user/.ssh/identity type -1
debug1: identity file /home/some_user/.ssh/id_rsa type 1
debug1: identity file /home/some_user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.2
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'some_public_server' is known and matches the RSA host key.
debug1: Found key in /home/some_user/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/some_user/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/some_user/.ssh/identity
debug1: Trying private key: /home/some_user/.ssh/id_dsa
debug1: Next authentication method: password
some_user@some_public_server's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: channel 0: free: client-session, nchannels 1
Read from remote host some_public_server: Connection timed out
Connection to some_public_server closed.
debug1: Transferred: stdin 0, stdout 0, stderr 116 bytes in 983.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.1
debug1: Exit status -1

```

And then it hangs out!

---

### Post by mexpolk on 2008-06-26
The problem persist and no answers. I've tried many things also (all tests using the same ssh client and same ssh server):

1. Connect physically on the same (local) network using the public name: **Works!**
2. Connect through Internet: **fails!**
3. Connect through PuTTY: **works!**
4. Connect through VirtualBox on a Windows XP client (I know, it sucks, but I'm kind of desperate) with PutTY: **works!**

It seems that the problem is the OpenSSH client. I've also tried uninstalling clearing the cache packages and nothing!

¿Any clues? ¿No one? :(

---

### Post by mexpolk on 2008-06-26
I've just connected successfully from my home (the same place was failing), the difference is that I've connected physically to the wired network. **It just fails when connected through wireless** ¿?

---

### Post by jaranguren on 2008-07-01
I have the same exact problem.  Wired works but ssh through wireless does not work.  

What wireless driver are you using?  I'm using ndiswrapper for Broadcom chip.

Could it be related to that?

---

### Post by jaranguren on 2008-07-01
Well, apparently I was not using ndiswrapper.  My wireless was using a module called "wl" and that was what causing my ssh problems.

I disabled it and reloaded ndiswrapper.  ssh works again!  :D

---

### Post by dave_t_uk on 2008-07-13
I seem to have the exact same problem - a hang in the exact same place, and for me too, it seems to be related to using wireless; specifically, I only get these problems when the client is wireless.  The server is always wireless in my case.

In case it wasn't made clear by an earlier post, the problem is not the timeout, the problem is that there is no text appearing after logging in.  I think the timeout and disconnect may be a consequence of this.

Also, this problem does not seem to be limited to ubuntu.  Let me point out that I have not got to the bottom of the problem!  But here are a few more pointers in the hope that someone can make sense of it.

Setup

[LIST]
[*]I have a WinXP client, and a SUSE server.
[*]My server is always wireless, and my client is either wireless or wired.
[*]I'm using 802.11g
[*]Both machines are on the same wireless network.
[/LIST]

Findings
[LIST]
[*]I get the same problem whether I use public/private key authentication or password authentication.
[*]***Surprising: if I 
```
# tail -f /var/log/messages
```
on the server, I see that when this problem occurs, as far as the server is concerned, the client has connected ok.  I also see the client as connected when I run 
```
$ w
```
from another command prompt on the server.  It's as though I'm logged in, only there is no text appearing when I type.
[*]I can log into a different (wired) server fine from my client, and that works fine.  This wired server is connected to the wireless access point.
[*]From that login on the different server, I can open a second ssh connection to the original server, and that works fine (i.e. if I use a wired server as a middle-man, it works fine).
[*]I see the exact same behaviour whether I use PuTTY or the command-line ssh client within cygwin.
[/LIST]

My conclusions from the above:
[LIST]
[*]The problem is probably not due to a linux driver (because I am experiencing the same problem in windows XP).
[*]The problem is a function of the client not the server (because a login from another machine worked fine).
[/LIST]

My only possible guess is that in some way, the bi-directional 2-hop communications (i.e. client-AP-server for the key strokes, then server-AP-client for the echoed characters) are not getting through when both the client and server are wireless.  Maybe one transmission is blocking another.

I've yet to try the server in wired mode to see if this makes a difference.

@rainrunner87: Thanks for posting your problem, I'm kind of reassured that someone else is having the same problem.  It's still very annoying though!

Dave

---

### Post by iucoen on 2008-07-23
> **jaranguren said:**
> Well, apparently I was not using ndiswrapper.  My wireless was using a module called "wl" and that was what causing my ssh problems.

I disabled it and reloaded ndiswrapper.  ssh works again!  :D

That is bizarre. Why would wl driver have problem with just SSH? All my HTTP and other TCP connections are working fine. There's gotta be another explanation.

Also, when I'm using the wl driver, I can't even ssh in to the laptop from another machine (same problem, ssh hangs after typing in password) So the problem is neither client nor server specific. It has something to do with how the SSH protocol interacts with the wl driver.

Does SSH do any ioctl or setsockopt that makes the wl driver unhappy?

---

### Post by iucoen on 2008-07-23
Mods, can we move this thread to a networking/wireless category. Maybe experts in those areas can enlighten us?

---

### Post by jim10 on 2008-08-03
I am getting the same problem, I just installed hardy 64 on a new dell laptop. I tried to use sshfs to transfer files over to the new computer but it kept timing out after I entered the password. I then tried to ssh into a few other servers and I got the same problem.

Switched over to a wired connection and everything worked perfectly. I was using the same wl restricted wireless drivers.

---

### Post by smalldog on 2008-08-06
I am using a dell laptop which wireless LAN card is Broadcom 1395, and installed with ubuntu 8.04 with wl restricted driver enabled. As all of you, the ssh session was hanged after ssh authentication. However, it only happen when I using ssh-client(command line mode). It can built up ssh connection, if I using putty instead.

---

### Post by jim10 on 2008-08-06
I think it has something to do with my router as well. I connected from my friend's router and Starbuck's router and it worked just fine. Then I tried my home router and it failed like it previously did.

This is very odd, I use ssh all the time as well as many other services and have never had a problem with this router before.

---

### Post by dakap on 2008-08-10
Hi,

Had that problem with SSH as well.
Solved it by replacing the bcmwl6.inf with bcmwl5.inf.

Apparently bcmwl6.inf is bad.
Followed the instructions in this link:
[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

Hope this works for you too!

---

### Post by jchau on 2008-08-11
dave_t_uk, I do think the server's wireless connection is at fault (at least it's not the sole fault).  I get the same problem when trying to connect to wired SSH server with a SSH client on Ubuntu on wireless (wl driver).  

I also tried this with several SSH servers; all of them seem to fail the same way when the Ubuntu OpenSSH client is wireless.  I've tried with WPA2 Personal, WPA, and unprotected wireless settings; same failure.  I also tried using different routers (I'm in a communications lab, we have many routers) and they fail in the same way.  

When I use my personal laptop (running Gentoo, using the OpenSSH SSH client, w/ an Intel IPW2200 wireless card, and with wpa_supplicant managing the connection), I do not have this problem, but I am also using a VPN connection on that computer, which may be working around the problem (even when connected to the same wireless routers).  

Using SSH through a wired connection works.  

This leads me to believe that dakap, in his post before mine <http://ubuntuforums.org/showpost.php?p=5561509&postcount=16>, is on the right track (but I haven't tried his solution yet).

---

### Post by dave_t_uk on 2008-08-11
Ok, here's some further developments.  Since my last post, I have reinstalled the operating system on the server.  It is now running ubuntu 8.04 instead of Suse SLED.  I believe that previously it was using some sort of 'wl' driver, but now it is using bcmwl5.inf with ndiswrapper.

I've also now got public key authentication working, but this doesn't improve or worsen the behaviour - it does authenticate though, even when I get no proper connection.

And yes, it may well have something to do with the access point.  In the last few minutes I have tried:

1) Connect from WinXP to Ubuntu via putty ssh via my own AP (linksys WRT54G, with DD-WRT firmware, WPA-PSK encryption) - hangs after login.
2) Connect from WinXP to Ubuntu via putty ssh via next-door neighbours access point (belkin 54g, no security :) ) - login works fine!

Since I've changed the server operating system and driver, I think it's fair to rule out server software, and the fact that it works over someone elses's network suggests that it's either:
- network hardware (i.e. the access point or it's firmware)
- network encryption (e.g. WPA).

Everything else works fine over both networks, internet, email, etc.  It's just ssh that seems to have this problem.

Anyone who's having this problem... what encryption does your network use?

The next step for me is to try temporarily removing the WPA encryption from my access point, and see if the ssh works again (that will tell me that it's the WPA encryption as opposed to my firmware modded access point).  

Perhaps I could also try temporarily enabling WPA encryption on my neighbour's access point but since there are currently 14 clients connected to it, I think most of the street would notice me doing this!

Dave

---

### Post by jchau on 2008-08-11
> **dave_t_uk said:**
> Ok, here's some further developments.  Since my last post, I have reinstalled the operating system on the server.  It is now running ubuntu 8.04 instead of Suse SLED.  I believe that previously it was using some sort of 'wl' driver, but now it is using bcmwl5.inf with ndiswrapper.

Did you intentionally switch to bcmwl5.inf?  My Ubuntu 8.04 install (i386 Desktop CD) defaulted to wl (after I used b43-fwcutter).  I assume from your statement that switching to bcmwl5 didn't help?

> I've also now got public key authentication working, but this doesn't improve or worsen the behaviour - it does authenticate though, even when I get no proper connection.

And yes, it may well have something to do with the access point.  In the last few minutes I have tried:

1) Connect from WinXP to Ubuntu via putty ssh via my own AP (linksys WRT54G, with DD-WRT firmware, WPA-PSK encryption) - hangs after login.
2) Connect from WinXP to Ubuntu via putty ssh via next-door neighbours access point (belkin 54g, no security :) ) - login works fine!

Since I've changed the server operating system and driver, I think it's fair to rule out server software, and the fact that it works over someone elses's network suggests that it's either:
- network hardware (i.e. the access point or it's firmware)
- network encryption (e.g. WPA).

I tried disabling encryption on my router (running Tomato) and it didn't help.  

> Everything else works fine over both networks, internet, email, etc.  It's just ssh that seems to have this problem.

Anyone who's having this problem... what encryption does your network use?

The next step for me is to try temporarily removing the WPA encryption from my access point, and see if the ssh works again (that will tell me that it's the WPA encryption as opposed to my firmware modded access point).  

Perhaps I could also try temporarily enabling WPA encryption on my neighbour's access point but since there are currently 14 clients connected to it, I think most of the street would notice me doing this!

Dave

I wouldn't suggest changing your neighbor's setting until you get permission to do so.

---

### Post by dave_t_uk on 2008-08-12
> **jchau said:**
> Did you intentionally switch to bcmwl5.inf?  My Ubuntu 8.04 install (i386 Desktop CD) defaulted to wl (after I used b43-fwcutter).  I assume from your statement that switching to bcmwl5 didn't help?

I was following [Ubuntu install instructions]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") specific to my hardware, and they recommended bcmwl5 with ndiswrapper.  Prior to this, on Ubuntu I don't know which wireless driver was being used, but the wireless connection did not work at all.  The 'wl' driver was while I was using SLED.  I know very little about this original 'wl' driver because it came preinstalled on the laptop.

---

### Post by dave_t_uk on 2008-08-12
I tried disabling the encryption on my access point, but this made no difference, I still get an ssh hang after authentication.  So maybe it really does have something to do with the access point or the firmware on it.  When I go through a different access point (also no encryption), it works fine.

I have a WRT54G, with firmware DD-WRT v23 SP2 (09/15/06) std (SVN revision 3932).

Anyone else who reads this who is experiencing the same problem, please could you state the access point type and firmware version if possible.

It occurs to me that it might have something to do with the IP addressing/routing too, exactly how, I can't be sure, but anyway, my access point operates DHCP and DNS on a 192.168.2.x subnet where 192.168.2.1 is the access point, and the clients are 192.168.2.100 and above.  The uplink to the internet is via an ethernet modem wired directly to the access point at 192.168.1.1 (although this should not be part of the exchange - and shouldn't matter).

I'm still quite puzzled about the root cause of this to be honest.

Dave

---

### Post by jim10 on 2008-08-16
Well I bought a new router...

I thought my ancient linksys BEFW11s4 v2 router was partially to blame for my troubles. This because I was able to ssh just fine when using Starbuck's wifi. I went out and bought a linksys WRT54G2.

But I am still getting the same ssh problems with the new router :(

I am using the restricted wl driver on hardy 64.

---

### Post by bigchirv on 2008-08-17
I just disabled the wl driver through the restricted drivers manager  - System > Administration > Hardware drivers (Sorry if the path is not accurate, translating from spanish on-the-fly :-))

Now I'm using the ndiswrapper driver with the bcmwl5 inf file and works perfectly.

The pertinent line of my lspci output describing my wireless card:

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

This is on an HP Pavillion dv6000 series.

---

### Post by wtgee on 2008-08-18
I just installed Ubuntu 8.10 (alpha 4) 64-bit on a new Dell 1535 using the Broadcom drivers and am seeing the same ssh problem with my wireless card.  I don't think it is a problem with the access point, just with the wireless.  I have two laptops sitting here and one of them can ssh without any problems and the new Dell doesn't.  Not sure what the resolution is, I'm still looking.

---

### Post by uncannybuzzard on 2008-08-19
this definitely has to do with the wl driver. i followed the instructions here: [http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088) (or rather, just used the ndisgtk app. it's a bit less messy).

i extracted the necessary folder from the exe and uploaded it here. to save some headache.

[http://xx-xy.org/DRIVER_US.tar.gz](http://xx-xy.org/DRIVER_US.tar.gz)

this solved my ssh problem.

running a broadcom 4312

---

### Post by the7erm on 2008-08-27
Thank you OH SO MUCH for the instructions on [http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)
IT WORKED!

I've been struggling for about 2 days just so I can ssh into the other machine!

Erm

---

### Post by mhogerheijde on 2008-09-08
I have the same problem, but what i find troubling is that using another ssh-program, e.g. Putty, the connection works fine!

I think this indicates that it is not especially the wireless driver but the combination of the cli-ssh client and the wl propriety driver.

I have a Linksys router with WPA enabled, a dell Studio 1735 using the wl driver from Broadcom and Ubuntu 8.04 x64.

---

### Post by dave_t_uk on 2008-12-17
I don't know if people are still experiencing this problem, but Ubuntu (and probably also the wireless drivers) have updated themselves over the last few months, and I have also changed my access point to a D-link one, for different reasons.  I can now connect seamlessly using the same Putty WinXP ssh client which failed previously.  The encryption settings, encryption passwords and both machines are identical to before.

To be honest, I don't know what fixed it, my guess is that it was changing the access point.

All the best to anyone else still trying to solve this problem.

Regards, Dave

---

### Post by trebonius on 2009-04-05
Wow.  This appears to be a disturbingly specific problem.  I'm having it too, and I have a wl-based wireless card AND a router running Tomato.  The common thread appears to be:
* wl module 
* Linux-based access point/router
* openssh client

If I read everyone's messages correctly, it sounds like changing any one of these variables will fix the problem.

---

### Post by crypto- on 2009-04-10
I've got a small data point to add to this discussion:

I have the same problem, a Dell Mini9 running Ubuntu, running with the wl wireless driver.

I too cannot connect to any hosts via ssh.

I too have a WRT54G.

However, mine is one of the very new ones that doesn't run Linux.

---

### Post by crypto- on 2009-04-10
UPDATE: FIXED!!!!

One of my pals found this link:

[http://mydellmini.com/forum/fixing-ssh-t1092.html](http://mydellmini.com/forum/fixing-ssh-t1092.html)


In /etc/network/if-pre-up.d/wireless-tools, add this to the bottom of the file:

/sbin/iwpriv eth1 set_vlanmode 0


I did a suspend/resume and ssh magically works.

---

### Post by csartanis on 2009-04-20
It is disappointing that this bug still hasnt been fixed.  I used the workaround posted above to make things work temporarily.

system:```

 Dell Inspiron Mini 9, purchased March 2009
 up-to-date Ubuntu linux
 OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
```

lspci:```

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Broadcom Corporation Unknown device 04b5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0

```

symptoms:```

 hang after password entry and successful authentication to ssh server

 ssh via wireless AP over internet DOESNT WORK

 ssh via lan WORKS
 ssh via wired connection over internet WORKS
 putty via wireless AP over internet WORKS
 ssh via wireless AP over internet with ndiswrapper WORKS
```

temp fix:```

 sudo /sbin/iwpriv eth1 set_vlanmode 0
```

cause:```

 bug in the wl driver?
 misconfiguration in ubuntu wlan init scripts?
```

---

### Post by uncannybuzzard on 2009-05-09
i just kinda ignored this for awhile and then built the newest version of the wl driver from source and installed it a month or so ago. seems to be fine now. also added 20% signal strength over ndiswrapper.

---

### Post by z987k on 2009-12-29
I think I'm having the same problem... not sure though.  For a while I thought it was the isp but now I'm fairly sure it's not.

Tried updating ssh to the latest(5.3p1)client to 5.1p1(server), disabled ipv6, try on multiple isps, wireless, wired, router/no router.  Ubuntu 8.04 + icewm.  Netgear WPN511 wireless card to a netgear rangemax router.

Almost anything that prints something back freezes ssh on the client side.  TCPdump shows the command going out but never gets anything back.
sudo /sbin/iwpriv ath0 set_vlanmode 0 returns Invalid command.

---

### Post by charding on 2010-10-04
I have a very similar setup:

- two machines (one server, one client) are both wireless
- Both have broadcom chips (4318 on server (b43 driver) and 4312 on client (wl driver))
- **Before** having problems I used a linksys wrt54g and everything worked perfectly. Now I'm living at another place and they have a different router ([http://www.tp-link.com/products/productDetails.asp?class=&content=spe&pmodel=TL-WR1043ND](http://www.tp-link.com/products/productDetails.asp?class=&content=spe&pmodel=TL-WR1043ND)), which is where I'm having trouble.

Things I've done:
- I've tried changing the mtu to 1492 and 576 on both machines and that doesn't help. 
- I've set ```
/sbin/iwpriv eth1 set_vlanmode 0
``` and that doesn't help
- Turned off both firewalls on both machines

My only answer to this is the router/AP I'm connected to. I can't get access to the router either.

---

### Post by tunerX on 2010-10-23
This just started happening to me after I did the last set of updates.

Everything was working fine and now I do not get any response from ssh client after authentication. PuTTY works fine and ssh client on mac works fine too.

It will work for a bit then become unresponsive. I close the terminal and open another and then it does not work for a while after than. It used to work just fine.

---

