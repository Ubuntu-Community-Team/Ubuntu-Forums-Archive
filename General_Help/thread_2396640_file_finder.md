---
title: "file finder"
date: 2018-07-18
forum: General Help
---

### Post by kevinorourke2008 on 2018-07-18
Hi guys maybe i'm being a bit dim here but could anybody recomend me a programme that would be able to search my system and portable media for audio files, or images?
I have so many mp3's scattered all over the place i really need to get them all on to one drive and need a searching program to accomplish this.

many thanks in advance.

---

### Post by kazakore on 2018-07-19
[http://man7.org/linux/man-pages/man1/find.1.html](http://man7.org/linux/man-pages/man1/find.1.html)

Although that is command line and I guess even with the -exec option you'll struggle to put things where you want. I do find it the easiest way to quickly find something and it has a lot of power though....

---

### Post by HermanAB on 2018-07-19
The way to recursively search the filesystem tree and do something, is indeed with the 'find' command.

After you have copied things where you want, you can use the 'hardlink' program to deduplicate the file system and reclaim oodles of space, without actually having to delete (and break) anything.

---

### Post by oldos2er on 2018-07-19
[Beets]("http://beets.io/") is great for audio files, but not images. It has a bit of a learning curve though.

For a generic GUI file search app, try [Angrysearch]("https://github.com/DoTheEvo/ANGRYsearch").

---

