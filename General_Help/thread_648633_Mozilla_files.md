---
title: "Mozilla files"
date: 2007-12-23
forum: General Help
---

### Post by DonDodge on 2007-12-23
Where does Firefox hide the bookmarks when running under Ubuntu? When I was doing  the setup, I was offered to have windoze settings imported. So Firefox grabbed my IE "Favorites" instead of my Firefox stuff. Now I have both links from IE but none of the zillions I've accumulated over the years in Firefox. and I can't figure out how to move them.

I can't find the bookmarks.html file used by Firefox in Ubuntu so I can substitute my real bookmarks.html file. All I find is "example" files in etc/firefox/profile and usr/share/firefox/defaults that aren't even the bookmark file Firefox is using. Of course, even if one of these was the file Firefox is using, I couldn't edit, rename or replace it because they're owned by root and I can't remember to work on files as root. 

When I try to have Firefox import my Firefox bookmarks, history and password data, it can't find any such program even with my windoze volume mounted. 

This shouldn't be such a big deal. I set up Thunderbird in Ubuntu to share  my mail folders over on the windoze volume with my regular windoze Thunderbird. That works like a champ.

Anybody know how I can teach Firefox/Ubuntu how to find  my information over in Firefox/Windoze? Or tell me how I can surgically implant the data into my Firefox installation over here in Ubuntu?

---

### Post by ed-koala on 2007-12-23
Firefox bookmark file can be found under  ./mozilla/Firefox/aodixyfy.default/bookmarks.html

I won't even try to guess what that weird directory is supposed to be, but the file is there.

---

### Post by DonDodge on 2007-12-23
I don't have that directory that I can find. Unless the dot you have in front of the slash means something I don't know about.

Does your bookmark.html file contain your actual bookmarks?

I did find another bookmarks.html in usr/lib/firefox/defaults/profile/ but it's just another example file with no real bookmarks that Firefox is actually using.

The Ubuntu file searching utility leaves a bit to desire.

---

### Post by rechick on 2007-12-24
You're almost at the right place. It is in:

/home/**username**/.mozilla/firefox/**xxxxx.default**/bookmarks.html

Replace **username **with your login name.
Replace **xxxxx.default** with whatever randomly generated profile directory your firefox created. (Firefox creates a random filename each time a new profile is created. In most cases this is only a single profile.)

Don't forget the "." in front of mozilla which makes it a hidden file in Linux/Unix systems. If you are browsing with Nautilus click on ***View > Show hidden files*** to see the directory.

---

### Post by DonDodge on 2007-12-24
I found it. I thought I'd previously found a persistent way to show hidden files. But no, that was the problem. Thanks.

---

