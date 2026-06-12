---
title: "skype sound and &quot;/proc/.../oss: Permission denied&quot;"
date: 2005-09-30
forum: General Help
---

### Post by cokhavim on 2005-09-30
whenever i do this:

sudo echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0p/oss
sudo echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0c/oss

i get the message:

bash: /proc/asound/card0/pcm0p/oss: Permission denied
bash: /proc/asound/card0/pcm0c/oss: Permission denied

the weird thing is that it didn't deny me permission before, and skype worked fine.  then for some reason, something broke.  i think something happened when i installed mplayer and then uninstalled it again.  (i don't really like mplayer.)

i tried to force writing to the oss using this:

sudo sh -c 'echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0p/oss'
sudo sh -c 'echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0c/oss'

but then skype sound becomes very high-pitched (however my microphone recording works fine).

what's going on?  was it mplayer that broke something?  what's broken, and how do i fix it?

thanks.

---

### Post by cokhavim on 2005-10-01
bump

---

### Post by cokhavim on 2005-10-03
bump

---

