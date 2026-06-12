---
title: "Resume from Suspend - hook for xmodmap"
date: 2015-03-23
forum: General Help
---

### Post by Tim_Johnson on 2015-03-23
I've recently upgraded from ubuntu 12.04 to 14.04.
Keymappings set by xmodmap are not restored when **suspend** is cancelled.
I have found and made slight edits to the script at [http://pof.eslack.org/archives/files/mba42/00_usercustom](http://pof.eslack.org/archives/files/mba42/00_usercustom)
The code is as below ```

#!/bin/sh

# /etc/pm/sleep.d/00_usercustom
# Script to run user custom actions.
#
# To Install:
#
# # change USER variable to your username
# sed -i "s/xxxxxxxx/$USER/" 00_usercustom_xmodmap
# chmod 0755 00_usercustom_xmodmap
# sudo mv 00_usercustom_xmodmap /etc/pm/sleep.d/00_usercustom_xmodmap
#
# See /var/log/pm-suspend.log for log.

. "${PM_FUNCTIONS}"

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
USER=xxxxxxxx

suspend_usercustom()
{
    # do nothing
    :
}

resume_usercustom()
{
    export DISPLAY=:0.0
    #su - $USER -c "sleep 3;xmodmap /home/$USER/.Xmodmap"
    su - $USER -c "xmodmap /home/$USER/.Xmodmap"
}

case $1 in
    suspend|hibernate) suspend_usercustom & ;;
    resume|thaw)       resume_usercustom  & ;;
    *) exit $NA ;; 
esac

exit 0  

# suspend   system state saved   to   RAM
# resume    system state resumed from RAM
# hibernate system state saved   to   disk
# thaw      system state resumed from disk

```
Since this script may have been originally written with a different distribution in mind,
I would welcome comments on this code. Such comments may save me some time
if they prevent me from screwing up.

Thanks
- tim -

---

### Post by Tim_Johnson on 2015-03-23
I would never venture to say that I have so far stumped the chumps and I would never suggest that anyone of the senior members of this community are chumps.
Having said that, with no comments : I have installed this application and it seems to work. I have not able to see any side effects.
My concern for input prior to implementation was that the original script appeared to be written in a slackware - related site, and I am always 
wary of cross-distribution implementations.

I have noted that ubuntu is in a state of flux and change when it comes to upgrades. I'd like to see more gotchas documented for upgrades.
Googling this issue came up with a whole lot of content that indicated confusion.
My criticism of this change is that it takes control away from the **user** and into the purvue of **root**.
All the same, I hope that my solution can help someone else.

---

