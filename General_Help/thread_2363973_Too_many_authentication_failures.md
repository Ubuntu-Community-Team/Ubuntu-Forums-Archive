---
title: "Too many authentication failures"
date: 2017-06-17
forum: General Help
---

### Post by ELMIT on 2017-06-17
Years on my Todo list was: replace ssh login with keys!

Finally I did. I selected one of my remote peers and used on my desktop:
```
ssh-keygen -t rsa
    saved file to /home/ronald/.ssh/id_rsa_remote_host
ssh-copy-id [email]ronald@remote.host[/email]

```
Perfect! Worked!

Now, I tried to create all other hosts I need to connect to. 15 keys created with ssh-keygen -t rsa  

Next step is to upload:
```
ssh-copy-id [email]ronald@remote2.host[/email]
```
Gives me erros:
Received disconnect from 128.199.206.96 port 22:2: Too many authentication failures

Reading more, I learned that you should only "upload" max 5 keys. So my copy-id should be:
```
ssh-copy-id -i ~/.ssh/id_rsa_remote2_host [email]ronald@remote2.host[/email]
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/ronald/.ssh/id_rsa_remote2_host.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
Received disconnect from 2400:xxxx:0:d0::xxxx:7001 port 22:2: Too many authentication failures
Connection to mastodon.elmit.com closed by remote host.
```

I have still another ssh window open. I tried to go into my home .ssh directory
```
cd ~/.ssh
-bash: cd: .ssh: No such file or directory
```
????

1. Why do I not have a .ssh directory? 
2. since I cannot connect now at all (Too many authentication failures) - except with the existing open window, how can I reset this?

FYI, it is a droplet at Digital Ocean:
```
uname -a
Linux remote 4.4.0-79-generic #100-Ubuntu SMP Wed May 17 19:58:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

lsb_release 
No LSB modules are available.
```

---

### Post by ELMIT on 2017-06-17
thank you lisati. I am always confused, when and  how to format.

---

### Post by Habitual on 2017-06-17
can I ask why 15 keys for 15 hosts?

---

### Post by ELMIT on 2017-06-17
I do not see a reason, why not 15, 50 or 500 keys.

However, my question how to solve the error "Too many authentication failures"

---

### Post by ELMIT on 2017-06-18
I got one step further:
with -o PubkeyAuthentication=no I can upload the key and it is in ~/.ssh/authorized_keys

```
ssh-copy-id -o PubkeyAuthentication=no  -i ~/.ssh/id_rsa_remote2_host ronald@remote2.host
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/ronald/.ssh/id_rsa_remote2_host.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
ronald@remote2_host's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh -o 'PubkeyAuthentication=no' 'ronald@remote2_host'"
and check to make sure that only the key(s) you wanted were added.

```

However, my wish was to login with ssh and the key without password. Now each ssh needs the password too.
How can I fix that?

---

### Post by ELMIT on 2017-06-24
Anybody?

---

### Post by efflandt on 2017-06-24
After you use -o PubkeyAuthentication=no to upload the key, why are you using that again with ssh to tell it "not to use keys", that is why it is requesting your password.

So ssh does not just blindly try all keys and run into "Too many authentication failures", I imagine you should configure **~/.ssh/config** on your client with individual **Host** sections specifying the **IdentityFile** for that specific host. You can include a wildcard **Host *** section for default keywords used if those keywords are not otherwise specified in a specific Host section. The word following Host can be an abbreviation or something easy to remember for ssh command line. The actual FQDN or IP would be specified with **HostName**. see "man ssh_config". Generally ~/.ssh and anything in it should not have read or write permission for anyone other than you (chmod -R go-rwx ~/.ssh).

There is no need for so many keys. If you use the same key for multiple  servers and only have your public key on the server, nobody can do  anything with that. And even if someone gets a private key, unless that  was generated with no password or pass phrase, nobody could do anything  with that without knowing the password or pass phrase.

---

