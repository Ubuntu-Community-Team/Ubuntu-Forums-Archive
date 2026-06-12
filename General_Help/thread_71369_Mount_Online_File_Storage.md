---
title: "Mount Online File Storage"
date: 2005-10-03
forum: General Help
---

### Post by andrewsawyer on 2005-10-03
I'm not sure what section this thread should be in, so if it is in the wrong section, please feel free to move it.

I have a domain, with 300mb of hosted space.  I only use about 3mb of that for my website, and I would like to use the rest as file storage.  Logging onto the server via firefox takes me to a standard cPanel page (not sure if that relates, but thought I'd mention it anyway).  Now, I'm not sure if this is possible or not, but could someone please tell me if:

1. It is possible to mount (as a directory in /media or /mnt) an online (not on my local network) file storage space, to allow a drag and drop facility to the remote server?

2. If Q1 is possible, is there a facility in Ubuntu to allow it to auto-sync (backup) my /home directory with the online server each night?  I hear you saying "cron-job", but I don't know much about them or how to set them up - let alone how to specify what they do.  If it is a cron-job issue, could someone explain how I might go about doing this?

3. Also, while backing up, I would prefer that it only backed up changed items - I'm using Bigpond ADSL, and I get capped to 64kb after 10Gb (total up or down), so I would prefer not to have a file in my home drive uploaded again and again if it's not been altered since last upload.

This may be simple, or it may be tricky.  If anyone could point me in the right direction, it would be much appreciated.

---

### Post by 23meg on 2005-10-03
1. if you have FTP access to your server (which is very likely), you should be able to do it with Places / Connect to server. someone correct me if i'm wrong, but that should be it; i've never tried it though.

2 + 3. it is a cron job + bash script affair. you can probably find readily written bash scripts that will do this for you if you google a bit, and with some slight modifications you should be set. actually you can do it from scratch as well with minimal bash knowledge; just type "man rsync" and you'll have gotten the ball rolling :)

---

### Post by rcerreto on 2005-10-03
Re Q1. That's pretty easy as long as you can have something useful running on the server side. Samba or NFS are the most common.
Beware of security issues, you could consider tunnelling via ssh:
[http://www.math.ualberta.ca/imaging/snfs/]("http://www.math.ualberta.ca/imaging/snfs/")
[http://www.ibiblio.org/gferg/ldp/Samba-with-SSH/Samba-with-SSH.html]("http://www.ibiblio.org/gferg/ldp/Samba-with-SSH/Samba-with-SSH.html")

Re Q2/Q3. Consider using rsync.

---

### Post by andrewsawyer on 2005-10-03
Fantastic guys - thank you.

I thought it would be a matter of bash prompts and all sorts.  I was getting ready for a whole heap of typing!

Thank you.

---

### Post by 23meg on 2005-10-04
you're welcome. so how's it going? did you try these out?

---

### Post by andrewsawyer on 2005-10-04
Going well actually thank you.

I've got it configured so that I can drag and drop.  I've not set up the cron-job yet, but I will get there.  Quick question though:

When I log into the hosted site, I get all the usual directories - mail, cgi-bin, public_html etc.

Now would it be more secure to create a directory here called backup and put everything into it (not in public_html), or should I put it in the public_html in a directory called backup, and password protect it?  I'm not bothered about accessing it from elsewhere (other than my laptop).  It is more of a backup incase of possibility of fire or my house getting turned over by a thief while I'm away.

If you could give me some suggestions on the merits/issues with both, it'd be appreciated.

---

