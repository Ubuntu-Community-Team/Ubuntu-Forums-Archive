---
title: "gedit-plugins not working"
date: 2007-08-03
forum: General Help
---

### Post by earther on 2007-08-03
I downloaded the  gedit-plugins and selected the ones I want in preferences but they aren't working.  I won't even consider using gedit for web development unless I can get them working.

Any ideas what the problem is?

---

### Post by apetresc on 2007-08-03
Could you specify exactly which ones aren't working, and what your expected behaviour for them is? A lot of the plugins, even once they're enabled, are not exactly intuitive to access. They may be there all along, you're just not looking in the right place. :)

---

### Post by earther on 2007-08-03
I have checked several plugins in "Preferences" but there are no indications in any of the gedit menus that they are active (and I looked in every one).  The "Configure plugin" option (under the plugin list in preferences) is also dead.  I'm especially interested in Tag Lines and Snippets to facilitate markup.

---

### Post by apetresc on 2007-08-03
> **earther said:**
> I have checked several plugins in "Preferences" but there are no indications in any of the gedit menus that they are active (and I looked in every one).  The "Configure plugin" option (under the plugin list in preferences) is also dead.  I'm especially interested in Tag Lines and Snippets to facilitate markup.

Hm, I see. Well, some of the plugins (like tag lists) don't even have a "Configure Plugin" screen, so this may be normal. They all work over here, though, so let's try to track this problem down. Try to follow the steps here, and tell me the first step where you can no longer follow (because something broke).

1. Open up a new Gedit session
2. Go to the Plugins tab in the Preferences
3. Enable the plugin called "Snippets" by clicking on the checkbox to the left.
4. Press "Configure Plugin" (This one **should** be highlightable once you've enabled it)
5. Open the "C" menu, and select the "do ... while" entry.
6. Select the "Shortcut Key" text box and hit Ctrl+D. That text should appear in the text box.
7. "Close" the Configure Plugin window, and the Preferences window
8. Close Gedit
9. Create a new file with a .c extension
10. Open Gedit
11. With the cursor in the text box, type "Ctrl+D"

Does the do-while snippet pop up?

---

### Post by earther on 2007-08-04
Yes, that worked!  It took some trial and error though . . .

Now how does the Tag list stuff work?? 

Thanks for your tutelage.

---

### Post by apetresc on 2007-08-04
> **earther said:**
> Yes, that worked!  It took some trial and error though . . .

Now how does the Tag list stuff work?? 

Thanks for your tutelage.

Glad to hear it worked :) The "Tag List" plugin is a little bit more subtle. Use these steps

1. Enable the Tag List plugin (I guess you know how to do this by now :))
2. Exit the Preferences window
3. From the "View" menu, make sure "Side Pane" is checked (enabled)
4. At the bottom of the side pane, there should be two or more tabs. One of those tabs should look like a "+" sign. Click that one.
5. There is your tag list :)

If you want more details on using the Tag List plugin, check out this link: [http://sernaonubuntu.wikidot.com/gedit#toc13](http://sernaonubuntu.wikidot.com/gedit#toc13)

---

### Post by earther on 2007-08-04
Found it!  Thanks so much for your help.  However, right now, I'm leaning towards Quanta+. Seems I will be able to create a toolbar with most often used markup tags which should really speed things along.

---

### Post by apetresc on 2007-08-04
> **earther said:**
> Found it!  Thanks so much for your help.  However, right now, I'm leaning towards Quanta+. Seems I will be able to create a toolbar with most often used markup tags which should really speed things along.

:) Glad you liked it. To be honest, I also recommend Quanta, it has a lot of good web-design-specific features. However, Gedit is worth learning because of the sheer utility. It's plugin is also the best LaTeX editor Gnome's got (if you happen to use LaTeX ever)

---

### Post by earther on 2007-08-04
[don't see a delete option]

---

### Post by earther on 2007-08-04
I'll still be using Gedit for saving txt files and general use but for web work, it will be Quanta+, I think.  I rarely prepare documents so probably won't need LaTeX but thanks for the info.

---

