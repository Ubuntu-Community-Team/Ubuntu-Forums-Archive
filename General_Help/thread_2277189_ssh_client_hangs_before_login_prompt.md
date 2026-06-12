---
title: "ssh client hangs before login prompt"
date: 2015-05-07
forum: General Help
---

### Post by xWEkxhW on 2015-05-07
Strange thing seems to be happening since I upgraded to 15.04. When I try to connect to another linux box using the ssh client, nothing happens, it just sits there blank. No login prompt. No error messages. It just sits there totally frozen.

I can ssh to localhost but nothing else.

The connection is made to the remote host, I can see in the iptables log it gets accepted on the destination host but there is no login prompt.

I can ssh into the other system from my Windows PC using PuTTY so it doesn't appear to be a problem with the destination server as such.

Any ideas?

Thanks :)

---

### Post by TheFu on 2015-05-07
Turn up the debug level on your ssh command
[B]
ssh -vvv userid@ipaddress[/B]

The client may have noticed the ssh identity for the other machine has changed, so it thinks a man-in-the-middle attack is underway. You'll need to manually clean that up.

---

### Post by xWEkxhW on 2015-05-07
Thanks

I've noticed it pauses for a minute or two on the "debug1: Connecting".... line
And then it connects normally.

Rather strange but I'm sure there's a reason for the delay, just a case of figuring out what :-)

---

### Post by TheFu on 2015-05-07
Either name resolution or negotiating a cypher.  Do both machines know how to find each other on the network either through DNS or /etc/hosts?

---

### Post by xWEkxhW on 2015-05-07
Name resolution is working as it knows the IP address already. I've probably done something silly - I'll investigate and post back if I discover anything :-)

---

### Post by TheFu on 2015-05-07
[B]sudo apt-get purge openssh-server
sudo apt-get install openssh-server
[/B]

The first command will clean up everything on the server-side.
If you modified the /etc/ssh/ssh_config on the client or ~/.ssh/config in your HOME, might want to clean that up too.
The defaults should allow a connection inside your LAN easily.

Oh - and if you've screwed with the permissions on the ~/.ssh/ directory either on the client or server, you'll never be able to connect.
700 - .ssh/
All files inside that directory can be 600 and it will work. A few can be more permissive, but most should not.

---

### Post by SeijiSensei on 2015-05-07
What's important is not "forward" resolution from a hostname to an IP address, but "reverse" resolution determining the hostname from the IP.  If both forward and reverse resolution are not correctly configured, SSH will hang while it times out on the name resolution step.  If reverse resolution isn't correctly configured, add entries in the server's /etc/hosts file for each of the clients it serves.

---

### Post by SeijiSensei on 2015-05-08
I've encountered another reason for SSH login hangs, and it's probably the same one you're experiencing.

On my 14.04 machine, the file /etc/ssh/ssh_config has the directive
```
GSSAPIAuthentication yes
```
When that is enabled, the SSH client [tries to use Kerberos]("https://support.ssh.com/manuals/server-admin/62/userauth-gssapi.html") authentication which leads to delays and these errors displayed by "ssh -v":
```

debug1: Unspecified GSS failure.  Minor code may provide more information
No Kerberos credentials available

```

To fix the problem, edit ssh_config and set GSSAPIAuthentication to "no".

---

### Post by TheFu on 2015-05-08
Yeah - SeijiSensei  - that could be it too.  I vaguely recall that as an issue the last year for some people.  Checked a few of my systems:
```
Host *
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```
is my /etc/ssh/ssh_config on this box.  Connections feel nearly instantaneous.  All my systems know about each other via /etc/hosts. No kerberos on these systems.

Ran a quick script: ```

$ ansible -i hosts -a "egrep GSSAPIAuthentication /etc/ssh/ssh_config" all
```

Found that all the hosts here have the same setting - yes.  

Also check my personal ~/.ssh/config for the same setting. ```

$ ansible -i hosts -a "egrep GSSAPIAuthentication ~/.ssh/config" cur
```
Nada.

Just providing another data point. The GSS stuff HAS been an issue for some systems, but just not mine.

---

### Post by x-mair-x on 2015-08-15
Hello all,
I have also from my ubuntu 14.04 computers (workstation,notebook) delay problems on login and hanging of communication issue (up to a minute) to a old debian 6 server and a ubuntu 14.04 server w. ubuntu server VMs !
I try the [COLOR=#000000]GSSAPIAuthentication to "no"  hint for ssh client and will give feedback if this helps 
bye[/COLOR]

---

