---
title: "A problem with broken packet (and file in it)"
date: 2007-12-16
forum: General Help
---

### Post by oldypoldy on 2007-12-16
Greetings. I have a problem regarding "broken packet" in Ubuntu. I'm not sure if this is right category for the post, but you can guide me on if not. I'm using Finnish translation of Ubuntu, but I'll translate the names of applications, contents of error messages etc to English. Translations might not be word-to-word.

When I try to add new programs with "Add or remove..." menu option, the program says that can't happen. The application describes the reason in a very subtle way (Finnish error message, quite hard to translate), but I think it has something to do with a broken packet.

When I go to Synaptic packet management, first thing I see is a warning:
"There's 1 broken packet in your system. Find the broken packet using filter 'broken'" (translation from Finnish message).
I choose the menu item: Edit -> Fix broken packets (translation from F).
Then I press the Apply (translation from F) button, one with green ok mark.
I get a summary window which says one packet will be updated. That packet is samba-common.
When I press Apply (translation from F) again, Symantec tries to apply changes. Then comes an error popup:
"Following problem were detected in the system (translation from F).
E: /var/cache/apt/archives/samba-common_3.0.22-1ubuntu3.5_i386.deb: unable to make backup link of `./usr/share/samba/upcase.dat' before installing new version"

There's a terminal option which let's me see feedback from commands underneath gui. It says:
"Preparing to replace samba-common 3.0.22-1ubuntu3.1 (using .../samba-common_3.0.22-1ubuntu3.5_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: error processing /var/cache/apt/archives/samba-common_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 unable to make backup link of `./usr/share/samba/upcase.dat' before installing new version: Toiminto ei ole sallittu"

When I exit Synaptic, open terminal and try "sudo apt-get install -f", it gives the exact same feedback that I see in Synaptic terminal window.

I decided to take a closer look to the /user/share/samba directory, opening the terminal and typing:
$ cd usr/share/samba/
$ lsattr

Then I saw:
----------------- ./lowcase.dat
----------------- ./panic-action
----------------- ./smb.conf
-----a-Ac-Z----t- ./upcase.dat
----------------- ./valid.dat

There seems to be something weird in upcase.dat file, regarding all those fancy flags. I tried removing the file with rm upcase.dat, but rm doesn't want to touch it. (I don't know if that was a bad idea anyway. But I'm an expert in bad ideas. ;) )

I would like to get rid of that broken thing and install new programs again. Any ideas? I'm not deeply familiar in Linux, though also not competely illiterate.

---

### Post by matthewcraig on 2007-12-16
I am not too familar with the extended file system, but, after reading the man page for lsattr, it seems you could modify those permissions with the chaddr command.  Check out the chaddr man page.  The t flag may be causing the block, which can be removed, or the Z flag may be causing the block, which cannot be removed.  Both flags are marked as experimental.

I suspect that the problem is a filesystem lock on that file, because you took the right steps in correcting a broken package.

Just FYI, you're wanting the translated word "package" not "packet".  This message title sounds like a networking issue.  Best of luck resolving the issue, and let us know when you found a resolution.

---

### Post by oldypoldy on 2007-12-16
Thanks for helping. Removed the t flag with chaddr, but that didn't help. Synaptic still can't fix the broken package nor can I remove upcase.dat. I'm clueless what to do.

---

### Post by oldypoldy on 2007-12-16
Hooray! Removed a flag from upcase.dat with command:
$ sudo chattr -a upcase.dat

Then removed upcase.dat with:
$ sudo rm upcase.dat
...I'm not sure if that was necessary. Just had to check if the file was still intouchable.

Then went to Synaptic and asked it to fix all broken packages. Current version of samba-common was neatly replaced with new one, and the broken package is gone.

Now I can live a normal life.

---

