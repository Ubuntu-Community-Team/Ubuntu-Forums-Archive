---
title: "rip entire website"
date: 2006-12-02
forum: General Help
---

### Post by sekcon on 2006-12-02
what would be the best way to rip an entire website from within ubuntu? 
i need it to be able to rip sites that have usernames and passwords aswell.
someone told me to use wget (i think) but not sure how to use it, can anyone tell me how to use it if thats what i should use?

thanks guys..

---

### Post by Cronjob on 2006-12-02
You can't get any better than wget.

If you want something with a fancy interface, you can use [httrack]("http://www.httrack.com/"). I don't recall if httrack uses wget or not.

If you want to use wget, you should read through the man page for it as it wields enormous power, but can sometimes be a little complex. It's one of the best tools you'll ever take the time to learn, though.

You'll specifically want to use the following options. You can also find options to change the reported user-agent if needed as well as handling cookies.

**--http-user**
** --http-passwd**

---

### Post by Eddy Dean on 2006-12-02
That's illegal. I don't think we're allowed to discuss something like this on these boards.


Greetz,
Eddy Dean

---

### Post by Cronjob on 2006-12-02
No, there's nothing inherently illegal about downloading a website or ftp site in general.

---

### Post by rejser on 2006-12-02
Does it work on sites with passwords, I mean, those have srver-side based code, all acces from outside that't not by ftp get compiled and won't give you any information.

---

### Post by lamego on 2006-12-02
1) It may be illegal - If it is the case do not ask for help here
2) It depends on what you want to rip from the site, wget will just crawl every link and try to download, if there are human based download validations it will work

---

### Post by xyz on 2006-12-02
Seen on [Ubuntu French Forum by **pabix**]("http://forum.ubuntu-fr.org/viewtopic.php?id=78954")
**BIG WARNING**: this is "recommended" ONLY for 'light' sites! Don't,for instance, rip ubuntuforums.org!!!

---

### Post by rejser on 2006-12-02
Well, it still don't work on server-side based code, tried on one site I manage that uses php, and one based on aspx. It take's the html output as seen in you web-browser, so for educational purpose (that I assume that sekcon was interested in), it helps nothing. 
But I was worried for a while I must say.
But for a normal html site that you wan't to look at the coding of its great

---

### Post by Cronjob on 2006-12-02
If the question itself is indicative of inherently "illegal" activity, then someone better hurry up and shut down The Internet Archive and the Wayback Machine and Google.

If asking for help with implementation and installation of proprietary codecs flies here, I'm sure asking how to use wget or another crawler/archiver is just fine. Especially since none of us necessarily know the intended use or the jurisdiction and laws of said jurisdiction in which the questioner intendeds to use it.

---

### Post by highneko on 2006-12-02
> **xyz said:**
> Seen on [Ubuntu French Forum by **pabix**]("http://forum.ubuntu-fr.org/viewtopic.php?id=78954")
**BIG WARNING**: this is "recommended" ONLY for 'light' sites! Don't,for instance, rip ubuntuforums.org!!!
Yes, I agree, light sites. I have been to sites where it's just annoying to download images, like they have sixty html pages for sixty images and have thumbnails for each one.

How would this be done but ignoring filenames with html extention, or filenames with the word "thumb" in them?

The wget man page is very nice, I'm currently reading through it.

---

### Post by bliffle on 2007-11-21
Oboy, "wget" just got me everything I wanted from the 2 websites of HTML and photos (basically) that I wanted to make available on my granddaughters machine. That way she doesn't have to tie up her mothers phoneline.and she can use it as a reference library.

I'd used 'wget' a few years ago for a rather narrow purpose so I didn't realize the power that is intrinsic in it's design. For example, if I found that I hadn't recursed far enough to get everything I wanted, I could run the 'wget' again with an improved "-r -l 3" to go 3 levels, and also append the new log info with "-a wget1.log" which I could scan for errors later, and if, for example, I was still getting errors increase the retry count with say "-t 3". Of course, I'd add the '-nc' parameter to "not clobber" data that DLed successfully before.

"wget" swings, man!

As an interesting side issue, one ought to notice that this is made possible by the (often-criticized) Command Line Interface (CLI). Windows and Mac people who encounter CLI for the first time ALWAYS complain about the seemingly obscure syntax of CLI and the fact that they, poor dears, have to RTFM! And maybe even THINK, a loathsome burden, apparently, for many computer users.

By separating implementation of a function from the parameter parsing it sets the software developer free to develop the vital hidden code that brings something to life without bogging down in UI considerations until later when the functionality is settled down. As a longtime software developer I can attest that this is a BIG reduction in development time and effort.

CLI swings too! Heckuva better job than that lame DOS box in windows!

---

