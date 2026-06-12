---
title: "any fix  for this ?"
date: 2006-09-05
forum: General Help
---

### Post by MintabiePete on 2006-09-05
This happens with Swiftfox  and Firefox 1.5.0.4 only  way I get out of it is go into system monitor  and knock out the  running  process , then its ok . But this is happening  more and more  frequently .

[IMG]http://img.photobucket.com/albums/v116/MintabiePete/Screenshot.png[/IMG]

What it says :  Firefox is aready running , but is not responding. To open a new  windows , you must first close the existing firefox process or restart your system .

---

### Post by orb9220 on 2006-09-05
The only time I had this happening in windows firefox was going to some pirate or porn sites would cause this to happen.

---

### Post by MintabiePete on 2006-09-05
You wouldnt know by  what process   this  actually  happens ?

---

### Post by orb9220 on 2006-09-05
Has to do with java and scripts I believe. Some sites are very aggressive to browsers. 
They are trying to install and run all kinds of scripts and end up overwhelming the browser.

Some others are what are called dirty sites these are web sites that have been hacked and code inserted into web site to cause havoc.

If it is happening when going to normal sites then I would be concerned that something in the browsers profile is corrupted or possible that an extension could cause this but not likely.

---

### Post by MintabiePete on 2006-09-05
Well I am not in the  habit of  going into porn sites , but I do  download  torrents  from time to time  , and a lot of those  sites  are  connected in some ways  to porn . But I can  go  days  without  doing that  and I still get that error , and only  in ubuntu , never in windows , although I will admit I spend  little time in windows now .

---

### Post by marianom on 2006-09-06
See if this helps:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by MintabiePete on 2006-09-06
Thanks for that link :)  I have  cleared the cache  and that seems  to have  done the  job  (crossed fingers):)

---

### Post by Big_J on 2006-09-07
Sometimes when I try to view a flash9 movie, firefox freezes for about a minute, and I tend to force it to quit, that's the only time I get that error in which case I just terminate the process

---

### Post by rafaelsdmf on 2006-09-08
Yeah I think that happens when you close up the app but no the "core" of it, so to speak. I'm shure that someone would come with a better explanation but in the meanwhile...

Open the console and type:
```

killall firefox-bin
```

And the universe should come to balance again :p

---

