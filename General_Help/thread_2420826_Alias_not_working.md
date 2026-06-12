---
title: "Alias not working"
date: 2019-06-11
forum: General Help
---

### Post by panja on 2019-06-11
I want to have a few aliases and did everything I though was needed to make it work, but it doesn't work...
This is on Ubuntu 18.04.2 server.

Uncommented in .bashrc: ```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Created ***.bash_aliases*** in my home folder.

Edited ***.bash_aliases*** and put the following in:
```
alias download_latest_redream="sh /home/retropie/scripts/download_latest_redream.sh"
alias n64audio="sh /home/retropie/scripts/n64audio.sh"
alias reset_last_played="sh /home/retropie/scripts/reset_last_played.sh"
alias vnc_start="sh /home/retropie/scripts/vnc_start.sh"
```

I've also tried:
```
alias redream_update='sh /home/retropie/scripts/redream_update.sh'
alias n64audio='sh /home/retropie/scripts/n64audio.sh'
alias reset_last_played='sh /home/retropie/scripts/reset_last_played.sh'
alias vnc_start='sh /home/retropie/scripts/vnc_start.sh'
```

After that I did a reboot.
When I login and do ***alias*** nothing is shown.
I can't do any of the 4 aliases.

Any one know what is going on here?

---

### Post by oldos2er on 2019-06-11
Use a single quote mark ' in place of the double quotes. No need to reboot, just run ```
source ~/.bashrc
``` when you're done.

---

### Post by panja on 2019-06-11
I've updated my post, probably you did not see it yet.
I did try single quotes as well.

Doing source ~/.bashrc works but after a reboot it's back to "stock". No aliases....

What I noticed btw.
When I login to my Ubuntu box my username@machinename is grey.
But after doing source ~/.bashrc my username@machinename is green...

---

### Post by panja on 2019-06-11
It's fixed now!

The problem was I'm using a .bash_profile file and it was not complete so bash was not loaded correctly.
It's working now!

---

