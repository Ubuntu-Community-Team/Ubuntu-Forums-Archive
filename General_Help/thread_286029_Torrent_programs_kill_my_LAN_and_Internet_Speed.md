---
title: "Torrent programs kill my LAN and Internet Speed"
date: 2006-10-27
forum: General Help
---

### Post by slacker9876 on 2006-10-27
Good Day Everyone, 
I have been downloading other flavors via bittorrent and Azureus and when I am downloading and seeding my access to the Internet and file copy across my LAN are very, very, slow. I read a couple of articles at other sites and all of them pointed not enough ports open. Well, I opened 6881-6999 in my router and all my PC's are still dirt slow when "torrenting." As a test I pulled Suse 10.1 DVD ISO from a local mirror and while it was going, none of my computers were latent on the Internet. Does anyone know what I can do to stop this insanity?

---

### Post by pmj on 2006-10-27
That LAN speeds would suffer from torrenting is a bit strange. Could this be a problem with your router? Some bad routers behave strangely, drop connections or get very slow when they're overloaded. In any case, I suggest you lower the maximum upload speed to maybe half or 75% of your maximum upload and see if that helps. You could also try to lower the maximum number of connections.

---

### Post by skymt on 2006-10-27
The sheer number of connections Bittorrent creates is guaranteed to slow a network. You should use a client that allows you to limit the maximum number of connections. Experiment with different numbers until you find a balance between Bittorrent download speed and network usage.

---

### Post by slacker9876 on 2006-10-29
Once I turned down the upload to 20K, it worked very well. Thank you!

---

### Post by marx2k on 2006-12-12
If using Azureus (recommended), use the AutoSpeed plugin or the built-in Azureus autospeed option. Works wonders.

---

