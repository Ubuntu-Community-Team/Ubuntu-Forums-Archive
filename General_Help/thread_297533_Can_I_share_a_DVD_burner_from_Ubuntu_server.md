---
title: "Can I share a DVD burner from Ubuntu server?"
date: 2006-11-11
forum: General Help
---

### Post by edmicman on 2006-11-11
I have a spare PC running ubuntu server as a file server. My primary machine is a winxp laptop, and I've cannibalized my old desktop for various other projects.

I have an internal NEC ND-3550A DVD burner that I need to use to burn something. Is it possible to put that drive in my ubuntu server, share it, and be able to use it from the XP laptop? If so, how?

I'm thinking it would be easier to put it in the linux server that to try and scrape up the parts to rebuild an xp desktop, possibly reinstall windows, etc. Thanks for any help or advice!

---

### Post by Spano on 2006-11-11
Out of curiosity I gave this a try.  My set up is CD-CDRW on Ubuntu server and Windows XP desktop connected on Samba network.
I un-commented these items from /etc/samba/smb.conf
```
[CODE]# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
```[/CODE]
Windows could see the share and I was able to map to the drive.  Nero software could see the drive as well, but I was unable to set it up as a destination drive for burning.  I gave up after a half hour.  Maybe with some tweaking of the smb.conf and a reading of the Nero docs?:-k

---

### Post by 13ojo on 2006-11-11
just out of curiosity,

wouldn't there be a command line utilty for burning .isos?

If so my idea would be

1)connect to server (SSH?)
2) apt-get install "this program"
3) copy file from laptop to server OR find path to access from server
4) run program with params to burn cd


I would think this is possible, but maybe im wrong

PS. looking through repositories a utility called CDW will burn cd's from the command line, not sure about DVD's.

I know this isn't exactly what you wanted, but its better than rebuilding a pc.

---

### Post by edmicman on 2006-11-11
Thanks for all the info!  Bascially, I didn't want to open up the server, put the drive in there, and try and struggle through configuring it if it couldn't be done in the first place.  

THe program in question is actually "ProShow Gold", though Nero would be nice, too.  It's a slideshow program that lets you burn a slideshow to a DVD movie, which will be perfect for my wedding in a a week :-D.  However, like I said, the DVD burner isn't on my laptop.  I don't know if ProShow will burn to an ISO or not - I have successfully booted with an ubuntu livecd and burned a DVD iso before, so I know that works.

I'll look into the sharing of the drive some more...I wonder if I can point ProShow to another drive.....I'll keep you posted with any results!

---

### Post by edmicman on 2006-11-11
Just wanted to give an update....

I played around on the server and shared the existing CDRW via samba.  Like the earlier post, I could see the share, but I couldn't make any "burning" program actually try and use it.  Google searches didn't turn up much either.  

It turns out ProShow Gold *can* create a DVD iso...so my next step was to recreate my barebones PC - reassemble the motherboard, put the DVD burner along with another CD drive to boot from, and see if I could boot via the ubuntu livecd, create the iso file, and burn it across the network.  

However, creating the ISO file on my laptop is slow anyway, and then messing with burning the iso on a different PC, etc....it's just, eh, a pain.  So I'm throwing XP on a spare drive on the desktop with the DVD burner drive; it won't have as much running, and I'll just install my slideshow software on there, work with it on there, etc., and just be done with it.  Bleh.  Anyway, thanks for all the help and advice nonetheless!

---

### Post by Spano on 2006-11-11
You probably don't have time to puzzle it out, what with the wedding and all.
Congratulations

---

### Post by 13ojo on 2006-11-12
Well you found a solution, thats whats important.

Congratulations and good luck with your wedding!

---

### Post by NorthCoast on 2006-11-12
This should work:
[http://joerghaeger.de/webCDwriter/](http://joerghaeger.de/webCDwriter/)

I use this on a CentOS server from any linux/windows/java client.  It should work on Ubuntu.  Hint, get writing working smoothly on the server as normal first and then doing it over the net is easy.

---

