---
title: "Need help with cron and tmp folder"
date: 2016-03-25
forum: General Help
---

### Post by kelbygreen on 2016-03-25
Hey,

I have a VPS but it is shared and seems the TMP folder is shared with other users. I am setting up flexget and had to change the TMP folder to one I created in home directory as another user is using the file flexget it trying to write to in the standard TMP folder. This works good I got flexget working but the only trouble is when I set up a cron job it is trying to write to the default TMP folder not the one on my home dir.

I am wondering is there a way in cron I can get it to use a different TMP folder? 

I am sure there is a way but I am not the best at linux. I tried to put this into cron but it does not work still.

TMP= ~/tmp2

I hope there is a way to get around this as I cant log into the server every 10 mins manually to run the job like I want cron to do.

---

### Post by QIII on 2016-03-25
Was the VPS set up this way by your provider (if so, fire your provider) or have you added other users?

What effect will altering cron have on those users?

---

### Post by kelbygreen on 2016-03-25
it is a seedbox setup by a provider, If was able to delete the said file then they will loose the use of flexget. They allow install of your own software on the server but I have no root access so cannot modify anything outside of my home folder.

---

### Post by kelbygreen on 2016-03-26
Its ok I got around it, I had to create a script to run the command and then sleep for 120s and run it again, I put this in a detached screen and it uses the tmp dir I created in the home dir. Its a bit crude but only way I could see around it and it works so thats the main thing

---

