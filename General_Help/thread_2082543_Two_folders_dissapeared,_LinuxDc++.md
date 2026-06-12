---
title: "Two folders dissapeared, LinuxDc++?"
date: 2012-11-09
forum: General Help
---

### Post by 3v3rgr33n on 2012-11-09
Hi

My problem is simple. People have had similar problems as I see but none of their solutions work.

I recently installed LinuxDc++, I then added two folders for Sharing. I added the Music and Videos folders.

After about two minutes, they disappeared.

The file .config/user-dirs.dirs looked like this [http://paste.ubuntu.com/1346412/](http://paste.ubuntu.com/1346412/)

I then changed it to [http://paste.ubuntu.com/1346418/](http://paste.ubuntu.com/1346418/) just to test if I can fix the music folder. I then added it(Created the music folder) to the Home folder. It appeared like normal but the contents are no longer there.

I also tried rebooting but it didn't fix the problem.

Please Help.


Additional info:
Before the folders disappeared, my computer made a beep sound.

Thanks.
Adeeb

---

### Post by 3v3rgr33n on 2012-11-12
It turns out the problem was LinuxDc++.

I was trying to find the folders by searching my filesystem for 'Music' and 'Videos'. I then decided to search for one the files which was in the folders.

```
find / -iname '*<parts of the filename>*'
```

I piped the results of the command to a file. When I was inspecting the file I came across the file I was searching for. It turns out it (LinuxDc++) moved my files and deleted the folders.
I found them in folder:

```
 /home/<my username>/.dc++/FileLists/<someone's username>/myFile
```

I'm guessing it's probably a bug in LinuxDc++

3v3rgr33n ;-)

---

