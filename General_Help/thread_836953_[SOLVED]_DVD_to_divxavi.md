---
title: "[SOLVED] DVD to divx/avi"
date: 2008-06-22
forum: General Help
---

### Post by Fingers &amp; Thumbs on 2008-06-22
Greetings fellow forumites.

  I've just bought a new external hard drive and want to start the huge task of backing up all my dvd's.

  I think I want to store them as divx but I'm open to suggestions.

My main question is which apps to use, I usually try a few and decide which I prefer, but as ripping dvd's is a long process, i figured I would trust the ubuntu community to help me decide.

  So I put it to you, what should I install??

---

### Post by angryhomer17 on 2008-06-22
Before you read all this, if you'd like a quick and dirty answer for software here it is: dvd95, dvdrip, k9copy, k3b, dvdbackup.

I'm going to assume that these dvd's are bought, and if not, that they are copies (say .iso's) of the dvd. So what you are starting with is pretty much an original dvd.

Now what you are backing up your dvd's for is important. Do you want the same bit for bit dvd, do you want to burn these to discs later, are you going to be watching these on a tv, pc, from a dvd player, a ps3, how much do you care about quality? Since I'm not sure what you quite want to do I'll give a little rundown of what I would suggest for each option:

**Option #1:** You want a full backup, bit for bit, of your dvd. This allows you to have the same quality as the original dvd, with the same menus, same everything. I'd use k3b and copy the disc. K3b will make an complete duplicate of the dvd and make an .iso. For the most part dvd's are around 7 gigs. So with a 500 gig hard drive, you might get 65 or so dvds backed up.

Now, if you want to burn the iso to a dvd, it's extremely simple. Just open k3b and click on the iso and it will burn a copy for you. There is a disadvantage to doing this though. You will need dual layer dvds, which are much more expensive than single layer (say $1.50 - $2.00 per disc). I haven't heard or read anything too great about dual layer dvds. The quality usually isn't all that great and many times you may end up with coasters.

**Option #2:** Create a duplicate, that is shrunk to be able to put on a single layer disc. You can get a 100 pack at best buy or shop around at tigerdirect or newegg and get a sale of $20 or so. That amounts to $0.20 per disc which is 7 to 10 times cheaper than a dual layer disc. 

The issue with this is that you are losing quality by compressing the dvd to fit in a smaller space. Now for some movies you really won't be able to  see much difference between the compressed and the original, but sometimes it can be pretty awful. For example, I just ripped Heat, a 3 hour movie, to fit on a single layer disc. I expected the quality to suffer, but it appears to be quite similar to the original. 

Now, The Butterfly Effect, a 2 hour movie, looks horrible after it's be re-compressed. There is a ton of pixelation and graininess. 

A Simpsons dvd from season 9, compressed to fit on a single layer, worked decently. There are parts where pixelation occurs around the edges of characters and action scenes may be a bit choppy, but for the most part it's ok. 

Oh, for this option I use k9copy and sometimes dvd95. They both work pretty well, if one fails then i try the other. If they both fail, then you can try ripping an exact copy using k3b and then compressing the iso with k9copy.

**Option #3:** Ok, the first two were more if you wanted to burn to disc later. This focuses more on playing on your computer. What I used to do, when I watched most of my movies on my computer, is use dvdrip to create a backup of movies. I haven't used this in a while so this may be slightly off. Dvdrip will take a dvd and copy the main movie for you at full quality. What's nice about this is that you get the full movie, at full quality, without any menus or extras. You just open the vobs with vlc.

If I remember correctly, dvdrip will rip to 1 gig vobs. Vob's are just containers for the mpeg video. There shouldn't be any problem with renaming a vob to a mpeg and playing it on your computer. I think i just used cat to merge the vob files into a 4 gig mpeg and then another 2 or 3 gig mpeg.

So it would be something like ```
cat 1.vob 2.vob 3.vob 4.vob > a_clockwork_orange_disc1.mpeg
```

Dvdrip also supports compressing the dvd to lots of different formats. These prolly include mpeg, avi, divx, xvid, and more. It's a really nice piece of software.

**Option #4:** This would include ripping your dvd's to something like divx, xvid, avi, mpeg. I think ffmpeg can take care of some of this. Quality will suffer mcuh more, the more you compress it, but it really depends on the movie.

-----------------------------------
So, to end, you've got a multitude of options. Each of them has it's benefits and drawbacks. What your choice is depends on what you want to backup for.

I've taken to ripping using k9copy. This allows me to watch movies on my ps3 or dvd player. Sometimes the quality suffers, but I'd rather watch my movies on a bigger tv than my smaller computer screen while I'm at home.

This sucks because I really hate poor quality. Ripping an exact copy gives me full quality, but it is much harder to play on anything but a computer.

Like I said earlier, some dvds don't compress as well as others. This is partially due to the way they were transferred to dvd. Sometimes the movie is highly compressed going to dvd in the first place. So compressing it even more gives a horrible picture. Other dvd's have much more leeway. Older movies tend to do better at compression, sometimes because they weren't that great in the first place. For example, I have Psycho at 1.4 gigs divx and it's ok. For an old movie like that there isn't that much data to begin with.

Hope this helps. :)

---

### Post by Fingers &amp; Thumbs on 2008-06-22
Thank you very much for such a comprehensive reply, it made me realise I should have been clearer with my question, but then, your reply has given me a great deal of knowledge I would not have gained if I had.

Basically, I want to playback the dvd's on my laptop, with a view to putting together a media server sometime in the not too distant future, so the process of returning the movies to blank media is not really any use to me; I have no seperate dvd player or ps3 and doubt I ever will. (although a friend of mine just got a ps3 and it did make me think about it, they're pretty awesome) So, in short, they will be for pc based playback in one form or another, but your detailed answer has certainly enlightened me to any issues that may arrise in the future, since times/needs change.

Thanks once again, I think I'll give dvdrip, or is that dvd::rip a try.

---

### Post by cariboo on 2008-06-22
Actually angryhomer17 forgot one. Acidrip, I like it because you can pick the quality you want the output file to be. It is in the repositories and yu can use synaptic to install it.

Jim

---

### Post by Nepherte on 2008-06-22
I always use this guide: [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)
Very good compression quality (x264, MPEG-4 that is) and the possibility to add several audio and subtitle tracks into one file.

---

