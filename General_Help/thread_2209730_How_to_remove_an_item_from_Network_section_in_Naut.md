---
title: "How to remove an item from Network section in Nautilus"
date: 2014-03-07
forum: General Help
---

### Post by Tony_Lillie on 2014-03-07
Ubuntu 13.10

I was trying to map a network share and did something wrong leaving me with a dead (as in it doesn't work) mapped share under the Networks section in Nautilus.
See here: [http://dl.dropbox.com/u/62495359/Selection_001.png](http://dl.dropbox.com/u/62495359/Selection_001.png)  My network share issue has been resolved and I just want to clean up this debris.

I would remove it, but the remove option is greyed out: [http://dl.dropbox.com/u/62495359/Menu_005.png](http://dl.dropbox.com/u/62495359/Menu_005.png)

All I want is to remove this dead end share. I've searched for hours and come up empty handed.

Help please.

---

### Post by mcduck on 2014-03-07
I suppose the big question is "how were you trying to map the share?".

Were you perhaps trying to do it from /etc/fstab or some other method other than just using the file manager's "Connect to Server" dialog?

---

### Post by steeldriver on 2014-03-07
The list of recent Nautilus remote server connections in 13.10 appears to get saved in ~/.config/nautilus/servers - it's an HTML file so to remove individual entries is a bit tricky, but you can delete the whole file and start over

---

### Post by Tony_Lillie on 2014-03-07
Yeah, that's part of the problem. I don't remember what i did to get that entry, except to say it didn't come from the "connect to server" dialog. Also, I know I did not edit my fstab file. It was an annoying little problem and I tried 20 things before I resolved it, so that's why I don't remember exactly what I did.

I went through my command line memory and found this gem of a command. ```
sudo mount -t cifs //mediaserver/public /media/sambashare -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
``` It failed to work for my situation, but could it have created the network item I now wish to remove?

I suppose it's pointless to ask, but WHY (oh why oh why oh why) would the remove option be greyed out. That's just so very stupid!

What exactly will happen if I delete the entire [COLOR=#000000]/.config/nautilus/servers file and "start over"? That seems a bit dramatic to me for something as simple as removing a single useless share.


Other thoughts please??[/COLOR]

---

### Post by Tony_Lillie on 2014-03-07
Well, I attempted to open the [COLOR=#000000]/.config/nautilus/servers file and edit it ```
sudoedit /.config/nautilus/servers
```, and it was an empty file. There was nothing in it. So, either I did something wrong, or there are no entries in that file. It would seem the solution lies elsewhere.[/COLOR]

---

### Post by steeldriver on 2014-03-07
Sorry - I may have misunderstood your issue. I thought you were talking about removing it from the list here:

[ATTACH=CONFIG]250925[/ATTACH]

---

### Post by mcduck on 2014-03-07
> **Tony_Lillie said:**
> Yeah, that's part of the problem. I don't remember what i did to get that entry, except to say it didn't come from the "connect to server" dialog. Also, I know I did not edit my fstab file. It was an annoying little problem and I tried 20 things before I resolved it, so that's why I don't remember exactly what I did.

I went through my command line memory and found this gem of a command. ```
sudo mount -t cifs //mediaserver/public /media/sambashare -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
``` It failed to work for my situation, but could it have created the network item I now wish to remove?

I suppose it's pointless to ask, but WHY (oh why oh why oh why) would the remove option be greyed out. That's just so very stupid!

What exactly will happen if I delete the entire [COLOR=#000000]/.config/nautilus/servers file and "start over"? That seems a bit dramatic to me for something as simple as removing a single useless share.


Other thoughts please??[/COLOR]

That command would point towards mounting through fstab (even though the command itself doesn't do any permanent changes.)

I'd recommend running the following commands to make sure it's unmounted, and to remove the mount point:
```
sudo umount /media/sambashare
sudo rm /media/sambashare
```
...and after that check the fstab to make sure you really didn't add anything there.

(The option is greyed out if you used any other method than the "Connect to Server" dialog, as any other method would be a system-wide configuration as as such something individual users shouldn't be able to mess with)

---

### Post by Tony_Lillie on 2014-03-07
No worries. Thank you for your help.

The linked screenshots in my original post show the "item" I want removed from the Nautilus sidebar under the Network heading.

---

### Post by Tony_Lillie on 2014-03-07
Thank you for your swift response.

I had already done both of those commands to no avail. The "item" is not mounted because it was a failed attempt, and the mount point has been removed. Though, just for reference, I needed to use ```
sudo rmdir /media/sambashare
``` because rm alone would not delete a directory.

My fstab file is empty.

Other thoughts??

---

### Post by Tony_Lillie on 2014-03-08
Just pinging this post to move it to the top.

Anyone got any other thoughts on this issue. I know it's not life and death, but it's the little things that annoy us, right? Can it really be that difficult to remove this useless share? 

Somebody out there knows how to fix this.

---

### Post by steeldriver on 2014-03-08
What do you get if you do

```
ls -l /run/user/$(id -u)/gvfs
```

I can possibly reproduce your issue if I mount a remote USB share and then unplug it...

---

### Post by Tony_Lillie on 2014-03-08
Well, once again I am an idiot. Apparently I DID actually edit my fstab file, but when I attempted to look at it during the course of this thread I made a typo in the terminal and thought I was looking at an empty fstab file. I was obviously not looking at the \\etc\fstab file.

Thus I have removed the entry from the genuine \\etc\fstab file and all is well.

Thanks for all the help guys. I'm going to go enjoy some humble pie.

---

