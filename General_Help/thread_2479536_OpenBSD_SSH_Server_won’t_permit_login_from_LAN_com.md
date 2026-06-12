---
title: "OpenBSD SSH Server won’t permit login from LAN computer nor Localhost"
date: 2022-09-28
forum: General Help
---

### Post by xanizen on 2022-09-28
I tried to login in from Windows based SSH application MobaXterm, and was rejected by Ubuntu.
[https://i.imgur.com/iizSkHW.png](https://i.imgur.com/iizSkHW.png)
[https://i.imgur.com/w3zRH0m.png](https://i.imgur.com/w3zRH0m.png)

The Ubuntu system is port forwarded: 
[https://i.imgur.com/YKNzfQx.png](https://i.imgur.com/YKNzfQx.png)

I then tried to test the localhost, 127.0.0.1, directly on the Ubuntu system, and was rejected as well.
[https://i.imgur.com/yu2NR7s.png](https://i.imgur.com/yu2NR7s.png)

Executing ‘ssh –v localhost’, as recommended [here]("https://ubuntuforums.org/showthread.php?t=1008018&highlight=SSH+localhost"), generated the following output:
[https://pastebin.com/F5cHrrpY](https://pastebin.com/F5cHrrpY)

This is the content of ‘/etc/ssh/sshd_config’
[https://pastebin.com/5Z46Esdf](https://pastebin.com/5Z46Esdf)

 The following were added/enabled:
  
```

PasswordAuthentication yes
KbdInteractiveAuthentication yes
AllowUsers ken@192.168.1.224

```

 Disabled/commented out:
  ```

#AuthenticationMethods publickey, keyboard-interactive

```

---

### Post by &amp;KyT$0P# on 2022-09-28
I haven't clicked all those links, but for one thing, you don't put the [FONT=Courier New]@[COLOR="#FF0000"]<ip address>[/COLOR][/FONT] in [FONT=Courier New]AllowUsers[/FONT] directive.  Try removing that and restarting sshd?

---

### Post by TheFu on 2022-09-28
$ ssh -vvvv .... 
more 'v's mean more details.  The resulting debug information will make the issue clear.

I won't be clicking on images. Relevant text would be 20 lines and text isn't much of a security risk like images are.

I don't have Windows with that ssh program.  None of my BSD or Linux systems are having ssh connection issues, so it is unlikely to be a bug. Something local to your setup, is my guess.

Put the sshd_config file back to the installation defaults and ensure the firewall on the system allows the sshd inbound port ... or disable it for testing.

---

### Post by xanizen on 2022-10-07
Thank you for the responses.
  I’ve since gone ahead and verify that port 22 is open with the terminal commands, ‘ss -ltnp' and ‘nmap localhost’, resulting in the following:
  ```

  kaign@kaign:~$ sudo nmap localhost
  Starting Nmap 7.80 ( https://nmap.org ) at 2022-10-07 16:29 EDT
  Nmap scan report for localhost (127.0.0.1)
  Host is up (0.0000050s latency).
  Not shown: 997 closed ports
  PORT     STATE SERVICE
  22/tcp   open  ssh
  631/tcp  open  ipp
  3306/tcp open  mysql
   
  Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds
 
```
   
  I attempted to check the fire wall status, sudo ufw status verbose, and got ‘Status: inactive’.
   
  I followed the advice here on stackexchange, [https://askubuntu.com/a/654448](https://askubuntu.com/a/654448), and edited 2 statements in sshd config
  ‘PermitRootLogin prohibit-password’ &#8594; ‘PermitRootLogin yes’
  AllowUsers ken@192.168.1.224 **kaign**
   
  I was able to login as localhost, with my standard password.
   
  Also when logging in to SSH from Windows on MobaXterm application, I had to do <Ubuntu username>@<Ubuntu system local ip> instead of <Windows username>@<Ubuntu system local ip>.

---

### Post by TheFu on 2022-10-07
```
# PermitRootLogin prohibit-password
PermitRootLogin yes
```
is a complete security failure. There are other options besides yes/no.  Use one of those, but really, nobody should be using remote root to log into a system.  There's an option to allow sshkey-based authentication, but that really should be limited to backups.  

DevOPs tools all understand sudo, so a random deployment account should be used, not root.  Don't use root.

While I'm looking at the nmap, the IPP is probably fine. There isn't much damage that having a print server on the LAN can cause, but if you don't actually have that need, best to set the cups to be localhost only.

mysql is frequently hacked, so, again, if you don't need it to be available for other systems on the LAN, then it should only allow localhost connections. There is a setting for that in the config file.

And as a 2nd safety thing, use both tcp-wrappers and some firewall to prevent inbound connections from everywhere except specific systems you 100% know need access.  That's called a default DENY policy and is a core best practice for all networks.

---

