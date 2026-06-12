---
title: "beryl keyboard and video in firefox problems"
date: 2006-12-09
forum: General Help
---

### Post by mattgaunt on 2006-12-09
Hey every1

Ive got a few lil problems just wondered if any1 could help

1.) Ive installed beryl and it runs like a dream, but the xmodmap.uk although it works, i think the alt key might not work at all, cos when i press ctrl+alt+and left mouse it should let me rotate the cube, but it doesnt unless i go to system->preferences->keyboard and add a new UK layout and delete the old one, anyone have any ideas??

2.)I cant watch videos that are wmv on websites through firefox, i.e. [www.storyoftheyear.net](www.storyoftheyear.net), it works fine but on the video diary's on the actual site, it loads up with mplayer plugin but it doesnt actually work, anyone have any ideas for fix??

Thanks in advance for any help

Byee

---

### Post by bulldog on 2006-12-09
Did a little forum searching, and here's what I found:

Create a new text document (there's a text editor in Applications > Accessories if memory serves ). Paste this in and save it to your home directory.```


xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```


Then right-click the file, and click the "Executable" check boxes.

Now you'll need to move the file into /usr/bin - the easiest way to do that will be through Terminal (as you need permissions to write to the directory):```


sudo mv filename /usr/bin
```


Then go to your System menu > Preferences > Sessions > Starup programs and add your file to the list.
Try this one,it works very well on my Edgy.

---

### Post by mattgaunt on 2006-12-26
thnk u so much worked perfectly!!!

Matt

---

