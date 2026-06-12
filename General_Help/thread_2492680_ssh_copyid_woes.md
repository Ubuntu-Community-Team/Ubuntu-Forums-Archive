---
title: "ssh copyid woes"
date: 2023-11-19
forum: General Help
---

### Post by Old Jimma on 2023-11-19
Hello Forums:

I have several computers at my home.

Some of them are connected to my home network by a cable and others are connected by wifi.

One of them, [SIZE=5] **lucy.van.pelt** [/SIZE], will act as the computer that will so back-ups over ssh using rdiff-backup.

Other machines,  [SIZE=5] **charlie.brown** [/SIZE] and  [SIZE=5] **snoopy** [/SIZE] are the computers that will have their data backed up to [SIZE=5] **lucy.van.pelt** [/SIZE].

To do this, I need to 
[LIST=1]
[*]set up ssh keys on  [Blucy.van.pelt[/B]
[*]share those keys with **charlie.brown** and 
[*] **snoopy**
[/LIST]

I usually screw this up, so I'm checking the forum to make sure I get the procedure right.

The first thing I'm going to do is to set up UFW (uncomplicated fire wall) on **charlie.brown** and **snoopy** by adding this line to both of their UFW rules:

[HTML]
sudo ufw allow from Lucy's.IP.address to any port 22
[/HTML] 

[SIZE=5]
[B]Right?
[/B][/SIZE]

The next thing I'm going to do is to create they ssh keys on [Blucy.van.pelt[/B] as follows:

[HTML]ssh-keygen[/HTML]

And lastly, copy the keys to **charlie.brown**  and **snoopy** as follows:

[HTML]
ssh-copy-id charlie.brown@charlie.browns.IP.address
[/HTML]

and


[HTML]
ssh-copy-id snoopy@snoopys.IP.address
[/HTML]

[SIZE=5]**Right?**[/SIZE]


Finally, I will check to make sure this worked by logging into charlie.brown and snoopy using:

[HTML]
ssh charlie.brown@charlie.browns.IP.address
[/HTML]

and

[HTML]
ssh snoopy@snoopys.IP.address
[/HTML]


[SIZE=5]**Right?**[/SIZE]

I'll be grateful for you all to correct my big ideas here.

Thanks,
Old Jimma

---

### Post by TheFu on 2023-11-19
Dots in computer names mean something specific.  Best NOT to have those at all since it will complicate your networking.
After you remove the dots, feel free to use hyphens or just go with shorter names,  snoopy, charlie, lucy would be my choices.

Start over with cleaned out ~/.ssh/ directories on all the systems.  Also, RSA keys have had an issue on some ssh servers (not openssh), so it would be good to generation new keys using
```
    $ ssh-keygen -t ed25519
```
on each client system.
Run:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
to push the ED25519 public key(s) to the other systems.
All done.  If the username is the same on the ssh client and server, it doesn't need to be provided.

You can setup an alias in the ~/.ssh/config file for each host that maps to different usernames, different IP addresses, and non-default ports, if you like.  All ssh-based tools honor these alias and automatically use the username, IP/dnsname, port, and any other setting inside it.
An example ~/.ssh/config file:

```
host pihole
  user ubuntu
  hostname 172.22.22.80
  port 62022

host **pihole-r**
  user root
  hostname 172.22.22.80
  port 62022

```
So this command
```
ssh **pihole-r**
```
 becomes:
```
ssh -p 62022 root@172.22.22.80
```
and I never need to remember the non-standard port or userid again.  BTW, rdiff-backup is included.  However, rdiff-backup really needs to run as root, which means on the client and the server, whether the backups are push or pull, you'll need all these setups to be for the backup (root equivalent) account or for root.  That means the keys need to be in those specfic accounts on both the client and the server, not your personal account. Make sense?  Are snoopy and charlie.brown root equivalent accounts?  If not, you are wasting time and it won't work.

BTW, remote root over ssh is disabled by default on all Ubuntu systems.

---

### Post by Old Jimma on 2023-11-20
Thanks, TheFu.

Thanks for the help, and especially for the one on root-equivalent accounts.

I've gotta rake leaves and will get back to you soon about the exact code I'll use on the "pull" computer (now named Lucy) that I'll run from sudo crontab.



I got a new minicomputer to do the back ups with rdiff-backups.

While a pi has rdiff-backup, it wouldn't do backups because the version on the pi was not the same version on my other computers. That's a pi thing and I got tired of fighting it. Using the pis to do other things now.

Old

---

### Post by TheFu on 2023-11-20
"Pull" backups can mess with your head. I have some notes for setting up my root-equiv accounts and getting the ssh-keys setup correct, but I won't post them here. Only someone able to setup and secure their ssh connections for this need should do it.  Call it a barrier to entry.  BTW, do you ever join ALE on Sundays?

---

### Post by ActionParsnip on 2023-11-20
You can manually copy the public key if you like. It's not mandatory to use the ssh-copy-id command. Just copy the public key file over and append it to the ~/.ssh/authorized_keys for the user you want to authenticate as (for backups you may want to use root so the file will be /root/.ssh/authorized_keys)

---

### Post by TheFu on 2023-11-20
> **ActionParsnip said:**
> You can manually copy the public key if you like. It's not mandatory to use the ssh-copy-id command. Just copy the public key file over and append it to the ~/.ssh/authorized_keys for the user you want to authenticate as (for backups you may want to use root so the file will be /root/.ssh/authorized_keys)

Yep.  Just be certain the file/directory permissions are correct or ssh won't work.
Also, ensure that any spaces introduced in the middle of the key from the copy/paste (or better select/paste) action get removed.  ssh keys have 3 parts, 2 spaces and sometimes the copy/paste will insert newlines in the middle of the key part of the public ssh-key.

---

### Post by Old Jimma on 2023-11-20
Hello The Fu:

You wrote, "rdiff-backup really needs to run as root, which means on the client and the server, whether the backups are push or pull, you'll need all these setups to be for the backup (root equivalent) account or for root. That means the keys need to be in those specfic accounts on both the client and the server, not your personal account. Make sense?"

I am not sure what you mean, exactly.

Does this mean that on all client computers that will be backed up as well as the server computer that will do the backing up,[LIST]
[*]the public keys need to be created on the server's super user account and then transferred to 
[*]then tranfered to the super user account on the client machine?
[*]
[/LIST]

Also, does this mean that when the backups take place,
[LIST]
[*]they take place between super users on both server and client on the server and client machines?
[*]
[/LIST]

When I was dong rsync over ssh with a pi, I didn't do this... and it worked well.

Thanks,
Old

---

### Post by Old Jimma on 2023-11-20
Hi TheFu:

I haven't been to ALE in 20 years!

I checked the website [https://ale.org/](https://ale.org/) . Cool that is is a jitsi meet! I sort of liked meeting down at Emory.

---

### Post by Old Jimma on 2023-11-20
Hi The Fu:

You wrote: "I have some notes for setting up my root-equiv accounts and getting the ssh-keys setup correct, but I won't post them here."

Golly! Is there a secret handshake?

---

### Post by TheFu on 2023-11-20
> **Old Jimma said:**
> Hi TheFu:

I haven't been to ALE in 20 years!

I checked the website [https://ale.org/](https://ale.org/) . Cool that is is a jitsi meet! I sort of liked meeting down at Emory.

Some of the Emory meetings were great. Going to Emory for me, up in Squidbillyland, was quite the effort.

Now we meet at 3 different places around town, but most of them have become virtual. Tuesday evenings and Sundays. There's a meetup page, or you can just see the ale.org website, but most meeting schedules are in meetup. The Sunday group has 15+ people every week.

> **Old Jimma said:**
> 
Secret handshake ... 


No, but it can drastically decrease system security if not handled correctly and I think if someone is struggling with ssh already, it is very likely they will end up providing remote root access they didn't intend.  I can't do that.

If you don't do system backups with root, you are losing ownership, group, permissions, ACLs and xattrs, which is 50% of what is needed for proper backups. Data can can't be put back exactly like it was with those extra things is useless.  If all you backup is a HOME directory, then root isn't needed, but that's a weak backup.  At least get /etc/ and /usr/local too, which means different userids and all that other stuff.

---

