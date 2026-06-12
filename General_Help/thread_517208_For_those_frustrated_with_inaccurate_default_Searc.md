---
title: "For those frustrated with inaccurate default Search tools..."
date: 2007-08-04
forum: General Help
---

### Post by OzzyFrank on 2007-08-04
If you're one of many who are frustrated with the (lack of) results you get in "Search for files" and the Search option within a Nautilus window, here are some suggestions.

First off, the growing popularity of the new Linux version of the Google Desktop Search is warranted, as it gives you results in a familiar Google page (within your web browser). Only thing is that it is useless straight after install as it slowly indexes in the background, and this first time takes quite a few hours. Get info on how to add to your sources and download/install from here [http://desktop.google.com/linux](http://desktop.google.com/linux) (you can download the .deb file and just click it to install, but if you decide to set up the sources and apply the signature key, just download it through Synaptic, as it will be in the list of available apps after that).

If you prefer a small stand-alone app that is definitely more accurate than the default options, I strongly recommend Catfish. Once installed it is found as "File search" in Applications > Accessories. Under "Search method" you can choose from installed engines, in my case "find", "slocate" and "beagle-query". I just left it on the default find and got hits I should have in the normal methods, but at least I know I can choose other engines if need be. Hope this helps someone. Cheers.

---

### Post by ZipoTe on 2007-08-04
can't you type:  sudo apt-get install google-desktop-linux?

and yes, catfish it's really nice. I use it and it take few seconds to find what are you looking for ^^ I think it should be installed by default :)

---

### Post by OzzyFrank on 2007-08-04
For Google, I suggest adding the repository and the key needed to access it, simply to ensure you get the latest updates. They even admit it's pretty new, and seem open to suggestion. Oh, and as for apt-get, not sure for this package, but it didn't take me long to realise that "apt-get install" weren't magical words to install ANY package... some simply couldn't be found, but I would find them elsewhere in downloads. Would probably work for Google, but then you'd still need to add the repo and key for the updates.

And 100% on Catfish being the new default search tool! Compact, but with a few good options easy to get at (hidden files, different engines), fast, and accurate. Amazing watching the search in Nautilus not find a file in the folder I was pointing to, yet it comes up with all these unrelated "hidden" XML files (that I can't see as actually existing there). And "Search for files" is actually much better, but needs to have a day or two before it notices new files, hehe!

---

### Post by kleo skywalker on 2007-08-05
Thank you for this information, I am frustrated with inaccurate default search tools.
I have a question though: do any of these tools (google desktop search and catfish) include information in tags while searching?
For example, I want to be able to search for songs by artist name (which I put in a tag, not the name of the file). Can either of these tools do that?
Thanks.

---

### Post by OzzyFrank on 2007-08-05
Google searches a bunch of things, including emails and stuff. It's only new and they encourage input, so you could always send them your suggestions if need be. Anyway, the results are impressive, with searching a lot more things (like the emails) and having thumbnails and the usual Google paragraph of text.

Just found a limitation with Catfish, being the inability the drag-and-drop results, like other little seach apps. Double-clicking a file "opens" it (so if it's an unknown type, in my case that stupid ClamAV opens to scan it, hehe). The only other option available with right-click is "Jump to" which does nothing for files, and surprisingly folders either. Wish it at least had the "Open Folder" option, but still is way more accurate than the other search apps (besides Google, though that needs to be indexed).

Google is impressive, though needs your browser to run. Here are the current search options:

	Index the following items so that you can search for them:
  Email
 Web history
 Media files	 OpenOffice.org Writer
 OpenOffice.org Calc
 OpenOffice.org Impress	 PDF & PostScript
 HTML files
 Other files

---

### Post by ferd on 2007-08-05
I agree completely. I was able to remove Nautilus from my KDE installation with all it's necessary support because CATFISH is just as thorough.

---

### Post by kleo skywalker on 2007-08-07
> **kleo skywalker said:**
> Thank you for this information, I am frustrated with inaccurate default search tools.
I have a question though: do any of these tools (google desktop search and catfish) include information in tags while searching?
For example, I want to be able to search for songs by artist name (which I put in a tag, not the name of the file). Can either of these tools do that?
Thanks.

Catfish doesn't include information in tags while searching, Google Desktop does BUT there's still a hitch. Say I search for songs by artist name (which is stored in a tag, not in the title), I get X results. I can play one song at a time by clicking on individual results, but can't play all songs in the results or enqueue them. Like in Windows, you can do a similar search - not using google desktop of course, but then you can simply select all results, right-click and say Open or Enqueue. Is there any way to do that kind of a thing on Feisty?

Sorry for the bother, I'm just trying to figure out how to listen to music the way I like.

Thanks.

---

### Post by oldos2er on 2007-08-07
I've found the search function in GNOME Commander file manager to be more than adequate.

---

