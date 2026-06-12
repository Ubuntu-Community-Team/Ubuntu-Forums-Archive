---
title: "Apt downloads SLOW!"
date: 2007-01-06
forum: General Help
---

### Post by gitargr8 on 2007-01-06
I just recently went from the 32 bit version of Kubuntu to the 64 bit version, but nothing really works well with it.

Anyway, when I fired it up for the first time, adept_updater came up and said it had 84 updates. So I went through and tried to install them, but it took F..O..R..E..V..E..R.. to download anything. (the total size was 162MB and I'm on a 3Mb/s cable connection)

So I figured that perhaps it was just the auto updater program that was slow, so I canceled out, and ran apept_manager, and did the full update/upgrade and the same thing.

Alright. So I get sick of using Konqueror to look for help online, and I download firefox. This takes no time at all, so I know it's not the connection. But, when I try to run firefox, it can't find the firefox-bin file. So I do some searching and I find that I need some 32bit packages. Time to run Apt again...

```

sudo apt-get install -y ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

```

and I'm downloading on the average around 6516B/s. 6.5KB/s when I know my connection routinely gets 200KB/s? What gives? Are the repositories just overloaded these last two days? I'm on a wired connection to my router, by the way.

Thanks for the help,
~Ryan

---

### Post by fuscia on 2007-01-06
same here. 30 minutes to install sylpheed-claws? something's wrong there.

---

### Post by Aspero on 2007-01-06
Same here, and I have the privileged of updating from a fresh install... please god help us all.

---

### Post by Atreus12 on 2007-01-06
I'm in the same boat. Fresh install, this is taking hours.

I'm actually helping a friend install...so far he's not impressed. ](*,) 

-Andrew

---

### Post by Aspero on 2007-01-06
I think Bill Gates is in our serverz stealing our codez. Anyone know of alternative mirrors for edgy main?

---

