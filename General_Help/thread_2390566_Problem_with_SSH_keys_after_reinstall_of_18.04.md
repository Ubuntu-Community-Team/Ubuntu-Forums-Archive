---
title: "Problem with SSH keys after reinstall of 18.04"
date: 2018-04-30
forum: General Help
---

### Post by jochristian on 2018-04-30
Hi,

I got an issue after doing an full reinstall of Ubuntu 18.04. My ssh keys are not working anymore..

I copied all of the keys to /home/user/.ssh/ from my old Ubuntu installation. Same name and permissions on the keys. 600 for private key and 644 for public.

I then did ssh-add.

But when trying to login to hosts that worked on my old install I get this message.

sign_and_send_pubkey: signing failed: agent refused operation.

Also in /var/log/auth I see this error message:

Apr 30 11:28:44 jochr-ubuntu gnome-keyring-daemon[5834]: Apr 30 11:36:55 jochr-ubuntu gnome-keyring-daemon[5834]: the /usr/bin/ssh-add command failed: Child process exited with code 1

Any Idea on what could be wrong? I have used an couple of hours now searching Google. But so far now luck.

/Jo Christian

---

### Post by TheFu on 2018-04-30
18.04 release notes say that keys less than 1024-bits aren't supported anymore.
If that isn't your situation, I'd increase the verbosity and check the log files for hints.  ssh is pretty clear in the logs.

---

### Post by jochristian on 2018-04-30
> **TheFu said:**
> 18.04 release notes say that keys less than 1024-bits aren't supported anymore.
If that isn't your situation, I'd increase the verbosity and check the log files for hints.  ssh is pretty clear in the logs.

Hi, thanks for the reply.
They key is 4096-bits. So this should not be the problem.
To me it looks like the ssh-agent process crash? exit 1.

Any suggestions on how to troubleshoot further? No problems using the exact same key in Ubuntu 17.10. Tried it now on another laptop (copied it the same way).

---

### Post by TheFu on 2018-04-30
Did you turn up the verbosity and check the logs?
I've posted ssh troubleshooting links in these forums before.

---

### Post by jochristian on 2018-05-01
> **TheFu said:**
> Did you turn up the verbosity and check the logs?
I've posted ssh troubleshooting links in these forums before.

Yep, looking at the verbose log. ssh -vvv this is what I see.

[I]debug1: Offering public key: RSA SHA256:s/fahypgKy+xit1tieVTM5DErLDCKWkWnppTcEiXVWE /home/jochristian/.ssh/id_rsa
debug3: send_pubkey_test
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 60
debug1: Server accepts key: pkalg rsa-sha2-512 blen 535
debug2: input_userauth_pk_ok: fp SHA256:s/fahypgKy+xit1tieVTM5DErLDCKWkWnppTcEiXVWE
debug3: sign_and_send_pubkey: RSA SHA256:s/fahypgKy+xit1tieVTM5DErLDCKWkWnppTcEiXVWE
[B]sign_and_send_pubkey: signing failed: agent refused operation
[/B]debug1: Trying private key: /home/jochristian/.ssh/id_dsa
debug3: no such identity: /home/jochristian/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/jochristian/.ssh/id_ecdsa
debug3: no such identity: /home/jochristian/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/jochristian/.ssh/id_ed25519
debug3: no such identity: /home/jochristian/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password[/I]

Still seems to be some issue with the agent?

---

### Post by TheFu on 2018-05-01
Did you find the link, follow it and follow the steps?  ~/.ssh/ needs to be 700, BTW.
What do the server-side logs show?

I took the error message you posted (bold), put it into google and found this link: [https://askubuntu.com/questions/762541/ubuntu-16-04-ssh-sign-and-send-pubkey-signing-failed-agent-refused-operation](https://askubuntu.com/questions/762541/ubuntu-16-04-ssh-sign-and-send-pubkey-signing-failed-agent-refused-operation)
Any of that help?

Have you tried making new keys on the new box and pushing those to which ever remote system you want?  BTW, I'd choose an elliptical key these days for better security.

---

### Post by jochristian on 2018-05-03
Hi,

I ended up creating new elliptical keys. Everything working fine now. No idea why the RSA key failed to work.
Just need to update around 50 servers with the new key now :-)

Thanks for your help

/Jo Christian

---

### Post by mat26393 on 2018-05-04
I had the same problem and found that the permissions for the key file were too open (0644).
The following command solved it: ```
chmod 600 .ssh/id_rsa
```

---

### Post by TheFu on 2018-05-04
If you aren't pushing keys to remote systems using **ssh-copy-id**, then you are doing it the hard way.
It handles the permissions for you.  Since I switched to that tool around 2006, I've never had ssh permissions issues.  There are very specific rules and a few other things to check ... my ssh troubleshoot article: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by t-no on 2018-05-16
> **mat26393 said:**
> I had the same problem and found that the permissions for the key file were too open (0644).
The following command solved it: ```
chmod 600 .ssh/id_rsa
```
Thanks! This solved it for me.

---

### Post by TheFu on 2018-05-16
Just use ssh-copy-id in the future. There are lots of mandatory permissions about ~/.ssh/ and all the files inside.  If you create the keys using ssh-keygen and push the public files to the other side as suggested, then there isn't any need to touch permissions. They are handled correctly by the tools.

And while we are here, please learn to use the ~/.ssh/config file. It will make your ssh connections much easier. You'll never need to remember IPs or port for any tool that uses ssh underneath again.  They all honor the settings in the config file.

---

### Post by drfernandes on 2019-01-13
[COLOR=#000000][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **mat26393** [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13763137#post13763137")[/COLOR]
[COLOR=#000000][I]I had the same problem and found that the permissions for the key file were too open (0644).
The following command solved it:Code:
chmod 600 .ssh/id_rsa
[/I][/COLOR]
It worked for me too on Ubuntu 18.04, after  upgrading from 16.04. Thanks

---

