---
title: "Prevent X-Window Closing and Execute Script on Attempted Close"
date: 2007-07-26
forum: General Help
---

### Post by psych787 on 2007-07-26
I need a generic way of preventing an X window from closing the same way trap can protect a shell script. To keep this post simple, I'll describe it on a point-by-point basis.

**Why this is important:** 
Recently, I've been looking around to replace Seamless Windows with something more responsive and metisse-friendly. One way to do this would be to launch a dedicated VM for each application. VirtualBox has the necessary command-line functionality (ex. acpipowerbutton), front-end (VBoxSDL), and guest screen resizing to make this practical.

**The roadblock:**
I need something similar to the trap command in bash to work for a launched program. That way I can prevent the VBoxSDL window from instantly closing (taking the VM with it), and send the appropriate shutdown commands to it.

**Here's how I want things to work:**
```

#!/bin/bash
<X11 trap> "VBoxManage controlvm 2e31f98e-749f-44cd-b3ba-f0f160854192 acpipowerbutton" <X11 term signal>

VBoxSDL -vm 2e31f98e-749f-44cd-b3ba-f0f160854192

```

Could someone please fill in those two blanks or offer an alternative method? Thanks.

---

### Post by pvincent on 2008-02-01
Hi, 
very clever your idea about a X11 trap for window closing.
However, I don't know how to implement this signal.

I'm busy doing almost the same trick but with basic bash trapping.
What I think is : 
[LIST]
[*]launch vboxsdl
[*]wait forever and trap all signal
[*]when signal, execute vboxmanage -controlvm xxx -savestate, then exit the bash script
[/LIST]

---

### Post by pvincent on 2008-02-01
At this stage, my bash script does not work.
Here is the script :
```

#!/bin/bash

vboxsdl -vm windouille  &
echo 'Press [CTRL-C] to hibernate your windouille box...'

trap 'vboxmanage controlvm windouille savestate; exit ' ABRT EXIT HUP INT TERM QUIT

while (( 1 )); do
        wait
done; 

```

I've already posted on virtualbox forum to ask for any help :  [http://forums.virtualbox.org/viewtopic.php?p=15092#15092](http://forums.virtualbox.org/viewtopic.php?p=15092#15092)
waiting for an answer

---

