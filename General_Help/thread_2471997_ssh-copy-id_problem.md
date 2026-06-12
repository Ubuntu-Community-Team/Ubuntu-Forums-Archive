---
title: "ssh-copy-id problem"
date: 2022-02-15
forum: General Help
---

### Post by Old Jimma on 2022-02-15
Hello Forums:

I use a Raspberry Pi to back up files on each of my ubuntu compters using rsync.

However, I'm having trouble with one of my machines: I can't get the ssh-copy-id command to install the .ssh folder from the pi server to the ubuntu client.

Here is the command and the messages I get on the client:

> 
ssh-copy-id username1@192.168.1.124
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/pi/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 192.168.1.124 port 22: Connection timed out




This worked on my other ubuntu clients.

I am able to ping 192.168.1.124 from the pi server, and I'm able to ping the pi server from the ubuntu client.

I will be grateful for your suggestions.

Thank you,
Old Jimma

---

### Post by ActionParsnip on 2022-02-15
Can you SSH to the server side normally and fill out your password.

You can always use scp to copy the file over
```

scp $HOME/.ssh/id_rsa.pub username@192.168.1.124:/tmp

```

Then SSH over to the server and run
```

cat /tmp/id_rsa.pub | tee -a $HOME/.ssh/authorized_keys > /dev/null
rm /tmp/id_rsa.pub

```

Manual, but will work.

---

### Post by SeijiSensei on 2022-02-15
Often I'll just copy the public key, open an editor on the remote machine, and paste the key into $USER/.ssh/authorized_keys.

---

### Post by Old Jimma on 2022-02-15
I am not able to access the other machine (client) from the raspberry pi (host) using

> 
ssh othermaching$othermachine.IP.address


Also, after creating the /tmp director on the client,
> 
scp $HOME/.ssh/id_rsa.pub  othermaching$othermachine.IP.address:/tmp

does not work.

---

### Post by kevdog on 2022-02-16
If you're not planning on doing any automated scripting which would be necessary if you needed to run this type of setup for a lot of machines -- can you not just as @SeijiSensi suggested just ssh into target machine, open a text editor to edit ~/.ssh/authorized_keys and just copy the public key from the source on one terminal window, and paste the public key into ~/.ssh/authorized_keys on the server within a second terminal window.  Sometimes this is much easier and foolproof.    Public service announcement but try to use ed2559 ssh keys -- thought to be more secure than rsa keys (which I'm aware is the gold standard -- well at least 2048 and if not 4096 bytes).

---

