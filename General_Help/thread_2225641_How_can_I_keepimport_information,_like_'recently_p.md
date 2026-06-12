---
title: "How can I keep/import information, like 'recently played' tracks, with rhythmbox?"
date: 2014-05-22
forum: General Help
---

### Post by lucianloonstra on 2014-05-22
Dear all,

On my desktop I am using the 12.04 distro (because of the stability) and I want to upgrade to 14.04 (I am not sure yet if I'm going to upgrade it from within 12.04 or do a fresh install). Because I have reasonably large music collection, I want to keep information about tracks - the information about the number of times a track is played and the dates tracks are played in particular -, and import that information in rhythmbox (or, if that is possible and necessary, in another musicplayer, but I assume rhythmbox is the default player in 14.04).

[ATTACH=CONFIG]253372[/ATTACH]

Otherwise I have to rediscover the music I want to listen to, which is, however entertaining it may be, considering the amount of tracks, very time consuming. So, my question is: How can I do this? Does anyone have experience with this, and, if this infomation is contained in a certain file, does rhythmbox recognize this within a fresh install?

---

### Post by bluefrog on 2014-05-22
have a look at .local/share/rhythmbox

---

### Post by tgalati4 on 2014-05-22
I would boot a live session of 14.04, copy your old rhythmbox files to the correct location in the Live Session.  Bring up rhythmbox and report what happens--everything will be in RAM so it won't get saved when you shut the machine off or reboot.  Understand that database formats change over time, so it's possible that the rhythmbox version in 14.04 may not be happy with a 12.04 version of the database.  If it works then you are set.  If it doesn't, then you might be out of luck.

Even if the database does read correctly, I would worry about stability of the old data versus adding new data.  The database may get corrupted over time.  I would spend some time on the project page and ask there.

---

### Post by lucianloonstra on 2014-07-03
Thanks, I'll try your suggestions and will post the results here. This may take a while though: I'll wait for the 14.04.1 release before installing it on my desktop.

---

### Post by lucianloonstra on 2014-10-29
I got it working, with thanks to bluefrog and tgalati4! First I tried it on a live usb - like tgalati4 suggested -, and now I got Ubuntu 14.04 installed and it works. For anyone who wants to do the same thing, this is what you should do in order to get it to work (this works for me at least): 

- In Ubuntu 12.04, make a copy of this file: rhythmdb.xml (it should be in this folder:  .local/share/rhythmbox). 
- Replace the content of the 'same' file in Ubuntu 14.04 with the content of the file you copied from your 12.04 OS.

The files in 12.04 and 14.04 are the same, except for two things, and you have to change them in order to get it to work:

- The version number (you find this in the second line) is "1.8" (in the 12.04 version), you should change that to "1.9".
- In 14.04 the locations are named differenly. So you need to rename all the locations in the file. This means renaming this: "///media/your-hd-name/" to this: "///media/your-username/your-hd-name/". 

If you safe it like this and start rhythmbox, it should work.

---

