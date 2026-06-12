---
title: "SSH Closes immediately after Login"
date: 2015-08-10
forum: General Help
---

### Post by Andrew_McCann on 2015-08-10
I use SSH to connect to the server which has worked well for  months...then suddenly now when I login the Putty session (and other  forms of SHH) simply closes and that's it!!! Any help would be  gratefully received. Many thanks!

---

### Post by TheFu on 2015-08-10
ssh -vvvv userid@IP

What does that say?

---

### Post by Andrew_McCann on 2015-08-14
I'm sorry but I don't understand what you want me to do? I am using Putty and I take that 'ssh -vvvv userid@IP' (where userid is my username and @IP is then IPAddress of the server right?) when I run this from my other server I get this:
```

andrew@Rhino-10:~$ ssh -vvvv andrew@192.168.0.11
OpenSSH_5.9p1 Debian-5ubuntu1.4, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.11 [192.168.0.11] port 22.
debug1: Connection established.
debug1: SELinux support disabled
debug1: identity file /home/andrew/.ssh/id_rsa type -1
debug1: identity file /home/andrew/.ssh/id_rsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_dsa type -1
debug1: identity file /home/andrew/.ssh/id_dsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debia                                                                                                                                                             n-5ubuntu1.3
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp                                                                                                                                                             521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diff                                                                                                                                                             ie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com[/email],ecdsa-sha2-n                                                                                                                                                             [email]istp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ssh-rsa-ce                                                                                                                                                             [email]rt-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh                                                                                                                                                             [email]-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nis                                                                                                                                                             tp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,                                                                                                                                                             hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@op                                                                                                                                                             enssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,                                                                                                                                                             hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@op                                                                                                                                                             enssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp                                                                                                                                                             521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diff                                                                                                                                                             ie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,                                                                                                                                                             hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@op                                                                                                                                                             enssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,                                                                                                                                                             hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@op                                                                                                                                                             enssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: Server host key: ECDSA 15:ca:c4:a2:e7:4c:c5:1b:0b:46:8c:e6:25:55:bf:06
The authenticity of host '192.168.0.11 (192.168.0.11)' can't be established.
ECDSA key fingerprint is 15:ca:c4:a2:e7:4c:c5:1b:0b:46:8c:e6:25:55:bf:06.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.11' (ECDSA) to the list of known hosts.
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
debug2: key: /home/andrew/.ssh/id_rsa ((nil))
debug2: key: /home/andrew/.ssh/id_dsa ((nil))
debug2: key: /home/andrew/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/andrew/.ssh/id_rsa
debug3: no such identity: /home/andrew/.ssh/id_rsa
debug1: Trying private key: /home/andrew/.ssh/id_dsa
debug3: no such identity: /home/andrew/.ssh/id_dsa
debug1: Trying private key: /home/andrew/.ssh/id_ecdsa
debug3: no such identity: /home/andrew/.ssh/id_ecdsa
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
debug3: packet_send2: adding 48 (len 62 padlen 18 extra_pad 64)
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.11 [192.168.0.11] port 22.
debug1: Connection established.
debug1: SELinux support disabled
debug1: identity file /home/andrew/.ssh/id_rsa type -1
debug1: identity file /home/andrew/.ssh/id_rsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_dsa type -1
debug1: identity file /home/andrew/.ssh/id_dsa-cert type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa type -1
debug1: identity file /home/andrew/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debia                                                                                                                                                             n-5ubuntu1.3
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp                                                                                                                                                             521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diff                                                                                                                                                             ie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com[/email],ecdsa-sha2-n                                                                                                                                                             [email]istp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ssh-rsa-ce                                                                                                                                                             [email]rt-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh                                                                                                                                                             [email]-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nis                                                                                                                                                             tp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour12                                                                                                                                                             8,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rij                                                                                                                                                             [email]ndael-cbc@lysator.liu.se[/email]
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,                                                                                                                                                             hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@op                                                                                                                                         debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
Password:
debug3: packet_send2: adding 48 (len 68 padlen 12 extra_pad 64)
 you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.11' (ECDSA) to the list of known hosts.
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
debug2: key: /home/andrew/.ssh/id_rsa ((nil))
debug2: key: /home/andrew/.ssh/id_dsa ((nil))
debug2: key: /home/andrew/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/andrew/.ssh/id_rsa
debug3: no such identity: /home/andrew/.ssh/id_rsa
debug1: Trying private key: /home/andrew/.ssh/id_dsa
debug3: no such identity: /home/andrew/.ssh/id_dsa
debug1: Trying private key: /home/andrew/.ssh/id_ecdsa
debug3: no such identity: /home/andrew/.ssh/id_ecdsa
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
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1

```

---

### Post by TheFu on 2015-08-14
If both servers can ssh into each other, the issue is with your connection from putty.
Does putty have a way to increase logging or debugging to see the issue?

---

### Post by PaulW2U on 2015-08-14
Hi Andrew_McCann, welcome to the Ubuntu Forums.

Please use code tags for terminal output as they will improve the readability of your posts.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by TheFu on 2015-08-15
[http://ubuntuforums.org/showthread.php?t=2277189&p=13338931#post13338931](http://ubuntuforums.org/showthread.php?t=2277189&p=13338931#post13338931) gas some other ideas.  Definitely check the pemissions on the remote ~/.ssh/ directory and files inside.  They need to be 600 for most of the files and 700 for the directory.

---

### Post by Andrew_McCann on 2015-08-17
> **TheFu said:**
> If both servers can ssh into each other, the issue is with your connection from putty.
Does putty have a way to increase logging or debugging to see the issue?

At the bottom of the log you will see "Connection to 192.168.0.11 closed." so therefore no the servers can NOT ssh each other.

---

### Post by TheFu on 2015-08-17
Have you checked the ~/.ssh/ permissions and permissions of the files inside that directory?  ssh has built-in protection against improperly set permissions on the remote system.

Guess I need to ask 1 question at a time.

---

### Post by Andrew_McCann on 2015-08-17
I haven't checked that no and thanks for the suggestion. The problem I now have is that I followed the instructions you send in the link above and used the 'sudo apt-get purge open-ssh-server' which ripped ssh out of my server. When I tried to 'sudo apt-get install open-ssh-server' it just gave me a load of 404 errors Not found [I.P: 91.189.91.14 80] and failed to fetch from security ubuntu pool etc.... 'Unable to fetch some archives....' so I can now not run ssh at all! I've tried many ways install ssh and nothing works now :-(

---

### Post by TheFu on 2015-08-17
The package name is "openssh-server" - I need to write an ssh troubleshooting guide.  Give me an hour or so.

Ok ... [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)  hope that helps. Any corrections?

---

### Post by Andrew_McCann on 2015-08-18
Hello TheFu and thank you for this, however I made a typo...I did indeed call the package 'openssh-server' and not the 'open-ssh-server', so I still get the errors as detailed above. Can you try this and see if you get the same thing?
I'll have another go in the mean time using your very helpful trouble shooting guide.

---

### Post by TheFu on 2015-08-18
Please run the exact **update** command followed by the **install** command below and post the output displayed (copy/paste!!!!) in total if under 1 pg in length. If over 1 pg in length, cut the uninteresting parts, but leave the cmd, start, errors, end and a few lines before and after the errors. Please make it clear where you remove stuff ... <snip> is commonly used.
Also, please use "code" tags so things line up as expected. You've been doing that and it is appreciated.

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install openssh-server
```

Whenever someone posts their entire dmesg here, I think they've forgotten we are volunteers, not paid.  We are used to seeing the output from these commands, but I don't want to look through all that crap to find 3 lines either. **grep** is your friend.  For example, with the update above ... all the working http hits - I don't need to see.

---

### Post by Andrew_McCann on 2015-08-19
WOW! Thanks TheFu and the commands above worked like a charm! Perfect and thank you so much!!!

---

### Post by Andrew_McCann on 2015-08-19
Hello again TheFu and you've been such a help with this issue, I wondered if you could help with my only other problem detailed here:
[http://ubuntuforums.org/showthread.php?t=2290175](http://ubuntuforums.org/showthread.php?t=2290175)

I'd really appreciate it if you can :-)

---

### Post by TheFu on 2015-08-19
> **Andrew_McCann said:**
> Hello again TheFu and you've been such a help with this issue, I wondered if you could help with my only other problem detailed here:
[http://ubuntuforums.org/showthread.php?t=2290175](http://ubuntuforums.org/showthread.php?t=2290175)

I'd really appreciate it if you can :-)

Sorry - can't help with that. Won't touch network manager, most GUIs or non-wired networking stuff. After doing 1000+ wifi deployments, I avoid all wireless. Over the years I've learned that if wifi doesn't work out of the box on Linux, it is easier to just buy a supported device. Won't touch cell-data stuff.

There are a few articles on my blog about linux, networking, troubleshooting, and hardware which might be helpful. Plus, I think you should read this one: [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) soon.  The issues from above appear to be from lack of proper system maintenance.

---

