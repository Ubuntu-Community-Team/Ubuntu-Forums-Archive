---
title: "Is this right? This is frustrating"
date: 2007-12-20
forum: General Help
---

### Post by benniebrown07 on 2007-12-20
i copied this post from another thread but I have another question. When I follow this process am I supposed to copy it exactly how I see it or am I supposed to substitute some thing for something else (I.e backupmovie/ for .mydvd? ) Heres the post:

Re: DVD burning 

--------------------------------------------------------------------------------

Quote:
Originally Posted by jasrog 
Is there a command available to install something in ubuntu that decrypts dvd's so I can back-up my dvd movies? 

Install dvdbackup from the repository.

Then insert your DVD movie in the drive and type this in the terminal:

dvdbackup -i /dev/dvd -M -o dir/

This will backup the whole DVD movie with extras and menus, etc. You might want to have a Dual layer burner for this too. It will put the backup in the directory that you put in place of dir/. example: dvdbackup -i /dev/dvd -M -o backupmovie/

After it finishes this then insert your blank DVD disc into the drive and type from terminal:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video dir/

example using the backupmovie/ directory that contained my backup would be:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/

The dvdbackup command will put into the backupmovie/ subdirectory the disc title of the movie. So be sure to include that at the end of the growisofs command. Such as:
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video backupmovie/GHOST/

This works great, and I can backup my DVD movies with way even dual layer movies.

---

### Post by igknighted on 2007-12-20
If you want a GUI app there are plenty that work well... k9copy and dvd::rip come to mind.

If you want to learn more about the syntax of the specific command you mentioned, try typing 'man dvdbackup' or 'dvdbackup --help'.

I've never used that one myself so I cannot comment on it specifically.

---

### Post by ~LoKe on 2007-12-20
```
sudo apt-get install dvdbackup
cd ~/ && mkdir dvdbackup
dvdbackup -i /dev/dvd -M -o ~/dvdbackup ## replace /dev/dvd with the device name
growisofs -speed 1 -dvd-compat -Z /dev/dvd -dvd-video dvdbackup/moviename ## replace /dev/scd0 again, replace moviename with the folder created in ~/dvdbackups this it for burning the DVD
```

If /dev/scd0 was your device, and "GHOST" was the name of the movie...this is what it would look like.

```
sudo apt-get install dvdbackup
cd ~/ && mkdir dvdbackup
dvdbackup -i /dev/scd0 -M -o ~/dvdbackup
growisofs -speed 1 -dvd-compat -Z /dev/scd0 -dvd-video ~/dvdbackup/GHOST
```

You could make a couple scripts, one for each of the two steps (remember to change the folder and device names if necessary):
> echo "dvdbackup -i /dev/scd0 -M -o ~/dvdbackup" > dvdrip && chmod +x dvdrip && sudo mv dvdrip /usr/bin/
> echo "growisofs -speed 1 -dvd-compat -Z /dev/scd0 -dvd-video ~/dvdbackup/$1" > dvdburn && chmod +x dvdburn && sudo mv dvdburn /usr/bin/
So to rip and burn a DVD...

> dvdrip ## When this finishes, swap out your DVD with a blank one
dvdburn GHOST ## This burns a DVD with the movie "GHOST"

---

