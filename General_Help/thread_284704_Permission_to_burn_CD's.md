---
title: "Permission to burn CD's???"
date: 2006-10-26
forum: General Help
---

### Post by MyNameUhBorat on 2006-10-26
I'm trying to burn an iso in GnomeBaker and I keep getting this error message


Error trying to open /dev/sg0 exclusively (Permission denied)


I tried a music CD and got the same message. I've burned discs before and never had this problem. Any suggestions and/or fixes?

---

### Post by taurus on 2006-10-26
You probably need to belong to group cdrom to use (burn) it.  Do you see your name on it with this command from a terminal?

```
id
```

---

### Post by MyNameUhBorat on 2006-10-26
Here's what I get. My name isn't in front of cdrom

uid=1000(jeremy) gid=1000(jeremy) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(jeremy)

I really appreciate your help taurus.

---

### Post by Spano on 2006-10-26
You can use this command to add yourself to the group
> sudo adduser jeremy cdrom
but it looks like your all ready a member. Not postive so try the command.
You could check your /etc/fstab file.  The line for cdrom should look something like this:
```
/dev/hda      /media/cdrom0   udf,iso9660  user,noauto  0  0
``` 
"user" being the key word in that line.
You could also try opening GnomeBaker from terminal as root and user and note any error messages.
```
sudo gnomebaker
```

---

### Post by MyNameUhBorat on 2006-10-26
hmm wierd all I had to do was type sudo gnomebaker, and I was able to burn something. Very strange. How do I make it, so I don't have to use the terminal every time?

---

### Post by Spano on 2006-10-26
Don't know.  I checked google and found refrences to similar problems.  Something to do with udev and /dev/sg0 ,but were beyond my experience.  
I would add a custom application launcher to the menu using System> Prefrences> Menu Layout
with the command to launch being
```
gksudo gnomebaker 
```
Then keep your eye on the forum to see if others are having the same problem.  Good luck.

---

### Post by MyNameUhBorat on 2006-10-26
Thanks a lot man I really appreciate your help. I don't seem to have permission to a lot of things, like adding files to my external hard drive etc. Really strange, this permission denied thing only started yesterday. Very strange.

---

### Post by Spano on 2006-10-26
Your welcome.  Hopefully these are bugs that will shake out over the next couple of weeks.

---

### Post by pampa on 2006-10-26
That is because you are running gnomebaker as the system administrator (root) and of course this user has access to all the hardware.

---

### Post by eradicator_006 on 2006-10-26
> **MyNameUhBorat said:**
> I'm trying to burn an iso in GnomeBaker and I keep getting this error message


Error trying to open /dev/sg0 exclusively (Permission denied)


I tried a music CD and got the same message. I've burned discs before and never had this problem. Any suggestions and/or fixes?

Same problem here when trying to burn cds.  Funny thing is, I can burn dvds fine using gnomebaker.

---

