---
title: "SSH access.. how to"
date: 2006-12-06
forum: General Help
---

### Post by telovoyagarcar on 2006-12-06
I am now at a friend's home trying for the first time to access my computer at home using Putty.
I have the default Edgy installation... so
should i do anything to be able to connect to it using SSH?
because im trying now and i get a connection refused message... i was thinking that SSH comes enabled by default..
I opened the port in my firewall, so i know that is not the problem.

Thanks

---

### Post by johnnymac on 2006-12-06
You may need to install openssh - sudo apt-get install ssh should get you going.  If you have the firewall open for that port then it's matter of not having it installed.

---

### Post by Iowan on 2006-12-06
> **telovoyagarcar said:**
>  i was thinking that SSH comes enabled by default..

IIRC, the SSH *client* comes installed, but the ssh-server does not.

---

### Post by Arisna on 2006-12-06
lowan is correct that only the client comes installed by default.  Also, if you are behind a router/firewall, you will need to forward port 22 to the machine you want to access, I believe.

---

### Post by steve.horsley on 2006-12-06
The others are right - you need to install package openssh-server. 

You must also read up on the files /etc/hosts.allow and hosts.deny (or set up a firewall) so you can configure ssh to only accept connextions from IP addresses you trust - there are a lot of SSH password guessing bots out there that just connect to any SSH server thay can find and guess usernames and passwords all day long.

---

### Post by telovoyagarcar on 2006-12-07
Thank you guys..
i just installed open ssh

Do you know if there is an option like to automatically ban remote hosts that fail to provide the correct password for like 3 attempts or something like that? This way i dont have to worry about bot nets or stuff alike.

---

### Post by RAOF on 2006-12-07
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

is a good howto.  If you're concerned about security, check out the "Public key authentication" section - disable password logins, and the bots can try username/password combinations as long as they want, they won't gain access.

---

