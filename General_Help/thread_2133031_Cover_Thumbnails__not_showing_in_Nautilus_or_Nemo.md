---
title: "Cover Thumbnails  not showing in Nautilus or Nemo"
date: 2013-04-06
forum: General Help
---

### Post by SuperFreak on 2013-04-06
I think since the last update I have not been able to view file icons as thumbnails. I also installed a new hard drive for my data files so this may relate to the problem.File icons show as an icon with checkerboard pattern and clock face. I tried this solution
> Try executing this on a terminal:

sudo chown -R <user>:<user> ~/.thumbnails

replacing the two instances of <user> with your username. Then logout and login again.


but still does not work(see screenshot)

I should add that I have Cover Thumbnailer installed. It has worked for a long time but does not display album covers or pictures anymore.

---

### Post by SuperFreak on 2013-04-08
Bump:(

---

### Post by SuperFreak on 2013-04-09
OK I found a link that describes my problem perfectly (almost) with a solution [here]("http://tuxrocket.com/archives/tinker/803"), but the description is for OPEN Suse and I am leary of putting commands into terminal for another OS. The commands are :

```
rm -rf ~/.thumbnails
```

and

```
killall nautilus
```

I know the .thumbnails directory exists in root directory, is it safe to use the above command and will as the article describes start that directory over again?

---

### Post by CaptainMark on 2013-04-09
Yeah this is safe to, deleting the thumbnails cache will simply force any applications that store thumbnails here to re-draw them as and when it needs them, its no big deal unless you have terrabytes of files to view all at once and a really low spec processor,

---

### Post by SuperFreak on 2013-04-11
deleting the cache had no effect.
all my .pdf,.flac,.mp3,.jpg files have that clock face on the file folder (both in Nautilus and Nemo). It was working fine a week ago until I replaced my data Hard Drive.

---

### Post by CaptainMark on 2013-04-12
I've had a similar problem with .ogg files in the past and back when it happened to me, after googling around a bit I found an old post on this forum which worked for me, delete (or rename if you want to keep it as a backup) the directory ~/.local/share/mime/ then immediately log out of the system, once you log back all will (hopefully) be well

---

### Post by SuperFreak on 2013-04-12
Thanks for the suggestion. Found the MIME file. I renamed and moved the file and rebooted but problem remains

---

### Post by CaptainMark on 2013-04-12
Okay the following instructions will erase all cached thumbnails for nautilus and nemo and ensure no thumbnails remain in the RAM and get written straight back the thumbnails cache (which is probably happening at the moment),

From COLD boot power on the computer but DO NOT login, switch to a virtual terminal by using Ctrl+Alt+F1 and use the following codes```

rm -rf ~/.thumbnails
mv ~/.local/share/mime ~/.local/share/mime.bak
rm -rf ~/.cache/thumbnails
```Now switch back to Ctrl+Alt+F7 and login to your desktop, you should have removed all traces of thumbnails for the file browser and force it to redraw them when you access the files again, if the problem still remains, I'm totally stumped, sorry.

Regards

---

### Post by SuperFreak on 2013-04-13
Mark,

I appreciate the help you gave me. I followed your commands and I am afraid the folders still appear with the clock face on them. I have left Nautilus and Nemo open for the last hour hoping that it is just a question of time to restore the folder icons to a graphical state.

---

### Post by SuperFreak on 2013-04-17
Does anyone else have this problem or know how to solve it? It has become much more difficult to search through my picture folders. I think this problem may have arisen with update from 12.04.1 to 12.04.2

---

### Post by SuperFreak on 2013-04-30
Reinstalled 12.04.2 and Thumbnails are working. I imagine it cleaned up all sorts of cruft at the same time

---

### Post by CaptainMark on 2013-04-30
Glad you got it sorted albeit an inconvenient method, 
We clearly had the right train of thought but apparently there are more thumbnail cache's than you could shake a stick at for nautilus, why they don't just have one place for thumbnails and be done with it I don't know

---

### Post by SuperFreak on 2013-04-30
Thanks for the help Mark. It's good to know that the Ubuntu community can help with problems. The reinstall probably corrected other problems anyway

---

### Post by majedaly on 2013-06-03
Thanks Superfreak,
That solved my problem

---

### Post by hariscakty on 2013-07-13
In my pc this is simple case. Nemo or nautilus not showing thumbnail because .thumbnails folder not own by user. Cek ~./thumbnails and ~/.cache/thumbnails. 

Change ownership the .thumbnails folder can solved this case.

thanks.

---

### Post by ignacioaznar74 on 2013-10-17
I did this:
sudo rm -R /home/<user_name>/.thumbnails/*
sudo rm -R /home/.cache/thumbnails/*

Be careful whit the rm command.
I refreshed my images folder and the thumbnails appeared.
Maybe, the owner of these folders is the problem.

---

### Post by rewyllys on 2013-12-30
> **ignacioaznar74 said:**
> I did this:
sudo rm -R /home/<user_name>/.thumbnails/*
sudo rm -R /home/.cache/thumbnails/*

Be careful whit the rm command.
I refreshed my images folder and the thumbnails appeared.
Maybe, the owner of these folders is the problem.
In Linux Mint 13 with Cinnamon 2, when I opened any containing folder with Nemo, I was bothered by having icons instead of thumbnails for recently acquired images. (Specifically, for images added to the folder after I had switched from Nautilus to Nemo.)

Inspired by IgnacioAznar's comments, I did nothing more than to simply refresh (i.e., re-load in Nemo) the files in the containing folder; and, lo and behold, Nemo had replaced the icons by thumbnails!

Thank you, Ignacio.:p

*Edit added 10 minutes after the above comments:*  It turns out that an intermediate step is necessary.  After further experimentation, I learned that I had to view the "icon-only" images in ImageViewer **before** clicking the refresh (re-load) button, in order for the refresh operation to display thumbnails of the (previously "icon-only") images.  

There may be alternative intermediate steps that would work in place of the viewing in ImageViewer, but apparently something more is needed than merely the refresh operation.

---

### Post by jan4 on 2014-06-08
> **ignacioaznar74 said:**
> I did this:
sudo rm -R /home/<user_name>/.thumbnails/*
sudo rm -R /home/.cache/thumbnails/*
<snip>
Maybe, the owner of these folders is the problem.

Ignacio put me on the right track =d>

He made me aware of the ~/.cache folder which also contains thumbnails. As it turns out the subfolder "Large" was owned by root and was read-only for others. Started Nautilus as root, removed the subfolders in ~/.cache/thumbnails and rebooted. Problem solved! :guitar:

Tx!!

---

