---
title: "Simple DVD to MPEG Conversion Software?  (.vob to .mpeg)"
date: 2006-11-20
forum: General Help
---

### Post by SendDerek on 2006-11-20
Hello!

I would simply like to get a DVD ripped into an .mpeg so that I may share with family and friends via email.  Even simpler, I would like to convert the .VOB files into a single .mpeg video.

It's a DVD with and ultrasound of me and my wifes first baby and we're excited to share.  So, it's not like a DVD movie or anything like that.

Any suggestions or tutorials?

I've found [this one here]("http://www.smorgasbord.net/howto_rip_dvds_in_mpeg_4_avc_x264_multi_audio_subtitles_matroska"), but it seems too involved for what I need.  There's no sound in this DVD.

Thanks for any help!

---

### Post by beerorkid on 2006-11-20
well I have not done it, but I think I can help.

Get DVDrip installed, [autamatix2](http://www.getautomatix.com) works pretty good for that, although it is probably in the repos.
You can prob use that to get the files off the DVD.  Or might you be able to just drag and drop them?

Then use this [http://www.ubuntuforums.org/showthread.php?t=193754](http://www.ubuntuforums.org/showthread.php?t=193754)
it is a nautilus script that works wonders.  Really amazing work, I use it for a bunch of stuff.  It can handle VOB's.

---

### Post by SendDerek on 2006-11-20
> **beerorkid said:**
> well I have not done it, but I think I can help.

Get DVDrip installed, [autamatix2](http://www.getautomatix.com) works pretty good for that, although it is probably in the repos.
You can prob use that to get the files off the DVD.  Or might you be able to just drag and drop them?

Then use this [http://www.ubuntuforums.org/showthread.php?t=193754](http://www.ubuntuforums.org/showthread.php?t=193754)
it is a nautilus script that works wonders.  Really amazing work, I use it for a bunch of stuff.  It can handle VOB's.

Well, so far it was just drag and drop, so that was nice and easy.  I now have 5 .vob files and I think I saw a program in the repositories that will combine .vob files.  

I actually found that script and so far it doesn't work.  It just gives me an error message saying this:

> 
You have not selected a valid video type.
MimeType= Application/octet stream


I'm pretty sure I have all the proper programs installed for that to work.  Any ideas?

---

### Post by beerorkid on 2006-11-20
oh man I have seen that error a bunch of times.  I am sure you have searched that error and seen a bunch of problems people have had with it.

I was using a capture card in dapper and it seemed like the files I made with it were corrupt.  The error happened after a long time of it working correctly.  Even windows movie maker thought the files were corrupt.  I think it had something to do with codecs, but was never able to fix the issue.

I am betting the files are not your normal vob's then and the script has issues with them.  I am having no problems (yet?) in edgy.

I will look around a bit.

---

### Post by SendDerek on 2006-11-20
Wow.  

Thanks for the ever-so-quick reply on that one.  I literally just went to brush my teeth and the answer was there. lol

Thanks for checkin' for me.  I'm going to try it again now and see what happens...

...Nope.  Didn't work.  I even ripped it using vobcopy.  It gives the same error message.

---

### Post by SendDerek on 2006-11-20
Bump.

I've kinda done all this last minute and it's my fault, but I need a solution pretty quick please if somebody wouldn't mind.

---

### Post by adamkane on 2006-11-21
"I need help, and I need it now!" <- Poor form on the forums.

I think you need tovid, and a fully functional ffmpeg and mencoder.

There's plenty of info available.

You didn't offer any details or error messages. Be specific, if you want help.

---

### Post by orb9220 on 2006-11-21
Some links
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)
[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

Sorry only two I have right now.

Update link looks promising [http://applications.linux.com/article.pl?sid=06/11/13/2129256&from=rss](http://applications.linux.com/article.pl?sid=06/11/13/2129256&from=rss)

---

### Post by SendDerek on 2006-11-21
> **adamkane said:**
> "I need help, and I need it now!" <- Poor form on the forums.

I think you need tovid, and a fully functional ffmpeg and mencoder.

There's plenty of info available.

You didn't offer any details or error messages. Be specific, if you want help.

I usually hate it when people whine with a "help me now!" attitude too, but I was being as polite as I could when asking for help.  Was that not polite?

And if you read through my posts, I did give an error message.  It was with that video-convert script.

Thanks for the suggestion.  I'm looking into it now.  Believe it or not, I actually did search the forums and google and I didn't come up with anything better than the video-convert script.

[quote=orb9220]
Some links
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)
[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

Sorry only two I have right now.

Update link looks promising [http://applications.linux.com/articl...29256&from=rss](http://applications.linux.com/articl...29256&from=rss)
[/quote]

Thank you very much for your responce.  I downloaded cinelerra and it looks very powerful.  I'm going to give it a shot.  I'm still going to try tovid as well.

For now, this thread is finished as I believe you guys have helped me find a solution.

Thanks again.

---

### Post by LaVache on 2006-11-21
Acidrip is the program you'll want to use to convert from a vob to an mpeg.  Use the ubuntu synaptics package mgr to add the program and the dependencies should be taken care of at the same time.

Acidrip is basically a front-end for mencoder, so it may help you to reference the mencoder tutorials/docs if it first appears confusing:  [http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html")

I think that you'll easily get the hang of it with a bit of trial and error.

---

### Post by Nasso on 2006-12-15
I find it easiest to just use k3b for this problem.

Start a new dvd-video project under file. Locate all your .vob files and drag them to the VIDEO_TS-folder in the project. Burn the project but instead of burning to a disk just "burn" to a file (iso).

That is if it is okay to have it in iso-format :)

---

