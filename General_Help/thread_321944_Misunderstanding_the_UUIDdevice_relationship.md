---
title: "Misunderstanding the UUID/device relationship"
date: 2006-12-19
forum: General Help
---

### Post by jimbob on 2006-12-19
Well I thought I understood this UUID thing but now I'm back to square one.

My Edgy installation which was working fine a couple of weeks ago (haven't booted it for a while)  stopped mounting the swap partition which hasn't changed in fstab at all.

I noticed that the UUID in fstab differed from the one listed in /dev/disk/by-uuid.  I saw a reference to this in an earlier post but I can't find it now.

The cure was to substitute the one in by-uuid for the one in fstab.  Joy again.

How can this happen?  Does this list get regenerated each time I boot or what?  If so, then why didn't any of the others change?

My swap partition is used by either Dapper, Edgy or Feisty - whichever one I have booted at the time but that shouldn't make any difference in my way of thinking.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by hikaricore on 2006-12-19
I'd love to know how this works also, as I've modified/moved/resized every partition on my system I no longer have any UUIDs in edgy lol.  fstab is pointing at nothing but /dev points like it's supposed to be.  But the mystery still compells me to ask wtf?

---

### Post by bodhi.zazen on 2006-12-19
> **jimbob said:**
> Well I thought I understood this UUID thing but now I'm back to square one ....  

LOL

I assume you re-formatted the swap partition as that is the only way I know of the uuid would change.

You can use /dev/hdxy in fstab rather then uuid if you like.

To list your partitions by uuid: ```
ls /dev/disk/by-uuid -lh
```

Hope this link helps : [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

---

### Post by bodhi.zazen on 2006-12-19
> **hikaricore said:**
> I'd love to know how this works also, as I've modified/moved/resized every partition on my system I no longer have any UUIDs in edgy lol.  fstab is pointing at nothing but /dev points like it's supposed to be.  But the mystery still compells me to ask wtf?

See if this helps:

[How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by hikaricore on 2006-12-19
> **bodhi.zazen said:**
> See if this helps:

[How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

I'm just going with "you misunderstood my post" and drop it at that.  Thank you for the links prior to the post I'm replying to, they explained UUIDs properly so that if I feel so compelled to correct my fstab file which I'm very familiar with, I'll be able to do so.  :P

---

### Post by bodhi.zazen on 2006-12-19
> **hikaricore said:**
> I'm just going with "you misunderstood my post" and drop it at that.  Thank you for the links prior to the post I'm replying to, they explained UUIDs properly so that if I feel so compelled to correct my fstab file which I'm very familiar with, I'll be able to do so.  :P

LOL hikaricore :lol: 

Hey, no offense intended, but you know it is hard to "guess" someone's knowledge base or how to best enlighten the situation. For some reason I assumed you were asking about fstab.

As you say, fstab is soooo yesterday :(

now you can uuid with the geeks of today :twisted:

---

### Post by hikaricore on 2006-12-19
> **bodhi.zazen said:**
> LOL hikaricore :lol: 

Hey, no offense intended, but you know it is hard to "guess" someone's knowledge base or how to best enlighten the situation. For some reason I assumed you were asking about fstab.

As you say, fstab is soooo yesterday :(

now you can uuid with the geeks of today :twisted:

Lol none taken, I'm just grumpy.

Manually scanning in hundreds of people's photos and putting them on merchandise for the christmas rush is numbing.

Thanks again for the info tho. >.<

---

### Post by bodhi.zazen on 2006-12-19
> **hikaricore said:**
> Lol none taken, I'm just grumpy.

Manually scanning in hundreds of people's photos and putting them on merchandise for the christmas rush is numbing.

Thanks again for the info tho. >.<

Ahhh yes,

Can't wait for the post holiday "lost my receipt returns rush" myself :p

---

### Post by jimbob on 2006-12-20
> **bodhi.zazen said:**
> LOL

I assume you re-formatted the swap partition as that is the only way I know of the uuid would change.


  I haven't touched that partition since it was created over a year ago. 

Obviously there is another way unbeknown to all of us that is occurring.

Back later with some more observations and hopefully some answers.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

