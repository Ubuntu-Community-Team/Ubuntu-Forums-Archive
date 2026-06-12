---
title: "ssh from desktop to server with no password"
date: 2007-03-16
forum: General Help
---

### Post by theolster on 2007-03-16
I'm trying to ssh from two desktops to my server.  The resaon for this is that I'm trying to run Unison as a cron job.  The guide I'm trying to follow is [here]("http://cookbook.sitellite.org/index/sitewiki-app/show.LoadBalancingWithUnison").
The bit where I get stuck is when I try to copy the public key over to the server, the command goes like this:> scp public_key_file.pub [email]user@ServerA:~/.ssh[/email]/authorized_keysWith the following warning: *Note that this file on Server A may already exist. In that case, don't overwrite it like this, but instead paste the entire contents of the public key file at the end of this file on Server A.*
But when I paste the contents of the pub key into this file I still get asked for the password, and if I overwrite the file, I do get access, but the other machine doesn't

Thanks for your help

---

### Post by irwa82 on 2007-03-17
Hi,

Try copying the key to the other machine then do

cat keyfile >> ~/.ssh/authorized_keys

This should append the key to the end of the existing authorized_keys file.

---

### Post by dreadlord_chris on 2007-03-17
You need that key to be on both boxes that will be accessing the ssh server

---

### Post by theolster on 2007-03-20
This worked a treat, thanks guys!

---

