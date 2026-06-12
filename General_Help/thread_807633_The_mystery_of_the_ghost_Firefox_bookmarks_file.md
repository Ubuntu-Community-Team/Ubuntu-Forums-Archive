---
title: "The mystery of the ghost Firefox bookmarks file"
date: 2008-05-26
forum: General Help
---

### Post by luiznetto on 2008-05-26
I'm using the Firefox 3 Beta 5 that comes with Ubuntu 8.04. I wanted to backup my firefox bookmarks file onto my memory stick, so I went to the directory 

/home/me/.mozilla/firefox/somethingweird.default

(where "somethingweird" is something that changes every time you install firefox, I don't know why), and I did

$ cp bookmarks.html /media/disk

When I looked into my memory stick though, I found out that the bookmarks.html file that was there was NOT the one that I had in my Firefox. Then I went back to that same directory again and I did

$ firefox bookmarks.html

and when firefox opened the file, I saw that that was NOT the file that was active in my Firefox, but one that had been modified long ago. So i thought, what the heck is going on here? Perhaps there's a hidden file that I cannot see? So I acquired root privileges, and I searched the directory carefully, but I couldn't find the file that is my actual current Firefox bookmarks file. That file must be hidden somewhere in the system; my Firefox is working all right, and when I add another entry to the bookmarks it stays there and works fine. So, where on earth could that file be? This is the weirdest thing I've ever seen in my life.

Any help will be appreciated.

Luiz

---

### Post by the yawner on 2008-05-26
Mmm... Why not just backup your bookmarks into a file?
Click Bookmarks > Organize Bookmarks to open the bookmarks library. Then click Import and Backup > Export to save your bookmarks to a filename of your choice.

---

### Post by ryanhaigh on 2008-05-26
Firefox 3 uses a new mechanism for bookmarks/history/etc, I believe they are now stored in a sqlite based database file. The bookmarks.html is probably as you said your old one which was likely imported into the new system. I personally liked the 'its just html' bookmarking, but as long as bookmarks don't just randomly disappear and I can still export them in html I think I can accept this change, especially given the speed of v3.

---

