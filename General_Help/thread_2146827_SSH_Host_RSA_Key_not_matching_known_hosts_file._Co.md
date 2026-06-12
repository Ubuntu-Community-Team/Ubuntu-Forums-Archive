---
title: "SSH Host RSA Key not matching known_hosts file. Connection works."
date: 2013-05-19
forum: General Help
---

### Post by viejo79 on 2013-05-19
I've done a completely fresh ssh setup with a host on rasberrypi and client on ubuntu. I've removed the known_hosts file on ubuntu and connected successfully to the host. Where I am confused is, when I cat ssh_host_rsa_key.pub on the host, I do not get the same key listed as when I look at the known_hosts file on the client. The ssh_host_rsa_key returns what I expect:  ssh-rsa .... username@host. The known_hosts file does not match this same format. 
Everything is working, I'm just confused as to why they do not match. :confused: I'm a noob and am diving into this all, I just can't figure out the mismatch and would like to know my error. Thanks for any help.

---

### Post by Lars Noodén on 2013-05-20
The latest versions of Ubuntu have the [ssh](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh.1.html) client set to record a hash of the remote host's address.  So if you just see a long jumble of letters and numbers, that is what is happening.  In that case you are just seeing a hash of a fingerprint instead of a fingerprint.  

If you want to turn off that function, you can change [~/.ssh/config](http://manpages.ubuntu.com/manpages/raring/en/man5/ssh_config.5.html) to stop it.

```

HashKnownHosts no

```

Without the hashing, if someone were to manage to get into your account or otherwise lift the known_hosts file from your machine, they would have a list of other machines to try getting into.

---

### Post by viejo79 on 2013-05-20
Excellent, thank you. :D
Is there a thank you button like on xda?

---

