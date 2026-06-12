---
title: "tar doesn't like shell scripts!"
date: 2006-10-14
forum: General Help
---

### Post by Count Noobulus on 2006-10-14
What the hell?

Tar doesn't seem to appreciate being summoned from a bash script. I'm trying to configure my own add-on cd for my Ubuntu livecd setup so I'm not dedicating 10 minutes to fire up everything manually. I'm experiencing some strange behavior trying to execute shell scripts that are on - and dragged off the cd to Desktop. It's like they don't exist. If I run for ex: "sudo tar xvfz path/to/file -C /dir" in the terminal, it extracts the files to the dir I want that's permission protected. Works like it should. If I want to invoke the above in any way from a script I know how, tar reports an error of the file/dir not existing before giving me the finger and signing off.

This is what's been in the script on cd:

#!/bin/bash
sudo tar xvfz path/to/file -C /dir 

or

tar xvfz path/to/file -C /dir 

Errors when called everytime from command line whether I do this:

sh path/to/file/on/disc

or this:

sudo sh path/to/file/on/disc.. and every variation thereof.

I don't know what's wrong. I tested first with a cd script just calling the "eject" command and it worked fine. Tar doesn't appear to like being called anywhere other than the terminal however. This has not been pleasant. I've altered the permissions of the relevant dirs and still nothing.

Am I fishing for dirt?

---

