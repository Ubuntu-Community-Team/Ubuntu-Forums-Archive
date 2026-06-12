---
title: "bash script help"
date: 2006-11-16
forum: General Help
---

### Post by 16november on 2006-11-16
Hi, all- first post here.
Sorry if this is way easy, but I'm kind of new to all this.
i've written a simple bash script to launch an application with wine. The script works fine, but I get the popup asking  what I want to do with it- run in terminal, open with editor or just run. What I'd like to do is just run it. Does anyone know how I can include this in my script in order to bypass the popup and just run the darn thing, so my users don't have to be bothered with another question from a new OS that they will already be opposed to.(we're moving towards a pretty big migration on alot of people who are not exactly computer literate to begin with).
thanks

---

### Post by CatKiller on 2006-11-16
As an alternative, you could make a launcher to do it instead. Right-click on the Desktop and select "Create Launcher..." and fill in the boxes. Either to run your script, or to run your Wine application.

Otherwise, there's an option in the Nautilus Preferences screen to say what you want it to do with executable text files. I don't personally know of any other way to do what you want.

---

### Post by 16november on 2006-11-16
thanks- I created a launcher initially, but it didn't do what I wanted, so I wrote the script. Now I've created a launcher to run the script as an app, and viola!
thanks for guidance.

---

### Post by CatKiller on 2006-11-16
No worries. Glad you got it sorted.

---

