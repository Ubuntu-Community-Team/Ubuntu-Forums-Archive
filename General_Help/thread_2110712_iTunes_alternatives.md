---
title: "iTunes alternatives"
date: 2013-01-30
forum: General Help
---

### Post by family682guy on 2013-01-30
Ok, so once again, I'm fairly new to ubuntu. I'm not too terribly new, but new enough to still need help. An issue I need help with now is a good iTunes alternative. 

I know Rhythmbox is able to sync with an ipod, I have a 5th gen ipod that I've synced with it before and it worked perfectly. Now, I'm not an iPhone kind of person, but I do alot of iPhone repairs. Are there any good alternatives to iTunes that will work with all iPhones? At the moment, I cant seem to get rythmbox to play nice with it. Ill try to sync music like I would do with an ipod, but nothing happens.

Thank you for an help you might be able to give me.

---

### Post by BBQdave on 2013-01-31
> **family682guy said:**
> I know Rhythmbox is able to sync with an ipod...

[Rhythmbox external devices help]("https://live.gnome.org/Rhythmbox/FAQ"):

Create a .is_audio_player file on the device. You can  set a few fields in this file to override the media-player-info device  information like this: 

audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg

I use this file with a Sansa Clip+ to sync play lists with Rhythmbox. Not sure if it will work with an iPhone?

---

### Post by family682guy on 2013-01-31
> **BBQdave said:**
> [Rhythmbox external devices help]("https://live.gnome.org/Rhythmbox/FAQ"):

Create a .is_audio_player file on the device. You can  set a few fields in this file to override the media-player-info device  information like this: 

audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg

I use this file with a Sansa Clip+ to sync play lists with Rhythmbox. Not sure if it will work with an iPhone?

Hmmm... I'm not much of an iphone person. I'll have to research how to create a file on the device. I don't think it'll be as easy as how to do it on an android. I'll do some digging and post my findings.

Thanks again for the reply.

---

### Post by family682guy on 2013-01-31
So, Ubuntu doesn't play nice with the iphone 4s I have here with me. It wont even let me open the iPhone up from unity. I have two icons that show up on unity. One is just the name of the iPhone, the other is Documents on the iPhone. I can't open either. When I click to open, Ubuntu freezes up for about a minute or so and then resumes like I never even click on the icon. Interesting, huh? 

Any ideas?

-Also, when I first plug in the iPhone, it says "Unable to mount iPhone. Location is already mounted."

---

### Post by family682guy on 2013-01-31
Ok, so I was able to finally get music onto the iPhone. I fixed the "Could not mount iPhone" problem. All I had to do was simply unmount the iPhone and the remount it. Once I had that part solved, this is what I did. Mind you, this is a work-around not a solid solution.

Ok, so there are two icons in unity for the iPhone, one labeled simply "iPhone" (I figure this would actually be whatever you named your iPhone) and the other is labeled "Documents on iPhone". Thats the one I'm interested in.

I downloaded a music player app named "EZMP3" on the iPhone. Once that was installed, I then connected the iPhone to my netbook and opened "Documents on iPhone". There you will see an icon for EZMP3. If not, ctrl-h. I double clicked and then saw a folder named "documents". All I had to do was drag and drop the music files (which are mp3's) into this folder. Once all of the music was on there, I exited and unmounted the iPhone, opened up EZMP3 and bam. Music. 

I hope this can help someone.. idk if there is a better way but this is what I found out. I tried doing the same in the icon named just "iPhone", but sadly, I yielded no results. I will continue to work on this and, hopefully, post the results later.

Also, as a side note, be sure to also unmount the iPhone before unplugging it. That will keep the "Could not mount iPhone" problem from coming about.

---

