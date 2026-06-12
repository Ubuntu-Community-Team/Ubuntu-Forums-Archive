---
title: "Play older real streaming files"
date: 2008-05-26
forum: General Help
---

### Post by petunia50 on 2008-05-26
Hello,
I would like to play an audio stream from the archive of a show called 'Science Friday'. It is the radio communication record between the crew of Apollo 13 & mission control in Houston.
It was first broadcast on April 14, 2000. I have real player 11 installed & it won't play this older file: 20000414.totn.02.ram

The file is located at:
[http://www.sciencefriday.com/pages/2...r2_041400.html](http://www.sciencefriday.com/pages/2...r2_041400.html)


Will someone tell me if it is possible for me to listen to this?
Thank You:confused:

---

### Post by drs305 on 2008-05-26
When I tried opening it the site reported it was a bad link:
[http://www.sciencefriday.com/pages/2...r2_041400.html](http://www.sciencefriday.com/pages/2...r2_041400.html)

This link does take me to a page but I think it's an author talking about his book. I searched for 'Apollo 13' and also 'April 14, 2000' but didn't find the audio of the actual transmissions.
[http://www.sciencefriday.com/pages/2000/Apr/hour2_041400.html](http://www.sciencefriday.com/pages/2000/Apr/hour2_041400.html)

---

### Post by petunia50 on 2008-05-26
Sorry,
This url should work.  I just tried it.

[www.sciencefriday.com/pages/2000/Apr/hour2_041400.html](www.sciencefriday.com/pages/2000/Apr/hour2_041400.html)

The real audio is near the bottom of the page.  Not the first link, that is Mission controller Gene Krantz discussing his book.  Farther down the page is says: listen in real audio".
My apologies.

---

### Post by drs305 on 2008-05-26
Okay, I just installed the latest version of linux realplayer, RealPlayer 11. When I tried to play the file, it said I lacked the lpcj component. A brief internet search indicated that the latest versions of realplayer won't play those any longer and don't support it. I can't verify that but can state that the current version won't. I could not find any updates or add-ons in the brief time I've been looking.

However: I did find a site which has older linux versions of realplayer and one user indicated that he installed realplayer 8, which supports lpcj, and was able to run the older files. 

The address for the older versions is:
[http://forms.real.com/real/player/blackjack.html](http://forms.real.com/real/player/blackjack.html)

Good luck.

Added: I just looked at the site and RP8 is available as an .rpm  If you haven't installed an rpm  package before, install alien, a program that will convert it to a deb file for easier installation.

---

### Post by petunia50 on 2008-05-27
Okay.
I followed the link to the legacy versions of real player.  I saw the rpm file & also the .bin version.  I had previously used the installation instructions from the current version of real player to install real player11 from a.bin & tried to use those instructions to install rp8, but I didn't have any luck.  this is getting a bit beyond my level of technical skill.
Thank you for your help.  Btw, how do I send a thank you so that will show up in your thanks tally?

---

### Post by drs305 on 2008-05-27
> **petunia50 said:**
> Okay.
I followed the link to the legacy versions of real player.  I saw the rpm file & also the .bin version.  I had previously used the installation instructions from the current version of real player to install real player11 from a.bin & tried to use those instructions to install rp8, but I didn't have any luck.  this is getting a bit beyond my level of technical skill.
Thank you for your help.  Btw, how do I send a thank you so that will show up in your thanks tally?

I tried downloading the rpm, but as you found out, only a bin file was available. I tried executing it but received error messages. I installed a few extra development packages but still couldn't get it to install. If I come up with some other way I'll post back.

Since you asked, 'thanks' are conveyed by clicking the gold star/ribbon in the lower right of the writer's post ...

---

### Post by drs305 on 2008-05-27
Update:[http://ubuntuforums.org/images/rank_7.png](http://ubuntuforums.org/images/rank_7.png)

The reason I got the errors was because I am running a 64-bit system and this file needs some 32-bit libraries. I finally got RP8 installed. I had to manually type the url into the location bar - it wouldn't cut & paste ([http://www.npr.org/ramfiles/totn/20000414.totn.02.ram](http://www.npr.org/ramfiles/totn/20000414.totn.02.ram)). It connected and I thought I had achieved success -- but no. It opened the location, identified the file, but then just sits there with the buffering message and 0:00/47:24.6  However, I WAS able to find a 1999 file on the same site and, after a delay, IT PLAYED - so there might be a problem with that particular link. The link that sucessfully played had a .01.ram ending, while yours and another with a .02.ram ending did not. That should just be coincidence.

If you want to try it yourself and have a 32-bit system:
Change to the directory in which you downloaded the bin file. Hint: in terminal, you only have to type the first few letters of the file and then can hit the tab key to autocomplete the entry. So type "chmod u+x rp8" and then hit tab to complete.
```
chmod u+x rp8_linux20_libc6_i386_cs1.bin
```


Next, you have to install some extra libraries. You won't know which one until you get the install error. So start the install (same tab technique):
```
./rp8_linux20_libc6_i386_cs1.bin
```

Look at the installation error message the first time you run the install. Go to synaptic and install the correct library for the missing .so I think I used libxml++2.6c2a-dev  It may be different on a 32-bit system. 

Then try the install again. At this point, I was successful it getting it installed and running but it never got past buffer. 

If you want more help just let me know. It's becoming an obsession!!!

---

### Post by drs305 on 2008-05-27
One hour later...

I just left the NASA link buffering in RP8. One hour later, it started playing. (I have a 6.0 DSL connection, so it wasn't delayed on my part!)

I'm listening to the interview right now. :-D

---

