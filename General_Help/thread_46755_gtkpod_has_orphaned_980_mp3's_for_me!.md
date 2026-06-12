---
title: "gtkpod has orphaned 980 mp3's for me!"
date: 2005-07-06
forum: General Help
---

### Post by aussieskin on 2005-07-06
Okay I am about to cry..well no I am past crying now....but here is my problem

I recently (about a week ago) gave windows the sack and employed linux ubuntu instead...so far I have had many headaches,although most of them are getting fixed, my latest problem is my iPod...

I installed Grip and finally got it working with Lame to convert my cd's to mp3's (which is working ok, although about a million times slower than itunes did it on windows)
Then I got GTkpod working, and finally got it to read my ipod. I then copied one new CD onto the ipod..unmounted the ipod...plugged in my headphones to test it and it was all good! Until I then plugged my ipod back into the computer and copied another CD onto it.....I thought that worked, although when i unmounted the ipod and tried to listen to it all my music had gone....

So I replugged back in the ipod to the computer and had a look in gtkpod where I found the option to 'check ipod's files' which I did, and alas it has shown my entire music collection as 'orphaned'....But I cant actually access them through my ipod. I copied them all to my hard drive but they still arent showing up on my ipod...grrr

Now I am at a loss at what to do....I thought about deleteing the files form my ipod and then just copying them across again from my hard drive, although I'm not convinced that the files on my hard drive have all the artist and album details saved with them....

any help on this would be awesome.... thanks!

---

### Post by daageep on 2005-07-08
caveat: i'm not the most experienced user but this worked for me.

i have never gotten gtkpod to work properly. it uploads my songs onto the right places (itunes/music/f00 or something like that), but my ipod does not detect them. they get "orphaned" when i scan with gtkpod.

i *think* the problem may be that gtkpod is not writing the song info on the itunes database file, which i think tells the ipod what mp3s to play. i think the itunes database file may be picky on what program messes with it. 

so i tried using gnupod and had success transferring files onto the pod. strangely, only half the files would play when i tried. but after testing the gnupod-uploaded songs, i remounted the ipod and used gtkpod to see what was happening. then i noticed that on the left playlist column, instead of "gtkpod" playlist it was a gnupod playlist. from there, i could upload all the files I wanted and they would work.

i tried this method for the entire day and it worked for me. i did a fresh recover (formatting the ipod) with the ipod updater, tried uploading songs with gtkpod, ipod did not see the songs. i formatted again, used gnupod to add the gnupod database file and uploaded one song with gnupod, then wrote to the gnupod database file. i umounted the drive and mounted it. in gtkpod, now the playlist reads gnupod, and all the uploads with gtkpod work perfectly.

i suspect the itunes database file does not work too well with gtkpod but this is just a guess. however gtkpod works better with the gnupod database files and writes onto it properly.

---

