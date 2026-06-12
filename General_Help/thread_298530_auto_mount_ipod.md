---
title: "auto mount ipod"
date: 2006-11-11
forum: General Help
---

### Post by terranz on 2006-11-11
I had my beloved iPod mini stolen an little while ago and now have a 2nd gen 4gb nano.

My problem is it doesn't come up in Ubuntu.  I even tried it in suse 10.1 and nothing showed there either.

About an hour ago I thought it had worked but when I double clicked on the drive icon I was shown errors which I was unable to copy.

The errors said something about error mounting sda and filesystem errors

My system is a fully updated install of dapper

---

### Post by terranz on 2006-11-12
I've followed some instructions which let me mount sda2 (the data partition) but this is like a step backward in linux history.

I would like it to pop up onto my desktop like a usb drive or my old mini.

any ideas?

how does ubuntu automount USB drives?

---

### Post by terranz on 2006-11-12
Below are two posts by me made to the hardware forum which got me 0 replies.  Maybe this is a better place to ask the question.

---------------
I had my beloved iPod mini stolen an little while ago and now have a 2nd gen 4gb nano.

My problem is it doesn't come up in Ubuntu. I even tried it in suse 10.1 and nothing showed there either.

About an hour ago I thought it had worked but when I double clicked on the drive icon I was shown errors which I was unable to copy.

The errors said something about error mounting sda and filesystem errors

My system is a fully updated install of dapper

******************

I've followed some instructions which let me mount sda2 (the data partition) but this is like a step backward in linux history.

I would like it to pop up onto my desktop like a usb drive or my old mini.

any ideas?

how does ubuntu automount USB drives?

---

### Post by aysiu on 2006-11-13
I think people aren't answering because they don't know what the problem is. For most of us, you plug in the iPod or device, and it just shows up.

It may seem like a step backwards, but it's better to set it up to automount than to not have it mount at all.

This should help--plug in the iPod first, though:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The instructions are for Windows partitions and drives, but if the iPod is FAT32 or NTFS, the same principle should apply, and if you mount it inside the /media directory (say, to /media/ipod), it will show up as an icon on your desktop.

---

### Post by deeptingler on 2006-11-13
check out this thread which helped me...

[http://www.ubuntuforums.org/showthread.php?t=268550&highlight=ipod+nano+2g](http://www.ubuntuforums.org/showthread.php?t=268550&highlight=ipod+nano+2g)

---

### Post by terranz on 2006-11-13
> It may seem like a step backwards, but it's better to set it up to automount than to not have it mount at all.

Automount is what i want :) 
I meant manual mount was a step backwards.

Thanks for the replys

---

### Post by nipun_jain on 2006-11-14
Well, I just plugged in my iPod nano, second generation intu edgy and it got auto detected rythmbox opened up recognised all the playlists. I even have an iPod icon on my desktop. So it seems that iPod nano 2g does automount. What I did before plugging in the ipod was to search for "ipod" in synaptic and install a few things like ipod identifier. You should try that and get back to us whether it worked or not.

---

### Post by terranz on 2006-11-14
I will post an account as soon as I try these things out.

---

