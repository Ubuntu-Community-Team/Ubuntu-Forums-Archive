---
title: "[SOLVED] dpkg not installed on Fiesty.."
date: 2008-03-24
forum: General Help
---

### Post by TidusBlade on 2008-03-24
I, helping a friend here install a few things on his server and it seems that it does not have dpkg installed on his server, and it's brand new and untouched so I dunno whats wrong. Anyways, I tried to install it through source and aptitude, but aptitude requires dpkg and source spits out errors that Im missing a few things.
Anyways, my question now is there a way to install dpkg other than through aptitude, dpkg, or source?

Thanks =]

---

### Post by warp99 on 2008-03-24
You can download the packages and libraries from another computer and use the following command:

[HTML]dpkg -x foo.deb /directory_to_extract_to [/HTML]

then copy the extracted files to the other machine. Remember to download the correct packages at packages.ubuntu.com. ;)

---

### Post by forestpixie on 2008-03-24
That's not very easy to look for - search for install dpkg and you get everything - except how to install with dpkg.

I wonder if you can get it from the install cd - put the dpkg package in the right place and reinstall it 

Found this - it might help - [http://ubuntuforums.org/showthread.php?t=103087](http://ubuntuforums.org/showthread.php?t=103087)

Good luck I can imagine that it's going to be a pain :(

Edit - that's what happens when you get halfway through a post and go looking again - you get other answers.

---

### Post by TidusBlade on 2008-03-24
Problem is it's a server :P
So I would have to go all the way to Germany and have access to the server racks to do that lol
I think we figured something out, that the whole OS was a screwed up install, turns out theres tons of essential files missing or something so he requested a reinstall, and Ill see how it goes =]

Thanks everyone!

---

### Post by warp99 on 2008-03-24
I thought of another way to install missing essential packages. You can boot to the install disc, then locate the package on the disc and extract the deb with the following command:

[HTML]sudo dpkg -x foo.deb /media/root_target_drive[/HTML]

or if you have a different install disc, let's say Gutsy versus Feisty, you can boot to that disc then download the deb and extract using the same string listed above. :)

---

