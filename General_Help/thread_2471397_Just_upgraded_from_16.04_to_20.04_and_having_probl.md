---
title: "Just upgraded from 16.04 to 20.04 and having problems running ksh scripts"
date: 2022-01-29
forum: General Help
---

### Post by chris53 on 2022-01-29
Hi there.   I just recently upgraded my laptop from 16.04 to 20.04 and I am having a problems running KSH scripts.    Very strange.     I just tried to execute my env.ksh script and nothing took affect.   I looked around online to find a solution and have tried all sorts of stuff.  I figured I would reach out to the experts..     Below is a snippet from my env.ksh:

#!/bin/ksh
########################################################################
# Environment Variables for Development                                #
########################################################################
export DEV_HOME=/home/cwegescheide/Desktop/Development
export SRC_FILE_DIR=$DEV_HOME/DataFiles/SrcFiles
export TGT_FILE_DIR=$DEV_HOME/DataFiles/TgtFiles
export ARCHIVE_DIR=$DEV_HOME/DataFiles/Archive
export SCRIPT_DIR=$DEV_HOME/Scripts

I did a cat on /etc/shells and this is what I see:
 /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/ksh2020
/usr/bin/rksh2020


Any help would be greatly appreciated.   This is driving me nuts.  

Thanks in advance,
Chris

---

### Post by Impavidus on 2022-01-29
I'm not entirely sure about your situation, but two things strike me as somewhat odd.

First, is ksh actually installed? It could be a symlink to ksh2020 mentioned in your post. There's no ksh on a default Ubuntu system, I think.

Second, to export the environment variables from your script to the applications you launch from your terminal, you have to source the script, not execute it. When you execute it, a new shell is started, it runs the script, sets environment variables in the script, exports them to any child processes, but not to the parent process, and the environment variables are gone again when the script terminates.

Maybe in the past your script was automatically sourced.

---

### Post by chris53 on 2022-01-29
> **Impavidus said:**
> I'm not entirely sure about your situation, but two things strike me as somewhat odd.

First, is ksh actually installed? It could be a symlink to ksh2020 mentioned in your post. There's no ksh on a default Ubuntu system, I think.

Second, to export the environment variables from your script to the applications you launch from your terminal, you have to source the script, not execute it. When you execute it, a new shell is started, it runs the script, sets environment variables in the script, exports them to any child processes, but not to the parent process, and the environment variables are gone again when the script terminates.

Maybe in the past your script was automatically sourced.

Thank you for your reply, and yes, that makes sense.   I ran a script which accesses the environment file to resolve where the log file would be written and indeed it was there.   I think I confused myself.   :)   I appreciate your reply.   And yes, I installed ksh.

Cheers,
Chris

---

