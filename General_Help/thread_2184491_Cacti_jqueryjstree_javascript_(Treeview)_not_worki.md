---
title: "Cacti jquery/jstree javascript (Treeview) not working after upgrade to 13.10"
date: 2013-10-29
forum: General Help
---

### Post by duteweerd on 2013-10-29
Hi all,

I have a question about Cacti 0.8.8b:

After the dist-upgrade to 13.10 (from 13.04) my cacti has a strange problem with displaying the treeview. It looks like the jstree javascript is not running correctly.
I have checked if the requested packages are available ( libjs-jquery-cookie and lbjs-jquery). There are installed and configured correctly.

Normaly the ouput is:
+ tree
   - host
+ tree
   - host

Now the output is (it is flat without any folder icons)
o tree
   o host


Before the update (Cacti 0.8.8a and Ubuntu 13.04) everything was displayed correctly. Does someone has the same strange problem after the dist-update or is there someone who can help me?
I checked all the links, apache is running fine and the Javascript files are in the correct place.

Thank you!
Br, Duteweerd.

---

