---
title: "mount - Just one more step and we've got this!"
date: 2014-05-17
forum: General Help
---

### Post by lile001 on 2014-05-17
I'm about a step away from having a convenient hack, but can't quite wrap my brain around the right steps.  This will be easy for someone who knows his or her stuff. 

OK, I have a second hard drive, that I like to point to a folder under my /home directory.  Right now, I am using two manual steps to accomplish this:

1.  Open Nautilus, click on Bigdrive1, which mounts it. 

2. execute this command in a terminal
```

$ sudo mount --bind  "/media/lawrence/Bigdrive1/larry" "/home/lawrence/Bigdrive"
 
```

OK, now I have a giant hard drive inside my home folder.  Cue the maniacal mad scientist laughter.  

I'd like my brainbox to do this at boot, so I don't have to do it manually.  

Now here is a bit more info:
after clicking on the name of the drive in Nautilus and mounting Bigdrive1 via gui, I can see this:
```

$ mount  
/dev/sdb1 on /media/lawrence/Bigdrive1 type ext3 (rw,nosuid,nodev,uhelper=udisks2)


```

I keep reading pages about mount and other related stuff (Yeah, I RTFM'd but didn't grok TFM.) and come away with a spinning head.  I don't quite know enough to string that info together and get this all to happen automagically at boot.


/Edit

[This thread ]("http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up")has some useful stuff about startup scripts, including an interesting note about using crontab at reboot.  One more hint, but I still can't quite string it all together.  

```
[COLOR=#333333][FONT=UbuntuRegular]One approach is to add an @reboot [cron]("http://en.wikipedia.org/wiki/Cron") task.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Running crontab -e will allow you to edit your cron.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Adding a line like this to it:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]@reboot /path/to/script[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]will execute that script once your computer boots up.[/FONT][/COLOR]
```

/Edit

And yes, I have a little script called mountbigdrive.sh all ready to go if I can figure out where to put it to make things click when I reboot.

---

### Post by tgalati4 on 2014-05-17
If you always want this mount, then simply put it in /etc/fstab (file system table).

Spend some time here:  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by bazsound on 2014-05-17
fstab is the easiest way to get stuff to mount @ boot, im too like you though and get a headache reading through the nfo. personally i just stick with the /media folder.


Create a directory there and add it to fstab, just make sure you format it right and use the right options, you should be able to find a guide by googling. and if yoiu really want to mount it inside home then just change the mount point to where your folder is for it

---

### Post by lile001 on 2014-05-17
FSTAB!  OK, now the light is going on.  I'll look into that and get back to you folks when next my brain becomes fuddled.  Won't be long.

---

