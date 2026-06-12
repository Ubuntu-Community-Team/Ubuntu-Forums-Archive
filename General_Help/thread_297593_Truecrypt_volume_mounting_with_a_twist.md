---
title: "Truecrypt volume mounting with a twist"
date: 2006-11-11
forum: General Help
---

### Post by gnyffel on 2006-11-11
Hello.

I've succesfully built and installed Truecrypt 4.2a from source on my Edgy Eft install, and it works without a hitch. I've encrypted my other (storage one, as opposed to system) partition.

Now, when I type 'truecrypt -u /(partition) /(mountpoint)' in the terminal it asks me for a password. I type the password, it mounts the volume. This I've made into a shortcut on the Gnome Panel for my convenience. No problem. Now to the tricky part.

Within my encrypted volume I have made a hidden volume, and this hidden volume makes use of a keyfile. What I want to do is to make my shortcut on the Gnome Panel ask me for a keyfile so that I can mount either volume depending on what password I enter and whether or not I specify a keyfile.

e.g.:
Enter password for '/dev/hda3': passwordforhiddenvolume <return>
Specify keyfile for '/dev/hda3': /path <return>
*mounts hidden volume*

or:
Enter password for '/dev/hda3': passwordvolume <return>
Specify keyfile for '/dev/hda3': <return>
*mounts volume*


Of course I could just use the -k switch, but doing so would require me to put in the location of my keyfile, rather defeating its purpose.

So I guess what I'm looking for is some switch I've missed (I can't for the life of me get any more information out of the man page) or some very clever scripting thingy that some of you might know.

Anyone? Please? :)

---

