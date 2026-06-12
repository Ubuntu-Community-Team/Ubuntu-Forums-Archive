---
title: "Stopping broken symbolic links flashing"
date: 2016-02-27
forum: General Help
---

### Post by AugustinMa on 2016-02-27
I a previous thread, Mehmet asked the following question:

>  Broken links in a bash shell appear with a red background and flash, at least on the Linuxen (plural?) I've used. I don't mind the colours but would like to turn off the flashing. So far I have been unable to figure out how. I've tried searching various places for this, but I can't find anything useful. I suspect that I'm not searching for the correct key words. The closest I can get are conversations explaining how to find broken links or adjust the colours the terminal displays. I have this problem in the bash shell. It happens with Konsole in KDE and with xterm so I don't think it depends on the emulator. I get the same behaviour on Kubuntu and Scientific Linux. In Konsole, I seem to have control over the colours, but not the flashing. Using my .bashrc file, I know how to change the colours, but I don't know of a code for flashing. I'm also not sure how to modify the colours associated with different file types. Could someone please point me in the right direction? Am I thinking along the correct lines? Quote from [http://ubuntuforums.org/showthread.php?t=1342254](http://ubuntuforums.org/showthread.php?t=1342254) 
 Unfortunately, it is an old thread and it is locked, so I cannot reply directly there. 

What's more worrisome, the thread, without any solution, shows up on the first page of result in search engines. 

For the record, I found a simple solution, summarized below.

I have added the solution to the linux Meta wiki here: [http://linux.overshoot.tv/wiki/ls](http://linux.overshoot.tv/wiki/ls) 
we can complete the article with more, updated information as necessary.

--

 Change the following two files:

~/.bashrc 
# Change the color for a broken symlink flashing red
# [http://linux.overshoot.tv/ticket/6154](http://linux.overshoot.tv/ticket/6154) 
d=~/.dircolors
test -r $d && eval "$(dircolors $d)"

Edit ~/.dircolors and change what you want. 
Remove the '05' in the following two lines to get rid of the flashing colour:

ORPHAN 01;37;41 # orphaned syminks
MISSING 01;37;41 # ... and the files they point to

---

