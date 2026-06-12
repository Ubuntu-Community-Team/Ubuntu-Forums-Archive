---
title: "GCONF and themes problem"
date: 2007-07-21
forum: General Help
---

### Post by yogithebear73 on 2007-07-21
Problem with gconf:
After installing Automatix2 and getting Java SDK, Azureus, Java JRE, audio/video plugins, a few other things i dont remember. I restarted. Upon logging in, I noticed that my mouse was moving incredibly slowly; changing mouse settings did not help until I restarted and tried to change them again. The mouse is still incredibly slow. The keyboard will not repeat backspace. All icons for menus are gone. 

Trying to edit themes from System>Preferences>Theme results in this error: "The default theme schemas could not be found on your system. This means that you probably do not have metacity installed, or that your gconf is configured incorrectly."

The panels are not behaving correctly, windows do not appear on the panel, even after adding window selector. window list give a single icon that behaves like a drawer for opened windows.

I'm sure there are several other problems I just haven't found yet. I have forum surfed and found no resolutions for this, and very little response from the Ubuntu community. Also, as a side note, why has the google search forums been removed? If you choose advanced search, it used to pull up a main search query box powered by google. The regular search engine for this forum is completely inane and nearly never returns anything that has any significant link to the search query. Please put it back?

confused and frustrated...

---

### Post by tbroderick on 2007-07-21
Everything like metacity and gnome is installed, right? If yes, then try deleting your user's hidden gnome folder. It's where gnome keeps all your personal settings.

```

/home/your_user_name_/.gnome2
```

You can use the terminal or nautilus. From the terminal you would use rm.
```

rm -rf ~/.gnome2

```

Be careful when using the rm command that you don't mistype anything. You don't want to delete you entire /home.

---

