---
title: "Importing settings."
date: 2007-04-25
forum: General Help
---

### Post by Bliz0r on 2007-04-25
Hello, I just recently started using ubuntu, and I wondered if it is possible to import my settings from the firefox I got installed on windows? I got bookmarks in mind. When I installed 7.04 I could choose some settings, but I only got my IE bookmarks. :(

So, is there anyway I can get my windows FF settings (bookmarks) to my FF on ubuntu?

---

### Post by freakavoid on 2007-04-25
You might want to try [this]("https://addons.mozilla.org/en-US/firefox/addon/2109") extension. Though keep in mind if you back up your whole profile and try to import it elsewhere you first have to create another firefox profile (firefox -ProfileManager) and do it there to be able to overwrite the main profile.

---

### Post by Bliz0r on 2007-04-25
Hm, I downloaded that and performed a backup on my windows, and saved it on a folder, I'm on linux now and I got no idea how to load it?

---

### Post by freakavoid on 2007-04-25
If you didn't do a complete profile backup you can skip this and continue with step two.
1. Close all firefox windows. Open a terminal and type "firefox -ProfileManager" without the quotes and create a new profile and open firefox with this new profile.
2. Install FEBE to import your settings. Go to tools->FEBE->FEBE Options and choose your backup directory i.e. the directory containing your backup file. Go to tools->FEBE->restore and choose your restore type, point to the correct file, wait for the report.

I hope that helps you.

---

### Post by Bliz0r on 2007-04-25
Thanks alot, it worked :)

---

