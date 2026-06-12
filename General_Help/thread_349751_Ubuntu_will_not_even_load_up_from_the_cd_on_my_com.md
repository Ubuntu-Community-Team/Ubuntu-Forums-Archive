---
title: "Ubuntu will not even load up from the cd on my computer!"
date: 2007-01-30
forum: General Help
---

### Post by dtwazere on 2007-01-30
Hi guys,

Im currently running xp and ive decided its time for an upgrade to vista. I saw a lot of fuss on the bbc website about linux and ubuntu so ive come to give it a try before i fork out a few hundred pounds for vista.

I downloaded a copy of ubuntu, put it in my drive and select the first option, it shows the loading screen then after 1 minute, the bar stops and just dissapears and stays blank.

Ive tried that safe graphics mode as well.

Please help guys i really like the look of ubuntu!

---

### Post by qamelian on 2007-01-30
> **dtwazere said:**
> Hi guys,

Im currently running xp and ive decided its time for an upgrade to vista. I saw a lot of fuss on the bbc website about linux and ubuntu so ive come to give it a try before i fork out a few hundred pounds for vista.

I downloaded a copy of ubuntu, put it in my drive and select the first option, it shows the loading screen then after 1 minute, the bar stops and just dissapears and stays blank.

Ive tried that safe graphics mode as well.

Please help guys i really like the look of ubuntu!
The first step is to provide as much detail as you can about your hardware. Once you've done that maybe some on the forum can give you some advice.

---

### Post by dtwazere on 2007-01-30
Ok,

I have a dell dimension 8400 desktop
I have 1gb of ram
I have a radeon x1650 pro 
a soundudigy blast (i think thats how you spell it)
intel pentium 4 3.ghz

hope that helps,

i just tried re burning a copy of that cd and i get the same problem

---

### Post by floke on 2007-01-30
It could be...

(a) You are trying to install using the wrong disc - did you get the i386 version?
(b) The disc download might have errors on it. This happened to me for my first 2(!) discs, since you are downloading a lot of data. There are various checksums that can test whether the disc was been burned correctly, but to be honest I've no idea how to run them in Windows (in Ubuntu though its easy!). So - I would download the i386 ISO image again. Then burn it on slow speed and try again.
(c) If this fails try downloading a copy of the alternative install CD - this is an installer without the LiveCD features.

I've been watching the Vista hoo-ha all day and can't help thinking that if only people knew - IF ONLY THEY KNEW - how absolutely vaaaastly superior Linux/Ubuntu is then MS would be dead in an instant. Flip 3D is a poor, poor toy compared to Beryl; the security is nothing compared to Linux; and the cost you know about yourself.

So - please don't give up on this. Try the steps above. There are plenty of other people in this forum who will be happy to help out if you have trouble. 

At the end of the day, what have you got to lose?

---

### Post by jimbob on 2007-01-30
Did you verify the md5sum on the iso you downloaded before burning the CD?

  Try downloading and burning the alternate CD and see if that works any better for you.  There have been some reports of problems with the live/install CD.

Also, try burning at a very slow speed - maybe 4x and see if the CD comes out any better.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by dtwazere on 2007-01-30
thanks for the message,

ill try what you have mentioned and get back to you with it tommorow, i just came to this website on the off chance that linux would be better than vista and i am very impressed and i dont even have it working yet!

Im not going to give up on ubuntu easily, now that i have seen the price for ultimate vista!

The only thing i have to lose is time and i have plenty of it ;)

Just one thing, will the alternate let me run it live without installing it as i am not ready to possibly wipe out my installation of xp yet!

---

### Post by wesley_of_course on 2007-01-30
Wesley here ; Yes ! Enjoy  and Welcome !

---

### Post by dtwazere on 2007-01-30
checked the checksum it matches b950a4d7cf3151e5f213843e2ad77fe3.

im going to see if it will run on microsoft virtual pc

---

### Post by dtwazere on 2007-01-30
it works in virtual pc,

will this alternate version allow me to dual boot with xp just in case i need to?

it wont overwite my instllation of xp will it?

---

### Post by floke on 2007-01-30
Well, I didn't do it that way so have no real idea what the alternative installer looks like. But, a quick browse on line shows that you can dual boot from it - although the partitioning might be trickier since it's text based.

See here for instance: [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
(although this is for an older version - but it clearly shows you can dual boot - just that you have to manually edit the partition table to do so).

One other way around this would be to download an ISO of Knoppix - which is designed to run from a LiveCD rather than be installed. From this you could use the GParted tool to partition your hard drive through a graphical interface, then use the alternative installer to put Ubuntu on the space you've just made.

I'd do a bit of research on installing from the alternative version first though, so that you know what's going on.

Best of luck, and let us know how it goes!

Oh yes, and Welcome to Ubuntu!

---

