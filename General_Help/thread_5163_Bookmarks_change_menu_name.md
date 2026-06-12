---
title: "Bookmarks: change menu name"
date: 2004-11-16
forum: General Help
---

### Post by xinelo on 2004-11-16
This is my first post to this forum, so hello to everybody :) 

This must be a simple question for anyone who has helped localise any software ever.

For a pedagogic reason which is not relevant here now, I would like to change the "Bookmarks" menu title, so I would have a different word, say "Favourites", in the menus bar.

Could somebody tell me what file I need to find and what chains of characters of what lines I need to modify?

Thanks for the help! If you can't help me, thanks for trying! 
xinelo

PS Btw, I forgot to say that ubuntu is impressive. It's the first distro I try which configures perfectly my laptop's 15" screen resolution. I'm very pleased.

---

### Post by p!=f on 2004-11-16
Howdy :)
 
 I don't get it. 
 Where do you want to replace "bookmarks for favorites"? Epiphany, Firefox, another application or Gnome menus?

---

### Post by HungSquirrel on 2004-11-16
I think he means in Firefox.

---

### Post by p!=f on 2004-11-16
I wouldn't go for that bussiness in this case. :) If you are not losing your hair when looking at "bookmarks" instead of "favorites" I'd leave that alone. Not because it's not possible but it's not easy and it would be overwritten during next package update anyway.
  
 If you're not satisfied with the answer open your Midnight Commander under root privileges and start your adventurous journey at /usr/lib/mozilla-firefox/chrome. :D

---

### Post by xinelo on 2004-11-16
Hey, thank you very much for your replies. My apologies for miserably forgetting mentioning that I in fact meant Firefox. It was kind of obvious but still where was my mind... 

You may feel curious, so the reason why I want to do that is that I'm using the Brazilian locale for Firefox and everything is translated except that word (I imagine that they've borrowed the English word, but it's not ok for me). I know it would be overwritten with next update but I need to take some screenshots with that word changed just to put them in a document. After that (and before) I always use the English version. 

Sorry about the waffle. Let's say that I'm not happy with the software (the localization is part of it) and I'd like to adapt it to my needs ;) Only that I don't know how to do that... :( 

Anyway, thanks a lot for your replies. Now at least I know what file I should head for, I'll have a look, but just in case somebody else reads this I'd be thankful if given more precise details about the lines to modify. 

xinelo

---

### Post by HungSquirrel on 2004-11-16
For my American English version of Firefox I see the following when I ls /usr/lib/mozilla-firefox/chrome:

```
esheldon@sage /usr/lib/mozilla-firefox/chrome $ ls
browser.jar     comm.jar           help.jar              pipnss.jar
chromelist.txt  content-packs.jar  icons                 pippki.jar
chrome.rdf      en-unix.jar        installed-chrome.txt  toolkit.jar
classic.jar     en-US.jar          overlayinfo           US.jar
```
I am assuming all my localization information is located in en-US.jar.  The name of the localized file will of course vary depending on language.  I think the setting you're looking for will be in there.  You can open the JAR file with file-roller.

I do not know which specific file in the JAR you need to edit, and I have a program due tomorrow in Java class so I have to be going.  Sorry I couldn't help more!

---

### Post by xinelo on 2004-11-17
Thanks HungSquirrel, I appreciate it. I'm getting closer. I just hope somebody else knows precisely what I should do. 
Cheers, xinelo

---

### Post by HungSquirrel on 2004-11-18
You're in luck, I have more time now.  ;)

If you extract the contents of the JAR to your home folder, you can search through it and edit the contents.  Now run a search (Computer -> Search for Files...) within the folder you extracted for anything containing the text *bookmark*.  I got 25 results.  I think those are the files you might want to look at.  You will probably have to edit most or all of them to get all the occurances of the words Bookmark and Bookmarks if you want to make sure everything has the right value, including Help files.

Open the files in your default text-editor, and use the find function to look for occurrances of 'Bookmark' within the files themselves and edit them if appropriate.  (If you tell find to Match Case, your searches will be much more accurate because the localized word for Bookmark and Bookmarks will probably be capitalized.)  Once you have finished completely, right-click on the locale folder that was extracted, and choose Create Archive...  Enter the full name of the JAR you extracted.  For example, English-US would be **en-US.jar**.  Then, open up a terminal in the folder containing your new JAR and do the following, of course replacing en-US with your locale.

Back up the old JAR:
```
sudo cp /usr/lib/mozilla-firefox/chrome/en-US.jar /usr/lib/mozilla-firefox/chrome/en-US.jar.BAK
```

Replace the JAR with your new one:
```
sudo cp en-US.jar /usr/lib/mozilla-firefox/chrome/
```

All of this is theoretical as I haven't really played with editing the JARs much yet.

Hope that helps you!

---

