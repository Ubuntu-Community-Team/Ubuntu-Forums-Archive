---
title: "x2go Segmentation fault"
date: 2016-09-21
forum: General Help
---

### Post by izznogooood on 2016-09-21
Well, this one is hard to explain. I am trying to get x2go working with Mate and 16.04 with an Ubuntu installation (Follow?)
This means that I have an ubuntu desktop running ubuntu 16.04, I installed mate with the mate developer PPA because x2go does not support Unity.
I Installed x2go as instructed by the dev site. I also followed the steps installing x2go in osX & ubuntu (in vmware). 

When you connect it looks fine. But some (only some) programs ends with: Segmentation fault (In an osX client & ubuntu client) 

This video will show you what the problem is and the settings for the connection. 
[https://www.youtube.com/watch?v=z6gVcS1_w2Q](https://www.youtube.com/watch?v=z6gVcS1_w2Q)

Some operation fails while others executes without a problem.... Help?
As x2go does not have a forum I am a little lost at this moment....

---

### Post by #&amp;thj^% on 2016-09-21
Yup seen it here also... but my work around might not work for you but no harm trying.
There is now a clean workaround to fix this problem: Just add a line

   ```
X2GO_NXAGENT_DEFAULT_OPTIONS+=" -extension BIG-REQUESTS"

```
to... "/etc/x2go/x2goagent.options"

Credit to Colin Finck

---

### Post by izznogooood on 2016-09-21
Thank you for the suggestion :). But it does not help, in fact more programs fail. Perhaps you could share you´re setup?

---

### Post by #&amp;thj^% on 2016-09-21
Not at my buntu machine ATM
But here is My Arch set-up
```
#
# This file can be used to specify default options that are passed to nxagent.
#
# These options can be overriden by the client!
#
# See the output of `nxagent -help` for the full list of options.
#
# Remember:
# "-extension" disables an extension.
# "+extension" enables an extension.

X2GO_NXAGENT_DEFAULT_OPTIONS=""

# Disable XFIXES.
# Workaround for https://bugs.launchpad.net/ubuntu/+source/libxfixes/+bug/985202
#
X2GO_NXAGENT_DEFAULT_OPTIONS+=" -extension XFIXES"

# Uncomment to disable GLX, the old mesa version is hopelessly outdated anyways.
# Unbreaks the gnome3 control center
#
#X2GO_NXAGENT_DEFAULT_OPTIONS+=" -extension GLX"

# Launch X2Go's X-server x2goagent with option "-nolisten tcp".
#
# This is the default setting and the X2Go developers really recommend not to
# touch this. However, if you play with this (i.e. if you comment it out) you
# should really know what you are doing.
#
# For everyone else: don't touch the line below!!!
X2GO_NXAGENT_DEFAULT_OPTIONS+=" -nolisten tcp"

# Enforce clipboard behaviour in X2Go sessions globally (for all connecting clients)
# Possible values for the -clipboard option: both, server, client, none
# If this option stays commented out, clients can choose the sessions' clipboard behaviour...
#X2GO_NXAGENT_DEFAULT_OPTIONS+=" -clipboard both"
X2GO_NXAGENT_DEFAULT_OPTIONS+=" -extension BIG-REQUESTS"

```

---

### Post by izznogooood on 2016-09-22
Thank you, but I was thinking more in the line of Distro, client OS and desktop environment of what you have working.
This segmentation fault is pusling me since i have not located a common thing among the failing programs.

And did you edit any options in /etc/ssh/sshd_config ?

Anyone who has a running setup may comment please ;)

---

### Post by izznogooood on 2016-09-23
So I found the problem. 

Every time something required accelerated graphics it crashed, so switching to Nouveau "fixed" the issue....

Now i have a new problem. As this is my main Desktop and not a server I dont want to use the Nouveau driver, oh well :D

---

### Post by zingmars on 2016-09-27
Just a heads up - it seems to be a problem with x2go not playing nicely with nVidia drivers. The fix is to set the LD_LIBRARY_PATH variable to where your nVidia driver is located (for example for nvidia-361 drivers it's "LD_LIBRARY_PATH=/usr/lib/nvidia-361").

---

### Post by izznogooood on 2016-09-27
My man! :popcorn:

---

