---
title: "Wiping data on old laptop running ubuntu 10.10"
date: 2018-06-26
forum: General Help
---

### Post by jamiefromedinburgh on 2018-06-26
I have discovered an old laptop (DELL Latitude D620) which has ubuntu 10.10 installed on it. I would like to pass this on for recycling but wish to ensure that any personal data is wiped first.

Google searches have suggested that pressing and holding F8 or Ctrl + F11 would allow me to restore to factory settings. However neither of these approaches work for me.

Any other suggestions?

Thanks

PS I am new on this forum, have never really used ubuntu (since a brief encounter when installing on this laptop about 8 years ago) and am also technically incompetent so keep it simple please!!

---

### Post by QIII on 2018-06-26
I would suggest using [DBAN]("https://dban.org/") to wipe the drive and then send it to the recycler.

If you want a bit of extra peace of mind, remove the drive after you wipe it, use a cordless drill to put about a dozen holes in it and pop it back in.

A cutting torch adds a nice touch if you are so inclined.  :)

---

### Post by yancek on 2018-06-26
You can also use the Linux shred command if you have another Linux system available.

---

### Post by HermanAB on 2018-06-26
It depends on how paranoid you are.  You could simply overwrite the whole disk with zeroes or random numbers.  Boot from a Linux install CD/memory stick and use the good old kitty:
# cat /dev/zero > /dev/sda

However, since late last century, all disk drives have the ability to self erase.  This feature not only overwrites the tracks, but also overwrites the area between the tracks.  This secure self erase feature can be activated by the hdparm command.  The only problem is that it is incredibly slow.

Other methods using shred/dban are effectively the same as using cat as described above.

Arguably the most fun way to erase a drive is with a medium sledge, or a .308...

---

### Post by jamiefromedinburgh on 2018-06-26
Thanks for the speedy responses guys - much appreciated! My technical incompetence may be about to show I'm afraid - sorry.

I don't have any linux install cd or memory sticks, my internet security does not seem to like DBAN and I have no idea if I have another LINUX system available to allow me to use the shred command (I don't understand how to apply a command either). That only leaves the various drilling and sledge hammering options. If one of the earlier options is simple without added extras then can you provide a dummy's guide of instructions for me.

Sorry for the techy ignorance - I did warn you!!!

---

### Post by Holger_Gehrke on 2018-06-26
Your internet security doesn't like dban.org because the certificate they use for https connections has expired yesterday. But since the download is on [sourceforge]("https://sourceforge.net/projects/dban/") anyway, you can just use that link ...

Holger

---

### Post by Hadaka on 2018-06-26
Hi try these simple ommands
here is a couple links that will help explain the commands.
* Check disc size and [COLOR=#ff0000]label[/COLOR]
[https://www.tecmint.com/how-to-check-disk-space-in-linux/](https://www.tecmint.com/how-to-check-disk-space-in-linux/)
```
df -h | awk '/sd/{print$1}'
```
*wipes the drive
[https://teachmelinux.com/how-to-wipe-hard-drives-with-dd-command-in-linux/](https://teachmelinux.com/how-to-wipe-hard-drives-with-dd-command-in-linux/)
```
dd if=/dev/urandom of=/dev/sda1
```

*Note-it takes time for the drive wipe--possibly hours.

---

### Post by jamiefromedinburgh on 2018-06-26
Thanks for all your help.

---

