---
title: "scp: better to passworkd or ssh keys?"
date: 2021-08-14
forum: General Help
---

### Post by Old Jimma on 2021-08-14
Hello Community:

I'm setting up a secure server to back up (in my case, copy, really) files on another computer

From the server the scp command can be used to access and copy files on the host.

However, to access and copy those files to the client, scp needs either
[LIST]
[*]the pasword of the host client (see this: > [https://unix.stackexchange.com/questions/366733/using-scp-with-passwords#366735](https://unix.stackexchange.com/questions/366733/using-scp-with-passwords#366735), or
[*]ssh keys (see this: > [https://linuxize.com/post/how-to-setup-passwordless-ssh-login/](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/)) to be shared.
[*]
[/LIST]

My question to the forum is: which is best???

Not knowing much about ssh keys, I'm disinclined to use them since I don't fully understand them, they look complicated, and I wonder if there will be unforseen problems down the road as a result of using ssh keys.

Would appreciate your advice to learn whether using a ssh yields further benefits beyond including a password (while using sshpass that would precede scp in the same command line) that I should consider.

Thank you!
Old Jimma From the Old Country

---

### Post by scorp123 on 2021-08-14
If you want things to run automatically at some point (e.g. automatic backups) then you need SSH keys.

Only using passwords has the downside that this method isn't as safe. Meaning: Anyone who knows the account and the password can get access to those files. This can make sense in certain scenarios but might be undesirable in others. You can compare this to knowing the PIN code to a door. Anyone who knows the PIN can get in and do whatever they want.

Using SSH keys means that you need to have those keys if you want access to those files. Either you have them or you don't. If you don't: No access for you. Ever. You can compare this to having an ID to enter a secured building, e.g. a bank. Either you have that ID and it matches you ... or you don't and can't get in. Ever. No matter what or who else you might know.

SSH key security can be further tightened by applying a passphrase to them. Meaning you now also need to be in posession of the keys AND know the password that unlocks them. You can compare that to needing an ID and a door password to get past the guards guarding a door at a secured building. Either you have a matching ID AND you know the password to get past the guards ... or you don't and can't get in. Ever.

It's usually "best practices" to go for a SSH key because SSH usernames and passwords can be too easy to guess for intruders. And if they can guess those things they're in.

---

### Post by HermanAB on 2021-08-14
A key is a very long computer generated password. So if you are willing to manually type in a very long password, then there is no difference.

---

### Post by Old Jimma on 2021-08-14
Thanks to Scorp123 and hermanAB for their replies!

---

### Post by HermanAB on 2021-08-14
Note that a 2048 bit key is equivalent to about 50 English words.  So to equal a key system with passwords, you would need to memorize parts of War and Peace or something…

---

### Post by TheFu on 2021-08-14
Keys - 100% better.  I only use a password 2 times.
[LIST]
[*]During the install
[*]When pushing keys from my client machine(s) via ssh-copy-id
[/LIST]
After that, never again.

A 2048-key is like a password of 256 characters.
If you use elliptical key generation, add a 0 to that complexity.

ssh-keys are the only thing I know that is both more secure AND more convenient.  That never happens ... except with ssh.  Plus, those keys are automatically used for every other ssh-based tool from scp, sftp, ssh, sshfs, rsync, rdiff-backup, x2go, vim, and 50+ other things.

Using ssh-keys is about as "no brainer" a decision as I know in this world.  Add in using the ~/.ssh/config file for the 2nd no-brainer choice.  Again, all ssh-based tools honor that config file too.

I stopped using RSA-based keys a few years ago for the added security of using ed25519 keys. There's only 2 differences during setup and after that, no difference.

Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

---

