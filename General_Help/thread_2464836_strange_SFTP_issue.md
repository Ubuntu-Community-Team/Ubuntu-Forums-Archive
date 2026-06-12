---
title: "strange SFTP issue"
date: 2021-07-13
forum: General Help
---

### Post by sun142 on 2021-07-13
Ubuntu 18.04.4 LTS

**earlier I used to login on sftp server flawlessly , but after 2 months I tried login and getting below error**:

 Trying private key: /home/twin/.ssh/id_rsa_ms
debug3: sign_and_send_pubkey: RSA SHA256:hNE3A+j/qbmsQFAP59oUR/YXeKinl5juxoV8ywFET30
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 52
debug1: Authentication succeeded (publickey).

then...

debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 32000 rmax 35000
debug2: channel 0: rcvd adjust 1248009
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: subsystem request accepted on channel 0
debug3: receive packet: type 96
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug3: receive packet: type 97
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug3: send packet: type 97
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r43 i3/0 o3/0 fd -1/-1 cc -1)


debug3: send packet: type 1
debug1: fd 0 clearing O_NONBLOCK
debug3: fd 1 is not O_NONBLOCK
Connection to xyz.com closed by remote host.
Transferred: sent 2400, received 1312 bytes, in 0.4 seconds
Bytes per second: sent 5851.2, received 3198.6
debug1: Exit status -1

I tried debugging using various sources but no luck.. **issue is only this server** and **I could login from other servers(centos) fine as of now** .

---

### Post by TheFu on 2021-07-13
[https://bbs.archlinux.org/viewtopic.php?id=234233](https://bbs.archlinux.org/viewtopic.php?id=234233) has some things to try.  Looks like one person's issue was using some funky terminal.
If it was me and I'd touched any sshd_config settings, then I'd purge the ssh package and reinstall fresh, not touching the sshd_config and test again.  
If that works, then the problem was in the system-wide settings.  
If it doesn't, then the issue is with my keys. Create a new userid, create new keys - I'd use 
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```and try again. RSA keys are so, so, 1990s.

---

### Post by sun142 on 2021-07-14
No didn't help, even I created another aws ubuntu instance and copied both pri/pub keys from a client server(centos) that access sftp ( fine) still same issue even on new ubuntu server

---

### Post by TheFu on 2021-07-14
AWS is **not** standard Ubuntu.  Look up what the How-Tos for that environment say about ssh access. I can't help.  Also, can't help without seeing the actual commands, the actual output and the actual config file.

BTW, NEVER put the private key on any remote system.  That breaks the entire purpose of "private".

---

### Post by sun142 on 2021-07-15
> **sun142 said:**
> Ubuntu 18.04.4 LTS

**earlier I used to login on sftp server flawlessly , but after 2 months I tried login and getting below error**:

 Trying private key: /home/twin/.ssh/id_rsa_ms
debug3: sign_and_send_pubkey: RSA SHA256:hNE3A+j/qbmsQFAP59oUR/YXeKinl5juxoV8ywFET30
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 52
debug1: Authentication succeeded (publickey).

then...

debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 32000 rmax 35000
debug2: channel 0: rcvd adjust 1248009
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: subsystem request accepted on channel 0
debug3: receive packet: type 96
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug3: receive packet: type 97
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug3: send packet: type 97
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r43 i3/0 o3/0 fd -1/-1 cc -1)


debug3: send packet: type 1
debug1: fd 0 clearing O_NONBLOCK
debug3: fd 1 is not O_NONBLOCK
Connection to xyz.com closed by remote host.
Transferred: sent 2400, received 1312 bytes, in 0.4 seconds
Bytes per second: sent 5851.2, received 3198.6
debug1: Exit status -1

I tried debugging using various sources but no luck.. **issue is only this server** and **I could login from other servers(centos) fine as of now** .

reveled its ip whitelisting issue, server allows only selected subnet to connect .

---

### Post by TheFu on 2021-07-15
If this is solved, please use the *thread tools* button and mark it that way.
If not, please ask a question.

---

