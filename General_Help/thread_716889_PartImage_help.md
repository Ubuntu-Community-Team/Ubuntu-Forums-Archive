---
title: "PartImage help"
date: 2008-03-06
forum: General Help
---

### Post by dxtremeb on 2008-03-06
I'm trying to set up a PartImage client-server connection.

I have Debian installed on one of the clients. I would like to save that installation as a backup to my server (192.168.1.1), so that I can retrieve it for my four other clients to download and set up. partimaged is running on the server, and I'm using SystemRescue on the client to save the image to the server.

Here's where the problem comes in at: I get an error when trying to save the partition to the server. It says "Version Mismatch", or some such like that.

I used partimage -v on the client and it is 0.6.6, while the server is 0.6.4. I have no idea how to upgrade the server to 0.6.6, since I have the latest version from the Debian repositories.

Any help?

---

### Post by dxtremeb on 2008-03-10
Anyone?

---

### Post by azucaro on 2008-03-10
Is it possible to compile the older version on your server? You should be able to manually install using ./configure --PREFIX=/other/directory just for the purposes of taking your backup. Since you have the newer version your dependencies are probably already taken care of (which is why I recommend doing this on the server). 

You would then call the version of partimage in your PREFIX (/other/directory/bin/partimage) and follow the same steps that you did before. This time, though, you should have compatible versions. 

This is interesting. I hope that once you make your backup that it can then be read by other versions (specifically the newer one). Else what value do you have in backing up something that you can't possibly restore? You'd probably want to test that functionality so you won't be surprised later on.

-Ant

---

