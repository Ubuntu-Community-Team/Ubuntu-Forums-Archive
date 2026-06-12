---
title: "How to change color of ALL Thunderbird scrollbars"
date: 2022-01-28
forum: General Help
---

### Post by Ralph L on 2022-01-28
I am running Xubuntu 18.04 latest update. A recent Thunderbird update messed up its scrollbars. They became very narrow and lost my theme coloring scheme.  i restored the scrollbar width, stepper arrows, and squareness with:```

In Config Editor I changed the following:
                   widget.non-native-theme.scrollbar.size to 16
                   widget.non-native-theme.gtk.scrollbar.thumb-size to .95
                   widget.non-native-theme.gtk.scrollbar.round-thumb to false
                   widget.non-native-theme.gtk.scrollbar.allow-buttons to true
``` I also set (with Config Editor) toolkit.legacyUserProfileCustomizations.stylesheets to True, and created, in Thunderbird's profile folder, a new folder called "chrome". In chrome I put a file named "userContent.css" containing ```
               html
               {
               	scrollbar-color: rgb(102, 178, 255) lightgray;
               }
``` According to what I googled this should have changed the scrollbars to a light blue on light gray. And it did do this for the Preferences window and for any lengthy message.  However, it did not change the scrollbar color for the Inbox list nor the folder list (usually on the left part of the tbird window). I googled extensively and found several websites giving instructions to do what I did (above), but no mention that only some of the scrollbars would be changed. I used this same method to change scrollbar colors in Firefox and that worked.

Any help in getting ALL of Thunderbird's scrollbars' color changed is appreciated.........

---

### Post by #&amp;thj^% on 2022-01-28
Be careful though
[https://developer.mozilla.org/en-US/docs/Web/CSS/scrollbar-color](https://developer.mozilla.org/en-US/docs/Web/CSS/scrollbar-color)

---

### Post by &amp;KyT$0P# on 2022-01-28
Try the following code in **both** userChrome.css **and** userContent.css -
```
* {
  scrollbar-color: rgb(102, 178, 255) lightgray !important;
}
```

If you want to have it in just one place, you can put this in a single, other CSS file which you [@import]("https://developer.mozilla.org/en-US/docs/Web/CSS/@import") in the actual userChrome.css and userContent.css.  URLs in userChrome.css and userContent.css are relative to inside the [FONT=Courier New]chrome[/FONT] folder alongside userChrome.css/userContent.css.

---

### Post by Ralph L on 2022-01-28
1fallen: Thank you for the response. I tried what you suggested and it didn't fix the problem. In fact I used the website you referenced to get SOME of the scrollbars in tbird to change. The problem is that the fix does not change the "folders" scrollbar nor the Inbox scrollbar--the ones most used. It does change the scrollbar in Main menu>Edit>Preference and the one in long messages. So with things "half working" I don't know if I have done something wrong or if there is a bug in Tbird. Have you been successful in getting the Inbox and Folders scrollbars to change color??

Thanks again,

---

### Post by Ralph L on 2022-01-28
halogen2:  That worked!!! Thank you very much for replying. In testing I found that I needed both files that you specified--userChrome.css changed the Inbox and Folders scrollbar and userContent.css changed the scrollbar for the long messages and Edit>Preferences. I never would have guessed that! Anyway thank you both for replying. Everything seem to be fine now.
Incidentally, for anyone who is trying change Firefox's scrollbar size and color, see [https://ubuntuforums.org/showthread.php?t=2470903](https://ubuntuforums.org/showthread.php?t=2470903) .

---

