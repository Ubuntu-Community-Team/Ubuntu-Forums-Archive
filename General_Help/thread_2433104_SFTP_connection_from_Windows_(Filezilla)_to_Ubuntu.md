---
title: "SFTP connection from Windows (Filezilla) to Ubuntu."
date: 2019-12-13
forum: General Help
---

### Post by mangonels on 2019-12-13
Hello.
I've been attempting to establish an SFTP connection from Windows using Filezilla to Ubuntu 19.04.
What I've done until now:

Created the local SSH keys (for windows, with puttygen). I'm currently using these in order to make my connection with PuTTy even safer, works fine.

I'm currently attempting at also using them on Filezilla for SFTP. I've followed both these tutorials:
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04)
[https://www.digitalocean.com/community/tutorials/how-to-use-filezilla-to-transfer-and-manage-files-securely-on-your-vps](https://www.digitalocean.com/community/tutorials/how-to-use-filezilla-to-transfer-and-manage-files-securely-on-your-vps)

After having followed both sets of instructions, I still cannot get the SFTP connection to work.

The first tutorial says all I have to do in order to achieve a connection is to configure that account... The prerequisites (which I already met) are also quite scarce, so I'm assuming that was enough.

Maybe I need to also install a regular FTP system such as vsftpd in order to get the SFTP to work? Or need to actually activate something on Ubuntu?

In any case for now, when attemtping to access Ubuntu using sftp with Filezilla and loading the private key, I get rejected by the server on connecting. But I added the public key as an allowed connection, for the account I created (apparently it needs to be added per account in each ~/.ssh/authorized_keys file, at least for regular ssh connections).

The key of this issue is that I don't even know what and if I did anything wrong, so I'm asking to see if I'm maybe missing something important, or anyone has any way of troubleshooting this.

---

### Post by TheFu on 2019-12-13
You do not need vsftpd. Plain FTP has absolutely ZERO, nothing, nada, to do with sftp.

If ssh works from the client to the server, then sftp should work too. If it doesn't, it is definitely a client-side issue.  I don't use Filezilla or MSFT stuff enough to be helpful.
On Unix systems, the way to push public keys to a remote username@remote-server is with **ssh-copy-id**. This has to be done once for from each client userid to each username@remote-server.  If there is only 1 username on the remote-server to be accessed from the local client, then 1 time is it.  I don't know if Windows has a similar tool or not.  All ssh-copy-id does is create/setup the ~/.ssh/ directory and properly push the public key to the remote machine, into the correct file and maintain file permissions as required for ssh/scp/sftp/rsync and 50 other ssh-based tools.
When you add the public key manually, be certain it doesn't get added as multiple lines. Each entry must be on 1 line.  Life is much easier if you can dump Windows.  ;)

Sorry, cannot help with filezilla, but support for 19.04 ends in about 1 month, so it is time to move to 19.10.

---

### Post by mangonels on 2019-12-14
I add the public key manually for each user, each code in one line, for the account they need access to. It is indeed working for ssh (putty) but not sftp (filezilla), I'll keep testing stuff, but I'm using the same private key.

Is it mandatory for me to prepare an account specially for this (as I did)? Or should I be capable of accessing the server through sftp with any account as long as it has the public key registered on the server? In any case I already tried all my accounts, all of them should have access from my computer since I'm using the right private key corresponding to the public key on the server, and it works on putty.

I may focus on asuming something is wrong with how I set up filezilla, or some credential.

Also, OVH default installed Ubuntu Server 19.04 for me... Maybe because I skipped advanced configurations. I'm guessing I can still update it. **Edit:** Updating now

---

### Post by TheFu on 2019-12-14
> **mangonels said:**
> I add the public key manually for each user, each code in one line, for the account they need access to. It is indeed working for ssh (putty) but not sftp (filezilla), I'll keep testing stuff, but I'm using the same private key.

Is it mandatory for me to prepare an account specially for this (as I did)? Or should I be capable of accessing the server through sftp with any account as long as it has the public key registered on the server? In any case I already tried all my accounts, all of them should have access from my computer since I'm using the right private key corresponding to the public key on the server, and it works on putty.

I may focus on asuming something is wrong with how I set up filezilla, or some credential.


I wouldn't assume that filezilla uses the same key or key format that putty uses.

ssh-keys are per userid, per system, based on the client.  The public key from 1 userid+1 system can be pushed multiple times to different systems and different userids on those systems, but each remote userid has to have the public key placed correctly, with the correct file, file permissions, and directory permissions.  That is what ssh-copy-id is all about, keeps us from screwing up a very simple process, which humans seem to screw up all-the-time.

When I google: "filezilla using ssh keys from putty?" some fairly clear instructions result. Do those not work?  Is a log file part of filezilla?  Can you increase the verbosity?  Does the sshd on the server-side see anything? Have you tried runnnig a separate sshd in debug mode on a different port and watched the log messages?

 Check that the ssh version of the key is supported too.  ssh1 vs ssh2.  I think all ssh1 connections should be blocked for the last 20+ years. Bad security.

---

### Post by mangonels on 2019-12-14
I did it! it was the damn port. I was using the default 21 for ftp... I realized I should be using my custom ssh port instead, obviously.
Good, thanks a lot for your help. Even if it looked like I got lost with my previous posts, I finally got to an even better situation than I was before, thanks to the added ssh security and destroying and re-building what I already had.

I still have much to learn though.

[B]Edit:
[/B]Do you think just following these instructions (which you already linked to me in previous post) for a restricted sftp access account may be enough to solve my need for a restricted access account?:
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04)

---

### Post by TheFu on 2019-12-14
> **mangonels said:**
> I did it! it was the damn port. I was using the default 21 for ftp... I realized I should be using my custom ssh port instead, obviously.
Good, thanks a lot for your help. Even if it looked like I got lost with my previous posts, I finally got to an even better situation than I was before, thanks to the added ssh security and destroying and re-building what I already had.

I still have much to learn though.

No way would anyone but you know to check the port.  If the sftp-server process wasn't seeing any connection attempt, that would be a hint.

Plain FTP  is very different from sftp.  Mixing those things up is a mistake.  Plain FTP should pretty much NEVER, EVER, be used since 2002. Lots of people, even in these forums, will say they want FTP when they mean sftp.  It causes no end of confusion.

Too bad you are on Windows. With Unix-like OSes as the client, you can setup a ~/.ssh/config file that handles non-default users, ports, names, hostnames, IPs, specific connection settings.  With any ssh-based tool, that config file and those settings will be found and used.  It is fantastic for non-default port setups.  ssh, sftp, scp, rsync, x2go, thunar, nautilus, caja and 50+ other clients all honor it.

Instead of trying to remember **ssh -N -p 21022 [email]user987432@ec255-33-22-11.west.amazon.com[/email]**
I just type:  **ssh xyz-srv** and all those other settings are picked up.  For caja, I'd put **sftp://xyz-srv/** into the URL and it uses the correct port, userid, and remote address.  No more wondering what the correct port, userid, or funky DNS/IP is. I don't know, don't care and don't need to know.

To be helpful to the community, please use the "thread tools" button and mark this thread **SOLVED**. People looking for answers will find it faster and people looking to help will know not to bother, since it is SOLVED.

---

